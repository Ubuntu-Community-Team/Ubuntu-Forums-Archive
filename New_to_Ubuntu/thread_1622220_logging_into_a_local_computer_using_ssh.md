---
title: "logging into a local computer using ssh"
date: 2010-11-15
forum: New to Ubuntu
---

### Post by Mick8882003 on 2010-11-15
I am trying to log into a, local, computer using ssh. But I am getting a connection error "unable to connect"

any help would be appreciated. 

Mick

edit heres the atcual error message:

ssh: connect to host 192.168.0.50 port 22: Connection refused
rsync: connection unexpectedly closed (0 bytes received so far) [Receiver]
rsync error: unexplained error (code 255) at io.c(601) [Receiver=3.0.7]

---

### Post by ayenack on 2010-11-15
Hello Mick8882003.

Does the ssh-server machine have a static IP?

Can you be more specific about the problem?

Did you set up a custom port for ssh to listen on?
Did you set up keys?

As much info as possible.

---

### Post by Mick8882003 on 2010-11-15
> **ayenack said:**
> Hello Mick8882003.

Does the ssh-server machine have a static IP?

Can you be more specific about the problem?

Did you set up a custom port for ssh to listen on?
Did you set up keys?

As much info as possible.

all computers have static ip's
its a local network, a router and some wireless comp's
no, port 22
keys, well I have set up something in the past that allowed me to do a script in one go using one password...

not sure if this is helpful.

Mick

---

### Post by ayenack on 2010-11-15
Have you allowed ssh in the firewall on the server machine?

If not try this on the server.

**Sudo ufw status** (This will let you know if ufw is running.)

If it's enabled type this.

**sudo ufw allow 22** (This will allow connections on port 22 (ssh).)

Reboot the server and try again.

If ufw is not running you enable it by typing. Be careful though as it may block other services you have set up on the server.

**sudo ufw enable** (UFW ([Uncomplicated Firewall]("https://help.ubuntu.com/community/UFW")).)

---

### Post by CharlesA on 2010-11-15
Is openssh-server installed on the machine you are trying to connect to?

---

### Post by Mick8882003 on 2010-11-15
mickpc@mickpc-G41MT-ES2L:~$ sudo ufw status
[sudo] password for mickpc: 
Status: inactive

Mick

---

### Post by CharlesA on 2010-11-15
Could you physically log into the machine you are trying to connect to and run this please:

```
netstat -ln
```

Post it please.

---

### Post by Mick8882003 on 2010-11-15
netstat -ln
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 0.0.0.0:5298            0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN     
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN     
tcp6       0      0 :::5298                 :::*                    LISTEN     
tcp6       0      0 :::22                   :::*                    LISTEN     
tcp6       0      0 ::1:631                 :::*                    LISTEN     
udp        0      0 0.0.0.0:5353            0.0.0.0:*                          
udp        0      0 0.0.0.0:36265           0.0.0.0:*                          
udp        0      0 0.0.0.0:68              0.0.0.0:*                          
udp6       0      0 :::5353                 :::*                               
udp6       0      0 :::39974                :::*                               
Active UNIX domain sockets (only servers)
Proto RefCnt Flags       Type       State         I-Node   Path
unix  2      [ ACC ]     STREAM     LISTENING     8705     /var/run/cups/cups.sock
unix  2      [ ACC ]     STREAM     LISTENING     8730     /tmp/.X11-unix/X0
unix  2      [ ACC ]     STREAM     LISTENING     11184    /tmp/ssh-XnqZky1445/agent.1445
unix  2      [ ACC ]     STREAM     LISTENING     11224    /tmp/.ICE-unix/1445
unix  2      [ ACC ]     STREAM     LISTENING     11265    /tmp/orbit-mickpc/linc-5cc-0-682e85a900da
unix  2      [ ACC ]     STREAM     LISTENING     11521    /tmp/orbit-mickpc/linc-5a5-0-5d1db6e893edd
unix  2      [ ACC ]     STREAM     LISTENING     11718    /tmp/keyring-otZTHh/pkcs11
unix  2      [ ACC ]     STREAM     LISTENING     14392    /tmp/orbit-mickpc/linc-68c-0-12ae3d3b786b7
unix  2      [ ACC ]     STREAM     LISTENING     15521    /tmp/orbit-mickpc/linc-6cd-0-29309e5378543
unix  2      [ ACC ]     STREAM     LISTENING     10938    /tmp/keyring-otZTHh/control
unix  2      [ ACC ]     STREAM     LISTENING     11724    /tmp/keyring-otZTHh/ssh
unix  2      [ ACC ]     STREAM     LISTENING     11746    /tmp/orbit-mickpc/linc-5d3-0-27bb12eecd032
unix  2      [ ACC ]     STREAM     LISTENING     11764    /tmp/orbit-mickpc/linc-5cf-0-1b92cbbace89a
unix  2      [ ACC ]     STREAM     LISTENING     13410    /tmp/orbit-mickpc/linc-65c-0-342ee2cfa0f29
unix  2      [ ACC ]     STREAM     LISTENING     12270    /tmp/orbit-mickpc/linc-5e9-0-3f9bfd2579b20
unix  2      [ ACC ]     STREAM     LISTENING     12337    /tmp/orbit-mickpc/linc-5e7-0-72a48c2b80f0d
unix  2      [ ACC ]     STREAM     LISTENING     12336    /tmp/orbit-mickpc/linc-5e6-0-7ff3de6f80f05
unix  2      [ ACC ]     STREAM     LISTENING     12390    /tmp/orbit-mickpc/linc-5ec-0-719942a499e63
unix  2      [ ACC ]     STREAM     LISTENING     12459    /tmp/orbit-mickpc/linc-61c-0-2a973fc8b205d
unix  2      [ ACC ]     STREAM     LISTENING     12517    /tmp/orbit-mickpc/linc-620-0-508d5dfbc8c8
unix  2      [ ACC ]     STREAM     LISTENING     12668    /tmp/orbit-mickpc/linc-624-0-6ca5800ac5523
unix  2      [ ACC ]     STREAM     LISTENING     12728    /tmp/orbit-mickpc/linc-5eb-0-64881c6ff1d05
unix  2      [ ACC ]     STREAM     LISTENING     12738    /tmp/orbit-mickpc/linc-62e-0-4dd0c9bf183
unix  2      [ ACC ]     STREAM     LISTENING     12742    /tmp/orbit-mickpc/linc-62f-0-6382b07e26f
unix  2      [ ACC ]     STREAM     LISTENING     12875    /tmp/orbit-mickpc/linc-644-0-7e5a13a032330
unix  2      [ ACC ]     STREAM     LISTENING     12904    /tmp/.esd-1000/socket
unix  2      [ ACC ]     STREAM     LISTENING     12908    /home/mickpc/.pulse/5d8897ca62462324662a54ed00000006-runtime/native
unix  2      [ ACC ]     STREAM     LISTENING     12980    /tmp/orbit-mickpc/linc-64c-0-35e466153ed74
unix  2      [ ACC ]     STREAM     LISTENING     13428    /tmp/orbit-mickpc/linc-659-0-161f6fd6a3b60
unix  2      [ ACC ]     STREAM     LISTENING     13445    /tmp/orbit-mickpc/linc-660-0-3c8a6d0ba549e
unix  2      [ ACC ]     STREAM     LISTENING     13490    /tmp/orbit-mickpc/linc-663-0-15744e18aa54c
unix  2      [ ACC ]     STREAM     LISTENING     13500    /tmp/orbit-mickpc/linc-664-0-43c379e7aacf7
unix  2      [ ACC ]     STREAM     LISTENING     13512    /tmp/orbit-mickpc/linc-65f-0-549f5f52ac162
unix  2      [ ACC ]     STREAM     LISTENING     13706    /tmp/orbit-mickpc/linc-67c-0-5cd6b6dc4725f
unix  2      [ ACC ]     STREAM     LISTENING     13844    /tmp/orbit-mickpc/linc-67a-0-2318fde25dfaa
unix  2      [ ACC ]     STREAM     LISTENING     13998    /tmp/orbit-mickpc/linc-682-0-71bb10b0235e5
unix  2      [ ACC ]     STREAM     LISTENING     6081     @/com/ubuntu/upstart
unix  2      [ ACC ]     STREAM     LISTENING     322340   /tmp/orbit-mickpc/linc-6bc-0-2f3dff632cd66
unix  2      [ ACC ]     STREAM     LISTENING     17473    /tmp/orbit-mickpc/linc-6fe-0-25ddb33b2c4a3
unix  2      [ ACC ]     STREAM     LISTENING     532807   /tmp/orbit-mickpc/linc-17ad-0-55870af1970e8
unix  2      [ ACC ]     STREAM     LISTENING     753841   /tmp/orbit-mickpc/linc-1c3a-0-3ffbe8a1ed847
unix  2      [ ACC ]     STREAM     LISTENING     107806   /tmp/orbit-mickpc/linc-84f-0-7e4e59cfd5db4
unix  2      [ ACC ]     STREAM     LISTENING     8729     @/tmp/.X11-unix/X0
unix  2      [ ACC ]     STREAM     LISTENING     9481     @/tmp/gdm-greeter-tYzcBVWR
unix  2      [ ACC ]     STREAM     LISTENING     7272     /var/run/dbus/system_bus_socket
unix  2      [ ACC ]     STREAM     LISTENING     11197    @/tmp/dbus-9uStCPDAE5
unix  2      [ ACC ]     STREAM     LISTENING     9623     @/tmp/gdm-session-JiGGyFSc
unix  2      [ ACC ]     STREAM     LISTENING     7345     /var/run/avahi-daemon/socket
unix  2      [ ACC ]     STREAM     LISTENING     7642     /var/run/acpid.socket
unix  2      [ ACC ]     STREAM     LISTENING     11223    @/tmp/.ICE-unix/1445
mickpc@mickpc-G41MT-ES2L:~$

---

### Post by ayenack on 2010-11-15
**NOTE:- Forget about this post you posted the above as I was typing this.**

OK. Have you got any other services running on the server?

FTP, SAMBA, are you sharing internet connection through it or anything like that, or is it just an ssh server at the moment?

---

### Post by Mick8882003 on 2010-11-15
No other services (i think) just trying to backup some programs to the (local) server.

Mick

---

### Post by ayenack on 2010-11-15
OK can you enable ufw on the server. Like this.

**sudo ufw enable**

Then.

**sudo ufw allow 22**

Reboot the server and try to log in again.

---

### Post by Mick8882003 on 2010-11-15
Still getting port 22 closed.

Mick

---

### Post by ayenack on 2010-11-15
> **Mick8882003 said:**
> Still getting port 22 closed.

Mick

EMmm.

Do you mean you the connection is still being denied or that 22 is closed?

Did you follow any guides when you installed the server also can you ping the server.

To ping open a terminal and do this.

**ping 192.168.0.50 -c5** (Do this from outside the server.)

---

### Post by Mick8882003 on 2010-11-15
when i do namp 192.168.0.* port 22 comes up closed.

Mick

---

### Post by ayenack on 2010-11-15
Try pinging the server from a client machine.

In terminal.

**ping 192.168.0.50 -c5**

---

