---
title: "Problem of installing ubuntu 9.04 live cd in Acer Aspire 4920 laptop."
date: 2009-05-01
forum: New to Ubuntu
---

### Post by maqtanim on 2009-05-01
I am an absolute beginner in Linux world. I've tried Ubuntu 8.10 live cd (that I've recieved from Ubuntu via postal mail) in my laptop, [Acer Aspire 4920]("http://www.shopacer.co.uk/scp/Acer_Aspire_Laptops/Acer_Aspire_4920_Series.html"). This laptop is pre-installed with Windows Vista. Every time I wanted to run the live cd, after the startup screen it shows the following message:

[INDENT]BusyBox v1.1.3 (Debian 1:1.1.3-3ubuntu3) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

/bin/sh: can't access tty; job control turned off
(initramfs)
[/INDENT]
To be frankly I don't know what these lines mean. I've tried the same CD with another Dell laptop and it worked fine there. 

Is it a problem with my laptop only? How can I solve this? 

Thank you!!

---

### Post by cmnorton on 2009-05-01
Is a text-mode install offered on your live CD?

If so, are you using it?

---

### Post by maqtanim on 2009-05-02
Thanks for the reply. I am not sure what do you mean by "text-mode". Sorry for that, I am totally new in Linux arena. I am not familiar with Linux at all.

I've boot my laptop from the live CD, a list of options has been shown. I selected the first one (install or run ubuntu from the live CD). Then a progress bar has been displayed (just like starting of Windows XP). Then all of a sudden the above message has been displayed and no keys were functioning.

I've tried the same CD in other laptops and desktops and it worked fine there except mine ACER. I am not sure what to do!

---

### Post by cmnorton on 2009-05-02
You'll have the option of an alternate install. Try that.

---

### Post by zeroseven0183 on 2009-05-02
Are you considering installing Ubuntu side-by-side with Vista or are you going to wipe it out and have Ubuntu as your only operating system?

If you want dual-boot then you can go to Windows, run the LiveCD and select the option Install inside Windows.

If not, you can run the whole LiveCD until you get to the Ubuntu desktop (please don't select Install on the menu, "Try" it first) and double-click the Install icon.

---

### Post by delcypher on 2009-05-02
The [alternate-CD (click here for link)]("http://www.ubuntu.com/getubuntu/downloadmirrors#alternate") can install Ubuntu without the graphical desktop. It's referred to as text-based because it is not graphical. 

Before trying the alternate CD you might want to try the following.

1. Check this disc is okay. At the boot menu select "Check CD for defects". If this test fails then either your disc is damaged or your disc drive is faulty.


2. Use safe-graphics mode. At the CD boot menu Press [F4] (modes) and select (by pressing enter) safe graphics mode. Then choose to install Ubuntu.

3. Try a few Kernel options. Sometimes the kernel (the underlying software that is linux) cannot detect your hardware properly and doesn't work properly. There are a few options you can specify to try and get things working correctly.

There's a [guide here (although it's quite old, it's still valid)]("https://help.ubuntu.com/community/BootParameters")

At the CD boot menu move down to "install Ubuntu", but don't press enter yet. Press [F6] a menu will pop up select maybe the first 3. Press [ESC] and then enter.

If you press [F6] then [ESC] you can manually add entries ( like in the guide). If you remove "quiet splash --" you will see a lot more information when you boot up (although you probably won't have time to read it).

Hope one these solutions works for you.

---

### Post by maqtanim on 2009-05-03
thanks guys... I'll let you know after trying all of your suggestions..

---

