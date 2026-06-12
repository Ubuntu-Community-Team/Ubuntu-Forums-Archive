---
title: "Please help with samba setup"
date: 2008-02-29
forum: Networking &amp; Wireless
---

### Post by mr tim esquire on 2008-02-29
I cant for the life of me get samba working at all.  I have ubuntu server running on the machine with all my data, i want to access this from Win XP machine.  Both are connected to a Linksys BEFSR81 router. Below is my smb.conf file.
My login name for the windows machine is 'user' and has no password.
On the ubuntu server i have done (using the same passwords for UNIX and SMB):
```

# useradd -d /home/user -s /bin/false -n user
# sudo passwd user
Enter new UNIX password:*******
Retype new UNIX password:*******
passwd: password updated sucessfully
# sudo smbpasswd -a user
new SMB password: *******

```
I am not allowed to enter a blank password for 'user' in UNIX!

When i try to access \\thefarm\stuff with user ******* i get the error
NETWORK ACCESS IS DENIED!

Any suggestions?
What am i doing wrong?
```

[global]
   workgroup = MOUSENET
   netbios name = thefarm
[stuff]
   path = /media/sdb1
   browsable = yes
   guest ok = yes
   write list = user

```

---

### Post by Iowan on 2008-02-29
The path to **stuff** looks odd - but probably not the issue.

---

### Post by mr tim esquire on 2008-02-29
Made a mistake copying form the config file it is as the same now.
The PC with Windows also has ubuntu installed i have the same access problems trying to browse to the share in ubuntu, which suggests there is a problem with the login?

---

### Post by mr tim esquire on 2008-02-29
is there any other way to share these files?  i'm really sick of samba.

---

### Post by tad1073 on 2008-02-29
Have a look at [this](http://ubuntuforums.org/showthread.php?t=678868&page=6).

did you enable the user:
```

sudo smbpasswd -L -a UBUNTU_USERNAME
sudo smbpasswd -L -e UBUNTU_USERNAME

```

---

### Post by mr tim esquire on 2008-02-29
ok i enabled the user 'user' and i still cant get access from Win or ubuntu Network browsers
Any more ideas?

---

### Post by tad1073 on 2008-02-29
> **mr tim esquire said:**
> ok i enabled the user 'user' and i still cant get access from Win or ubuntu Network browsers
Any more ideas?

Sorry, but I don't. I fixed my problem by doing a clean install of ubuntu. Everything worked out of the box after I did that, but I am sure you don't want to do that. By the way, are you behind a firewall other than iptables? My problem was with firestarter, a gui for iptables.

---

### Post by mr tim esquire on 2008-02-29
OK i have found a problem 
Both machines have static IPs
I can ping the server fine from my workbench comp
but when i ssh into the server i cannot ping the worbench comp
Any ideas why this might be?
should i foward somthing on the router?
thanks
tim

---

### Post by Iowan on 2008-03-03
What are the static IP's? Are they in the same subnet?
Ping by name, IP address or both?

BTW, it's possible to set up user without password - I'll see if I can find the link - saw it earlier tonight.

Not the one I was looking for, but [here]("http://ubuntuforums.org/showthread.php?t=710144&highlight=samba+null+password") is one to check.
[Another one.]("http://ubuntuforums.org/showthread.php?t=710599&highlight=samba+null+password")

---

### Post by jonandrews on 2008-03-04
I've put a step by step guide to networking Ubuntu / XP on a website:

[http://www.europe.eclipse.co.uk/Ubuntu/](http://www.europe.eclipse.co.uk/Ubuntu/)

See if that can help.

---

