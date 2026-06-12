---
title: "How to configure SAMBA in ubuntu?"
date: 2006-07-17
forum: Networking &amp; Wireless
---

### Post by nishant on 2006-07-17
i want to know dat how to configure samba in ubuntu linux?

what r d changes we have to make in smb.conf file?


tnx 
nishant

---

### Post by gerbman on 2006-07-17
The setup I use to share the second hard drive in my PC with my Windows laptop is the following:

1) In smb.conf, uncomment (remove the semi-colon before) "security = user" in the "Authentication" section.

2) Create share definition(s). These are at the bottom of smb.conf, with some examples commented out by default. The share definition for my second hard drive is the following:```
[hd2]
path = /mnt/hd2
available = yes
browseable = yes
public = yes
writable = yes
guest ok = no
```3) Check the smb.conf file for errors:```
testparm
```(check for any error messages)

4) Add user account for Samba access:```
sudo smbpasswd -a <username>
```where <username> is your account name

5) Restart Samba:```
sudo /etc/init.d/samba restart
```

6) Try it. You should be able to access the share from both Linux and Windows machines.

---

### Post by nishant on 2006-07-17
> **gerbman said:**
> The setup I use to share the second hard drive in my PC with my Windows laptop is the following:

1) In smb.conf, uncomment (remove the semi-colon before) "security = user" in the "Authentication" section.

2) Create share definition(s). These are at the bottom of smb.conf, with some examples commented out by default. The share definition for my second hard drive is the following:```
[hd2]
path = /mnt/hd2
available = yes
browseable = yes
public = yes
writable = yes
guest ok = no
```3) Check the smb.conf file for errors:```
testparm
```(check for any error messages)

4) Add user account for Samba access:```
sudo smbpasswd -a <username>
```where <username> is your account name

5) Restart Samba:```
sudo /etc/init.d/samba restart
```

6) Try it. You should be able to access the share from both Linux and Windows machines.















i tried this bt how to save file i vi editor
w and q is not workin.
is der any alternative?

---

### Post by tribaal on 2006-07-17
I suggest you use nano instead of vi, since it's much easier to learn.

- trib'

---

### Post by gerbman on 2006-07-17
```
sudo gedit /etc/samba/smb.conf
```would be the easiest.

---

### Post by elettronicha on 2006-07-17
> **nishant said:**
> i want to know dat how to configure samba in ubuntu linux?

what r d changes we have to make in smb.conf file?


tnx 
nishant
That's a FAQ, please read the official documentation and the related wiki page.

---

### Post by morequarky on 2006-07-17
@@ elettronicha

I would like to praise your name on the highest mountain for your intellegent response.  Everyone should aways check the FAQ, official documentation, and wiki pages.  We get tired of answering the same questions over and over again.

I have search for the last 15 $#%@^@$ minutes and still haven't found dapper samba setup anywhere!!  I googled it and could only find Warty stuff.  Pretty lousy docs if you ask me.

---

### Post by gerbman on 2006-07-17
> **morequarky said:**
> @@ elettronicha

I would like to praise your name on the highest mountain for your intellegent response.  Everyone should aways check the FAQ, official documentation, and wiki pages.  We get tired of answering the same questions over and over again.It might have been an intelligent response, but it was not very helpful. Newbies don't get much out of replies like that...they need direct links to information, lists of steps to perform, etc. Of course, I am assuming the OP is a newbie and not a more competent user who is simply lazy. 

> I have search for the last 15 $#%@^@$ minutes and still haven't found dapper samba setup anywhere!!  I googled it and could only find Warty stuff.  Pretty lousy docs if you ask me.I'm confused. You're telling the OP to read the documentation while at the same time complaining that there isn't any good documentation to begin with. :-k

---

### Post by elettronicha on 2006-07-17
> **morequarky said:**
> @@ elettronicha

I would like to praise your name on the highest mountain for your intellegent response.  Everyone should aways check the FAQ, official documentation, and wiki pages.  We get tired of answering the same questions over and over again.

I have search for the last 15 $#%@^@$ minutes and still haven't found dapper samba setup anywhere!!  I googled it and could only find Warty stuff.  Pretty lousy docs if you ask me.

Don't get warm so easily, guy :) Just go to the wiki search box and type 'samba': [https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)
Configuring samba is quite standard with every distribution, so if you have breezy or dapper or mandriva or debian or slackware makes no difference.
Anyway the topic is well discussed in the forum and, me too, I did configure samba reading the topics.;)

---

### Post by exaulz on 2006-07-23
> **gerbman said:**
> The setup I use to share the second hard drive in my PC with my Windows laptop is the following:

1) In smb.conf, uncomment (remove the semi-colon before) "security = user" in the "Authentication" section.

2) Create share definition(s). These are at the bottom of smb.conf, with some examples commented out by default. The share definition for my second hard drive is the following:```
[hd2]
path = /mnt/hd2
available = yes
browseable = yes
public = yes
writable = yes
guest ok = no
```3) Check the smb.conf file for errors:```
testparm
```(check for any error messages)

4) Add user account for Samba access:```
sudo smbpasswd -a <username>
```where <username> is your account name

5) Restart Samba:```
sudo /etc/init.d/samba restart
```

6) Try it. You should be able to access the share from both Linux and Windows machines.
Thank you so, so much.

---

### Post by gerbman on 2006-07-23
You're welcome :)

---

### Post by solusrex on 2006-07-24
I am truly at my wits end. I have been trying on and off for years to get shared folders talking in linux and usually just give up and rely on a usb hd instead but this time i have to...and i have spent the last week (all of it!!!) and am getting nowhere. Why is it so hard? Every other linux problem over the years has been easy thanks to these boards and other like them.

I followed the ubuntuguide samba tips to the letter, substituting the right usernames for my pcs. Yet nothing shows up on the (windows free) 'Windows network'. I dont know what's going on. Both machines have static IPs.

Is there a commerical piece of software akin to Rendezvous/Bonour for linux? It works a dream on my iBook and iMac and i would pay at least $100 for an equivalent that 'just works'

:confused: :confused: :confused: :confused: :confused: :confused: :confused:

---

### Post by solusrex on 2006-07-24
funny how it all works out...just gotten a little bit closer. This machine sees the other but the password is being rejected...

---

### Post by gerbman on 2006-07-24
> **solusrex said:**
> funny how it all works out...just gotten a little bit closer. This machine sees the other but the password is being rejected...Did you do steps 1 and 4 above?

---

