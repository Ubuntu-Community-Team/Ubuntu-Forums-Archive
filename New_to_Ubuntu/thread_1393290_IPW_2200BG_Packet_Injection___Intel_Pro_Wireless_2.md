---
title: "IPW 2200BG Packet Injection ::  Intel Pro Wireless 2200BG ::  Inspiron700M"
date: 2010-01-29
forum: New to Ubuntu
---

### Post by systemErr on 2010-01-29
Hi, 
 
I am trying to do WEP penetration testing and I have come across this forum with claims that my wireless network card can perform "packet injection." Except the instructions are for Ubuntu, I want to know is there a way to do this for Windows XP? 
 
I have a Dell Inspiron 700M (small laptop computer), with a built-in IPW 2200BG, and a broadcom wired NIC. 
 
 
Lots of places say this wireless card cannot do packet injection, so I am very curious if your claims are true. I do have versions of Aircrack-ng and Airdump-ng and all those other "-ng" programs for Windows, in addition, I have wireshark and net stumbler. 
 
Please provide detailed instructions for me and every other windows user out there how to get packet injection working on this wireless card! 
 
(My Ubuntu live cd doesn't work and I'm not even familiar with the O/S and I would prefer not to have to fight the HUGE learning curve.... Thanks for your understanding)

---

### Post by cariboo on 2010-01-29
> Lots of places say this wireless card cannot do packet injection, so I am very curious if your claims are true. I do have versions of Aircrack-ng and Airdump-ng and all those other "-ng" programs for Windows, in addition, I have wireshark and net stumbler. 

If most places say you can't do package injection with your wireless device, and you can't make it work yourself, I would suggest that what you want to do is not possible, unless you can get a supported wireless card.

With most laptops you can replace the mini-pci wireless card with a different one.

---

### Post by lemmy999 on 2010-01-29
Its simple. If you want to use that card to crack WEP then you will have to use linux. If you want to use Ubuntu thats OK. All you need to do is patch the driver using the correct driver. Check out the aircrack pages for instructions.

Windows does not support monitor mode for wireless NICS.

I didn't know that there were "versions of Aircrack-ng and Airdump-ng and all those other "-ng" programs for Windows". Are you sure?

---

### Post by systemErr on 2010-01-29
Hi, I'm 100% positive that there are Windows versions of Aircrack... since I downloaded and can use it on my Windows XP machine.  
 
Here's the direct download for Windows if interested:  [http://download.aircrack-ng.org/aircrack-ng-1.0-win.zip](http://download.aircrack-ng.org/aircrack-ng-1.0-win.zip)
 
 
I'd prefer not using a different O/S because, again, huge learning curve.
 
 
If anybody knows a windows way of doing it, please let me know!

---

