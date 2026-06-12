---
title: "Epson NX420 Printer Driver Installation"
date: 2011-06-05
forum: New to Ubuntu
---

### Post by Da_Bomb_Digity on 2011-06-05
hello, I'm trying to install this printer but I'm a complete noobe with linux. Can anyone help me out? I've already downloaded the drivers, and I'm trying to figure it out in the terminal but am having no luck. 

Thanks in advance!

---

### Post by ramjet_1953 on 2011-06-05
Hi, there and welcome to Linux.

Just to be sure that you have the correct driver, I suggest that you follow this link:

[http://www.openprinting.org/printer/Epson/Epson-NX420_Series](http://www.openprinting.org/printer/Epson/Epson-NX420_Series)

Download the .deb package (32 bit, or 64 bit, depending upon your system) to a convenient location.
(Either your desktop, or into your downloads folder.)

Once you have it, then just right click on it and select 'Open with Ubuntu Software Center'.

Regards,
Roger ;)

---

### Post by Da_Bomb_Digity on 2011-06-05
I did that, and now it's saying that it can't install the lsb. Any suggestions?

---

### Post by kamcknig on 2011-06-08
If you are still having trouble with this try installing lsb. 

From a terminal:
sudo apt-get install lsb

Then open the package you downloaded.

---

### Post by Da_Bomb_Digity on 2011-06-08
I tried that, it gives me this message:

The following packages have unmet dependeicies:
 lsb : Depends: lsb-desktop but it is not goingto be installed
E: Broken packages

---

### Post by kamcknig on 2011-06-08
Did you then try to install that?

apt-get install lsb-desktop

When I did it, mine didn't ask for that :/

---

### Post by Da_Bomb_Digity on 2011-06-08
When i did that, it gives me this message now: 
The following packages have unmet dependencies: 
 lsb-desktop : Depends: libqt4-gui (>= 4.3) but it is not going to be installed 
E: Broekn packages

---

### Post by kamcknig on 2011-06-08
try apt-get -f install lsb

-f tries to fix dependencies

---

### Post by SoFl W on 2011-06-08
Da_bomb,

I have an Epson Workforce 610 Wireless Printer/Scanner.  When I installed it to 10.4, I had to download the drivers from the [Japanese website]("http://www.avasys.jp/lx-bin2/linux_e/spc/DL1.do") which I found at these two Ubuntu threads.
[http://ubuntuforums.org/showthread.php?t=1393162](http://ubuntuforums.org/showthread.php?t=1393162)
[http://ubuntuforums.org/showthread.php?t=1407631](http://ubuntuforums.org/showthread.php?t=1407631)

The website has changed since my install, but I remember the drivers and software  did not appear in the correct order and the dependencies were solved by trying the other software and then coming back to the ones that didn't work.  I do not know if that is still the case.

However when I tested 11.4 (ubuntu, xubuntu) and selected network printer it found the printer after a bit and then I had to select the correct software to download, it did everything.  Did you try installing it with the add printer feature?

---

### Post by Da_Bomb_Digity on 2011-06-08
I tried that, and i get the same message as before. 

@SofI W: Will it still work? those drivers are for a different printer.

---

### Post by SoFl W on 2011-06-08
> **Da_Bomb_Digity said:**
> I tried that, and i get the same message as before. 

@SofI W: Will it still work? those drivers are for a different printer.


That site should take you to the drivers/software site.  Installing it should be the same, but using different packages.

Did you see if it is already available in CUPS?

---

### Post by Da_Bomb_Digity on 2011-06-08
> **SoFl W said:**
> That site should take you to the drivers/software site.  Installing it should be the same, but using different packages.

Did you see if it is already available in CUPS?

Yes it is there, but it won't install it because it says again that I have broken packages.

---

### Post by kingofspades8 on 2011-06-15
I'm surprised this became so difficult.  Have you tried just removing the drivers, then reconnecting the printer and letting Ubuntu figure it out.  It will give you a choice of 2 drivers to install automatically, one open source and one proprietary.

I have the same Epson model and printing works.

[http://www.omgubuntu.co.uk/2011/04/ubuntu-11-04-gets-automatic-epson-driver-download/](http://www.omgubuntu.co.uk/2011/04/ubuntu-11-04-gets-automatic-epson-driver-download/)

If you're gonna use it as a scanner you'll need to install iscan from the Avasys website.

[http://ubuntuforums.org/showthread.php?p=10943671#post10943671](http://ubuntuforums.org/showthread.php?p=10943671#post10943671)

---

### Post by wildmanne39 on 2012-07-30
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

