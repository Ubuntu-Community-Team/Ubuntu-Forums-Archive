---
title: "How to connect two machines on the network (both ubuntu)"
date: 2008-10-05
forum: Networking &amp; Wireless
---

### Post by erdosain9 on 2008-10-05
Hello. Well, that ... I have two machines with Ubuntu 8.04 and wanted to know how to connect network ... to share the Internet connection (first and foremost) ... and then to share files ...
The modem is connected to the board's internal network of the mother ... and the other computer is connected to another network plate ...
I want to connect them well, without router 

I have no knowledge yet on linux so if you give me a detailed explanation will be grateful ...

Greetings and thanks

translation of google

---

### Post by erdosain9 on 2008-10-05
someone knows how to do it?

---

### Post by Plumtreed on 2008-10-05
You may have to tell us more! Is this a wirelees network? 

I tried this concept but was pursuaded by others on this forum to buy a router/switch for 'networking'. It is more efficient and works better when the printer hangs off one of the machines.I got a cheap router that has 4 wired ports and a wireless facility for my notebook.

---

### Post by erdosain9 on 2008-10-05
is cablemodem. the modem is scientific atlanta series 2100...
I can not afford a router ... I do not mind losing the connection if the machine is turned off ...

---

### Post by Iowan on 2008-10-05
Just to get you started, [here]("https://help.ubuntu.com/community/Internet/ConnectionSharing") is information on connection sharing.  
File sharing has a few options - most involve some additional software.  For Ubuntu-Ubuntu. you could choose NFS, SSHFS, or Samba (actually for Windows networks, but works with Linux boxes, too).  A few more links for you:
[SSHFS]("https://help.ubuntu.com/community/SSHFS")
[NFS]("https://help.ubuntu.com/community/SettingUpNFSHowTo")
[Samba]("https://help.ubuntu.com/community/SettingUpSamba")
[http://ubuntuforums.org/showthread.php?t=202605]("http://ubuntuforums.org/showthread.php?t=202605")

---

### Post by erdosain9 on 2008-10-05
You could put it "in short" because I thought that I do not know much English and I follow complicated ... then with time I would like to learn more but now I just want to ensure "that"

---

### Post by cariboo on 2008-10-05
You can do what you want, quite easily, but you are going to need another network card to make it work. Have a look at this howto:

[http://ubuntuforums.org/showthread.php?t=91370](http://ubuntuforums.org/showthread.php?t=91370)

It should only take a few minutes to get it working if you follow the instructions step by step.

Jim

---

### Post by erdosain9 on 2008-10-06
Hello. thank you very much.


when I start to put the keys (I do not use sudo):
ifconfig ethX ip 
 

gives me this error:

SIOCSIFADDR: Permission Denied
SIOCSIFFLAGS: Permission Denied

what happens?

---

### Post by erdosain9 on 2008-10-06
nobody knows???

---

### Post by erdosain9 on 2008-10-07
¿??¿?¿?¿?¿?¿?

---

