---
title: "Ubuntu wont boot from usb on hp-mini."
date: 2010-12-25
forum: New to Ubuntu
---

### Post by hpmini on 2010-12-25
Hi!

Ive just recently bought a hp-mini 210-2013eo. I wanted to put ubuntu netbook remix on it so i went and downloadeed the iso aswell as the universal usb installer and put it on my usb thumbdrive. I rebooted my laptop and booted from the usb. There is a flashing white text at the top of the screen saying something about linux system, and then the screen goes black with a white blinking marker in the top left corner. Nothing more happens. I tried re-downloading the image and the usb installer. Didnt help. I tried booting the memstick in another computer and it worked like a charm. I downloaded the crunchbang iso, same procedure. Worked well on my other laptop, only a white marker on my mini. I hope someone can help me, because i am at a lost.

Thanks in advance,
Joakim.

---

### Post by amjjawad on 2010-12-25
> **hpmini said:**
> Hi!

Ive just recently bought a hp-mini 210-2013eo. I wanted to put ubuntu netbook remix on it so i went and downloadeed the iso aswell as the universal usb installer and put it on my usb thumbdrive. I rebooted my laptop and booted from the usb. There is a flashing white text at the top of the screen saying something about linux system, and then the screen goes black with a white blinking marker in the top left corner. Nothing more happens. I tried re-downloading the image and the usb installer. Didnt help. I tried booting the memstick in another computer and it worked like a charm. I downloaded the crunchbang iso, same procedure. Worked well on my other laptop, only a white marker on my mini. I hope someone can help me, because i am at a lost.

Thanks in advance,
Joakim.


Hello and welcome to Ubuntu :)

Kindly list the specifications of your machine especially the Graphics Card.

I know it worked on the other laptop but just to be in the safe side, please check the MD5SUM of your downloaded iso file. In my signature, there's a link (step1) with howto check md5sum.

What tool you used to create the LiveUSB? I would suggest: [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

### Post by hpmini on 2010-12-25
Intel Atom N455 Processor 1,66 GHz
1 GB DDR3 ram
250 GB Sata hdd 7200 rpm.
10,1" WSVGA Infinity BrightView 
Intel GMA 3150 up to 256 MB shared
WLAN 802.11b/g/n, LAN 10/100

I havent got access to the image at the moment because it is at another computer. it seems unlikely though, as i deleted the fist one, redownloaded it and then downloaded a different distro from a different sites, and all three had the same problem and they all worked on my other laptop. i will however check the md5 sum when i have access to the iso.

I used the "univesal usb installer" linked to at the instructionpage for ubuntu netbook remix. Im currently writing this from a ubuntu install on my laptop that was installed from windows and the booted from the hdd and finnished the setup. When i try sudo get-apt install ubuntu-netbook, it sauys i allready have it installed. But it doesnt look like the screenshots, how can i check version? 

Im about to put backtrck 4 on a usb stick which is based on a different kernel than ubuntu if i understood it correctly. hopefully that will work.

---

### Post by D4J0K3R on 2010-12-25
I don't know if it helps, but I've installed 10.10 netbook edition yesterday from a USB stick & I had an error message.
I found somewhere on the web that if you type: *help* <enter> the installation resumes flawlessly.
I know it sounds crazy, I didn't believe it, I tried it & at my surprise it works!
Then again, it might not be your case...

---

### Post by amjjawad on 2010-12-26
> **hpmini said:**
> Intel Atom N455 Processor 1,66 GHz
1 GB DDR3 ram
250 GB Sata hdd 7200 rpm.
10,1" WSVGA Infinity BrightView 
Intel GMA 3150 up to 256 MB shared
WLAN 802.11b/g/n, LAN 10/100

I havent got access to the image at the moment because it is at another computer. it seems unlikely though, as i deleted the fist one, redownloaded it and then downloaded a different distro from a different sites, and all three had the same problem and they all worked on my other laptop. i will however check the md5 sum when i have access to the iso.

I used the "univesal usb installer" linked to at the instructionpage for ubuntu netbook remix. Im currently writing this from a ubuntu install on my laptop that was installed from windows and the booted from the hdd and finnished the setup. When i try sudo get-apt install ubuntu-netbook, it sauys i allready have it installed. But it doesnt look like the screenshots, how can i check version? 

Im about to put backtrck 4 on a usb stick which is based on a different kernel than ubuntu if i understood it correctly. hopefully that will work.

Try to check MD5SUM and try to use [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

Before you create the LiveUSB, try to format it.

---

### Post by ubaidillah on 2010-12-27
> **hpmini said:**
> Hi!
 
Ive just recently bought a hp-mini 210-2013eo. I wanted to put ubuntu netbook remix on it so i went and downloadeed the iso aswell as the universal usb installer and put it on my usb thumbdrive. I rebooted my laptop and booted from the usb. There is a flashing white text at the top of the screen saying something about linux system, and then the screen goes black with a white blinking marker in the top left corner. Nothing more happens. I tried re-downloading the image and the usb installer. Didnt help. I tried booting the memstick in another computer and it worked like a charm. I downloaded the crunchbang iso, same procedure. Worked well on my other laptop, only a white marker on my mini. I hope someone can help me, because i am at a lost.
 
Thanks in advance,
Joakim.
 
You can try this [http://ubuntuforums.org/showthread.php?t=1653120&page=3](http://ubuntuforums.org/showthread.php?t=1653120&page=3)

---

