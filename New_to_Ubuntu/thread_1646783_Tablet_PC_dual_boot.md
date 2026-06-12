---
title: "Tablet PC dual boot"
date: 2010-12-16
forum: New to Ubuntu
---

### Post by rmockler on 2010-12-16
I recently purchased a Motion Computing LS800 tablet PC.  It is a neat machine, and functions well as a tablet system with Windows XP Tablet Edition software.  But, I was curious as to how it would do with Ubuntu, so I installed 10.04 for a trial run. Everything worked great out of the box, pen and all.  I didn't even have to calibrate the pen, it was perfect.  When I did the Ubuntu installation, the computer was in a dock with a keyboard attached. I had tested the onboard keyboard, and it worked fine, so I thought I was home free.  I removed the computer from the dock and keyboard, went into another room and booted it up. What a jolt I got when I realized that without a keyboard I was unable to successfully dual boot!  At that point in the startup process, my pen was not yet able to work, I could not access the onboard keyboard because Ubuntu had not started, and all I was able to do was the default boot into Ubuntu. So, in a nutshell, if I didn't have a keyboard attached, I couldn't boot into Windows at all. One of the features of the tablet PC is that normally a mouse and keyboard are not required to be able to operate the machine, but I guess booting up is not considered unless you don't want to choose between operating systems.  If any tablet PC users have experienced the same thing, I would be very appreciative if you have any suggestions as to how this situation can be overcome.

---

### Post by Favux on 2010-12-16
Hi rmockler,

In Applications > Universal Access onboard-settings try checking 'Show onboard when unlocking the screen'.  To get Onboard to show up in Universal Access you may need to go to System > Preference > Main Menu and check it so it is displayed.

You could also take a look at a mini-HOW TO I wrote '[HOW TO Install an On Screen Keyboard for login]("http://ubuntuforums.org/showpost.php?p=7959338&postcount=8")'.

---

### Post by rmockler on 2010-12-16
Thanx Favux, I tried your suggestion, and although it opened Onboard at the login screen, that was too late to handle the Grub OS selection screen.  I guess the Grub screen just happens too soon in the processing sequence, too early to involve any OS or user requests. The more I look at this, the less likely I feel my chances are of ever succeeding at managing that function (down arrow/up arrow, then enter) without a physical keyboard attached. I looked at Startup Manager with some hope, but I can't see how that will do it, either. Anyway, thanks for your help, I suspect the thread will be alive for a while.  I'll be checking it regularly.

---

### Post by Favux on 2010-12-16
Sorry, I misunderstood what you were asking.  I don't believe dual booting the way you want is possible without a physical keyboard unless one of your bezel buttons can function as a cursor arrow when booting.  It will be interesting to see how the new dual boot Android/Wn7 netbook/slates handle it.

---

### Post by rmockler on 2010-12-16
I saw a video about the Acer Aspire D250 a while ago, and although they called it "dual boot", the demo looked to me like virtual machine.  The system was already booted up, and they switched back and forth between Android and Win 7.

---

