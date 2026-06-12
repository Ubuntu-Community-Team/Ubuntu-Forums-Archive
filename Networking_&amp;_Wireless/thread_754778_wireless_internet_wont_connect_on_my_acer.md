---
title: "wireless internet wont connect on my acer"
date: 2008-04-14
forum: Networking &amp; Wireless
---

### Post by scaryjam823 on 2008-04-14
Well i just installed unbuntu ,to dual boot with vista, onto my acer apsire 3680-2682. The first thing i noticed while it was setting up is that my light to indicate my wireless connection was not on. I thought something just hasnt started it yet. So i waited for the setup to finish once it did i noticed the light still wasnt on. Ive searched around and i havent found anything that works yet. So please help me with this problem.

---

### Post by |{urse on 2008-04-14
you mentioned that a light wasn't on. aside from going through iwconfig is there a switch to turn your wireless on or off and also are there any function (fn) button combinations you may have not thought to try?

---

### Post by scaryjam823 on 2008-04-14
yea i checked all of that right when i saw it wasnt on. Tryed turning the switch on and off still got no light

---

### Post by |{urse on 2008-04-14
okay, open up a terminal (located under accessories in the main menu) and type

iwconfig

to determine what your wireless connections name is (eth0, wlan0, ath0 etc.)

then try

iwconfig eth0 mode Managed

iwconfig eth0 essid mynetwork

change eth0 to whatever your wireless connection was called when u ran iwconfig and change mynetwork to your network essid

---

### Post by |{urse on 2008-04-14
you'll prolly need to add a sudo to those, sorry im on a fedora box atm and am half asleep as well lol

---

### Post by scaryjam823 on 2008-04-14
i didnt add sudo to them because i didnt see ur post untill now. But this is what i got when i searched them

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:""  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


then i searched iwconfig wlan0 mode managed and i got this

Error for wireless request "Set Mode" (8B06) :
    SET failed on device wlan0 ; Operation not permitted.

ill try adding sudo to them if u think i should. Btw im gonna try and fix later (in like 6 hours) when i have access to another computer so it wont take so long every time i try something.

---

### Post by |{urse on 2008-04-14
yes you definitely should add sudo, again im sorry, half asleep here

---

### Post by scaryjam823 on 2008-04-14
k and no problem im about the same here. I about to go to bed and get some well needed sleep. Ill try adding sudo to them in a few hours when i wake up

---

### Post by scaryjam823 on 2008-04-14
well i added sudo to everything still got the same thing as before when i didnt add it.

---

### Post by mikeymo1741 on 2008-04-14
I used this solution: 

[http://ubuntuforums.org/showthread.php?t=197102](http://ubuntuforums.org/showthread.php?t=197102)


The broadcom 43xx adaptor does not play well with others.   

The driver I used was   bcm4318.all.gar.tz.     Installed that and the wireless started working and automatically connected.

---

### Post by |{urse on 2008-04-14
hmm doin some research,
The Acer laptop that you have uses the Acer InviLink for wireless, this is an atheros chipset. I just googled "acer apsire 3680-2682 wireless atheros ubuntu" sans quotes. and i hit this right off the bat

[http://ubuntuforums.org/archive/index.php/t-551621.html]("http://ubuntuforums.org/archive/index.php/t-551621.html") 

O this just in, some of the aspire 3680-2682 have the BCM94311MCG chip.. ill go see if i can find u a driver

eww you're gonna have to use ndiswrapper if in fact you have a BCM94311MCG

use the lspci command to find out which wireless chip you are using

lspci | grep Broadcom

(this will at least tell you if you have the Broadcom chip or not)

so. if you're using the atheros you can try the driver mentioned in the first link and if you're using the BCM chip then heres the how-to

[http://invaleed.wordpress.com/2007/11/20/install-bcm94311mcg-wlan-mini-pci-ubuntu-710/](http://invaleed.wordpress.com/2007/11/20/install-bcm94311mcg-wlan-mini-pci-ubuntu-710/)

---

### Post by scaryjam823 on 2008-04-14
yea thats the one i have bcm94311mcg. Just to clarify everything in the qutoe's im suppose to type in the termal right?

and do i have to have an internet connection while doing it?

---

### Post by dstew on 2008-04-14
Check the link that mikeymo gave you. It installs ndiswrapper with the driver for you. It is probably a simple thing to try.

---

### Post by scaryjam823 on 2008-04-14
well i give up. I tryed both links several times. None of them worked. Im just gonna uninstall ubuntu. Im tired of messing with it.thx for your help even though it didnt work u guys

---

### Post by |{urse on 2008-04-15
/me cries a little at that

Always hate to see a new user give up =/ , I fear that Broadcom has done more to ruin the linux experience for more new users than any other hardware manufacturer. :( Well if you ever decide to give it a go again all you need is the windows driver for the broadcom chipset and you load it in with ndiswrapper, pretty easy.

---

