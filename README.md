# 2c.SIMULATING ARP /RARP PROTOCOLS
## AIM
To write a python program for simulating ARP protocols using TCP.
## ALGORITHM:
# ARP:
## Client:
1. Start the program
2. Using socket connection is established between client and server.
3. Get the IP address to be converted into MAC address.
4. Send this IP address to server.
5. Server returns the MAC address to client.
## Server:
1. Start the program
2. Accept the socket which is created by the client.
3. Server maintains the table in which IP and corresponding MAC addresses are
stored.
4. Read the IP address which is send by the client.
5. Map the IP address with its MAC address and return the MAC address to client.
# RARP:
## Client:
1. Start the program
2. Using socket connection is established between client and server.
3. Get the MAC address to be converted into IP address.
4. Send this IP address to server.
5. Server returns the IP address to client.
## Server:
1. Start the program
2. Accept the socket which is created by the client.
3. Server maintains the table in which MAC and corresponding IP addresses are
stored.
4. Read the MAC address which is send by the client.
5. Map the MAC address with its IP address and return the IP address to client.
## PROGRAM - ARP:
# Server Side:
```
import socket
s=socket.socket()
s.bind(('localhost',8000))
s.listen(5)
c,addr=s.accept()
address={"165.165.80.80":"6A:08:AA:C2","165.165.79.1":"8A:BC:E3:FA"};
while True:
    ip=c.recv(1024).decode()
    try:
       c.send(address[ip].encode())
    except KeyError:
       c.send("Not Found".encode())
```
# Client Side:
```
import socket
s=socket.socket()
s.connect(('localhost',8000))
while True:
    ip=input("Enter logical Address : ")
    s.send(ip.encode())
    print("MAC Address",s.recv(1024).decode())

```
## OUTPUT - ARP:

<img width="666" height="363" alt="image" src="https://github.com/user-attachments/assets/fa233398-99ab-4c63-90c0-292e47307dc1" />

## PROGRAM - RARP:
# Server Side:
```
import socket
s=socket.socket()
s.bind(('localhost',8000))
s.listen(5)
c,addr=s.accept()
address={"6A:08:AA:C2":"165.165.80.80","10:94:BB:EB:44:34":" 169.254.201.22"};
while True:
    ip=c.recv(1024).decode()
    try:
       c.send(address[ip].encode())
    except KeyError:
       c.send("Not Found".encode())
```
# Client Side:
```
import socket
s=socket.socket()
s.connect(('localhost',8000))
while True:
    ip=input("Enter physical Address : ")
    s.send(ip.encode())
    print("MAC Address",s.recv(1024).decode())

```
## OUPUT -RARP:

<img width="799" height="438" alt="image" src="https://github.com/user-attachments/assets/39f3f5ff-b0f3-4293-9b09-5cd7a5e8832c" />

## RESULT
Thus, the python program for simulating ARP protocols using TCP was successfully 
executed.
