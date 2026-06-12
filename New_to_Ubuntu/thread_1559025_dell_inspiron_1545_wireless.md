---
title: "dell inspiron 1545 wireless"
date: 2010-08-23
forum: New to Ubuntu
---

### Post by spd1989 on 2010-08-23
I know this has been posted a few different times but I still can't seem to figure out how to get wifi working on my **dell inspiron 1545**. It has a **dell wireless 1397 WLAN Mini-Card b/g/n**. The proprietary drivers that come with ubuntu 10.04 do not work. I don't understand how to compile, and change things in terminal or anything like that because I am pretty new to ubuntu. My question is, is there a driver that anyone knows of that I can download and then start ubuntu up and just install it? the kind that I wouldn't need to edit in terminal or change any codes? or am I hoping for to much. Thank you for any help. 

p.s. I have googled every combination of dell inspiron, drivers, and wifi...and I just can't find a simple explanation.

---

### Post by JBAlaska on 2010-08-23
Put the LiveCD in your drive and go to: **System, Administration, Software sources** and check the box below "Installable from CDROM". Then open a terminal and do:
```
sudo apt-get update
```

Then:
```
sudo apt-get install bcmwl-kernel-source
```

Now reboot and select the Broadcom STA driver. in **System, Administration, Hardware Drivers**.

[COLOR="Blue"]Edit:[/COLOR] 
> p.s. I have googled every combination of **dell inspiron, drivers, and wifi**...and I just can't find a simple explanation.

[COLOR="Blue"]You just need to add "Ubuntu 10.04" to your search string.[/COLOR]

---

### Post by earthpigg on 2010-08-23
hi,

Dell wifi cards are rebranded Broadcom cards.

Thread on the subject: [http://ubuntuforums.org/showthread.php?t=1390979](http://ubuntuforums.org/showthread.php?t=1390979)

look at post 53

---

### Post by Nescitur on 2011-05-03
> **JBAlaska said:**
> Put the LiveCD in your drive and go to: **System, Administration, Software sources** and check the box below "Installable from CDROM". Then open a terminal and do:
```
sudo apt-get update
```

Then:
```
sudo apt-get install bcmwl-kernel-source
```

Now reboot and select the Broadcom STA driver. in **System, Administration, Hardware Drivers**.

[COLOR="Blue"]Edit:[/COLOR] 


[COLOR="Blue"]You just need to add "Ubuntu 10.04" to your search string.[/COLOR]

Wow, I just want to say **thank you so much** because I have been unable to connect to my wireless internet for about a month and a half now.  I tried everything I could find on the internet.  Today I figured I'd try once more because I knew I'd really need the ability to use wireless this summer in the library.  I found your post, and put sudo apt-get update into my terminal.  It downloaded something, and suddenly I had the ability to "Enable Wireless".  I didn't do any of the other stuff you suggested.  Somehow, that update code was all I needed.  I had hoped that by updating to 11.04 my wireless problem would go away, but I guess I needed this additional update.
Thank you!  No more hassle!

---

