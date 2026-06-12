---
title: "Removing a virus through ubuntu/linux"
date: 2010-04-27
forum: New to Ubuntu
---

### Post by chessercizes on 2010-04-27
Hey everyone,

So a friend of mine has a computer that got infected with a virus (nugel.e) and he asked me what to do and I'm not really sure what to tell him. I told him to just run a virus scan and whatnot, but to no avail.

So I was thinking, is there a way that you can run a virus / anti-spyware scan from an ubuntu or other linux distribution live cd to remove such viruses / malware?

Or really any suggestions on what I should do to help him out?

Anything would be greatly appreciated thanks!

-chessercizes

---

### Post by bkratz on 2010-04-27
> **chessercizes said:**
> Hey everyone,

So a friend of mine has a computer that got infected with a virus (nugel.e) and he asked me what to do and I'm not really sure what to tell him. I told him to just run a virus scan and whatnot, but to no avail.

So I was thinking, is there a way that you can run a virus / anti-spyware scan from an ubuntu or other linux distribution live cd to remove such viruses / malware?

Or really any suggestions on what I should do to help him out?

Anything would be greatly appreciated thanks!

-chessercizes


Here is a video on just that

[http://www.youtube.com/watch?v=9h3q5ss40oY&feature=response_watch](http://www.youtube.com/watch?v=9h3q5ss40oY&feature=response_watch)

---

### Post by HermanAB on 2010-04-27
Yes, you could boot with a Live CD and run ClamAV, but your friend will likely do better with BartPE (A Windows XP Live CD), Spybot Search and Destroy and ClamWin.

Google for BartPE and make him a CD with all the repair utilities on it.  I usually make a simple BartPE and keep the utilities on a USB memory stick - so I can update them easily.

---

### Post by Arand on 2010-04-27
F-Secure has a GNU-based LiveCD with their AV tools (there are probably many others, but this one sprung to mind).
ref. [http://www.f-secure.com/linux-weblog/2009/09/22/rescue-cd-311/](http://www.f-secure.com/linux-weblog/2009/09/22/rescue-cd-311/)

Note that the F-Secure AV tools included is proprietary freeware.

I would also like to opinionate rather strongly against ClamAV in these cases.
i.e. ClamAV sucks, don't expect it to be very useful (my general hunch from hearsay and very brief usage).


- Arand

---

### Post by lavinog on 2010-04-27
I find sometimes that removing the drive and attaching it to another win box with a decent virus scanner works pretty good.

He could also do a system restore to a previous date when the virus didn't exist (this could be a couple of months due to viruses sitting dormant on the machine)

The better solution is to do a complete wipe of the drive...this is when an ubuntu live cd can save the day.  Use the live cd to backup his important files. Some viruses can encrypt files in a way that requires you to be infected with the virus to view them...If you can't view the files/images in ubuntu, then this may be the case.

After the system is cleaned, let him know that MS is offering a free antivirus solution (microsoft security essentials)

---

### Post by chessercizes on 2010-04-27
> 
Here is a video on just that

[http://www.youtube.com/watch?v=9h3q5...response_watch](http://www.youtube.com/watch?v=9h3q5...response_watch)


Thank you!! Thats exactly what i was looking for and will definitely try it out.

> 
F-Secure has a GNU-based LiveCD with their AV tools (there are probably many others, but this one sprung to mind).
ref. [http://www.f-secure.com/linux-weblog...rescue-cd-311/](http://www.f-secure.com/linux-weblog...rescue-cd-311/)


Cool, That sounds good too. I made a cd of it just in case.

> 
The better solution is to do a complete wipe of the drive...this is when an ubuntu live cd can save the day. Use the live cd to backup his important files. Some viruses can encrypt files in a way that requires you to be infected with the virus to view them...If you can't view the files/images in ubuntu, then this may be the case.


Thank you also! I thought that wiping his computer clean would be the best option too. I'll definitely go and see what he thinks about it.

Thank you everyone for your help!

---

### Post by mike555 on 2010-04-27
+1 for Microsoft securities Essentials  , I have tested it on my old XP computers and installed it on other peoples computers ... no complaints ... 



 I have had good luck running the live antivirus .iso  from DrWeb ...    [http://www.raymond.cc/blog/archives/2008/11/15/free-drweb-livecd-to-scan-and-remove-virus-without-starting-windows/](http://www.raymond.cc/blog/archives/2008/11/15/free-drweb-livecd-to-scan-and-remove-virus-without-starting-windows/)

---

### Post by lavinog on 2010-04-27
> **mike555 said:**
> +1 for Microsoft securities Essentials  , I have tested it on my old XP computers and installed it on other peoples computers ... no complaints ... 
It appears to be a lot less bloated than other options too.

---

### Post by lkraemer on 2010-04-27
Check this site out:
[http://forums.majorgeeks.com/showthread.php?t=35407](http://forums.majorgeeks.com/showthread.php?t=35407)


These might help
LiveCD's
[http://trinityhome.org/Home/index.ph...=1&front_id=12](http://trinityhome.org/Home/index.ph...=1&front_id=12)
[http://www.caine-live.net/](http://www.caine-live.net/)

There is also a DR. Web LiveCD.  I don't have the URL Bookmarked.
[http://www.raymond.cc/blog/archives/2008/11/15/free-drweb-livecd-to-scan-and-remove-virus-without-starting-windows/](http://www.raymond.cc/blog/archives/2008/11/15/free-drweb-livecd-to-scan-and-remove-virus-without-starting-windows/)

Virus Scanner Rescue CD's
[http://download.bitdefender.com/rescue_cd/](http://download.bitdefender.com/rescue_cd/)
[http://dl.antivir.de/down/vdf/rescuecd/rescuecd.iso](http://dl.antivir.de/down/vdf/rescuecd/rescuecd.iso)
[http://www.f-secure.com/linux-weblog...lease-3.00.zip](http://www.f-secure.com/linux-weblog...lease-3.00.zip)
[http://devbuilds.kaspersky-labs.com/...ds/RescueDisk/](http://devbuilds.kaspersky-labs.com/...ds/RescueDisk/)


If your system was preloaded, readup on this information:
[http://www.howtohaven.com/system/cre...etupdisk.shtml](http://www.howtohaven.com/system/cre...etupdisk.shtml)

Or, maybe something here might apply:
[http://tech.icrontic.com/articles/repair_windows_xp/](http://tech.icrontic.com/articles/repair_windows_xp/)
[http://ubuntuforums.org/showthread.p...23#post5082723](http://ubuntuforums.org/showthread.p...23#post5082723)

If you have a M$ Windows CDR you could always try this:
[http://michaelstevenstech.com/XPrepairinstall.htm](http://michaelstevenstech.com/XPrepairinstall.htm)

lk

---

### Post by CharlesA on 2010-04-27
I've used Trinity Rescue Kit if I need to run virus scans and system recovery.

---

