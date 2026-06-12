---
title: "Noob Non-Techie: Connecting to my Network"
date: 2008-06-11
forum: Networking &amp; Wireless
---

### Post by mpschenck on 2008-06-11
Let me start by saying that I've only had about 6 hours experience with Ubuntu 8.04 in the last 2 days.  I switch my XP desktop over last night.  I read the forums and have managed to copy posted code so that Evolution will work through my Hotmail account.  

Now that you know just how inexperienced that I am let me present my next problem.

I have a home network with the new Ubuntu PC, a Vista laptop, and my wife's XP PC.  I'm using a Linksys WRT54GS router and I have a Linksys NAS200 hooked up to the router.  I don't know [read: too inexperienced] to set Ubuntu up to connect to the router.  Now I can get on the internet fine, everytime no problem. 

What I'm looking at is a box that reads "Connect to 802.1x protected wired network"

Network Name: (which I have entered) MayyS-Network
EAP Method: my choices...PEAP, TLS, or TTLS
Phase2 Type: choises...None (Default), PAP, MSCHAP, MSCHAPV2, or GTC
Identy: blank and don't know what goes here
Password: blank and don't know what goes here
Anonymous Identity: blank and don't know what goes here
Client Certificate File: opens a folder
CA Certificate File: opens a folder
Private Key File: opens a folder
Private Key Password: blank and don't know what goes here

I assume that these items come from information about my network and/or router, but I have no idea where to get the info. 

Any help would be greatly appreciated and anyone needs more info to be able to help just let me know. 

Thanks in advance

---

### Post by chewearn on 2008-06-11
> **mpschenck said:**
> I have a home network with the new Ubuntu PC, a Vista laptop, and my wife's XP PC.  I'm using a Linksys WRT54GS router and I have a Linksys NAS200 hooked up to the router.  I don't know [read: too inexperienced] to set Ubuntu up to connect to the router.  Now I can get on the internet fine, everytime no problem. 


Since you can get on the internet fine, no problem; then what is the problem?  I'm not sure what you are asking, and why you need to make the settings below:

> 
What I'm looking at is a box that reads "Connect to 802.1x protected wired network"

Network Name: (which I have entered) MayyS-Network
EAP Method: my choices...PEAP, TLS, or TTLS
Phase2 Type: choises...None (Default), PAP, MSCHAP, MSCHAPV2, or GTC
Identy: blank and don't know what goes here
Password: blank and don't know what goes here
Anonymous Identity: blank and don't know what goes here
Client Certificate File: opens a folder
CA Certificate File: opens a folder
Private Key File: opens a folder
Private Key Password: blank and don't know what goes here

* ...edit...*

---

### Post by mpschenck on 2008-06-12
I have files on the Linksys NAS200 I would need to get off, movies, pictures and stuff.  Its my back-up drive.

---

### Post by chewearn on 2008-06-12
Ok, in this case, it has nothing to do with the settings.

Here are a couple of things to check, in random order.  Please try them and post the results, or describe the error exactly (error messages will be helpful).


1. Some routers have to a setting that needs to be turned on, in order than devices connected to the router's ports can see each other.  Go into the router web interface and find out.

2. Most likely, NAS is sharing via Windows SMB.  If you browse from "Places > Network" in Ubuntu, can you see the NAS?

3. Can you ping the NAS?  Open a terminal and run:
```
ping <ipaddr>
```

Where <ipaddr> is the ip address of the NAS.  Press CTRL+C to end the ping.

.

---

### Post by mpschenck on 2008-06-12
> **AstalaVista said:**
> 
1. Some routers have to a setting that needs to be turned on, in order than devices connected to the router's ports can see each other.  Go into the router web interface and find out.

2. Most likely, NAS is sharing via Windows SMB.  If you browse from "Places > Network" in Ubuntu, can you see the NAS?

3. Can you ping the NAS?  Open a terminal and run:
```
ping <ipaddr>
```

Where <ipaddr> is the ip address of the NAS.  Press CTRL+C to end the ping.
.

1. Ok, I logged into the router and didn't find any thing that needed to be turned on.  I don't really know what what I'm looking for though.  Besides everything else on the network can see each other.

2 In "Places > Network" there is an icon "Windows Network". If I click that I get an icon "Workgroup". Clicking get me to an icon "mpsnetwork", which is the NAS200 drive I'm trying to get to. When I click the icon Ubuntu gives me the working curser for 20-30 seconds and then nothing.  There is a little box at the top pf the window that reads "Windows shares on mpsnetwork".  I should mention that when I do this the network drive (NAS200) disappears for the the Network screen on my Vista laptop, and while its annoying that I have to restart the laptop for it to show up there again, that is not a concern. 

3. When I ping the NAS200 this is what I get...

```
 mpschenck@mpschenck-desktop:~$ ping 192.168.1.100
PING 192.168.1.100 (192.168.1.100) 56(84) bytes of data.
64 bytes from 192.168.1.100: icmp_seq=1 ttl=64 time=0.347 ms
64 bytes from 192.168.1.100: icmp_seq=2 ttl=64 time=0.267 ms
64 bytes from 192.168.1.100: icmp_seq=3 ttl=64 time=0.262 ms
64 bytes from 192.168.1.100: icmp_seq=4 ttl=64 time=0.264 ms
64 bytes from 192.168.1.100: icmp_seq=5 ttl=64 time=0.254 ms
64 bytes from 192.168.1.100: icmp_seq=6 ttl=64 time=0.230 ms
64 bytes from 192.168.1.100: icmp_seq=7 ttl=64 time=0.250 ms
64 bytes from 192.168.1.100: icmp_seq=8 ttl=64 time=0.254 ms
64 bytes from 192.168.1.100: icmp_seq=9 ttl=64 time=0.255 ms

--- 192.168.1.100 ping statistics ---
9 packets transmitted, 9 received, 0% packet loss, time 7999ms
rtt min/avg/max/mdev = 0.230/0.264/0.347/0.036 ms
mpschenck@mpschenck-desktop:~$ 
 
```


Does this help?  All the files on the drive came from an XP machine.  Does that matter?  I guess the drive was formatted with the Fat32 (I think that's what it called) file system. Daoes that matter?

---

### Post by chewearn on 2008-06-12
Ok, clearer now.  I have seen users complaining about accessing windows share via the Places Network.  It's not working, or unstable.  Whether it's ubuntu issue, or something else, I'm not sure.


However, regardless of the issue, the second thing to try is use the menu
Places > Connect to Server


This will open a dialog box:

1. Service type dropdown, select: Windows share

2. Server: <ipaddr>
From your ping command, I see it's 192.168.1.100

3. Folder: <the shared path>
This one is tricky, you need to enter in the exact path according to the NAS else it won't work; it could be something like /shared/public, or /public, or /user/public. 

4. User name: <username>
As defined in the NAS, not your ubuntu username

5. Domain name
Usually can be left blank


After you click [Connect] button, it doesn't really connect (I know, that retarded).  Find the shortcut in the Places menu (or possibly on the Desktop) and click it again.


By the way, is this the product?
[http://www.linksys.com/servlet/Satellite?c=L_Product_C2&childpagename=US%2FLayout&cid=1175233152539&pagename=Linksys%2FCommon%2FVisitorWrapper]("http://www.linksys.com/servlet/Satellite?c=L_Product_C2&childpagename=US%2FLayout&cid=1175233152539&pagename=Linksys%2FCommon%2FVisitorWrapper")

.

---

### Post by mpschenck on 2008-06-13
This is what worked...


Places > Connect to Server

1. Service type: Windows share

2. Server: 192.168.1.100

3. Folder: /public disc 1

4. no user name

5. no domain name

Found the shortcut in the Places menu and my files were there!

> **AstalaVista said:**
> 
By the way, is this the product?
[http://www.linksys.com/servlet/Satellite?c=L_Product_C2&childpagename=US%2FLayout&cid=1175233152539&pagename=Linksys%2FCommon%2FVisitorWrapper]("http://www.linksys.com/servlet/Satellite?c=L_Product_C2&childpagename=US%2FLayout&cid=1175233152539&pagename=Linksys%2FCommon%2FVisitorWrapper")


Yes, thats the one.  I dropped a Western Digital 500gb 3gb/SATA drive in it.

Total $250 after tax.  It will also accept another drive the same size.

Thanks, AstalaVista!

---

### Post by chewearn on 2008-06-13
Great!  Please mark thread as solved, thanks.

---

### Post by mpschenck on 2008-06-14
> **mpschenck said:**
> 
Found the shortcut in the Places menu and my files were there!



Well they were there.  I was copying some pictures over to this computer (Ubuntu) and during the transfer my network "crashed".,   I even got kicked out of Warhawk (PS3).  Off the internet on every computer attached to the router. I had some error message on the computer screen and my Public Disc 1 shortcut was gone.  So I tried the above connection method again after rebooting my router and now I get this error... 

Can't display location "smb://192.168.1.100/public%20disc%201/"

Some of the files I was transferring made it across, But I don't know what happened.  Did I screw something up?

---

