---
title: "Can't see any network computers including self"
date: 2008-02-25
forum: Networking &amp; Wireless
---

### Post by FerociousStrike on 2008-02-25
Please forgive me as this is rather lengthy and I'm relatively new to Linux in general.

Whenever I go places>network the only thing that shows up is "Windows Network" I can't see my husband's Ubuntu machine or even my own computer. He is able to see both of us, although when he tries to click on my machine he says it gives him a permissions error (unfortunately I can't remember the exact error and can't check at the moment since he is booted in to XP :neutral:)

After I first installed Ubuntu a month or so ago I downloaded Firestarter and played around with it, but I don't have it run on startup, so it's generally not running (I know, I know). I found a few threads describing similar problems to mine involving a conflict between Firestarter and Samba and tried uninstalling Firestarter just to see if that helped at all, but it hasn't. 

Right after that I remember playing around with Samba trying to connect to my husband's XP drive, but quickly gave up when I wasn't able to see his computer under the "Windows Network" icon. At the time I thought this was just an issue with Samba, but after my husband installed Ubuntu and I still couldn't see his computer and he could see both of us on a vanilla install, I realized there was a deeper problem. :(

Unfortunately, most of the resources I've found deal with Windows networking and Samba. Ubuntu networking seems like it should work automagically but doesn't for me, so it's been a struggle to find any troubleshooting. 

I'm afraid maybe something I've installed/uninstalled/modified has broken my networking, because I don't know for sure if this problem is new or not since I just tried to get Ubuntu to Ubuntu sharing working last night. I think it's been present at least since I tried to get Samba working after I first installed Ubuntu since I don't ever recall being able to see my own computer or shares under the network browser.

Any help or troubleshooting this problem would be *greatly* appreciated! 

BTW, we're both running 64bit Gutsy if that helps at all.

---

### Post by Sam Lars on 2008-02-25
Try copying his configuration from
```
/etc/samba/smb.conf
```
to your computer, changing whatever is necessary in there.
If you're going from Linux to Linux, I think NFS is much simpler, or even SSH...

---

### Post by FerociousStrike on 2008-02-25
I overwrote my smb.conf with his, restarted Samba and still nothing. :(

I'm open to trying anything to get network sharing to work at all. 

I'm able to get to the internet and we can both ping each other, I just can't see any computers or shares at all.

---

### Post by Sam Lars on 2008-02-25
If you go into the Shared Folders in System > Administration, it should help you set up NFS shares... and maybe fix Samba...

---

### Post by FerociousStrike on 2008-02-26
I set up a NFS share under administration>shared folders and added my husband and myself as allowed hosts. Still can't see anything under places>network. 

I may just end up partitioning off my home folder and reinstalling Ubuntu, because I'm convinced I've screwed something up somewhere.

---

### Post by Sam Lars on 2008-02-26
Have you tried Places > Connect to Server?

---

