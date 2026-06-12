---
title: "Problem installing ATI proprietary driver"
date: 2009-11-02
forum: New to Ubuntu
---

### Post by QuestionMan on 2009-11-02
Firstly, I wanted a Proprietary driver because I have a 4850HD Sapphire card and want to use the actual drivers meant for the card. For a few reasons, yes Linux has their own drivers provided you can be happy with well.. no not when I can't play any games properly or have video playback isssues even with LQ .mkv's. It all seems to point to that those Linux ATI repositories drivers aren't going to cut it.

So upon, over the course of 2 days I've been rummaging through every possible lead via Google and I've come to ask here at last. Let me give a rundown of the troubleshooting I did at first to the last idea: I checked in the ATI Proprietary Driver Install Instruction PDF I consulted with the prerequisites from minimal to recommended. Those are starting from minimum:

&#1048698; XOrg 6.8, 6.9, 7.0, 7.1, 7.2, 7.3 or 7.4
&#1048698; Linux kernel 2.6 or above
&#1048698; glibc version 2.2 or 2.3
&#1048698; POSIX Shared Memory (/dev/shm) support is required for 3D applications

Recommended:
&#1048698; XFree86-Mesa-libGL
&#1048698; libstdc++
&#1048698; libgcc
&#1048698; XFree86-libs
&#1048698; fontconfig
&#1048698; freetype
&#1048698; zlib
&#1048698; gcc 

I checked predominately every website and checked to see if I already have them and I do to my knowledge.

So then I tried to go about installing it through the terminal with the command:
        ```
sh ./ati-driver-installer-9-10-x86.x86_64.run
```

The error is always w/o fail:
        ```
sh: Can't open ./ati-driver-installer-9-10-x86.x86_64.run
```



I've also tried to use other commands dealing with pre install steps like preping my kernal still can't compile the install... 

So.. next idea maybe I downloaded the wrong version of drivers. Well if that is the case then maybe the drivers I need for it aren't listed, oh btw I have Ubuntu 9.10 Karmic x64 since I'm reading under 4GB of RAM, x86 is 64-bit that would make x64 32-bit right? Well, just throwing that out there. I've also been reading somewhat outdated articles about ATI's recent compatibility effort for making drivers compatible with Linux operating systems including the Ubuntu distributions to the latest Karmic release. 
This is getting too long so I'll stop here at my surmise that either I have not installed the right driver since I can't even open it in the terminal or I'm missing a compiler to handle the type of file. I'm missing something or I would be able to open the file and install it. 

tl;dr or you skimmed it? Could you please give me help to guide me in the right direction to get this installed, any idea ,any input? That would be very helpful. ;)

Thank You

---

### Post by QuestionMan on 2009-11-02
Also I forgot to mention about the articles I forgot to include AMD/ATI compatibility efforts recently. I mentioned that because having an AMD build may be the problem.](*,)

Another piece of info that may be helpful is some my computer specifications:

AMD Athlon II x2  240 64-bit

The Linux kernal I'm using is 2.6.31-14

Which reminds me I may need to consult what type of Linux kernal the Proprietary drivers support..

---

### Post by QuestionMan on 2009-11-02
*Bump*

---

### Post by QuestionMan on 2009-11-02
*Big Bumpin*

---

### Post by QIII on 2009-11-02
If you keep bumping so quickly, you will draw the attention of the moderators.  24 hours is a safe bet.  Remember that we are all here voluntarily as we have time, so it may take a bit for someone who knows anything about the problem to respond.

I have an ATI GPU.

If your card is supported by the 9.10 driver, you can install it from Synaptic, since ATI jumped through hoops to get it out specifically for Karmic.  It is available off the shelf for everyone else now (I understand).

Go to Synaptic and search for "Catalyst" (if your card is supported. Look it up on ATI's site first).  Install it after uninstalling anything else you may have attempted to install.

Your mileage may vary.

---

### Post by QuestionMan on 2009-11-02
> **QIII said:**
> If you keep bumping so quickly, you will draw the attention of the moderators.  24 hours is a safe bet.  Remember that we are all here voluntarily as we have time, so it may take a bit for someone who knows anything about the problem to respond.

I have an ATI GPU.

If your card is supported by the 9.10 driver, you can install it from Synaptic, since ATI jumped through hoops to get it out specifically for Karmic.  It is available off the shelf for everyone else now (I understand).

Go to Synaptic and search for "Catalyst" (if your card is supported. Look it up on ATI's site first).  Install it after uninstalling anything else you may have attempted to install.

Your mileage may vary.

I understand I'll just leave this in here until it collects dust or answers. 
The card is a Sapphire HD4850 1GB 256-bit GDDR3 PCI Express 2.0 x16 HDCP Ready CrossFire Supported Video Card.

I checked synaptic package manager and I get the same ones I'm using, fglrx-amdcccle  2:8.660 oubuntu4. Which are not the same drivers provided specifically in the ATI driver download section. I want to download the drivers I downloaded which are ATI Catalyst&#8482; 9.10 Proprietary Linux x86 Display Driver... I'm pretty confused by this comment. 32-Bit packages must be installed for 64-Bit Linux drivers to install or work... :-k

---

### Post by QIII on 2009-11-02
The package is 64 bit...

[http://ns2.canonical.com/en/karmic/amd64/fglrx-amdcccle](http://ns2.canonical.com/en/karmic/amd64/fglrx-amdcccle)

That is the Karmic specific driver ATI provided to Canonical for inclusion in Karmic -- which they did before the driver was available for public consumption.

That is what I installed.

When I open it, it says Catalyst Control Center 9.10.

My GPU is working fine.  If you are getting different results (which is odd if it is an HD), then it might be worth a look through launchpad to see if others are experiencing the same problem.  If not, it may be a bug that needs to be added.

---

### Post by QuestionMan on 2009-11-02
Meh,it may be my ignorance I did uname -a:
```
2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2009 i686 GNU/Linux

```

I'm using a generic architecture not AMD64 bit designed.. I used the live-cd and updated it to 9.10 Karmic.. I may have to install the appropriate one. If this is not the case then please set me straight.

An update to this is I found that having x86 and AMD64 is only a marginal difference and that it wouldn't cause any issues in fact I've read it's easier to work with. Another update that I should let QIII or anyone else who comes by this thread is that I can't open my Catalyst center that comes with the version fglrx-amdcccle 2:8.660 oubuntu4 I have currently installed, but the drivers still configured the proper settings of screen resolution and refresh rate. With that said why can't I open the Catalyst center itself? I could before in 9.04. I reinstalled it and still wont respond.

---

### Post by QuestionMan on 2009-11-03
*Morning Bump*:twisted:

---

### Post by QIII on 2009-11-03
Right click the icon under Applications | Other and select "Add this launcher to panel".

When it's there, right click on it and select properties.

The launch command should look something like "gksudo amdcccle".

Let us know if that is not the case.

---

