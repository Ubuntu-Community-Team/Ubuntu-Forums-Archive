---
title: "Parrallel port PC to PC combining"
date: 2006-08-10
forum: Networking &amp; Wireless
---

### Post by Steve S. on 2006-08-10
I would like to hook up a Windows Millenium system as a backup to a Kubuntu system (Dapper) a la [http://www.windowsnetworking.com/articles_tutorials/dccmain.html](http://www.windowsnetworking.com/articles_tutorials/dccmain.html)

Can such a thing be done?  Has anyone done it?  Recomendations?

---

### Post by avtolle on 2006-08-10
Can it be done? Yes; have I done it (specifically, what you propose)? No; my question - Why?

---

### Post by avtolle on 2006-08-10
Upon a bit more reflection, I would recommend (if you are trying to back up your data, etc. files on the WinME box) you obtain an external HDD for this purpose. If, as I suspect, the object is to expend as few funds as possible, and you just happen to have the ME box around doing nothing, then I would encourage you to transfer the files (if you must) via serial port(s), recognizing that on the Ubuntu box, you will need to locate the appropriate drivers, etc. for a serial modem, IIRC. In pre-1987 or so days, files were often transferred between two computers via a "null modem" cable, which allowed serial to serial transfer, without copying files to floppies, then "sneaker netting" them to the other machine. Hopefully, there will be a guru or two around to help; my "talents" in this area, if any, are very rusty.

---

### Post by Steve S. on 2006-08-10
> **avtolle said:**
> Upon a bit more reflection, I would recommend (if you are trying to back up your data, etc. files on the WinME box) you obtain an external HDD for this purpose. If, as I suspect, the object is to expend as few funds as possible, and you just happen to have the ME box around doing nothing, then I would encourage you to transfer the files (if you must) via serial port(s), recognizing that on the Ubuntu box, you will need to locate the appropriate drivers, etc. for a serial modem, IIRC. In pre-1987 or so days, files were often transferred between two computers via a "null modem" cable, which allowed serial to serial transfer, without copying files to floppies, then "sneaker netting" them to the other machine. Hopefully, there will be a guru or two around to help; my "talents" in this area, if any, are very rusty.

Thanks, avtolle.  Yeah, I would like to know if anyone has any ideas on how to do this, simplicity and price highest priority, in that order. 

I have a friend that has a Millenium (ME) system.  I put together a dual boot XP (10G) and Kubuntu Dapper (20G) system for them, trying to give them a good intro to Linux even though they aren't overly inclined to computer technology.  There are just too many good music gathering (one of the top things they use their computer for) programs in Ubuntu.

Anyway, want to be able to transfer data to their system from the ME system.  They could do it via XP, since both drives can read each other (thanks to [http://www.ubuntuforums.org/showthread.php?t=217009](http://www.ubuntuforums.org/showthread.php?t=217009) and also [http://www.fs-driver.org/](http://www.fs-driver.org/) ) but I would of course like them to use the Kubuntu drive as much as I can get them to, if only to learn it.

So, however we can transfer it, please advise.

---

### Post by sugarat on 2006-08-10
I would strongly suggest abandoning such a venture, as once you've gone through all the trouble of trying to setup such a bizarre communications channel you could have just used bog standard ethernet - which, at at least 100Mbit is going to be far faster. 

With network cards being so utterly ridiculously cheap, there's no need to go fannying around with parallel or serial cables.

---

### Post by Steve S. on 2006-08-10
> **sugarat said:**
> I would strongly suggest abandoning such a venture, as once you've gone through all the trouble of trying to setup such a bizarre communications channel you could have just used bog standard ethernet - which, at at least 100Mbit is going to be far faster. 

With network cards being so utterly ridiculously cheap, there's no need to go fannying around with parallel or serial cables.

I have never set up a network, and certainly not between systems that are not the same OS.  Please advise on the best way to do this...in other words, please clarify your opinion, sugarat.

---

### Post by avtolle on 2006-08-10
Rapidly outpacing my knowledge here; have you explored Samba to network the two Comps. That's the application (as I understand) used to set up a network between a Windows box and a Linux box. Networking is  currently beyond me, but there  are some How Tos floating around which may be of some use.

---

### Post by Steve S. on 2006-08-10
> **avtolle said:**
> Rapidly outpacing my knowledge here; have you explored Samba to network the two Comps. That's the application (as I understand) used to set up a network between a Windows box and a Linux box. Networking is  currently beyond me, but there  are some How Tos floating around which may be of some use.

Thanks, avtolle.

Another point to mention (that goes hand and hand with the simplicity aspect that I mentioned before) is that my friend (and her husband) now have both systems in their house, so I am looking for something to be able to just tell them to do.  If it were me, with the systems in my posession, I would play around until I got it figured out, but they won't do that (the whole, "Oh, I can't do this" mentallity creaps up).

So, I am looking for the most readily simple way to get the data transferred for them.

Any further ideas with this in mind?

---

### Post by avtolle on 2006-08-10
Not really, especially with the above-stated restriction. (Not too serious suggestion follows:) Maybe they'll "invite" you as a house guest for a few days?

---

### Post by Steve S. on 2006-08-10
> **avtolle said:**
> Not really, especially with the above-stated restriction. (Not too serious suggestion follows:) Maybe they'll "invite" you as a house guest for a few days?

LOL "Hey, how's it goin'?  Just thought I'd stop by and play with your computers for the next few hours.  Hope you don't mind..."

Yeah, maybe I could do that.  But other ideas are welcome...

---

