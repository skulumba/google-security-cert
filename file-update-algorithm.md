
# Algorithm for file updates in Python

### Project Description

This project involves managing access to restricted content within an organization through an allow list of IP addresses stored in a file named "allow_list.txt". 
However, there are instances where certain IP addresses need to be removed from this list, indicating they should no longer have access to the restricted content. 
To automate this process, an algorithm is created to read the "allow_list.txt" file, identify the IP addresses specified for removal in a separate list, 
and then update the file accordingly.This ensures that access to the organization's restricted content remains secure and up-to-date.

##### Open the file that contains the allow list
```python

import_file = "allow_list.txt"
with open("allow_list.txt", "r") as file:

```
- For the initial step of the algorithm, I initialized the import_file variable with the file name "allow_list.txt".
  The **with** keyword ensures proper resource management by automatically closing the file after exiting the with statement.
  In the code with open(import_file, "r") as file:, the open() function takes two parameters. The first parameter specifies the file to be opened, 
  while the second parameter indicates the desired mode of operation, which is "r" for reading in this case.
  Furthermore, the **as** keyword is used to assign the result of the open() function to a variable named **file**. 
  This variable file holds the file object, allowing me to work with its contents within the scope of the with statement.
  
##### Read the file contents
```python
import_file = "allow_list.txt"
with open(import_file, "r") as file:
    ip_addresses = file.read()

print(ip_addresses)
```
-  I applied the .read() method to the file variable defined within the with statement.
   The resulting string output is assigned to the variable ip_addresses.
##### Output
  
![image](https://github.com/skulumba/google-security-cert/assets/75015106/17f40e69-b93e-4fff-8510-8fd99d381a12)

##### Convert the string into a list
```python
import_file = "allow_list.txt"

with open(import_file, "r") as file:
    ip_addresses = file.read()

ip_addresses = ip_addresses.split()

print(ip_addresses)
```
- Here the .split() function operates on the data stored in the variable ip_addresses, which comprises a string of IP addresses separated by whitespace.
  It transforms this string into a list of IP addresses. To store this list, I reassigned it back to the variable ip_addresses.
  
##### Resulting List 

![image](https://github.com/skulumba/google-security-cert/assets/75015106/1c9baa25-66af-4793-8b7e-5d0f5a43907b)

##### Iterate through the remove list
```python
for element in ip_addresses:
    print(element)
```
- The for loop begins with the for keyword, followed by the loop variable element and the in keyword.
  The in keyword signals that the loop should iterate through the sequence ip_addresses and assign each value to the loop variable element.
  This enables the execution of code statements for each element in the sequence.
  
##### Remove IP addresses that are on the remove list
```python
import_file = "allow_list.txt"
remove_list = ["192.168.97.225", "192.168.158.170", "192.168.201.40", "192.168.58.57"]

with open(import_file, "r") as file:
    ip_addresses = file.read()

ip_addresses = ip_addresses.split()

for element in ip_addresses:
    if element in remove_list:
        ip_addresses.remove(element)

print(ip_addresses)
```
- Here we read the contents of a file named "allow_list.txt", splits the content into a list of IP addresses,
  then remove any IP addresses that are present in the remove_list,
  and finally print the resulting list of IP addresses.
  
##### Update the file with the revised list of IP addresses
  
```python
def update_file(import_file, remove_list):
    with open(import_file, "r") as file:
        ip_addresses = file.read()

    ip_addresses = ip_addresses.split()

    for element in ip_addresses:
        if element in remove_list:
            ip_addresses.remove(element)

    ip_addresses = " ".join(ip_addresses)

    with open(import_file, "w") as file:
        file.write(ip_addresses)
)
```
- This function update_file takes two parameters: import_file (the name of the file to update) and remove_list (a list of IP addresses to remove).
  It reads the contents of the file, splits the content into a list of IP addresses,
  removes any IP addresses that are present in the remove_list, converts the resulting list back to a string,
  and then writes the updated string back into the original file.

##### Use function 
```python
def update_file(import_file, remove_list):
    with open(import_file, "r") as file:
        ip_addresses = file.read()

    ip_addresses = ip_addresses.split()

    for element in ip_addresses:
        if element in remove_list:
            ip_addresses.remove(element)

    ip_addresses = " ".join(ip_addresses)

    with open(import_file, "w") as file:
        file.write(ip_addresses)

# Call `update_file()` and pass in "allow_list.txt" and a list of IP addresses to be removed
ip_list = ["192.168.25.60", "192.168.140.81", "192.168.203.198"]
update_file("allow_list.txt", ip_list)

# Read updated file
with open("allow_list.txt", "r") as file:
    text = file.read()

# Display `text`
print(text)
```
- call the update_file function with the file name "allow_list.txt" and a list of IP addresses to be removed
  Then read and print the contents of the updated file

  
- Here we read the contents of a file named "allow_list.txt", split the content into a list of IP addresses,
  remove any IP addresses that are present in the remove_list, 
  convert the resulting list back to a string, and then write the updated string back into the original file.
  
## Summary
I developed an algorithm to eliminate IP addresses specified in a remove_list variable from the "allow_list.txt" file containing approved IP addresses. 
The process began by opening the file, converting its contents into a readable string, and further converting this string into a list stored in the variable ip_addresses.
Subsequently, I iterated through the IP addresses listed in remove_list. During each iteration, I checked if the element existed in the ip_addresses list. 
If it did, I utilized the .remove() method to eliminate the element from ip_addresses.
Following this, I employed the .join() method to revert ip_addresses back to a string. This allowed me to overwrite the contents of the "allow_list.txt" 
file with the updated list of IP addresses.
