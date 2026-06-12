---
title: "su not taking root password"
date: 2011-04-21
forum: New to Ubuntu
---

### Post by honey_bee on 2011-04-21
I am new in UBUNTU 10.10 and I want to use teh root account to assign static IP address to my ububtu linux. In the terminal windows when i write 
[PHP]$su
password:
authentication failure[/PHP]

i gave the password but no success

Kindly help me.I want to assign IP address 

thansk

---

### Post by Elfy on 2011-04-21
su is disabled in ubuntu

You can use sudo

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by leviathan8 on 2011-04-21
You can try instead 'sudo su'.

---

### Post by computerandu on 2011-04-21
Ubuntu prefers sudo command...

if you still want to be super user ...yous can use 

**sudo su **

enter the same password as for sudo command...u r a root user now...:P

---

### Post by spikoley on 2011-04-21
And use *gksudo* for graphical applications.

---

### Post by andymorton on 2011-04-21
Or alternatively sudo -s

---

### Post by mcduck on 2011-04-21
> **andymorton said:**
> Or alternatively sudo -s

...or , really, don't use "sudo su" or "sudo -s", as they will not set root user's environment variables and instead you end running with root user's permissions but using config files and variables from yur normal user. Which may result in nasty stuff like your user's files setting files becoming overwritten as root.

The correct command to start a root terminal session in Ubuntu is "**sudo -i**".

...and for the OP; unless you have enabled the root account yourself, you don't have a root password. The password you have is your user's password. "sudo" uses the user's password, while "su" would require the *target user's* password (in this case root's) and as you don't have one, you can't sue "su" like that.

---

### Post by coffeecat on 2011-04-21
> **honey_bee said:**
> I am new in UBUNTU 10.10 and I want to use teh root account to assign static IP address to my ububtu linux.

You can assign a static IP address using the network manager applet. No terminal needed. If you need to know how, post back.

---

