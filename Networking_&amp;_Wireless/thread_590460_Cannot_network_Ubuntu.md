---
title: "Cannot network Ubuntu"
date: 2007-10-24
forum: Networking &amp; Wireless
---

### Post by dmedici on 2007-10-24
I have been reading posts for days about networking Ubuntu to Ubuntu wired desktops. I have seen plenty of easy suggestions that do not work at all and plenty of complicated suggestions which I am not going to even attempt. 
In short, I have upgraded both machines to the Gutsy Gibbon. Neither can see the other. At this stage of the game, if Ubuntu cannot network quickly and easily to another Ubuntu machine, I am very sad to say that I am forever finished with Ubuntu. I cannot afford any more lost time with this. Windows, which I hate more than anything, at least will network very easily and with very simple steps. 
I was hoping that this new Ubuntu would at last be the thing I could use to replace my Windows machines. Is there anyone out there who can give me simple instructions on networking Ubuntu machines so that I can share files? 
In closing, I want to say that all the people on this forum who have worked with me in the past have been very courteous and I really do want to keep Ubuntu. I hope that there is an easy networking solution with this new edition so that myself and many others can find a way to leave Windows forever.

---

### Post by eugo on 2007-10-24
I had a similiar problem. I set up samba and configured a share, I can access this share by windows xp, but when trying Ubuntu-to-Windows, Ii go to Places -> Network -> Windows Network -> Workgroup -> it game me a error. "Sorry, could not display all the content". However I am still able to access them by typing: "smb://computername" or "smb://ip-address" in the address bar in Nautilus.

You can simplify this by adding shortcuts to your share by using 'smbclient' (type 'man smbclient'). This way, the share will be on the desktop, even after reboot.

However, I just recompiled my kernel like an hour ago (see [this thread](http://ubuntuforums.org/showthread.php?t=583426)) and now, when I go to my Workgroup in Network, it shows up my windows computers just fine.

If someone could verify this?

---

### Post by dmedici on 2007-10-24
eugo, many thanks for your super fast reply!  

I wanted to add another note - earlier I found a clue that I just tried and it is working. Someone in another post said that as soon as they added a Windows machine to the mix, things began to work. That is what is happening here. My W2K machine is on the network now and I can see one of the two Ubuntu machines from the W2K machine. I can see both the W2K and the other Ubuntu from one Ubuntu, and the other Ubuntu sees the W2K and - this is weird - shared files that I deleted days ago from the second Ubuntu machine. Go figure. 
So I can deal with that. At least I have something to work with now. eugo, I'm going to try your ideas but unfortunately, it won't be for a couple days as I am now booked solid for the next 48 hours. Will keep you all posted.

---

