---
title: "Can't get my wifi working"
date: 2007-02-22
forum: Networking &amp; Wireless
---

### Post by CaptainQuirk on 2007-02-22
I am having difficulty connecting to my wireless network with my Belkin F5D7050. I have searched and googled, and I've been left scratching my head. When I go to network settings the adapter is no where to be found, but when I go to the device manager everything seems to look fine. I have read about ndiswrapper and the ralink drivers for my specific usb wireless card, but I'm still not exactly sure where I am at. Is it simply a matter of configuring the wireless settings, or do I need to install different drivers to get my card to work? If it's the latter of the two, how exactly do I go about doing this?  I'm quite the newbie, and I'd really like to get up and running!

---

### Post by gradedcheese on 2007-02-22
You need drivers.  First, we have to identify the chipset.  Open a terminal (Applications->Accessories->Terminal) and run "lspci", and the post the output here.  Namely, the lines starting with "Ethernet Controller".  The chipset will be mentioned there.

---

### Post by [L2G] Slapshot on 2007-02-23
Hi Graded Hi Cap

Graded I use the same device and it's a usb stick. So Captain will need to do the command lsusb from the command line interface. I am also a noob but if you don't mind helping out here with commands and the like Graded, between the two of us I might learn a little and Cap should get his Wifi. Also I run the KDE version of Ubuntu ( well Pioneer Linux if truth be told ) as it is to me a bit easier as a transition to Linux from Windows. Consequently some of the apps Cap has I won't on my rig so We will definately need your assistance mate.

Cheers
Jacko

---

### Post by gradedcheese on 2007-02-23
Oh, ok.  Well, from google, it looks like this card maybe has a Ralink chipset (if you are lucky) or a Broadcom chipset (if you are not lucky).  Please post the lsusb output then and we'll see what we can find:

```

sudo update-usbids
lsusb

```

I don't use KDE (which I cannot stand) so I can't help you with KDE-specific tools.  I'll be happy to take you through some troubleshooting via the terminal though.

---

### Post by bmartin on 2007-02-23
If your driver is RT73.sys, I've posted a link to a site that solved the problem for me [here](http://www.ubuntuforums.org/showthread.php?t=353469). The nice thing about this is that it's a kernel module and doesn't use ndiswrapper. I bought mine about a month ago at a Circuit City near me and that's the driver it uses.

Look on your installation CD to figure out which driver you need.

---

### Post by benson444 on 2007-02-23
Like Slapshot I'm also using a Belkin 7050 usb wireless stick. There are several different versions of the device though so I guess they all need specific drivers. Enter this in a terminal:

lsusb

If the results show 0x50d:0x200 or 050d:705a then use this link (it's in italian but just type in the commands and follow as best as you can).

[http://wiki.ubuntu-it.org/RalinkRT73](http://wiki.ubuntu-it.org/RalinkRT73)

The id for my stick is 050d:705a and it works great.

---

### Post by bmartin on 2007-02-23
That looks suspiciously like my suggestion :-P But it's a good one and should get your device working 100% without ndiswrapper.

---

### Post by benson444 on 2007-02-24
Yeah, it worked 100% for me :-) Tried it on a newly installed Edgy and didn't need any extra packages to get it working. I'd used a different guide before, but that Italian one is the first to get WPA up and running.

---

### Post by CaptainQuirk on 2007-02-28
Thanks for the responses.  After having limited internet connectivity the past week, I'm finally ready to tackle this.  When I did lsusb, and I got 050d:0237.  I'm lost with the italian website.  This is my first experience with linux, so this is all new to me.  I went to the serialmonkey site and got the latest driver, now what?  Thanks again for the help :)

---

### Post by bmartin on 2007-02-28
Did you download the source code? If so, you should untar it, then do **make** and **sudo make install** to install the kernel module. If there's a light on your device, it should being to flash. It should be active.

After you get that working, you can move on to using wifi-radar to configure your access point and WEP key, if necessary. WPA access requires additional software and fits into a class all its own.

---

### Post by CaptainQuirk on 2007-02-28
> **bmartin said:**
> Did you download the source code? If so, you should untar it, then do **make** and **sudo make install** to install the kernel module. If there's a light on your device, it should being to flash. It should be active. 

Thanks for such a quick response.  Maybe it's the terminology that's throwing me off, but how do I go about "untarring" the source code?  What I downloaded was the latest BETA driver for  the RT2570 chipset at [http://rt2x00.serialmonkey.com/wiki/index.php?title=Download](http://rt2x00.serialmonkey.com/wiki/index.php?title=Download)  Also what exactly do you mean by "make" and "sudo make install"?  I'm so new at this, so I appreciate the patience.  :)

---

### Post by bmartin on 2007-02-28
Sorry, that was my mistake.

The file you downloaded ended with .tar.gz. This is called a "tarball". It's like a ZIP file in Windows... I don't know what the Mac equivalent is. One benefit tarballs have is preserving the permissions of files.

Anyways, inside the archive, there should be a /rt2570-1.1.0-b2/Module/ directory. In that directory, you'll find a file called **Makefile**. This indicates that you can compile the source code (the files within the .tar.gz file) using the "make" command.

It's easiest to make source code using a terminal. Change into the directory with the "Makefile" file and type **make**; the source code will be compiled. After that's done, type **sudo make install**.

You have to include the "sudo" part because the installation puts the compiled code into your kernel (the innermost part of your operating system) by way of a kernel module (.ko) file; altering your system files requires administrative privileges. Kernel modules are like drivers in a way; they extend the capabilities of Linux.

If you need any of this explained, I'm happy to try to clarify further. It might be helpful to take a look at some instructions for compiling Linux software from source code if you're confused about how to do that. The best example I could find of an install walkthrough from source was here: [http://liquidweather.net/howto/index.php?id=82]("http://liquidweather.net/howto/index.php?id=82").
I tried to find something explicit. This build is a bit different because there's no ./configure step (see the example).

---

### Post by CaptainQuirk on 2007-03-01
> **bmartin said:**
> Sorry, that was my mistake.

The file you downloaded ended with .tar.gz. This is called a "tarball". It's like a ZIP file in Windows... I don't know what the Mac equivalent is. One benefit tarballs have is preserving the permissions of files.

Anyways, inside the archive, there should be a /rt2570-1.1.0-b2/Module/ directory. In that directory, you'll find a file called **Makefile**. This indicates that you can compile the source code (the files within the .tar.gz file) using the "make" command.

It's easiest to make source code using a terminal. Change into the directory with the "Makefile" file and type **make**; the source code will be compiled. After that's done, type **sudo make install**.

You have to include the "sudo" part because the installation puts the compiled code into your kernel (the innermost part of your operating system) by way of a kernel module (.ko) file; altering your system files requires administrative privileges. Kernel modules are like drivers in a way; they extend the capabilities of Linux.

If you need any of this explained, I'm happy to try to clarify further. It might be helpful to take a look at some instructions for compiling Linux software from source code if you're confused about how to do that. The best example I could find of an install walkthrough from source was here: [http://liquidweather.net/howto/index.php?id=82]("http://liquidweather.net/howto/index.php?id=82").
I tried to find something explicit. This build is a bit different because there's no ./configure step (see the example).

Ahhh, it's beginning to make sense now.  I think I'm starting to "get it" and understand how it works.  That being said, I know I'm going to sound less than intelligent, but how exactly do I change directories?  I just extracted the tarball to my desktop.  Now what exactly do I type to get the to the correct directory?

---

### Post by bmartin on 2007-03-01
Open up a terminal. I'm not at my Ubuntu PC right now :-( I'm at work, at a Win XP PC.

It should be under Applications > Accessories > Terminal.

At the prompt, type the following command:

cd ~/Desktop/rt2570-1.1.0-b2/Module/

~ refers to your home directory. It's considered a special character in paths (references to files), so try to avoid using it in your file names.

I'm going to busy for a couple hours with a meeting. I'll get back to you in 2 hrs if you need any more help.

---

### Post by CaptainQuirk on 2007-03-01
> **bmartin said:**
> Open up a terminal. I'm not at my Ubuntu PC right now :-( I'm at work, at a Win XP PC.

It should be under Applications > Accessories > Terminal.

At the prompt, type the following command:

cd ~/Desktop/rt2570-1.1.0-b2/Module/

~ refers to your home directory. It's considered a special character in paths (references to files), so try to avoid using it in your file names.

I'm going to busy for a couple hours with a meeting. I'll get back to you in 2 hrs if you need any more help.

Ok, so far so good, I followed the steps and as far as I know it appears to have worked.  Now what should I do to check and see if it worked? Also, where do I get wifi-radar?

---

### Post by bmartin on 2007-03-01
There should be a **wifi-radar** package in the Ubuntu repositories. I'm not sure which repository it's in.

The command to install packages is as follows:

**sudo apt-get install <package names>**

You can specify multiple package names on the same line. So for wifi-radar, you'd enter **sudo apt-get install wifi-radar**.

If you get an error saying that the package isn't found, you'll have to enable additional repositories. Use Google to find instructions for your version of Ubuntu (I'm not going to assume you're using Edgy, but if you are, you can set up the repositories with a program called EasyUbuntu - you can find it with Google; it also sets up a lot of other "non-free" things that you might find useful, such as support for many other archive types and codecs).

If you're interested in what kind of software is in each repository, see [the Wikipedia article here]("http://en.wikipedia.org/wiki/Ubuntu_(Linux_distribution)#Package_classification_and_support").

---

