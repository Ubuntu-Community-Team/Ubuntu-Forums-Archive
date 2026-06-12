---
title: "Using STunnel with TCP Server+Client"
date: 2011-02-02
forum: New to Ubuntu
---

### Post by longphant on 2011-02-02
I have a TCP Server/Client where the Server listens on port 5000 and the Client outgoing port is 39000. 

I have Stunnel set up on the Server:
```

[custom]
accept  = 6000
connect = 5000
```... so it accepts connections on port 6000 and redirects it to 5000 (which my Server.c is listening on).

I tried to set up STunnel on the Client in the following way:

```
[custom_cl]
accept = 39000
connect = 192.168.1.3:6000
```...so it accepts any data from port 39000 and sends it to the Server (let's say it's at 192.168.1.3) at port 6000.

My client has this code:

    ```
client_addr.sin_family = AF_INET;
    client_addr.sin_port = htons(39000);
    client_addr.sin_addr.s_addr = inet_addr("0.0.0.0");
    bzero(&(client_addr.sin_zero),8);
    
    if (bind(sock, (struct sockaddr *)&client_addr, sizeof(struct sockaddr))
                                                                   == -1) {
         perror("Unable to bind");
         exit(1);
         }
```...so that it will always send out on port 39000. My problem is that I receive an "Unable to bind: Address already in use" because (I'm guessing) STunnel is listening on port 39000. What should I be doing?

---

### Post by gmargo on 2011-02-02
A TCP client uses **connect(2)**, not **bind(2)**.  The server uses **bind(2)**.

Good examples:
[http://www.prasannatech.net/2008/07/socket-programming-tutorial.html](http://www.prasannatech.net/2008/07/socket-programming-tutorial.html)
[http://www.pythonprasanna.com/Papers%20and%20Articles/Sockets/tcpserver.c](http://www.pythonprasanna.com/Papers%20and%20Articles/Sockets/tcpserver.c)
[http://www.pythonprasanna.com/Papers%20and%20Articles/Sockets/tcpclient.c](http://www.pythonprasanna.com/Papers%20and%20Articles/Sockets/tcpclient.c)

---

