---
title: "Clean install 10.10"
date: 2011-01-06
forum: New to Ubuntu
---

### Post by FNQ Bunyip on 2011-01-06
Well Hello , I'm all new to linux and this is my first atempt at using it ...

My Toshiba satellite L300 crashed , so I've got a new  hdd and its listed as there in the bios .. 

I have borrowed my missuses laptop and downloaded the Ubuntu 10.10 download and its saved on her system , I then burned it to a CD .. the saved file says its an ISO and Roxio opened and burnt the disk without any problems ..

BUT  neither machine will open / run the Ubuntu download...

what now ????

---

### Post by lbarnes on 2011-01-07
Place the burned .iso disk into the drive and restart computer.  Boot from cdrom by pressing space bar immediately after your bios screen.  You'll have the option to try ubuntu as a full os with no disk changes and the option to install ubuntu.

---

### Post by mikewhatever on 2011-01-07
You have to boot from the cd. Make sure that cdrom is before the hard disk in boot order in the bios.

---

### Post by FNQ Bunyip on 2011-01-07
Thanks , and Sorry for not being clear'a... I have followed the Boot from CD/DVD  sequence ...

was about too try copying to my USB stick but have found that the teenage daughter has lent it , agggrr Kids .... 

thank so far ...

---

### Post by jink2002 on 2011-01-07
Hey, welcome to Linux!

Basically, exactly what the guys above said. I'm not sure of your computer knowledge, so I'll break it down a little more. First, you want to power down the system with the CD inside the drive. Try powering up the system again. If the Ubuntu logo comes up, great. Follow the instructions on screen and format your drive in however you see fit. 

If that doesn't happen, power the system off and on again. Depending on your system, you'll use a different button to enter the BIOS. Usually, I've found it's either F11, F1, or F8. As soon as your system receives power, mash these buttons. You'll enter the BIOS. Find the section called "Boot Order". Change the order to: 
1) CD Drive
2) HDD
3) Removable Device

Save the changes and exit. Restart the system, and you should be all set. Hope this helps!
[]("http://ubuntuforums.org/member.php?u=507043")

---

### Post by NightwishFan on 2011-01-07
This page should help, sir.
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

---

### Post by FNQ Bunyip on 2011-01-07
Thanks again ,,  Is the use of InfraRecorder an absolute must ???  

I had no option as the download showed up as a Roxio burn image (Roxio Icon)  I can download IR if it is a must have ...

My computer knowlage is reasonable ,, have had computers since 1997 First was shop built ,,, built my own systems from then till 2008,,,then  bought 3 laptops and gave up on desktop machines , much ezyer for me to keep the 3 of us happy with our computing needs ... I dont ask a lot out of my machine so $700 machines are an ezy option ...
Allways had windoz , been a firefox convert for a few years , and have been thinking of a dule boot for about 12 months after long talks with a convert over a few too many beers , never got around to it .. then as I was presented with an open and clean slate , thought I'd take the plunge and go the whole hog from scratch ..

I'm looking forward to the learning as much as anything ...


Cheers ...

---

### Post by mikewhatever on 2011-01-07
> **FNQ Bunyip said:**
> Thanks again ,,  Is the use of InfraRecorder an absolute must ???  

I had no option as the download showed up as a Roxio burn image (Roxio Icon)  I can download IR if it is a must have ...

 ...

No, Infrarecorder is not a must. I believe Roxio is quite capable of burning an image. That said, icons are just icons, and nothing else. Some users around here has an iso image presented to them as a RAR archive icon, and naturally thought they needed to unpack it.

---

