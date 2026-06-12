---
title: "Sentech(IPwireless)  usb no working"
date: 2008-11-03
forum: Networking &amp; Wireless
---

### Post by deadly_sinn on 2008-11-03
howdy, i am using a usb ipwireless modem..i have installed 8.10 and  have done a list in terminal, it is connected but i cant use it! i read somewhere that in 8.4 the issue had been fixed and in network manager it showed up as an option..is this true?? and or how can i get it to work in 8.10?? i am a NOOB when it comes to most code so is there a fix out there?? please help!! either that or should i install 8.4?

---

### Post by mips on 2008-11-03
[http://mybroadband.co.za/vb/forumdisplay.php?f=90](http://mybroadband.co.za/vb/forumdisplay.php?f=90) if you don't come right.

---

### Post by deadly_sinn on 2008-11-04
bump...anyone?

---

### Post by deadly_sinn on 2008-11-04
anyone have a clue??

---

### Post by mips on 2008-11-04
Does it connect via ethernet or usb?

If usb post output of **lsusb** or **lsusb -v**

---

### Post by deadly_sinn on 2008-11-04
it connects via usb

---

### Post by deadly_sinn on 2008-11-05
i did lsusb a few days ago, didnt read the whole post..it detects the device as ipwireless and gave me a usb port..so it knows that it is there..just need to make it dialout...i just reinstalled 8.04, cuz i read that it worked, but i am back to square one...any clues?

---

### Post by deadly_sinn on 2008-11-05
bump..im desperate

---

### Post by mips on 2008-11-05
[http://www.neology.co.za/products/opensource/ipwireless/](http://www.neology.co.za/products/opensource/ipwireless/)

---

### Post by deadly_sinn on 2008-11-05
ok, i dled that but i have NO clue how to install it..and all the links on the site dont work...:P...i think this might drive me to drink:P..aha..thanks so far tho

---

### Post by mips on 2008-11-05
Sorry, I did not try the links. Maybe try and email the owner of the site.

I would also check the mybroadband site and do a search for Linux under the Sentech sub-forum.

This device is also in use in NZ but under a different name, searching on that that name would probably yield better results. I cannot remember the name though.

---

### Post by deadly_sinn on 2008-11-05
it is whoosh if i am not mistaken..i tried some of the things, but 8.10 has moved some things about and i wasnt sure what to do...i have found one or 2 scripts that i shall try on hardy and see what happens...will post my findings in the morrow:)..

---

### Post by deadly_sinn on 2008-11-05
hell yes..i got it sorted!!!!! here is the links to make it work in hardy..havent tried in 8.10...:P
this is what got me thinking to get things in the right direction...NOTE that this was the wrong answere [http://ubuntuforums.org/showthread.php?t=136989&highlight=internet+connection+problem](http://ubuntuforums.org/showthread.php?t=136989&highlight=internet+connection+problem)


this is the thing that fixed the problem that noswal was having...
i found the solution on stephens scribble pad..dont have the link but i will paste the post:
"Setup Sentech IPWireless Modem in Ubuntu

I have recently undergone the trials of getting my Sentech modem to work under Ubuntu. Sadly, the biggest cause of all my headaches was my own ignorance as a newbie to Linux.

Anyhow, the approach to getting things going comes courtesy of the Neology site (here). However I was unable to get this to work under Ubuntu 6.10. My connection worked fine under Windows XP.

While searching further I came accross a Forum entry in Neology where advice was given regards chap-secrets (here) and lo and behold there was a chat script shown with an extra line statememt: ATS7=30. This has to do with waiting for a call. The full chat script provided by rodent is shown below.

    TIMEOUT 30
    ABORT "NO CARRIER"
    ABORT "BUSY"
    ECHO ON
    SAY "Dialling sentech...\n"
    "" \rAT
    "OK-+++\c-OK" ATH0
    OK ATZ
    OK ATS7=30
    OK AT+CGDCONT=1,"PPP","sentech.co.za","username,password",0,0
    OK ATD*99#
    SAY "Waiting up to 2 minutes for connection ... "
    CONNECT ""
    SAY "Connected..."

At roughly the same time I got in touch with a very kind fellow (Ehsan Akhgari) who gave me some valuable pointers. He advised me to look into my XP temp directory for a file called IPWReg.log This file was created because the XP drivers run in Debug mode and log each connection. There I was able to see the connection syntax used by the XP driver including the correct user name and password.

In the chat script above, replace **username** and **password** with the user name and password exactly as shown in IPWReg.log.

This should do the trick. I notice that I need to reset the modem (switch it on and off) and stop pppd (using poff pppd) if my connection fails."

and that is that!!!! very exciting!!

---

### Post by mips on 2008-11-05
Glad to hear you got it working.

---

