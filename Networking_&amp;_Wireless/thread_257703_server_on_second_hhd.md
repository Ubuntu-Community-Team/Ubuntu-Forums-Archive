---
title: "server on second hhd"
date: 2006-09-14
forum: Networking &amp; Wireless
---

### Post by Greydog on 2006-09-14
Hi all,

I might be way off here but, can I use my SATA II 250 gig second drive as a music server?

It is installed in my AMD-64 box with 1 gig of ram and a wired connection to a D-link wireless router.

My plan is to use a wireless laptop, connected to my "patio" stereo amp" to access music files for outdoor listening.

I guess in addition to the "do-able' question, how would one go about the actual implementation? Do I install the server distro on the second drive (and how) or is there a better way to do this?

Any help or discussion is welcome.

Thanks everyone,

Greydog

---

### Post by dlehman on 2006-09-14
Well to start we would need the configuration of your laptop is it Ubuntu or is it running windows? if you are running windows I would setup samba on the amd box to share files and then map a network drive from windows to the samba share.  
I am not an expert with Ubuntu I just switched from gentoo tonight and the default install will allow me to access my windows shares I have not tried to access it the other way yet but will be soon

good luck

---

### Post by Greydog on 2006-09-15
Thanks for the reply, dlehman.

Well, I have a Dell laptop with Ubuntu installed, a Sony laptop with xp (for now) and another dell desk top with xp (maybe forever...wife's!)so I guess Samba is the way to go.

My home built box with a 64 bit proc. and ide drive (120 gig) is running i386. It has a second SATA 250 gig that used to have xp on it and that's where I'd like to put the server/storeage.

My main question is can I use the second drive as a server and still use the ide for normal day to day tasks?

After that answer, I'll figure out how to procede.

Thanks for any input

Greydog

---

### Post by dlehman on 2006-09-17
Well if I am reading your post correctly, no you cannot run two systems at the same time, however you can mount you second drive and share it with your windows computers using samba. as I said in my last post I just switched to Ubuntu so how they do it I’m not sure. In Gentoo I used a nice tool called webmin. I did find that if you go to the system menu and got either preference or administration you can click share folders then it will ask you to install samba for windows or nfs for Linux.  
Sorry I can't give more detail as when I installed Ubuntu I erased one of my partitions so I am booted into XP doing a data recovery.
do a Google on samba you will find a lot of great guides 

hope this helps

---

### Post by Greydog on 2006-09-17
Thanks.dlehman,

I think that I'm just going to try setting my second drive as a server and just see what happens.

As much as I want to get a music server up and running, it isn't *all* that importamt. The "party" season is nearly over here so, I have the fall and winter to work it out. 

I am really looking at this as more of a learning experience. If I can get things set up, I'll have Windows outta here before spring and all will be good.

The whole "music" thing is, more or less, a cover for getting a home network running on Ubuntu. I really just want to get the family MS un-hooked.

Thanks for your input. Again, this forum, and you, have provided good and friendly help. 

Greydog

---

