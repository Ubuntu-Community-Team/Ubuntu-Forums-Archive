---
title: "Netbook screen blank after Ubuntu installation"
date: 2011-06-10
forum: New to Ubuntu
---

### Post by sachin40 on 2011-06-10
Hello,

I freshly installed Ubuntu 11.04 on my Netbook from the site
[http://www.ubuntu.com/download/ubuntu/windows-installer](http://www.ubuntu.com/download/ubuntu/windows-installer)
I was able to download and I chose the 8GB option while installing. After rebooting, when it tried completing the installation, it cried that there was not enough space. Thereafter the system shutdown. And when I tried to start again, I get a complete blank screen. I cannot do anything now - neither go to Ubuntu nor go back to Windows. Totally stuck !!!
Note - I pressed f8 at boot time many times, but no effect. I cannot see anything at all due to the blank screen.
Kindly help.


From:
Sachin

---

### Post by wildmanne39 on 2011-06-10
> **sachin40 said:**
> Hello,

I freshly installed Ubuntu 11.04 on my Netbook from the site
[http://www.ubuntu.com/download/ubuntu/windows-installer](http://www.ubuntu.com/download/ubuntu/windows-installer)
I was able to download and I chose the 8GB option while installing. After rebooting, when it tried completing the installation, it cried that there was not enough space. Thereafter the system shutdown. And when I tried to start again, I get a complete blank screen. I cannot do anything now - neither go to Ubuntu nor go back to Windows. Totally stuck !!!
Note - I pressed f8 at boot time many times, but no effect. I cannot see anything at all due to the blank screen.
Kindly help.


From:
Sachin
Hi,post the information from this script so we can see what is where:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans

Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.

---

### Post by sachin40 on 2011-06-10
Hello,

I'm not sure how to do whatever you have mentioned from my Netbook. Other than that I have not installed Linux anywhere at all.
Just to repeat, the screen of my Netbook is blank at power on time itself. Any way to overcome that?

From:
Sachin

> **wildmanne39 said:**
> Hi,post the information from this script so we can see what is where:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans

Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.

---

### Post by wildmanne39 on 2011-06-11
> **sachin40 said:**
> Hello,

I'm not sure how to do whatever you have mentioned from my Netbook. Other than that I have not installed Linux anywhere at all.
Just to repeat, the screen of my Netbook is blank at power on time itself. Any way to overcome that?

From:
SachinHi, you need to boot from the livecd or usb drive however you tried to intsall it and then use the terminal to post what I ask for in post #2. You can get to the terminal by ctrl+Alt+t, sorry I did not include how to get the system going from the livecd ot usb drive in the last post.

---

### Post by sachin40 on 2011-06-11
I created the bootable usb drive. However no effect, the blank screen remains. Looks like it is not booting from the usb drive at all.
I'm also not able to get into the BIOS, despite pressing F8.
I'm totally stuck.


> **wildmanne39 said:**
> Hi, you need to boot from the livecd or usb drive however you tried to intsall it and then use the terminal to post what I ask for in post #2. You can get to the terminal by ctrl+Alt+t, sorry I did not include how to get the system going from the livecd ot usb drive in the last post.

---

### Post by wildmanne39 on 2011-06-11
> **sachin40 said:**
> I created the bootable usb drive. However no effect, the blank screen remains. Looks like it is not booting from the usb drive at all.
I'm also not able to get into the BIOS, despite pressing F8.
I'm totally stuck.Hi, f8 is probably not the key you need to use to get into bios, you need to read your screen carefully when you turn it on and it will tell you what key to hit. Also it should show information to get into boot menu hit that key and if you see your pen drive select it and see if it will boot from the pen drive.

---

### Post by fabricator4 on 2011-06-11
> **sachin40 said:**
> Hello,

I freshly installed Ubuntu 11.04 on my Netbook from the site
[http://www.ubuntu.com/download/ubuntu/windows-installer](http://www.ubuntu.com/download/ubuntu/windows-installer)
From:
Sachin


Hi, did you actually click on the Wubi installer on that page, or did you download and burn the LiveCD.  How much disk space did you have left when you started the Wubi install?

Do you get a boot menu when you turn the machine on?  Can you select and boot into Windows?  If so, delete the Wubi install, make more drive space on your machine, and try again.

Chris

---

### Post by VOT Productions on 2011-06-11
Do you have a System Repair disc or the original installation disc of Windows? If yes, what is your version of Windows?

---

### Post by wildmanne39 on 2011-06-11
> **sachin40 said:**
> Hello,

I freshly installed Ubuntu 11.04 on my Netbook from the site
[http://www.ubuntu.com/download/ubuntu/windows-installer](http://www.ubuntu.com/download/ubuntu/windows-installer)
I was able to download and I chose the 8GB option while installing. After rebooting, when it tried completing the installation, it cried that there was not enough space. Thereafter the system shutdown. And when I tried to start again, I get a complete blank screen. I cannot do anything now - neither go to Ubuntu nor go back to Windows. Totally stuck !!!
Note - I pressed f8 at boot time many times, but no effect. I cannot see anything at all due to the blank screen.
Kindly help.


From:
SachinHi, last night when I was looking at your post I did not notice that it is a wubi install,it was late and I missed it, please do not do what was mentioned in my post, here is a guide for wubi.
[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

---

### Post by sachin40 on 2011-06-13
Hello,

My blank problem got solved. I removed the batteries and inserted them back. And like magic the screen came alive showing the Windows and Ubuntu options. So I went ahead booted from Windows and deleted the Ubuntu. 
In the meantime, I created a USB bootable disk of Ubuntu, as mentioned on 
[http://www.ubuntu.com/download/ubuntu/windows-installer](http://www.ubuntu.com/download/ubuntu/windows-installer)

Then by going into bios (by using F2 key), I was able to change the booting option to USB.
then it booted from USB, and I choose the "try Ubuntu" option.
However thereafter it is taking a lot of time. The screen just displays Ubuntu and USB pen drive's LED keeps flashing, however nothing happens thereafter. How long do I need to wait?
I have a Lenovo Netbook Model 20015.

From:
Sachin.

> **wildmanne39 said:**
> Hi, f8 is probably not the key you need to use to get into bios, you need to read your screen carefully when you turn it on and it will tell you what key to hit. Also it should show information to get into boot menu hit that key and if you see your pen drive select it and see if it will boot from the pen drive.

---

### Post by wildmanne39 on 2011-06-13
> **sachin40 said:**
> Hello,

My blank problem got solved. I removed the batteries and inserted them back. And like magic the screen came alive showing the Windows and Ubuntu options. So I went ahead booted from Windows and deleted the Ubuntu. 
In the meantime, I created a USB bootable disk of Ubuntu, as mentioned on 
[http://www.ubuntu.com/download/ubuntu/windows-installer](http://www.ubuntu.com/download/ubuntu/windows-installer)

Then by going into bios (by using F2 key), I was able to change the booting option to USB.
then it booted from USB, and I choose the "try Ubuntu" option.
However thereafter it is taking a lot of time. The screen just displays Ubuntu and USB pen drive's LED keeps flashing, however nothing happens thereafter. How long do I need to wait?
I have a Lenovo Netbook Model 20015.

From:
Sachin.
Hi, if you are using 11.04 move your mouse over to the left of the screen and see if you have the unity launcher, there is nothing on the unity desktop. At the top of the screen in the right corner you will see your name,time, speaker not much more.

---

### Post by sachin40 on 2011-06-14
Hello,
 
Yes, the problem has been solved. After booting again, I could see Ubuntu getting installed.
Thanks for the all the inputs.
 
From:
Sachin
 
> **wildmanne39 said:**
> Hi, if you are using 11.04 move your mouse over to the left of the screen and see if you have the unity launcher, there is nothing on the unity desktop. At the top of the screen in the right corner you will see your name,time, speaker not much more.

---

