---
title: "[SOLVED] openvpn init script?"
date: 2008-08-21
forum: Networking &amp; Wireless
---

### Post by LRT on 2008-08-21
i got openvpn working but i'm not sure how to run it in the background.

```

# /etc/init.d/openvpn restart
* Stopping virtual private network daemon.       [OK]
* Starting virtual private network daemon.       [OK]
```

when i try to connect from a client it will fail.

only when i execute this command will the client connect successfully...

```
# openvpn /etc/openvpn/2.0/keys/server.conf
```

anyone know how i can fix this? do i need to create/modify an init script?

---

### Post by SpaceTeddy on 2008-08-22
the start/stop script of openvpn of ubuntu will search *.conf files in your /etc/openvpn and start them. Your config file is in /etc/openvpn/2.0/keys/ (why ever you would put a server config in a key directory...)

anyway, move the server.conf to /etc/openvpn and the start/stop script will work. 

hope it helps :)

---

### Post by LRT on 2008-08-22
first off, thanks for your reply.

when i put server.conf in /etc/openvpn/ and execute /etc/init.d/openvpn restart, it fails. it says "server (FAILED)". 

```
 * Stopping virtual private network daemon.       [ OK ]
 * Starting virtual private network daemon.       
 * server (FAILED)
                                                  [ OK ]
```

and ...

```

# openvpn /etc/openvpn/server.conf
Fri Aug 22 09:59:43 2008 OpenVPN 2.1_rc7 x86_64-pc-linux-gnu [SSL] [LZO2] [EPOLL] built on Jun 11 2008
Fri Aug 22 09:59:43 2008 Cannot open dh1024.pem for DH parameters: error:02001002:system library:fopen:No such file or directory: error:2006D080:BIO routines:BIO_new_file:no such file
Fri Aug 22 09:59:43 2008 Exiting
```

my keys are in /etc/openvpn/2.0/keys

the only way i can get my client to connect is if i put server.conf in /etc/openvpn/2.0/keys/ and execute `openvpn /etc/openvpn/2.0/keys/server.conf`

---

### Post by LRT on 2008-08-22
the only way i figured out how to fix this is to put server.conf in the same directory as the key files (/etc/openvpn/2.0/keys/). and then modify CONFIG_DIR in the init script (/etc/init.d/openvpn) to CONFIG_DIR=/etc/openvpn/2.0/keys

specifying an alternate location for the key files in server.conf like so,

ca /etc/openvpn/2.0/keys/ca.crt
cert /etc/openvpn/2.0/keys/server.crt
key /etc/openvpn/2.0/keys/server.key

so that i can put the server.conf file somewhere else produces the "file not found" errors i posted above.

---

### Post by SpaceTeddy on 2008-08-22
it cannot find the dh2048.pem... 
make sure that the path in your server.conf are correct. I'd say you need to use the absolute path to the files (i.e. instead of dh2048.pem you should use /etc/openvpn/easy-rsa/keys/dh2048.pem). 
Since you are now running it from a different directory, the openvpn exectuable cannot find these files anymore in the relative directory structure... 
make sure you change all path (do the dh, key, ca and crt) to absolute path

hope it helps :)

---

### Post by LRT on 2008-08-25
my server.conf file is sitting in /etc/openvpn/2.0/

the lines for my key files look like this:

ca /etc/openvpn/2.0/keys/ca.crt
cert /etc/openvpn/2.0/keys/server.crt
key /etc/openvpn/2.0/keys/server.key

and that is exactly where the key files are located.

CONFIG_DIR in the init script (/etc/init.d/openvpn) looks like this:
 
CONFIG_DIR=/etc/openvpn/2.0/

when i try to start the server (/etc/init.d/openvpn restart) it fails!

there may be a problem with the way i'm specifying the full path to the key files in server.conf

---

### Post by LRT on 2008-08-25
SpaceTeddy,

i didn't read your last post carefully.

you are correct, it couldn't find my dh1024.pem file because i didn't specify its correct path in server.conf. i fixed this now. thanks for your help!

---

