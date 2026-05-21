# 2c.SIMULATING ARP /RARP PROTOCOLS
## AIM
To write a python program for simulating ARP protocols using TCP.
## ALGORITHM:
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
P
## PROGRAM - ARP
client:
```
import socket

s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)

s.connect(("localhost", 8000))

while True:

    ip = input("Enter IP Address: ")

    s.send(ip.encode())

    data = s.recv(1024).decode()

    print("Server Reply:", data)

s.close()
```
server:
```
import socket

server = socket.socket(socket.AF_INET, socket.SOCK_STREAM)

server.bind(("localhost", 8000))
server.listen(1)

print("ARP Server Started...")
print("Waiting for client connection...")

client, addr = server.accept()

print("Connected with:", addr)

address_table = {
    "165.165.80.80": "6A:08:AA:C2",
    "165.165.79.1": "8A:BC:E3:FA",
    "192.168.1.1": "AA:BB:CC:DD"
}

while True:

    ip = client.recv(1024).decode()

    if not ip:
        break

    print("Requested IP:", ip)

    if ip in address_table:
        reply = f"MAC Address for {ip} is {address_table[ip]}"
    else:
        reply = "IP Address Not Found"

    client.send(reply.encode())

client.close()
server.close()
```
## OUTPUT - ARP

<img width="941" height="243" alt="image" src="https://github.com/user-attachments/assets/16612dc7-3612-483b-8293-c44469892a54" />

## PROGRAM - RARP
client:
```

```
server:
```

```
## OUTPUT -RARP
## RESULT
Thus, the python program for simulating ARP protocols using TCP was successfully 
executed.
