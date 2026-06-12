---
title: "Large file transfer from Ubuntu machine to Vista machine"
date: 2010-06-29
forum: New to Ubuntu
---

### Post by Lyos on 2010-06-29
I have a directory on my Linux machine (Ubuntu 9.10) that is I'd like to move to machine running Vista to free up some space on the Linux machine.  There are two problems.  1st: file size.  The directory in question is about 40gb and I'm not sure the most efficient way to accomplish this other than using an external HDD as a buffer (which I don't own).  The second is connecting computer's together via a home network is still really cryptic for me, so making a Linux comp talk to a Windows comp is a little outside my current skill.  They don't seem to recognize each other's wireless signal; I don't know which IP address to use; I've tried using an FTP software like FileZilla to connect to IP values I got off of Linux's ifconfig and Window's Ipconfig; this was to no avail.

Any ideas about an efficient, easy to digest way to transfer this much data?  I'm not afraid to learn new things but I'll need some pretty serious direction to do so because my last week of research into the topic has really gotten me no closer to understanding networks :confused:

---

### Post by okplayer02 on 2010-06-30
well first you have to identify the ip address for your linux and windows machine. 

the best way to transfer is via Samba
so if you have them on the same network then you can transfer. So identify that they are both on the same network by finding their ip address. 

[https://help.ubuntu.com/community/SettingUpSamba#SambaServer Configuration - Graphical](https://help.ubuntu.com/community/SettingUpSamba#SambaServer Configuration - Graphical)

you want to find the section called Configuration Graphical as that would be easiest solution for you. 

check this method to set up samba server on your ubuntu machine.

---

### Post by Jakiejake on 2010-06-30
Open one and the machine that the files are on and take out the HDD
Open the other and plug in the Sata or IDE cable from the HDD that you took out into the other machine then drag and drop!

---

### Post by Lyos on 2010-06-30
Well it appears to have worked but not as the Samba tutorial directed.  When I share a folder from the context menu I can see it on the Windows computer but it prompts for a password; using either the Windows or Linux machine login doesn't work.  But if instead I open Samba and tell it to add a directory, the directory shows up in Network Places on the Windows machine and the files are accessible.

So if you need both to be at the same IP address does this mean you must have a router (wireless or otherwise) as a buffer between the two?  Or is there a way to link 2 computers directly through either an ethernet chord or wireless card to wireless card?

And what if both are on a wireless network but don't have the same IP address, or I don't have control over the network's security permissions (e.g., an office or school wireless network)?   Do I have any options for transferring (not sharing) large files over the net in general?

Finally, what does it mean to make a computer a server?  Does this mean that anyone (barring security measures) who is at the same IP address can access/write-to/read-from the computer set up as a server?

> **Jakiejake said:**
> Open one and the machine that the files are on and take out the HDD
Open the other and plug in the Sata or IDE cable from the HDD that you took out into the other machine then drag and drop!

Thanks for the suggestion and that certainly would be simple, but I am trying to learn a bit of networking so I'm trying to avoid direct hardware transfers (e.g., using an external as a transporter or moving HDDs around).  Also, the 2 machines involved are both laptops and only have one SATA input each, so if I understand you correctly this type of transfer would be impossible without an HDD cradle (I have 3 laptops now but still no desktop #-o).  Am I understanding correctly?

---

### Post by okplayer02 on 2010-07-02
well its up to you to give us like a small diagram how your computers at home connect to the internet. did your ISP give you some type of box that all your computers connect thru. Do you know how to find the ip address for your Windows machine at the command prompt: so you click start then run and type cmd then in the black box type the command before
```
ipconfig
``` 


on your  Ubuntu machine click on applications and then accessories find terminal click on it then type the command 
```
ifconfig
```


you have to list the output here so we can help further. its really good idea to learn some basic command line skills you dont have to be an expert.

---

### Post by okplayer02 on 2010-07-02
i suggest you learn basic networking 

so for example on my small network i have 3 pc
192.168.10.4
192.168.10.5
192.168.10.1

all three computers are on the same network due to the 192.168.10. part

the 4th field just identifies each computer or host

here is a simple basic guide for you 
[http://www.comptechdoc.org/os/linux/usersguide/linux_ugbasicnet.html](http://www.comptechdoc.org/os/linux/usersguide/linux_ugbasicnet.html)

there is alot of basic guides out there in the internet its upon you to take a little time and read. it would be difficult to teach that here in a forum.

---

