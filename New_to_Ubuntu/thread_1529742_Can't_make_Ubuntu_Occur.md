---
title: "Can't make Ubuntu Occur"
date: 2010-07-12
forum: New to Ubuntu
---

### Post by severean0 on 2010-07-12
Hi
I'm trying to install ubuntu but when I do so, using a live USB, the screen goes blank and the monitor displays "out of range". I have googled around and as a result of that, I tried the same thing using the alternate, text-based installer. That didn't work as it couldn't mount the "CD", even though it was actually a USB.

---

### Post by mike555 on 2010-07-12
How high resolution is your monitor ?  I had that problem on an old crt that was 1024 x 768 ... perhaps you could borrow a monitor just to install, then set the resolution down .

---

### Post by severean0 on 2010-07-13
it's 1920x1080. I have also tried to install using my HDTV which supports 1280x768. I'm installing 10.04, but previous versions have installed fine, and then I've just needed to install ATI drivers for my Radeon 5850.

---

### Post by severean0 on 2010-07-13
Any Ideas? Surely installing the operating system is pretty basic stuff. If it's this hard just to install it, why bother with Ubuntu at all?

---

### Post by Jazzy_Jeff on 2010-07-13
> **severean0 said:**
> Any Ideas? Surely installing the operating system is pretty basic stuff. If it's this hard just to install it, why bother with Ubuntu at all?

Yours is not a common problem. It could be a problem with compatibility with the video card or the monitor. What video card and monitor do you have?

---

### Post by severean0 on 2010-07-13
My monitor is a pretty bog standard monitor. Made by an obscure Taiwanese company called Asus. You probably haven't heard of them. The colour of the monitor is black, which I hope is compatible. I have also tried to install using my HDTV, also black, made by an obscure Korean company called Samsung. It supports 1280x768. I'm installing 10.04, previous versions have installed fine, I've just needed to install ATI drivers for my graphics card which is made by the even more obscure comany ATI (it's a Radeon 5850). The point I'm sarcastically making is that these are not non-standard hardware, and previous versions of this OS have installed no trouble, so I don't understand why I'm having a problem.

---

### Post by Jazzy_Jeff on 2010-07-13
> **severean0 said:**
> My monitor is a pretty bog standard monitor. Made by an obscure Taiwanese company called Asus. You probably haven't heard of them. The colour of the monitor is black, which I hope is compatible. I have also tried to install using my HDTV, also black, made by an obscure Korean company called Samsung. It supports 1280x768. I'm installing 10.04, previous versions have installed fine, I've just needed to install ATI drivers for my graphics card which is made by the even more obscure comany ATI (it's a Radeon 5850). The point I'm sarcastically making is that these are not non-standard hardware, and previous versions of this OS have installed no trouble, so I don't understand why I'm having a problem.

I am just trying to help with your problem. If this is your attitude then good luck to you. God bless you. This is also posted in the Absolute Beginners section of the forums, so I normally expect most people with problems here to be beginners.

---

### Post by severean0 on 2010-07-13
apologies for my sarcasm, no offence intended. It should be a simple thing, I feel, but alas, windows 7 is serving me well enough, I guess I'll just have to stick with this perfectly functional, installable operating system, and leave Ubuntu to those who really know what they're doing with computers.

---

### Post by Jazzy_Jeff on 2010-07-13
In your previous posts you did not say that other versions had installed without any problems. Stick with whatever works for you. I just prefer my operating system to work for me and not the other way around.

---

### Post by severean0 on 2010-07-13
I did mention about earlier versions working before, but no matter, I'm still a relative newcomer to ubuntu. If you're willing to forgive my frustration and help me fix this I'd appreciate it. If so let me know what information you need.

---

### Post by javierrivera on 2010-07-13
> I don't understand why I'm having a problem.

And seems like you are trying quite hard to been unable to understand it being so rude.

Luckily there is a bit of useful information hidden in your post. Radeon 5850 doesn't work out of the box with 10.4. 

There are three workarounds in the [bug]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/560306") report:

a) Connect the monitor to the other DVI (if you have two). Try both before and after booting. After installing the ATI proprietary drivers both should work.

b) Install from the alternate CD, boot to the recovery console. Install ATI drivers from the command line.

---

### Post by Jazzy_Jeff on 2010-07-13
I personally use the Alternate CD. I find I have less issues with it. How did you put the image on the USB drive? I use a program called UNetbootin. Also make sure when you plug the USB drive in go into your bios and make sure it is at the top of the list when booting. I have to do this every time I plug the USB drive in.

Hope this helps. Let me know.

---

### Post by mike555 on 2010-07-13
try installing by adding ;

at the very first screen, the one with just the rectangle (it’s meant to be a keyboard) and a human figure, press any key - spacebar will do.

Then choose your language.

Then make sure you have “Try Ubuntu without any changes” selected, and then press F6

Add this to the end of the command line:

Code: Select all
    i915.modeset=0 xforcevesa

---

### Post by severean0 on 2010-07-13
> **javierrivera said:**
> And seems like you are trying quite hard to been unable to understand it being so rude.



Quite right; simple task- install the OS, standard-looking hardware, previous versions were okay, googling revealed no immediate compatibility issues, so I got frustrated. Apologies. Being a beginner, I'd need some more help using the solutions you mentioned.

> **Jazzy_Jeff said:**
> I personally use the Alternate CD. I find I have less issues with it. How did you put the image on the USB drive? I use a program called UNetbootin. Also make sure when you plug the USB drive in go into your bios and make sure it is at the top of the list when booting. I have to do this every time I plug the USB drive in.

Hope this helps. Let me know.

I've tried installing with the alternate, text-based installer. I put the image on USB using the tool mentioned on the ubuntu download page, at [www.pendrivelinux.com](www.pendrivelinux.com). The installer was "unable to mount the CD", so I couldn't install using that method. Perhaps that installer is not designed to be used with a USB, and I need to burn it to an actual optical disc..?

> **mike555 said:**
> try installing by adding ;

at the very first screen, the one with just the rectangle (it’s meant to be a keyboard) and a human figure, press any key - spacebar will do.



When you say the first screen do you mean the screen you see once you boot using the live image, or in the text-based installer?

---

### Post by javierrivera on 2010-07-13
> I'd need some more help using the solutions you mentioned.

Have you tried to change the DVI cable?. It's the easiest solution if it works. You should have two DVI ports in your card, they are the place where the monitor cable plugs. Try both.

If your computer has an onboard video card you can install Ubuntu using this card, then install the ATI drivers.

> Perhaps that installer is not designed to be used with a USB, and I need to burn it to an actual optical disc..?

You are right, you will need a real CD for the alternate install. The alternate installer will let you install Ubuntu, but you will be unable to boot to the GUI.

After installing you should choose to boot in safe-mode (press ESC while booting for a menu). The system will boot to a command prompt. There you should write:

```

$ sudo apt-get update
$ sudo apt-get install fglrx
$ sudo ati-config --initial
$ sudo reboot

```
> 
simple task- install the OS

We have probably quite different views on what is a *simple task*.

---

### Post by severean0 on 2010-07-13
"Install the OS" *should* be a simple task, unless it is your aim to retain Ubuntu as a niche operating system for IT professionals only. I believe that is at odds with Canonical's aim for the OS. Thanks for your help, I've tried the simple solutions, I'm not going to use the command line because I believe I shouldn't have to. I'll stick with Windows 7 for now, and perhaps at the next release of Ubuntu I'll give it a whirl.

---

### Post by QIII on 2010-07-13
I understand that this is frustrating.  I understand that you are frustrated.  That is natural, and I don't blame you.

Unfortunately, when *install the OS *involves a proprietary driver over which Canonical has no control the OS is not the issue.  It is how the hardware OEM provides it.

To install the Linux driver from the OEM requires the use of the terminal to initialize it.

Again, I have to dispel a common misconception:

Windows does not support hardware.  Microsoft makes no effort at all to accommodate particular hardware.  Hardware OEMs make certain that their drivers are compatible with Windows.  I don't blame them.  That is where the money is.

Because the OEMs have done that work, it appears to the user that Windows "supports" their hardware.  That is not the case.  But Microsoft does nothing to correct that misconception.  It works pretty well for them.  So why say anything different?  Look at the box the next time you buy hardware.  Does it say "Supported by Windows".  Or does it say something like "Designed for Windows" or maybe "Works with Windows"?  The fact that Windows has a driver available is due to the fact that the OEM made it available in the Microsoft driver base.  Microsoft certainly didn't write a driver for it.

AMD/ATI is committed to Linux and has been since AMD bought ATI in 2007.  There are simply some things about Linux that require a different approach to installing drivers.

Many nVidia drivers also have to be initialized through the terminal to be properly configured.

This is not unique to Ubuntu.  

It is not *our aim *to keep it a niche platform for IT professionals.  There are plenty of people who use Linux distributions who have trouble working their TV remotes.  My kids use Ubuntu and neither of them has any interest in computers or IT beyond turning the thing on and using Facebook or writing a term paper.

---

### Post by severean0 on 2010-07-13
Thanks for your response. I appreciate the problem faced by an open-source platform with proprietary drivers, its something I'm familiar with having installed such drivers with previous versions of Ubuntu. But at least the installation was possible. Even though the graphics weren't pretty, you could still see something on the screen during the install process and hence you were able to *install the OS*. I guess that is why I'm frustrated here; my lack of knowledge of linux prevents me from understanding why going from one version of a distro to the next makes basic support for the same piece of hardware disappear. I mentioned not using the command line because I believe someone from Canonical once claimed that use of the terminal was unnecessary in Ubuntu, because it's mature enough for general consumption, or words to that effect. Indeed, I'm running 10.04 netbook remix on my Samsung NC10 and it's frankly, awesome. Hardware support is flawless and installing the basics like Flash and audio codecs, hasn't necessitated the use of a terminal. I'm sure the next release of Ubuntu will be better, it always is, so I'll wait for that.

---

### Post by QIII on 2010-07-13
I equivocate on this subject.

Would it be possible to create scripts so that when you click the button to install the proprietary driver, the initialization would be done?  Probably.

Do I want someone deciding to run something like that in the background?  I don't know.  It does happen for other things.

Since you already have to enter your password and are running under elevated privileges already, 

```
sudo aticonfig --initial
``` 

is not that much of a stretch.  I guess the assumption there would be that if you want to install the proprietary driver, you want to initialize it, too.

---

### Post by javierrivera on 2010-07-14
> "Install the OS" should be a simple task

It is not. It can't be and it will never be. I know plenty of people who make a life just (re)installing windows.

You can try to hide the complexity under wizards and warming screens but as soon as something unexpected happens all will fall revealing the ugly face of computers. A very complex piece of technology.

> my lack of knowledge of linux prevents me from understanding why going from one version of a distro to the next makes basic support for the same piece of hardware disappear

You don't need any knowledge of linux to understand this. It's a bug. An error. A failure. A human mistake.

Someone enabled KMS in the radeon driver for the 58xx cards but while it was not enabled in the kernel. Nothing to blame ATI. Just a lack of coordination between ubuntu developers.
> 
Since you already have to enter your password and are running under elevated privileges already
He is unable to install Ubuntu.

---

### Post by severean0 on 2010-07-14
> **javierrivera said:**
> It is not. It can't be and it will never be. I know plenty of people who make a life just (re)installing windows.


You've misunderstood me- of course the task itself is not simple, I'm talking about the end-user experience. Indeed, it *should * be the most mind-numbingly simple task for the end-user, given that most PCs don't actually ship with this particular OS installed on them... and the installation process must therefore be conducted by the end-user him/herself.

---

### Post by javierrivera on 2010-07-14
I have a new idea. Maybe you can try a daily build of [Lucid]("http://cdimage.ubuntu.com/lucid/daily-live/20100714.1/lucid-desktop-i386.iso"). 

This is a testing image for the next version of Ubuntu 10.4, it will be 10.4.1 and should be released on June 27th. The fix for you bug have been marked as released, so this iso should work with your computer. Unluckily I can't test it as I don't have a Radeon 58xx.

Please if you can try it, report here your results.

---

### Post by QIII on 2010-07-14
> **javierrivera said:**
> He is unable to install Ubuntu.

Indeed.  If this were handled in the installation -- i.e.:  Oh, dear, I'm finding an ATI card, so I need to install the driver ....

But people also run into this sort of thing when they HAVE installed Ubuntu and then have to go to the terminal to activate after installing the proprietary driver.  So this goes beyond just initial installation.

---

