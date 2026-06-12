---
title: "Black screen when trying to boot from USB"
date: 2010-01-29
forum: New to Ubuntu
---

### Post by j2the242 on 2010-01-29
Hello everyone,

Ok so I have tried every method you awesomely helpful people have offered for me....and here is where I am at.

Unetbootin has successfully put the iso on my usb and i figured out how to boot from the USB.

Sadly all that I get once I boot from the USB is a black screen with a small white blinking line.

Ive left it for 5 minutes, 10, 20, and still just a black screen.

What  does this mean?

---

### Post by NightwishFan on 2010-01-30
Are you able to get to the Ubuntu Boot Menu, or does it just stay black after the vendor (bios) screen. (The boot menu is what says "Install Ubuntu" etc..)

If you cannot get to there, perhaps it is trying to boot from the wrong drive, or you incorrectly installed the USB.

---

### Post by j2the242 on 2010-01-30
it just goes black after the bios menu. I tried it with the usb drive and the flash drive, using unetbootin and 7-zip, using ubuntu, kubuntu, and easy peasy (all of these things were at different times obviously. I have been trying this for over 30 hours) 

All I get is a black screen with a blinking line, everytime, with no boot menu.

---

### Post by NightwishFan on 2010-01-30
If you are using Ubuntu ISOS, try the USB installer that is preinstalled. It has worked for me. When I am out of CDs, I use that to make bootable USBs, and supergrubcd to boot them to reinstall. (My pc cannot boot from USB). If you have used this, my advice is nigh worthless.

I think the problem is that the machine does not know how to boot it right. Can you choose a specific USB device to boot from in the bios?

---

### Post by C.S.Cameron on 2010-01-30
Check the MD5Sum of your iso. 
They go bad more often than you would think.

---

### Post by comicosmos on 2011-03-02
Hello,

I encountered the same problem.

I made a bootable USB disk with various kinds of tools, only to see the black screen on various kinds of desktop PC/laptops after BIOS screen.

Then I realized maybe this USB device is not "boot capable". It is a kingston 1G data traveller and I googled, only to confirm my suspicion.

(It is another story, I put it here just in case that somebody is curious: my kingston USB storage device uses [[COLOR=#0909f7]SK6281/SK6211[/COLOR]]("http://www.5z18.com/html/55-5/5343.htm") as the control IC. the old model SK6281AA does not support usb boot because the IC does not have the function. However, the newer model SK6281BA does support usb boot. As the manufacture didn't configure the function when shipped a geek need to download the appropriate software and  "open" the function himself. Sorry that I can only provide google search result in Chinese: [GoogleSearchResult]("http://www.google.com.hk/search?hl=zh-CN&newwindow=1&safe=strict&biw=1280&bih=886&q=SK6281%2FSK6211+%E9%87%8F%E4%BA%A7+%E4%B8%8B%E8%BD%BD&aq=f&aqi=&aql=&oq="))

I am afraid you have to try another USB disk. Good Luck!

---

### Post by CrimsonNinja on 2011-08-16
I'm having this same issue as well. the only thing is, at one point my usb was working fine to boot into the ubuntu and linux (2 separate times). But then I changed it to a different one (untangle) and when I changed it back to Backtrack it just kept giving me the blinking line everytime, no matter how many times I tries to re-format and re-install an OS on the usb.

---

### Post by CrimsonNinja on 2011-08-17
I used unetbootin another flash drive I had, same kind, and it works just like the other used to.

---

### Post by pi.boy.travis on 2011-08-17
Use gParted to make sure that the 'bootable' flag is on for the partition on the USB drive.

---

