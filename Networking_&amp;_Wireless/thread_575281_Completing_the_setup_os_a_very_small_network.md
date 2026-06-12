---
title: "Completing the setup os a very small network"
date: 2007-10-13
forum: Networking &amp; Wireless
---

### Post by PmDematagoda on 2007-10-13
As the topic suggests, I am nearly completing a very simple network between a Ubuntu computer and a Windows computer.

Now the problem, I can access the shared folders and files of my Windows computer with no problems, but I cannot access the shared documents of my Ubuntu computer using the Windows one as it asks for a username and password(Power of Linux proven;)), but I would greatly like to have a "full-duplex" network:).

---

### Post by PmDematagoda on 2007-10-14
Anyone?

---

### Post by PmDematagoda on 2007-10-16
Forgive me, but bump.

---

### Post by vacolten on 2007-10-16
I had some luck with this months ago but, as with a lot of things, out of sight out of mind.  I do remember that I had some trickiness setting up users in samba.  You have to create a folder (or series of folders) to allow samba access to - and give users permissions to access them through samba.

I had luck starting here:

[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

---

### Post by Stormboy on 2007-10-16
Hi
I think You need to install Samba.

sudo apt-get install samba

Then edit the /etc/samba/smb.conf file to suite your network.
You will need to create a samba user as well :)

btw I am a noob :)

---

### Post by notwen on 2007-10-16
[Here]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#Samba_Server") is another great Samba guide.  Good luck w/ getting your network working the way you want. =]

---

### Post by Stormboy on 2007-10-16
Was going to look for some links but got beaten to it :)

---

### Post by PmDematagoda on 2007-10-16
Thanks for everyone's help:), unfortunately my mom's laptop is not here right now so I will have to wait until the weekend to see if I can get it working properly, I will let you guys know how it went. Once again thanks a lot for everyone's help:).

---

