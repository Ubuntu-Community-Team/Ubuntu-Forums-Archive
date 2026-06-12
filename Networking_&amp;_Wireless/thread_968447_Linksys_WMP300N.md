---
title: "Linksys WMP300N"
date: 2008-11-02
forum: Networking &amp; Wireless
---

### Post by A4orce84 on 2008-11-02
Hey Everyone,

I recently installed Ubuntu 8.10 to play around with on my desktop and having trouble getting my Linksys WMP300N PCI Wireless adapter working on my desktop.

I searched around, and found the following post in the archives:

[http://ubuntuforums.org/showthread.php?t=539208&highlight=WMP300N](http://ubuntuforums.org/showthread.php?t=539208&highlight=WMP300N)

But still could NOT get my wireless adapter working, and wanted to post back up and see if anyone can help me out?

Thanks in advance, it is greatly appreciated!

--Asif

---

### Post by A4orce84 on 2008-11-03
Anyone?

---

### Post by A4orce84 on 2008-11-03
Quick Update, ran some info and got the following data:

Linksys WMP300N - This PCI Adapter is on the list (on Documents/Wiki on ndiswrapper's website)of cards *known* to work.

lspci outputs: 02:0a.0 Broadcom Corp BCM43XG(rev 01)

lspci -n outputs: 14e4:4329(rev 01)


Also looked at the following guides to install Linksys WMP300N, but with no luck:


1. [http://ubuntuforums.org/showthread.php?t=879127&highlight=WMP300N](http://ubuntuforums.org/showthread.php?t=879127&highlight=WMP300N)

2. [http://ubuntuforums.org/showthread.php?t=611273](http://ubuntuforums.org/showthread.php?t=611273)

***3. [http://ubuntuforums.org/showthread.php?p=3284373](http://ubuntuforums.org/showthread.php?p=3284373)



#3 being referenced multiple times in the archives, but still nothing is working properly. 

If I go to the "Windows Wireless Drivers"  System-> Admin-> Windows Wireless Drivers, I see the following:

[IMG]http://img.photobucket.com/albums/v405/A4orce84/IMG_2774.jpg[/IMG]

But when clicking on "Configure Network" I see:

[IMG]http://img.photobucket.com/albums/v405/A4orce84/IMG_2776.jpg[/IMG]


So I am at a loss after trying to get things working for 2 hours, if ANYONE can offer an help, I would be greatly appreciative!  Thanks!


--Asif

---

### Post by Bizz on 2008-11-05
You do not need to mess with that to get it to work. Just click in the top right corner on the network thing, and select a wireless network. It should try to connect.

If you want to get to the network connections open up System -> Preferences -> Network Configuration. 

I get that same message, I believe it spawns from the 8.10 update from 8.04, whenthey changed the network tool. Ndiswrapper must be looking for the old one.

Tell me how the WMP300N performs, I'm using it. It's amazing when it is up, but it will drop a lot. Wonder if it's just me.

---

### Post by A4orce84 on 2008-11-08
Hey Bizz and anyone else tracking this post,


I clicked on the network manager on the upper right, and as you can see I do NOT have an option for wireless networks:

[IMG]http://img.photobucket.com/albums/v405/A4orce84/IMG_2784.jpg[/IMG]

Any help that you could provide would be GREATLY appreciated, thanks everyone! I've been banging my head against the wall with this for a few days now!


--A4orce84

---

### Post by A4orce84 on 2008-11-10
Bump, anyone?

---

### Post by ptike007 on 2008-11-11
Have you upgraded from 8.04 to 8.10 or did you a fresh 8.10 install? When I did the upgrade I lost my wireless network card. (it was not the same card as yours)
You can try with a live cd if it detects the card. (maybe after doing some ndiswrapper stuff)

dunno if this is going to work


Here you have some guys who got it to work, hope this helps...

[http://ge.ubuntuforums.com/showthread.php?t=917847]("http://ge.ubuntuforums.com/showthread.php?t=917847")

---

### Post by Brainal on 2008-11-13
I don't know what the hell I did, but I got it to work. I vaguely remember having the CD in the tray and loading up the restricted drivers. There should be the STA wireless drivers. Loaded that and got it to work. The only problem is that I get droped once-in-a-while. Unfortunately, I haven't found a workaround.

---

### Post by woodhome on 2008-11-14
Guess I should put this in the public forum,I've shared it with A4orce84 in a private message already.

The short story is that after much trouble with the WMP300N, it's now working fine under Intrepid. I'm using ndiswrapper and the most recent driver for Windows XP. A previous driver was posted to the forum for use with Hardy, but when I tried it with Intrepid it didn't work at all. I tried everything else, including both broadcom drivers available in intrepid with no luck.  Then I extracted the most current version of bcmwl5.sys and bcml5.inf from a driver I downloaded from linksys and viola!

If you are using the bcmwl5 driver check to be sure the modified date on the .sys file is Oct 17, 2007.  Also usn "sudo ndiswrapper -l" to check any other drivers present and remove them according the instructions posted here.  

[http://ubuntuforums.org/showthread.php?t=539208&highlight=WMP300N](http://ubuntuforums.org/showthread.php?t=539208&highlight=WMP300N)  (this is the same url as the one posted previously)

The 10-17-2007 driver is attached.

---

### Post by A4orce84 on 2008-11-15
Hey Woodhome and everyone else tracking,

I reinstalled the latest driver (linked above) using the directions (also linked above) and have the same results as before.

If I click on the network manager, I still only see "VPN Connections" that I can click on and nothing else.

The hardware is installed like on the first screenshot, do I actually have to go and enable the wireless network or something?

I think I'm still missing something, if anyone can offer any assistance I would appreciate it greatly! =(


Thanks!


--A4orce84

---

### Post by woodhome on 2008-11-15
A4orce, 

I'm back on line now (with a recent install of Intrepid, and my WMP300N) so maybe we can get you fixed up.  How are you connected now?

---

### Post by A4orce84 on 2008-11-15
Still nothing, hit me up on AOL or MSN if you can.


AOL SN - A4orce84

---

### Post by A4orce84 on 2008-11-18
Anyone?

---

### Post by SMB6009 on 2008-11-28
I have the same card (WMP300N) and have tried to get it to work. I was able to use it in Kubuntu 8.04, but couldn't connect to WPA-personal encrypted networks. However I was able to connect to public networks. I just burned the Live CD for Ubuntu 8.10, and when I tried to follow the steps from Kubuntu 8.04, came up with the same problem youre having. I'm going to try this: 

[http://ge.ubuntuforums.com/showthread.php?t=917847]("http://ge.ubuntuforums.com/showthread.php?t=917847")

I'll let you know how it works!

---

### Post by cavere42 on 2009-01-22
After a lot of research on here, I bought the same card, expecting to have to go the ndiswrapper route.  I brought the machine in to work with me thinking I'd need their wired internet connection to update my fresh 8.10 install.
But when I installed the card the computer just automatically downloaded the restricted driver(Broadcom STA Wireless Device) and it's worked fairly well since then-but now I haven't been able to connect for the last few days.
I'm wondering whether the ndiswrapper method with the most current driver might be a BETTER way to go?
How do I know if the restricted driver is actually letting it connect as an N device?  Would the correct driver improve the performance?
Or should I leave well enough alone and be happy that it works as well as it does, without having to DO anything?

---

### Post by sony_gamer on 2009-02-05
I recently got the WMP300N card and using ndiswrapper, installed the driver uploaded on the first page.  In doing so i can see wireless networks on the G protocol but not the N, is there a method to see N networks?

---

