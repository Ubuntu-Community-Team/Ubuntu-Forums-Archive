---
title: "Connecting to BASH remotely"
date: 2010-04-25
forum: New to Ubuntu
---

### Post by maxmouse24 on 2010-04-25
I can connect to my computer through tightvnc but this brings up the whole desktop. I really just need the shell so I can run a few programs. how do I remote in and just get the shell?

Ubunto 9.10

---

### Post by mk1w86 on 2010-04-25
You can do this using SSH, you will have to install the SSH server on the computer you are connecting  to first by running:

```
sudo aptititude install ssh
```

If you are connecting from a Linux client you then run:

```
ssh username@serverip
```

on the client. ;)

If you are connecting from a Windows client you can use Putty:

[http://www.chiark.greenend.org.uk/~sgtatham/putty/](http://www.chiark.greenend.org.uk/~sgtatham/putty/)

---

### Post by thulefoth on 2010-04-25
There is a nice excerpt from a book on Techotopia about mk1w86's suggestion, quite a bit of detail.

[Configuring Ubuntu Linux Remote Access using SSH]("http://www.techotopia.com/index.php/Configuring_Ubuntu_Linux_Remote_Access_using_SSH")

---

### Post by maxmouse24 on 2010-04-25
Thank you 
I do have one more question. When I log in this way does a screen pop up on the server computer or is this in the background? I am wanting to access one of my employees computers and run some scripts in the background.

---

### Post by jrothwell97 on 2010-04-25
It will be in the background, since it's handled by another console.

That said, the talk of you wanting to ssh into one of your employees' computers and run some scripts in the background makes me slightly suspicious. This isn't the MI5 technical division. :P

---

### Post by maxmouse24 on 2010-04-25
still confused. I ran the server app and it is installed.

I go to my remote terminal and type ssh username@ipaddress 
nothing happens

---

### Post by mk1w86 on 2010-04-25
Check if the SSH daemon is running on the server by running:

```
sudo /etc/init.d/ssh start
```

Can you ping the server?

Also, just to make sure, have you replaced username and serverip in the SSH command with your details? :-s

---

### Post by maxmouse24 on 2010-04-25
I have started the ssh on the server

now do I just open terminal and type in the 

ssh username@ipaddress

username-the users name that I am using
Ip address of the computer as found in the remote desktop settings?

or do I need to use a seperate program on the client computer. both are running Ubuntu 9.10

---

### Post by mk1w86 on 2010-04-25
> **maxmouse24 said:**
> I have started the ssh on the server

now do I just open terminal and type in the 

ssh username@ipaddress

username-the users name that I am using
Ip address of the computer as found in the remote desktop settings?

Username is the account you are logging in to on the server.  You can find the server IP address by running:

```
ifconfig
```

on the server.

> or do I need to use a seperate program on the client computer. both are running Ubuntu 9.10

You can but it shouldn't be necessary, the normal SSH client on Ubuntu should be fine.

---

### Post by maxmouse24 on 2010-04-25
I get 3 diff ip addresses when I connect like that

none of them are the one that I vnc into.

when I type in the information it just blinks at me and does nothing

---

### Post by mk1w86 on 2010-04-25
> **maxmouse24 said:**
> I get 3 diff ip addresses when I connect like that

none of them are the one that I vnc into.

when I type in the information it just blinks at me and does nothing

Could you please post the output of:

```
ifconfig
```

on the server (the machine you are trying to use remotely) and on the client.

---

### Post by maxmouse24 on 2010-04-25
this is the client computer 

eth0      Link encap:Ethernet  HWaddr 00:0e:a6:59:79:bd  
          inet addr:70.142.40.171  Bcast:70.142.40.255  Mask:255.255.255.0
          inet6 addr: fe80::20e:a6ff:fe59:79bd/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:759173 errors:0 dropped:0 overruns:0 frame:0
          TX packets:676052 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:401045555 (401.0 MB)  TX bytes:98697697 (98.6 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:259 errors:0 dropped:0 overruns:0 frame:0
          TX packets:259 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:62491 (62.4 KB)  TX bytes:62491 (62.4 KB)

---

### Post by maxmouse24 on 2010-04-25
this is the server output

eth0      Link encap:Ethernet  HWaddr 00:1f:16:51:9a:fc  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:26 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet  addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:23:4e:47:43:a8  
          inet addr:192.168.2.104  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr:  fe80::223:4eff:fe47:43a8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:405394 errors:0 dropped:0 overruns:0 frame:0
          TX packets:443634 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:73920413 (73.9 MB)  TX bytes:128415202 (128.4 MB)

---

### Post by mk1w86 on 2010-04-25
Are the client and server on the same local network or are you trying to connect to the server over the internet?

---

### Post by maxmouse24 on 2010-04-25
over the internet

trying to remote into the server computer.

---

### Post by tom.swartz07 on 2010-04-25
> **maxmouse24 said:**
> over the internet

trying to remote into the server computer.

That'll do it!
You need to configure port forwarding for the computer. This usually involves getting the IP of the router and configuring the router to forward port 22 to the computer in question.

Normally its not too much of a problem, but if you dont have physical access to the router it can be harder.

1) you need to change the port forwarding on the router to point port 22 to the intended computer you want to connect to.
2) you need to verify that the ip address of the router wont change; usually you could register the router with DYNDNS to make sure that you always have the most up to date IP, DYNDNS also allows you to pick a name for the ip- rather than 72.128.34.1 you just have to type 'thenameipickedhere.com' into the ssh command.
3) ssh in using ```
ssh name@remoteipaddress
```
4) PROFIT!

---

### Post by mk1w86 on 2010-04-25
You will need to open the correct ports on the routers that connect both machines to the internet.

For more information on setting up SSH have a look here:

[https://help.ubuntu.com/community/SSH](https://help.ubuntu.com/community/SSH)

You might be interested in setting up key authentication instead of using normal password logins and using a port other than the standard 22 over the internet.

---

### Post by dfreer on 2010-04-25
Also note: When you successfully log into a remote machine, you'll be greeted with a very similiar bash prompt to what you are using. It may be that you logged in but didn't notice the change (should say something like "john@remotecomputername $" instead of "john@localcomputername $").

---

