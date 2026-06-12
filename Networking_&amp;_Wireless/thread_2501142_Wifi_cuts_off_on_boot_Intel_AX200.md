---
title: "Wifi cuts off on boot Intel AX200"
date: 2024-09-24
forum: Networking &amp; Wireless
---

### Post by sniper1k5 on 2024-09-24
Hello,
I use kubuntu 24.04.1 with Wifi 6 AX200 160mhz adapter. When the wifi works it works perfectly fine without any issues.
But i can't get it to work when it doesn't, usually i have to turn off the computer for like 2 hours before it starts working.
I tried restarting net services and alot of other stuff but nothing works, this is the 3rd time this happens and its really starting to annoye me.The wifi tab straight up says "No connections available" however in the settings my wifi is setup perfectly fine but it wont connect.

Anybody had this issue before?

---

### Post by sniper1k5 on 2024-09-24
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=294300&stc=1[/IMG]

---

### Post by techman12 on 2024-09-25
Greetings. I wish that I had answers for you, but unfortunately I don't. I can confirm that I also have two Intel WiFi 6 AX200NGW (AX3000) cards, one each in two different Dell machines. One was removed and replaced (as I thought it was a bad card) with another card of the same type and seems to work fine now - so far. When the second one started to act weird I thought that I would start investigating the message boards. Your description in the first message - sometimes it works, sometimes it doesn't, and your screen shot from your second message, are exactly the same as I am experiencing. I am using Kubuntu 24.04. I also have a very brief message on startup that notifies me that I appear to be connected to a network, but with limited connectivity or something along those lines. From other searching it appears others may be having similar issues. I have several of these same cards in older Dells running Kubuntu 22.04 with no problems.

---

### Post by brcisna-u on 2024-11-18
Just throwing this into the conversation.
ON two Dell machines I have have two wifi cards in each of them. AX200 and 200be Intel 
Each one if you reboot many times,,,each of the two cards will enumerate up,one number,,,then next reboot will enumerate back down one number,,,,if you look at 'ip a' each reboot.
This thread is pretty old by now,,, but with the latest iwlwifi package that i could find ,,cant remember the date labeled. this no longer happens,,,,but,,i do get strange power errors,,,warnings,, in dmesg ,,constantly on each of the two machines. Pretty certain the dmesg warnings are do to bluetooth on the cards.
the throughput on any combination of these cards is lousy,,,unfortunately.  Can only get around 160Mbps at best to  a wfii7 router.  Have seen YouTubes were people on macs are exceeding 2Gbps to a  wfi7 router..with same cards 
 
Good Luck!

---

### Post by prcowley on 2024-11-20
What were the error messages in the journal in relation to this?

I had no problem on 24.04 but when I moved to 24.10 I started having many problems with the WiFi dropping out. Still not fixed but a workaround is in the wifi config GUI screen, under the WiFi security tab, I changed the password setting to "store password for all users (not encrypted).  There seemed to be a timing issue if you router keeps renewing the lease time of the connection. In my case the router renewed the lease every 5 minutes (I share the router with 13 other people and I don't have admin access to it).  It seems to have worked so far (fingers crossed) but this might not be what is causing your issue.

Cheers
Pete

---

