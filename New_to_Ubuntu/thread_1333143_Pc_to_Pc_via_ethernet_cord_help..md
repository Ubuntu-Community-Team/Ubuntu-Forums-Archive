---
title: "Pc to Pc via ethernet cord help."
date: 2009-11-21
forum: New to Ubuntu
---

### Post by ariascarlos1990 on 2009-11-21
Ok. So Recently tried to format my old thumb drive to NTFS and totally F'd it up. So now My only option as of now is to create a Connection between My two computers to transfer files from one to another. First off one computer is running Windows XP and the other is running Ubuntu. (Only the Ubuntu computer has Internet) So I only have one IP address correct? I have installed nautilus, samba, smbfs, and ssh. and had no success with either of them. I am a total newb at this. ;) So if someone could please help me through this or give me reference to a newb level installation I would be so great full!

Thanks.

---

### Post by prshah on 2009-11-21
> **ariascarlos1990 said:**
> create a Connection between My two computers to transfer files from one to another. First off one computer is running Windows XP and the other is running Ubuntu. (Only the Ubuntu computer has Internet) So I only have one IP address correct? I have installed nautilus, samba, smbfs, and ssh. and had no success with either of them. I am a total newb at this. ;) 

This is quite a complicated matter for a newbie; I will try to help you, but I suggest you get a professional to do this for you. If you insist on doing this yourself, however:

Important points and summary:

a) When networking two computers together, you will have 2 IP addresses, one (unique) for each computer.

b) If you are connecting the two PCs via a single ethernet cord, you need a special type of cable called a "crossover" cable. You can purchase these or make your own if you have a RJ45 crimper.

c) If you are connecting the PCs to a "switch" or a "hub" then you can use any ethernet cable, crossover or normal.

d) Assign an IP address to the Windows machine, eg. 192.168.5.5 with a subnet mask 255.255.255.0. 

e) Assign an IP address to the Ubuntu machine eg. 192.168.5.7 (different from the Windows machine) with a subnet mask of 255.255.255.0 (Same as the Windows machine).

f) Enable file and folder sharing on the Windows machine.

g) Install and enable Samba on the Ubuntu machine.

h) Connect to the Windows machine using this command in the nautilus location bar ```
smb://192.168.5.5/sharename
```

i) Copy/paste your files back and forth.

j) "unmount" the network connection when done.

In the summary, I am giving no details at all. If after looking through this you want to continue this route, please post back for more specific instructions.

I would advise you to use a USB flash drive or external HDD or to get professional help, if this is a one-time transfer requirement.

---

### Post by t0p on 2009-11-21
You'll have only one *public* IP address when you're on the internet - that'll be your Ubuntu computer.  But when you connect the 2 computers together, they'll both need private IP addresses so they can talk to each other.

To connect 2 computers without a hub/router, you'll need **crossover cable**.  You can buy it from a computer equipment shop, or you can make it yourself by adapting normal ethernet cable: instructions [here]("http://www.littlewhitedog.com/content-8.html").

There are a lot of guides on the internet that explain how to connect 2 computers via crossover cable.

> **prshah said:**
> This is quite a complicated matter for a newbie; I will try to help you, but I suggest you get a professional to do this for you.


Whoa! Get professional help - *pay* someone - to do *this*?  But it isn't that hard to do.  Are you a professional yourself?

---

### Post by lkraemer on 2009-11-21
The best thing to do is to reformat the Flash Drive to Fat 32 and
use it, or purchase a new one.  There is an HP program that
will reformat it to factory specs, but I forget the name of the
software right now.  It works good.  If that isn't an option
then:............

This should help.
[http://ubuntuforums.org/showthread.php?t=1031300](http://ubuntuforums.org/showthread.php?t=1031300)
Posting #15

You will need to install filezilla on the windows machine,
then install vsftp server on the Ubuntu machine and configure.

Disable Wifi, use a Crossover cable, and setup your STATIC IP Addresses first.

All you need to do is start Filezilla, and log into the Ubuntu machine
with your Ubuntu Login & password.  Then xfer the files from the windows
machine by using UPLOAD/DOWNLOAD to get whatever files transfered as needed.

Works fine.

REMEMBER: You can ping 192.168.1.100 or 192.168.1.110 as needed to verify
the actual connection, along with watching the hardware LED's on the 
Ethernet port to make sure there are transmissions in progress.

When you are finished with the transfers:
Set the IP back to ROAMING and you should be all set.

lk

---

### Post by ariascarlos1990 on 2009-11-21
> **prshah said:**
> This is quite a complicated matter for a newbie; I will try to help you, but I suggest you get a professional to do this for you. If you insist on doing this yourself, however:

Important points and summary:

a) When networking two computers together, you will have 2 IP addresses, one (unique) for each computer.

b) If you are connecting the two PCs via a single ethernet cord, you need a special type of cable called a "crossover" cable. You can purchase these or make your own if you have a RJ45 crimper.

c) If you are connecting the PCs to a "switch" or a "hub" then you can use any ethernet cable, crossover or normal.

d) Assign an IP address to the Windows machine, eg. 192.168.5.5 with a subnet mask 255.255.255.0. 

e) Assign an IP address to the Ubuntu machine eg. 192.168.5.7 (different from the Windows machine) with a subnet mask of 255.255.255.0 (Same as the Windows machine).

f) Enable file and folder sharing on the Windows machine.

g) Install and enable Samba on the Ubuntu machine.

h) Connect to the Windows machine using this command in the nautilus location bar ```
smb://192.168.5.5/sharename
```i) Copy/paste your files back and forth.

j) "unmount" the network connection when done.

In the summary, I am giving no details at all. If after looking through this you want to continue this route, please post back for more specific instructions.

I would advise you to use a USB flash drive or external HDD or to get professional help, if this is a one-time transfer requirement.

This could be an option. but, when I say im a newb I mean it lol. Where and how would I find the IP addresses on the ubuntu and xp computers?

> **t0p said:**
> You'll have only one *public* IP address when you're on the internet - that'll be your Ubuntu computer.  But when you connect the 2 computers together, they'll both need private IP addresses so they can talk to each other.

To connect 2 computers without a hub/router, you'll need **crossover cable**.  You can buy it from a computer equipment shop, or you can make it yourself by adapting normal ethernet cable: instructions [here]("http://www.littlewhitedog.com/content-8.html").

There are a lot of guides on the internet that explain how to connect 2 computers via crossover cable.



Whoa! Get professional help - *pay* someone - to do *this*?  But it isn't that hard to do.  Are you a professional yourself?

So I know im gonna need a crossover cable. How would I go about finding/setting up the private  IP addresses?

> **lkraemer said:**
> The best thing to do is to reformat the Flash Drive to Fat 32 and
use it, or purchase a new one.  There is an HP program that
will reformat it to factory specs, but I forget the name of the
software right now.  It works good.  If that isn't an option
then:............

This should help.
[http://ubuntuforums.org/showthread.php?t=1031300](http://ubuntuforums.org/showthread.php?t=1031300)
Posting #15

You will need to install filezilla on the windows machine,
then install vsftp server on the Ubuntu machine and configure.

Disable Wifi, use a Crossover cable, and setup your STATIC IP Addresses fist.

All you need to do is start Filezilla, and log into the Ubuntu machine
with your Ubuntu Login & password.  Then xfer the files from the windows
machine by using UPLOAD/DOWNLOAD to get whatever files transfered as needed.

Works fine.

REMEMBER: You can ping 192.168.1.100 or 192.168.1.110 as needed to verify
the actual connection, along with watching the hardware LED's on the 
Ethernet port to make sure there are transmissions in progress.

REMOVE the STATIC IP addresses and you should be all set.

lk

I don't have the thumb drive anymore. And you cannot at files bigger then 4GB on a FAT32 formated thumb drive. learned that the hard way. ;) How do I remove the static IP address?

---

### Post by prshah on 2009-11-21
> **t0p said:**
> Whoa! Get professional help - *pay* someone - to do *this*?  But it isn't that hard to do.  Are you a professional yourself?

Yes, very much so; but I don't think there's any financial gain for me involved here; the OP is probably half the way across the world from me.

I hope OP will find the procedure as easy as you think it to be.

---

### Post by lkraemer on 2009-11-21
In Ubuntu, you set the Static IP as per this photo.  Removing the Static IP
requires you to set it back to ROAMING.  You can save both settings by
specifying a filename in LOCATIONS:, Saving, and then select one of those
filenames, and click on the GREEN Checkmark.

In Windows I haven't a clue.....been over two years without that hassle....
BLOAT, and Viruses!

lk

---

