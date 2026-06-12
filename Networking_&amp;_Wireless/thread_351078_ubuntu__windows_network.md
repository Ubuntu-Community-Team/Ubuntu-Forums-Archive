---
title: "ubuntu / windows network"
date: 2007-02-01
forum: Networking &amp; Wireless
---

### Post by farscape on 2007-02-01
Here's my story. I have 2 computers. One dedicated Windows XP PC. And a Dual boot(removable hard drives) WinowsXP and Ubuntu(6.06) PC. When I frist installed Ubuntu, I could see network shared folders and a shared drive(external usb HD) on the XP box from ubuntu. I could transfer files to and from the windows machine. 
Now, I recently changed the workgroup settings in my windows machines from MSHOME to ONE. Why, I just thought it was a good idea to change it from the default setting. Now my Ubuntu box see's a windows network but that's it. It doesn't see any shares. Nothing. Under servers it says Windows Network. I can't go any farther than that. 
Did some searching on how I could make ubuntu join the new workgroup. No luck. Screwed around with smbconfig but I'm locked out. Can't change it. I'm not even sure that will fix it. So i chanced the Windows workgroup back to MSHOME. Same thing. It still doesn't see it. 
How do I fix this? do I reconfigure/reinstall samba? Is there a setting somewhere I'm missing? I'm at a loss here. 

Thanks

Everything else is working great though. :D

---

### Post by farscape on 2007-02-03
Alright. Any good resources for learning samba and what it's all about so I can dig myself out of this hole. Wouldn't hurt to learn it anyway. 
I'm not opting for a reinstall yet. There must be a way to fix this. I'll find it. 
I'll be hunting. 

\\:D/

---

### Post by mmelville3 on 2007-02-03
I am having similar trouble. I have a window XP desktop. I recently installed Ubuntu on my laptop. I was able to set up networking so the two computers could see each other over the network. I was happy. Now it doesn't work and I'm trying to figure out why.

On the windows machine I go to My Network Places>View Workgroup  computers and I get this error popup:

"Workgroup is not accessible. You might not have permission to use this network resource. Contact the administrator of this server to find out if you have access permissions.

The list of servers for this workgroup is not currently available"

On Ubuntu I go to Places>Network Servers>Windows Network and I see nothing.

This was working the other day. And now is not. I'll let you know if I get anywhere with this.

---

### Post by farscape on 2007-02-03
> **mmelville3 said:**
>  I'll let you know if I get anywhere with this.

I'm sure it has something to do with samba.......ummmmmm.......I think. :confused: 
I'll also keep ya posted if I get anywhere with this issue.

I'm starting here:
[http://www.howtoforge.com/samba_setup_ubuntu_5.10]("http://www.howtoforge.com/samba_setup_ubuntu_5.10")
and here
[https://help.ubuntu.com/community/SettingUpSamba]("https://help.ubuntu.com/community/SettingUpSamba")

---

### Post by mmelville3 on 2007-02-03
I have found a solution that works for me. Go to Places>Network Servers>Windows Network. This brings me to smb:///.  This window displays nothing. I change the path to smb://[ip address of the windows machine]. NOTE: 2 slashes, not 3.  I see the shared folders on the windows machine. I am happy again.

To get the [ip address of the windows machine]:

go to start>run
type cmd
in the command window type ipconfig
look for the ip address labeled 'IP Address'
that's the ip address to type in to the path in ubuntu

:D

---

### Post by farscape on 2007-02-04
> **mmelville3 said:**
> I have found a solution that works for me. Go to Places>Network Servers>Windows Network. This brings me to smb:///.  This window displays nothing. I change the path to smb://[ip address of the windows machine]. NOTE: 2 slashes, not 3.  I see the shared folders on the windows machine. I am happy again.

To get the [ip address of the windows machine]:

go to start>run
type cmd
in the command window type ipconfig
look for the ip address labeled 'IP Address'
that's the ip address to type in to the path in ubuntu

:D

HOLY CRAP! IT WORKED! I've been working on this most of the day. Thank you very much!!

---

### Post by mmelville3 on 2007-02-04
Glad I could help. I still can't view the network workgroup from windows but oh well. I don't need to anyway.

---

### Post by BonRouge on 2007-03-06
Not wanting to dig up old posts, but I have the same problem as above. My Windows PCs don't see the Ubuntu one. The Ubuntu one can browse the PCs files OK though. How do I get to see the Ubuntu machine on the Windows network? 

I want to connect printers to the Ubuntu and have the others go through that.

Help would be appreciated.

---

