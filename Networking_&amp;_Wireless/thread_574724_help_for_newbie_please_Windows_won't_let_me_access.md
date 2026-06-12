---
title: "help for newbie please Windows won't let me access Ubuntu and vice versa"
date: 2007-10-13
forum: Networking &amp; Wireless
---

### Post by tedo_59 on 2007-10-13
Hi,
I'm a linux novice and have set up Ubuntu 7.04 on my desktop and am trying to network to my Win XP laptop. I have installed SAMBA. They are connected via a wired linksys router and when I ping the ip address of my laptop the connection is confirmed. I have followed all the instructions on the video about how to set up a network ([http://www.youtube.com/watch?v=Ad17kma8rNM](http://www.youtube.com/watch?v=Ad17kma8rNM)). When I go to my laptop and look at my workgroup computers I can see my ubuntu desktop server in MSHOME, but when I double click on this i get a message "TINTIN_SAMBA_SERtintin-desktop server (SAMBA, UBUNTU) is not accessible. You might not have permission to use this resource. Contact...."

Do I have to give the computer name a permission in some way? At the moment I have just set up the Win XP login user with the permission on Ubuntu. Do I have to do something with port forwarding? 

In the Ubuntu network browser i can see a windows network icon, and when I cliick on it i see two icons - "mshome" and "workgroup". When i click on either of these i get a message from Ubuntu "The contents could not be displayed".

Help gratefully appreciated.

Thanks.

Odet

---

### Post by banewman on 2007-10-13
Are both the computers in the same workgroup? ie both "workgroup" or both "mshome" ?

---

### Post by mrdaze0 on 2007-10-13
take a look at the instructions to setup samba located here.  [http://www.samba.netfirms.com/](http://www.samba.netfirms.com/)
this goes into permissions and users.

---

### Post by tedo_59 on 2007-10-13
Thanks. Both computers are in mshome.  I am logged in under the same name (odet) and password in both computers. I still get the same messages. 

I followed the instructions on the link and set up a new samba config file, and the users and permissions. So the samba config file is now:

# Global Parameters
workgroup = mshome
netbios name = Samba
encrypt passwords = yes

[homes]
read only = no
browseable = no


[music]
path = /home/odet/mp3
available = yes
browsable = yes
public = yes
writable = yes

[global]
wins support = no
workgroup = MSHOME


Thanks again.

Odet

---

### Post by mrdaze0 on 2007-10-13
workgroup = mshome <------ should this be MSHOME
:
:
workgroup = MSHOME  <----- or this be mshome

windows is picky about capitalization not sure but maybe this is affecting it.

the only experience i have with samba was it working right off the bat so i am just guessing

---

### Post by tedo_59 on 2007-10-13
Thanks, tried that. Any ideas for trouble shooting to try to narrow it down a bit?
cheers

Odet

---

### Post by tedo_59 on 2007-10-14
Some success. I set up a user account on my linux box with the same name and password as the win xp account on the laptop. I can now access my linux files from the win xp machine. I can also see the win xp machine from linux but it won't let me access the files (it asks for a password for an mshome guest account for the laptop, which I haven't set up, i'll give that a try). Does this mean I can only access files on the linux when I am logged in with the same user name and password on both machines?

---

### Post by lamadredelsapo on 2007-10-14
Have you created user accounts for samba in the Ubuntu box? You should follow [this howto]("http://ubuntuforums.org/showthread.php?t=202605&highlight=configure+samba") it worked great for me.

---

