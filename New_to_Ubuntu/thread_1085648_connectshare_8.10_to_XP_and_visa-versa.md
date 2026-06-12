---
title: "connect/share 8.10 to XP and visa-versa"
date: 2009-03-03
forum: New to Ubuntu
---

### Post by funkyali on 2009-03-03
Hi,

I am running ubuntu 8.10 and and an XP machine all on the same network. I've not configured anything as yet. I would like to know how to do the following: 

1. Remote desktop to my XP machine from my Ubuntu machine.
2. Remote desktop to my Ubuntu machine from my XP machine.
3. Read/write/delete files between my XP and ubuntu machine.
4. How can I access my ubuntu machine remote from outside my network? I use logmein.com to connect to my win xp machien but not sure how to do it with ubuntu.


Thanks for your help.

---

### Post by funkyali on 2009-03-03
bump...

---

### Post by funkyali on 2009-03-03
I can now see that thy are on the same workgroup.

When I go Places>Network I can see my Win xp pc but when I click on it is asks for a password and when I enter in a password it will not connect.

any ideas?

---

### Post by e_james on 2009-03-03
I hope you get some useful replies to this thread because I have also been looking for answers to most of your questions. I think I can be of some help with the file sharing and I would like to warn you now that Linux has the annoying habit of changing the file modified datestamp to today when copying files to FAT32 filesystems (both locally and remotely). I am sure there is a way to prevent this, but most linux users don't seem to see it as a problem. 

I need to go and see to an unexpected visitor now. More later.

---

### Post by e_james on 2009-03-03
I believe this link 

[https://help.ubuntu.com/search.html?cof=FORID%3A9&cx=003883529982892832976%3Ae2vwumte3fq&ie=UTF-8&q=windows+shares&sa=Search](https://help.ubuntu.com/search.html?cof=FORID%3A9&cx=003883529982892832976%3Ae2vwumte3fq&ie=UTF-8&q=windows+shares&sa=Search)

provides more than enough information to connect to Windows shares from ubuntu but the procedures I have read so far are rather complex. Try this instead -

Click on Places | Network then double-click on Windows Network - <Workgroup> - <PC name> etc. When you have connected to the share you want, add a bookmark. This bookmark can be used to remount the share any time you need it. I use this technique to play back DivX files stored on my Windows PCs using my Eee PC 901. The only problem I have is that the wireless range seems to be a bit less than I was hoping for.

Accessing Linux files from Windows is something I have yet to try, but I think I will be able to do it with some further study.

I have managed remote desktop Linux - Linux using vnc and I have connected to Linux from Windows using UltraVnc (no desktop), but I can't get Linux to connect to a Windows remote desktop although it semms it should be simple. I think there's some fundamental Linux concept I haven't understood yet.

Hopefully you will get more helpful replies from other forum users but, if not, perhaps we can work out something together.

---

### Post by e_james on 2009-03-03
Oops! You sent another message I hadn't noticed. Have you checked your Windows sharing settings? Did you set it to private?

---

### Post by stchman on 2009-03-03
> **funkyali said:**
> Hi,

I am running ubuntu 8.10 and and an XP machine all on the same network. I've not configured anything as yet. I would like to know how to do the following: 

1. Remote desktop to my XP machine from my Ubuntu machine.
2. Remote desktop to my Ubuntu machine from my XP machine.
3. Read/write/delete files between my XP and ubuntu machine.
4. How can I access my ubuntu machine remote from outside my network? I use logmein.com to connect to my win xp machien but not sure how to do it with ubuntu.


Thanks for your help.

It is my experience that Linux has problems seeing and connecting to SMB shares on Windows machines.  You can however share a folder on a Linux machine and the Windows machine will see it and connect.

I am pretty much Ubuntu at my home so I use NFS for my network.

You can install VNC on both machines.  You can also install NFS on a Windows machine.

---

### Post by funkyali on 2009-03-03
> **e_james said:**
> Oops! You sent another message I hadn't noticed. Have you checked your Windows sharing settings? Did you set it to private?


Still need to work out the sharing but I managed to remote from my ubuntu to my xp pc

first off check windows setting right click on my computer then select properties and allow remote desktop.

then in ubuntu go to application>internet>Terminal Server Client

enter in your xp pcs IP address and change the protocol to RDP. enter in a username and password. It should then connect. now jus tto see how to remote and have two users logged into the same pc at the same time.

---

### Post by e_james on 2009-03-03
Hey that works for me too, but only for one of my Windows PCs so far. If I play a divx file on the remote PC using RDP, I get sound but not picture. If I use RDPv5 I get picture (better than using Windows RDP) but not sound. When I last tried Linux to Linux there was no sound and I was told this was normal. I don't want to try too much right now in case I crash the Windows PCs but I am thinking you can certainly connect 2 users to one PC if they have different user accounts.

---

### Post by funkyali on 2009-03-04
> **e_james said:**
> Hey that works for me too, but only for one of my Windows PCs so far. If I play a divx file on the remote PC using RDP, I get sound but not picture. If I use RDPv5 I get picture (better than using Windows RDP) but not sound. When I last tried Linux to Linux there was no sound and I was told this was normal. I don't want to try too much right now in case I crash the Windows PCs but I am thinking you can certainly connect 2 users to one PC if they have different user accounts.

glad it worked for you too. I did create another user and it just logged off the other user. I remember seeing something about user restriction. 


Oh yes this is the post [http://ubuntuforums.org/showpost.php?p=1948777&postcount=5](http://ubuntuforums.org/showpost.php?p=1948777&postcount=5) 

I'm not sure if this user is around but I might try and get that dll.

---

