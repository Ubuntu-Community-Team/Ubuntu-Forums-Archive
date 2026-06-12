---
title: "Would like to switch, but need to address these few issues..."
date: 2010-06-07
forum: New to Ubuntu
---

### Post by Unhyper on 2010-06-07
I've been using Windows since 3.0, so I'm pretty used to it. Windows, however, doesn't really let you define for yourself how you use your computer; it defines it for you, and expects you to adjust. Which is all well and good until you experience Linux.

I've gone back to Windows, come back to Linux, gone back to Windows... The reason I've kept going back has nothing to do with "it's what I'm used to" or "it just works." I doubt anyone moves from Windows to Linux because Windows "just works."

I would like to dump Windows entirely, because experience has shown me that I am no good at dual-booting. I can set it up easily and all that, but I dislike rebooting into another OS. I run my system 24/7 and like my apps and email client etc to be more or less instantly available. So I tend to stick with one OS more than the other. I don't find myself learning Linux too well if I keep spending a lot of time logged into Windows.

There are just a handful of issues that I have not been able to resolve, but I would like to, so I can wave goodbye to Windows entirely. I don't worry about minor issues, usually there are ways around them. The following issues are not minor issues for me.

1) Divx encoding that produces Divx files that are compatible with my standalone DVD/Divx player. For years I have used Divx Author to encode various video formats into Divx, for playback on my DVD player. I have not found any application that can do this successfully on Linux. I know there are many apps that are supposed to do this, acidrip, dvd::rip, k9copy, arista, et al. But either the outputted file doesn't play on the player at all, or the output is out of sync or jerks every second or so as if the program took one frame every second and copied it a few times (not audio). I don't know whether this is a software issue or a settings issue or a codec issue.

2) Word 2007. I need it for a particular purpose. I know about OO.org and it's great etc. However, I use a collection of macros that I have purchased for Word, a commercial add-on. There is no replacement for this product either for Linux or Mac. It is very inconvenient to boot into Windows just to use Word when I do my actual writing under Linux apps like OpenOffice. Wine does not play nice with Office 2007.

3) I can't seem to get my Lightscribe drive to burn labels. I replaced a LabelFlash drive with a LightScribe and bought a fair amount of LS media for the purpose of using them, but again, kind of a pain to boot into Windows just to burn a label.

4) Adobe Flash Pro doesn't run through Wine either, to my knowledge. Some websites I've worked on in the past utilize Flash, and it is impossible to modify those components without access to Adobe Flash. As far as I know there is no Linux alternative for Flash Pro due to closed code.

Please note that this is not a list of "things Linux fails at" or any sort of attempt to criticize Linux or FOSS developers. These are just real issues that prevent me from ridding myself entirely of Windows, which is something I'd like to do. I know dual-booting works for many people, but it's just not something that's really been working for me. I'd appreciate any suggestions or advice you may have. Thanks.

---

### Post by anewguy on 2010-06-07
I don't know your hardware specs, but have you considered running Windows in a VirtualBox virtual machine?  I currently don't because I had to sell my "good" PC and what I have now is more than a little slow with vbox on it.  You could always try it - just go to the Sun/Oracle site and download the PUEL version, not the one from the repos in Ubuntu.  The reason I say that is that Ubuntu stays with free open source software, and the version of VirtualBox that is open source doesn't support USB.  The PUEL version is still free, it's just not open source, but it has USB support.  Whatever you are currently running in Windows should be able to be run in Windows in a virtual machine.

I know this doesn't get you completely away from Windows, but it does let you have Linux as the operating system with Windows just running as an app in Linux.  No need to dual-boot, etc..

Just a thought based on your needs.

Dave ;)

---

### Post by Unhyper on 2010-06-07
> **anewguy said:**
> I don't know your hardware specs, but have you considered running Windows in a VirtualBox virtual machine?  I currently don't because I had to sell my "good" PC and what I have now is more than a little slow with vbox on it.  You could always try it - just go to the Sun/Oracle site and download the PUEL version, not the one from the repos in Ubuntu.  The reason I say that is that Ubuntu stays with free open source software, and the version of VirtualBox that is open source doesn't support USB.  The PUEL version is still free, it's just not open source, but it has USB support.  Whatever you are currently running in Windows should be able to be run in Windows in a virtual machine.

I know this doesn't get you completely away from Windows, but it does let you have Linux as the operating system with Windows just running as an app in Linux.  No need to dual-boot, etc..

That might work. I am concerned about how well Windows would perform in a virtual machine, though, especially when it comes to video encoding. But you're right in that it could work... I've added my specs to my signature, should've done that to begin with.

---

### Post by anewguy on 2010-06-07
> **Unhyper said:**
> That might work. I am concerned about how well Windows would perform in a virtual machine, though, especially when it comes to video encoding. But you're right in that it could work... I've added my specs to my signature, should've done that to begin with.

Well, you've got PLENTY of machine to run it!  I'm not sure on the video encoding.  There is a package of vbox "additions" included with the install that you have to activate after installing vbox, and that includes help with the video.  I know that people do say to not expect the same graphical experience in games, but I would think for what you have mentioned it should work.

I'd give it try and see what happens!  If you are running 64-bit Ubuntu (I don't) you may have to see if there is a 64-bit version of VirtualBox as well (I personally just don't know).

Dave ;)

EDIT:  I just looked on the net and apparently there are 32-bit and 64bit versions of VirtualBox.  I would assume you must match the type to your OS type (32 or 64 bit).

EDIT-EDIT:  Just a side note, man I wished my computer had the specs of yours!

---

### Post by WinterRain on 2010-06-07
I don't know which version of windows you use, but for me, xp runs faster in vbox than my native install. A defrag took only 10 seconds. With that much memory, you could just leave windows running and minimize it like any other app, and you should be good to go.

---

### Post by Eddie Wilson on 2010-06-07
That's basically the same system I have and I do run XP in a vm when I have to. It runs really well. As far as the LightScribe disc burning goes I do it all the time in Ubuntu. It works in a Windows vm also. VBox may be a good bet for you.

---

### Post by Mariane on 2010-06-07
Nice machine you've got here. Someone told me you need a quadricore to run win7 in virtualbox but that xp can be run in virtualbox on almost anything. 

As for scripting text processing, I would do it using LaTeX. OK, the first few times you use LaTeX you swear against the idiots who invented a text processing method under which the texts you write have to be compiled and debugged. But once you get the hang of it writing becomes so much easier... And you don't have to pay anyone to write a script for you, you can do it yourself. It's fun and not very difficult because LaTeX is very well documented and there are a lot of examples to pick from. 

Mariane

---

### Post by Xianath on 2010-06-07
Virtualization is slow when it comes to abstracting hardware such as disks, network and USB. CPU intensive tasks carry almost no penalty (not much more than, say, WOW or WOW64 in Windows). With this CPU you shouldn't have any trouble encoding  DivX from DVD in a virtual machine. Note that you won't be able any hardware-accelerated transcoding such as AVIVO or CUDA in a VM, but with these specs it shouldn't be an issue. Give your VM 2GB of RAM (for Windows 7) and two CPUs, a large enough fixed-size disk (MUCH faster) and you're done.

---

### Post by const451 on 2010-06-07
[http://www.codeweavers.com/](http://www.codeweavers.com/) is another product that allows you to run windows apps on Linux. I haven't used it but I heard it is quiet good. You have to pay for it though, I think it's $70. I have the same dilemma with Excel.

---

### Post by raydeen on 2010-06-07
7 should run fine on even on the original dual core machines. I've got a 7 virtual machine on my work MacBook that performs adequately. No Aero or other fancy touches but it runs alright. Memory is what you'll need to get it running well. I've got 2 gigs and that is probably the minimum. On my home machine, I go the other way. I have 7 installed with 10.04 running in a VBox vm and it runs great. 3D acceleration and everything.

---

### Post by QIII on 2010-06-07
If you use VirtualBox, be sure to use the PEUL version and not the OSE version so you have USB support.

You can add the repo (sorry, not at my Ubuntu machine right now to give you the details) so you can keep it updated as virtualbox.org makes updates without having to reinstall every time.

Also remember to re-run Guest Additions for each new update.

If you have multiple monitors, virtualizing is great.  You can have a virtual machine open and displayed on one monitor while having your primary open and displayed on another.

I've stopped multiple-booting altogether.

---

### Post by anewguy on 2010-06-07
Looks like others agree with my advice - what the heck, go for it!

Dave ;)

---

### Post by QIII on 2010-06-08
Here's my line in sources.list

```
deb http://download.virtualbox.org/virtualbox/debian lucid non-free
```

You'll need to add the key, etc...

[http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

---

### Post by HotShotDJ on 2010-06-08
RE: LightScribe --  see: [https://help.ubuntu.com/community/LightScribe](https://help.ubuntu.com/community/LightScribe)

It works perfectly.  I recommend using Inkscape to create your labels.  Just be sure to export your labels to *.png format (very easy in Inkscape).  Then you just run "sudo 4L-gui" from a terminal (you can add it to your menu if you'd like) and import the image.  After you've played around a bit with the software, you'll get used to where all the options are.

---

### Post by Unhyper on 2010-06-08
I am really grateful to all of you for your suggestions!

---

### Post by tyler9 on 2010-06-08
const451:
"http://www.codeweavers.com/ is another product that allows you to run windows apps on Linux. I haven't used it but I heard it is quiet good. You have to pay for it though, I think it's $70. I have the same dilemma with Excel."

Fyi, for current/future reference: CodeWeavers offers a free 30-day trial of CrossOver Linux standard, which sells for $40:
[http://www.codeweavers.com/products/cxlinux/download_trial/](http://www.codeweavers.com/products/cxlinux/download_trial/)

Some supported apps at bottom of page:
[http://www.codeweavers.com/products/cxlinux/](http://www.codeweavers.com/products/cxlinux/)

---

### Post by formaldehyde_spoon on 2010-06-08
I recently ripped some DVDs to DivX, they turned out very nice.  I wonder why your player doesn't like them...?

---

### Post by anewguy on 2010-06-08
Let's not lose track of the OP's entire set of requirements.  I would imagine that burning the disk and burning the label can be important, but remember there are other requirements as well.  Some of these seem a little bigger to me than dvd problems - like Ms Office.

I stick by my original suggestion - install Ubuntu (as dual-boot for now), install the puel version of virtualbox, install windows in a virtualbox vm, run the apps in the vm.  The OP has PLENTY of computing power for this.  Once the OP is satisfied with Linux, and with Windows running in a vm, then they can consider getting rid of the install Windows and stick with the vm.

I strongly suggest the OP download the PUEL version, make room on the disk and create the partitions, install virtualbox, install Windows in the vm, and then play with it.  You can always remove it if it doesn't meet your needs.

Dave ;)

---

### Post by Unhyper on 2010-06-28
I hate to bump a solved thread, but I just wanted to report back in case someone else had similar issues and came across this thread. I always wish people reported back as to whether ideas contributed helped them solve their issues...

Running Windows XP in a virtual machine works absolutely beautifully. It runs so smoothly that I could probably use Win 7, but since all the software I need to run on Windows work with XP, I didn't see much point. I can minimize it and have it run in the background without any noticeable performance hit to my main OS. Most of the time I don't run it, because I only need access to certain Windows apps intermittently. However, it is a **huge** relief for me just knowing that I don't have to dual-boot anymore.

---

