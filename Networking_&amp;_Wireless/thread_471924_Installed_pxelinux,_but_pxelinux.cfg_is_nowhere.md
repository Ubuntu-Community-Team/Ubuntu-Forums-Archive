---
title: "Installed pxelinux, but pxelinux.cfg is nowhere"
date: 2007-06-12
forum: Networking &amp; Wireless
---

### Post by drewrockshard on 2007-06-12
I am currently creating a PXE multiboot environment.  I ran the following command to install the TFTP server, DHCP Server, and PXELinux:

apt-get install netkit-inetd tftpd-hpa dhcp3-server lftp

I now have a directory called: /var/lib/tftpboot

The problem is, there is no files in this. Where's the pxelinux.cfg files/directories.  I remember doing this awhile back on a different system with no issues; worked right out of the box.

Any ideas?

---

### Post by drewrockshard on 2007-06-14
No offence, but this forum really sucks. Pretty much every question I've asked has been resolved by myself.

There's really no "fix", persay.  You have to create the pxelinux.cfg directory and the files that are relavent to it.  Also, you need to copy the pxelinux.0 bootloader to your TFTP root, or wherever you point your DHCP server to for the bootloader.

If you don't know where the pxelinux.0 file is at on your system, just do:

```

updatedb
locate pxelinux.0

```

If nothing comes up, you will need to install pxelinux.  I dont know what the name of that package is offhand, whether it is pxelinux or syslinux, or pxe, or what...so to find out, type in:

```

apt-get update && apt-cache search pxelinux

```

...Thanks

(this has been resolved)

---

### Post by chili555 on 2007-06-14
> No offence, but this forum really sucks. Pretty much every question I've asked has been resolved by myself.Sorry, but a search of your posts doesn't agree. You contributed, quite well, to a RAID question, you got an answer from someone else about console beep and no one helped you with pxelinux. Not quite the track record you described.

I'd wager not 2% of the guys here know what pxelinux even is.

We're not paid customer service reps; we're volunteers. We have, believe it or not, other lives.

In fact, this forum rocks.

---

### Post by drewrockshard on 2007-06-16
> **chili555 said:**
> Sorry, but a search of your posts doesn't agree. You contributed, quite well, to a RAID question, you got an answer from someone else about console beep and no one helped you with pxelinux. Not quite the track record you described.

I'd wager not 2% of the guys here know what pxelinux even is.

We're not paid customer service reps; we're volunteers. We have, believe it or not, other lives.

In fact, this forum rocks.

So, you'll reply to a rant, but not to a question - nice :P

First off, why would only 2% of this forum know what pxelinux is?  It's part of Syslinux, which in turn is what Knoppix and alot of Live Linux CDs run off (not the PXE, but the Syslinux).  I would think there are more than Ubuntu geeks here .. right?

About the fact that I had some help here and there with a few questions, I stand corrected.  I've been to a few other forums and the same things have happened.  

"We have, believe it or not, other lives"? .. no **** .. ?

That's probably one of the dumbest statements I've heard in my life.  I'm not some Linux wack sitting at home seeing what trouble I can make on a forum.  I rarely use forums for this very reason, too many self-centered bastards that seem to think they know it all - but unfortunately, 8/10 answers that are posted to a forum are either false (not intentionally) or misspelled (untested).  Then you have the few that are dead on.  

The truth is, I spend most of my "other life" in a Datacenter managing thousands of Linux machines. The reason for my initial question, was for the fact that I am simply thinking about helping to deploy a AP System, and was needing more information on this and how it works.  In the past two days, I've learned alot about how PXELinux works. 

As stated before, I rarely ask questions on here and other forums because I either don't get an answer, I get a wrong answer, and yes, sometimes, I get a perfect answer.  

So, personally when it comes to me, I do believe at this point and time, this forum does suck, at least for me.  Even if someone said "you know, I really don't know about PXELinux, but I found some info here, here and here .." I'd at least be thankful and give them props for that - but no - I have some rude registered user that just wants to correct my statement and not even state much about my initial post of PXELinux...

Please, in the future, save your breath and only post an answer that is relevant to the initial question, or don't post anything at all....

-- Thanks --

---

### Post by MeeMaw on 2007-06-17
> **drewrockshard said:**
> So, you'll reply to a rant, but not to a question - nice :P

First off, why would only 2% of this forum know what pxelinux is?  It's part of Syslinux, which in turn is what Knoppix and alot of Live Linux CDs run off (not the PXE, but the Syslinux).  I would think there are more than Ubuntu geeks here .. right?

About the fact that I had some help here and there with a few questions, I stand corrected.  I've been to a few other forums and the same things have happened.  

"We have, believe it or not, other lives"? .. no **** .. ?

That's probably one of the dumbest statements I've heard in my life.  I'm not some Linux wack sitting at home seeing what trouble I can make on a forum.  I rarely use forums for this very reason, too many self-centered bastards that seem to think they know it all - but unfortunately, 8/10 answers that are posted to a forum are either false (not intentionally) or misspelled (untested).  Then you have the few that are dead on.  

The truth is, I spend most of my "other life" in a Datacenter managing thousands of Linux machines. The reason for my initial question, was for the fact that I am simply thinking about helping to deploy a AP System, and was needing more information on this and how it works.  In the past two days, I've learned alot about how PXELinux works. 

As stated before, I rarely ask questions on here and other forums because I either don't get an answer, I get a wrong answer, and yes, sometimes, I get a perfect answer.  

So, personally when it comes to me, I do believe at this point and time, this forum does suck, at least for me.  Even if someone said "you know, I really don't know about PXELinux, but I found some info here, here and here .." I'd at least be thankful and give them props for that - but no - I have some rude registered user that just wants to correct my statement and not even state much about my initial post of PXELinux...

Please, in the future, save your breath and only post an answer that is relevant to the initial question, or don't post anything at all....

-- Thanks --

So you're going to say the forum sucks because we don't know as much about PXELinux as you do, _therefore, can't give you a correct answer_ - so when we don't answer it's because we all suck? Also, there may only be 2% that know what PXELinux is...... not all of us spend all day administrating Linux systems - some of us are moms or secretaries or retirees.... (and the "rude registered user" you refer to has helped hundreds of forum posters, myself included, and is far from being as rude as you are.) Maybe YOU shouldn't post if you know so much.... OR, maybe you should try to help some of the noobs instead of insulting everyone.

Maybe I shouldn't post this because it's not the answer to your question....... but I believe you're out of line.  The people who think they can help, will, and if you don't get an answer it's not because we suck, it's because we honestly don't have an answer for you.

---

