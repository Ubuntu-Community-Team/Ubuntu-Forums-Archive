---
title: "SAMBA multiple users help"
date: 2008-07-25
forum: Networking &amp; Wireless
---

### Post by poopsacky on 2008-07-25
Hi,

I set up SAMBA file server using this howto: [http://prash-babu.blogspot.com/2008/05/how-to-setup-samba-in-linux.html](http://prash-babu.blogspot.com/2008/05/how-to-setup-samba-in-linux.html)

Then I typed "gksudo nautilus" and made a shared folder in my /home folder that has read/write access.

On the samba server, I only created one passworded user account, which is used by 4 xp computers. (i made a shortcut on each of the user's computer)



My problem is that the users report getting intermittent messages saying the hard drive is full when they try to save a file. The only way to correct this is to** quit w/o saving**, and then re-opening the file. Only then can they save again, but the drive full problem might come back later.

Do I need to allow multiple users or make seperate accounts for each user? I'm not sure what the problem is since these users can access the files and save most of the time. I tried searching forums but have yet to find someone with the same problems.. Please help, TIA!

---

### Post by ARhere on 2008-07-25
does each of the four XP computer have the network drive mounted?  I ask becasue you said the four XP machines all use the same samba user account.  I am not a network admin but this might lead to problems if the same account tries to access the same file(s) at the same time.

If you want to make it easy and use the same account, then give each person a separate folder to work in, might help a little.

I am not sure I can help but tell me more and I will try.

-AR

---

### Post by poopsacky on 2008-07-25
I dont have the drives mounted, only a shortcut link to the \\server\shares folder. I have to make a quick correction. It seems that the biggest problem that the users get is getting the "drive is full" error message.

The users shouldn't be accessing the same files so I don't think that's the problem, not 100% sure tho.

---

### Post by ARhere on 2008-07-25
By the way.. this is how I share folders to multiple XP boxes.

I create a separate folder for each person/XP box and use the same samba account for all shares.  I then change the "My Documents" location to the network drive/shared folder for that persons name.
[COLOR="DarkRed"]Right Click "My Documents"-->Properties: change "Target Folder Location"[/COLOR]
All samba configurations were done using the standard samba shares GUI in 8.04

For whatever reason, I have had odd problems when XP users follow a link like you said, but NEVER when the "My Documents" is linked to the network drive.  It doesn't even need to be mapped in Windows.

-AR

---

### Post by poopsacky on 2008-07-25
ARhere: Thanks for your suggestion. I cannot implement this, however, because the users are all modifying a large centralized archive of files. They should never be working on the same job so I don't see a benefit in giving them seperate folders to work with.

My current method is basically ported from what I did in XP. I had setup a xp desktop computer and shared over 100GB of files on it to 3 other computers. The 4 computers combined would all work on the files shared on that one desktop. I've just recently changed and moved the shared files from the xp desktop to a dedicated samba file server.I had tested everything beforehand and no problems came up. Today, the first day that I implemented everything the uesrs are reporting problems..

I am new to liux in general, but am willing to learn. I had thought that everything was flawless but this problem came out of nowhere....

If there are any other suggestions I would greatly appreciate them, TIA!

---

### Post by ARhere on 2008-07-25
> **poopsacky said:**
> ... I had setup a xp desktop computer and shared over 100GB of files on it to 3 other computers. ...

How much free space is on the data drive?  When you moved the data drive over from a Windows machine, did you remember to remove the page file Windows uses?  If you are unaware of what I am talking about, remember Windows uses free space on all hard disks as a type of swap file.  Windows can dynamically resize this file but Linux does not.

Try that and let me know.

-AR

---

### Post by nycste on 2008-07-25
sorry to hijack thread but i have 2 things to ask or say

1. great thread, i hope you fix your problems with your 3 buddies/co workers this is something my buddy and i are working on setting up ourselves we are new to linux as well

2. i have ssh and samba installed, my buddy said that ssh is always enabled or on or accessable unless you go to services settings, then unclick remote shell server (ssh) and that disables instant access to my buddy trying to connect who knows my connection info while we were on a lan

so my concern lies in is shh securly closed off now untill i reclick that option and second samba if i have nothing directly shared, does someone who somehow enters my network have access to my stuff and or ability to be harmfull or i have to setup a shared file/folder like the thread user is having issues with


again sorry for hijack figured this might be a decent place to ask these concerns of mine, and perhaps yours thread starter !

---

### Post by ARhere on 2008-07-26
> **nycste said:**
> sorry to hijack thread but i have 2 things to ask or say

1. great thread, i hope you fix your problems with your 3 buddies/co workers this is something my buddy and i are working on setting up ourselves we are new to linux as well

Ok Hijacker... :)   His problem is an isolated incident as using Linux as a file share usually works flawlessly with Windows.  I have been doing it for 10 years now with no problems.

> **nycste said:**
> ...so my concern lies in is shh securly closed off now untill i reclick that option and second samba if i have nothing directly shared, does someone who somehow enters my network have access to my stuff and or ability to be harmfull or i have to setup a shared file/folder like the thread user is having issues with

I suggest you do a little reading up on ssh and samba.  It is good that you are curious and want to try, but you will save yourself a lot of headache if you spend just 10 minutes reading over the basics.
[https://help.ubuntu.com/6.06/ubuntu/serverguide/C/configuring-samba.html](https://help.ubuntu.com/6.06/ubuntu/serverguide/C/configuring-samba.html)
[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

In short, with remote access protocals, you are safe unless someone knows your username/password.  If they do, then change it.  With Samba, you can open an entire drive for full access, or you can restrict each file's access rights.  It is all about how you wish to enable your security, thus the beauty of Linux.

-AR

---

### Post by poopsacky on 2008-07-27
> **ARhere said:**
> How much free space is on the data drive?  When you moved the data drive over from a Windows machine, did you remember to remove the page file Windows uses?  If you are unaware of what I am talking about, remember Windows uses free space on all hard disks as a type of swap file.  Windows can dynamically resize this file but Linux does not.

Try that and let me know.

-AR

That computer is still up and running, I just built a new server with 2x750GB hdds in a RAID1 and once the samba shared folder was created I moved all of the 100GB of files onto the samba shared folder.

---

