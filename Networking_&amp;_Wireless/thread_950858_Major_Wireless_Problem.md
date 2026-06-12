---
title: "Major Wireless Problem"
date: 2008-10-17
forum: Networking &amp; Wireless
---

### Post by elnio on 2008-10-17
Hi i recently installed ubuntu n8.04 but i have a major problem connecting to my wireless router..I have a toshiba satellite A210-183 notebook with realtek wifi card.After installing the updates of ubuntu seems to be working but no connections are seen...Please tell me what to do i am in despair cause i really need this for my university..thanks in response

---

### Post by Mark_in_Hollywood on 2008-10-17
> **elnio said:**
> Hi i recently installed ubuntu n8.04 but i have a major problem connecting to my wireless router..I have a toshiba satellite A210-183 notebook with realtek wifi card.After installing the updates of ubuntu seems to be working but no connections are seen.

Toshiba Europe has a forum with help for Linux

[http://forums.computers.toshiba-europe.com/forums/forum.jspa?forumID=21](http://forums.computers.toshiba-europe.com/forums/forum.jspa?forumID=21)

Before you try that, try this:

in a terminal type 

iwconfig

and post the results here.

---

### Post by elnio on 2008-10-17
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     802.11b/g  Mode:Managed  Channel=93  
          Access Point: Not-Associated   Bit Rate:11 Mb/s   
          Retry:on   Fragment thr:off
          Link Quality=0/100  Signal level=0 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

Those are the results of wiconfig...
Please give me a guide to fix this...
I can't find my network in the list,it just says "wireless Networks" and nothing underneath

---

### Post by Mark_in_Hollywood on 2008-10-17
I believe this means that the driver isn't there. As most wireless drivers are built-in in Ubuntu's kernel, you should stop here and ask your question, showing what iwconfig displayed at UbuntuForums Wireless & Networking sub-forum (see link at bottom, this post). Guys there specialize in this. You may need ndiswrapper and the drivers that you got from Toshiba. It's not hard to do, but I'm not familiar with Toshibas at all.

Read up here before you post again at Wireless & Networking:

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

it explains a lot and when you get ready to do it, it won't be difficult. I did it once several years ago before I got a wireless card that has it's driver built-in to the linux kernel. What you are going to do is use the Realtek driver supplied by Toshiba and "wrap" (ndisWRAPPER) the Linux around it,

[http://ubuntuforums.org/forumdisplay.php?f=336](http://ubuntuforums.org/forumdisplay.php?f=336) (Networking & Wireless)

---

### Post by elnio on 2008-10-17
This doesn't help me...i can't find a thing in the forum cause nothing seems to change if i install windows driver..please somebody come on..someone must know...

---

