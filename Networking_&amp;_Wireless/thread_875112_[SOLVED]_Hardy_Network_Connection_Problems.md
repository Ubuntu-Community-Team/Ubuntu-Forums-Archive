---
title: "[SOLVED] Hardy Network Connection Problems"
date: 2008-07-30
forum: Networking &amp; Wireless
---

### Post by ncc1701 on 2008-07-30
Before I Install a fresh version of Gusty, I thought I might ask if there is a fix for my problem.

I am having network connection problems after upgrading from Gusty to Hardy. Periodically, the connection gets dropped. I know there is a lot of information about wireless connection problems, but I am wired up to a router. At first I thought it was my router, but I still can remotely access the router and other services forwarded to other computers on my network. It seams the problem is only on the Ubuntu box. After several minuets it's able to reconnect but then is soon dropped again.

Is this a known bug in Hardy? Is there a fix for this or should I just go back to Gusty?

Thanks!

---

### Post by Iowan on 2008-07-30
Do you have Roaming Mode enabled?  (I'm guessing a bit, I haven't upgraded to Hardy yet).

---

### Post by ncc1701 on 2008-07-30
No I do not...should I?

Also, when I am at home, I can locally run this command 
```
/etc/init.d/networking restart
```
and it works again

---

### Post by Iowan on 2008-07-30
Probably not - I'd have suggested you turn if off... 
You can check the bug list.  I remember something like this when Hardy first came out (but don't remember the solution).  I remember thinking it sounded like DHCP releasing/resetting the connection.  I'll see if I can find the thread...

[http://http://ubuntuforums.org/showthread.php?t=726894]("http://http://ubuntuforums.org/showthread.php?t=726894")

---

### Post by ncc1701 on 2008-07-30
Great thanks! I have removed the network manager and we'll see if the connection stays. I will let you know.

---

### Post by ncc1701 on 2008-07-30
Nope, that didn't work eaither...I still lost the connection.

I guess the next step would be to reinstall Gusty :?

---

### Post by Iowan on 2008-07-30
I forgot to outright ask if your connection is static or via DHCP.  
While I'm remembering... seems like there was a thread about ACPI doing odd things (of course I don't remember where).

BTW, yet another thread WAS solved by a re-install.

---

### Post by ncc1701 on 2008-08-01
I got Gusty installed and setup again and it seams to be working. I haven't had a timeout...yet, hopefully not!

Thanks for your help!

---

### Post by ncc1701 on 2008-08-01
Well, I guess I spoke too soon.

Must be the router. Funny thing is it's only with the Ubuntu box. Other servers with different ports work fine. I am using static IP in Ubuntu but still the same problem, but if I restart the network in Ubuntu, it works again...

On to the next step...

---

