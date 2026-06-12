---
title: "Wifi - Linksys WPC11 and Scanning capability"
date: 2005-10-11
forum: Networking &amp; Wireless
---

### Post by Zaxor on 2005-10-11
Hey all,  let me first say that for the first time ever with Linux, my wireless card is actually working!  Now that I've got that out of the way with a minimum of difficulty (thanks, ubuntu :) ) I would like to expand on it.

As the title suggests, I'm using a Linksys WPC11 v3 wireless card.  When I try:

iwlist eth1 scanning

It tells me that the interface does not support that operation.  How can I get a list of available networks through this card?  I know from Windows that it is obviously capable of it, how do I have to convince Ubuntu?

Thanks for your help! :-)

---

### Post by greenwom on 2005-10-19
I have a WPC11 v4 and it does scan.....

maybe lookinto a updated driver... if you downloaded the archive with the windows driver point ndiswrapper to  the XP or Win2000 driver.  Minght work.

your cards link...
[http://www.linksys.com/servlet/Satellite?childpagename=US%2FLayout&packedargs=page%3D2%26cid%3D1115416835852%26c%3DL_Content_C1&pagename=Linksys%2FCommon%2FVisitorWrapper&SubmittedElement=Linksys%2FFormSubmit%2FProductDownloadSearch&sp_prodsku=1121874576896](http://www.linksys.com/servlet/Satellite?childpagename=US%2FLayout&packedargs=page%3D2%26cid%3D1115416835852%26c%3DL_Content_C1&pagename=Linksys%2FCommon%2FVisitorWrapper&SubmittedElement=Linksys%2FFormSubmit%2FProductDownloadSearch&sp_prodsku=1121874576896)

I didn't see a difference in the data sheets, I would think scanning was a function.  Good luck... post your results and a how-to if you get it to work.  I noticed others have had the same problem.

---

### Post by Yimmy on 2006-03-30
I'm not sure how to fix it, but the problem is it's using eth0 and not wlan0.  I've been trying to find a way to fix this since I installed Ubuntu.  

I couldn't get ndiswrapper to work with the linksys wpc11 v3 windows xp drivers.  I'm scared to mess with it too much since the card is the only way I have to connect to the internet with that machine.  The old Inspiron 3800 doesn't have an ethernet jack, only a modem, and at least it's working ... sort of.

I'm still searching and I'll post if I find the answer.  This seems to the the unanswered question for the WPC11 v3 card.

James

---

### Post by Yimmy on 2006-04-06
So I just found out that it's not necessarily the eth0 vs wlan0 causing the inability to scan.  I don't have any answers yet, but I'm still looking.  Anybody else had any successes with the linksys wpc11 ver 3 card and scanning?

---

### Post by forumposters on 2006-07-16
Did you ever get this working?  I'm about to install ubuntu for the first time myself on a Dell Inspiron 3800 with a Linksys wireless card...

---

### Post by Surgez on 2006-08-13
the wireless connectivity is restricted in usermode. You will need admin rights, as allowed under sudo in Ubuntu.

Try:  sudo iwlist eth1 scanning 

and you will get the result

---

