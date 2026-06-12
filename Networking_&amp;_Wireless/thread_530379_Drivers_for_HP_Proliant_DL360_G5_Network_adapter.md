---
title: "Drivers for HP Proliant DL360 G5 Network adapter"
date: 2007-08-20
forum: Networking &amp; Wireless
---

### Post by eisublime on 2007-08-20
I've got a couple of new HP DL360 G5s that I just installed 6.06 on.  During the installation, it was unable to install drivers for the network adapters which are NC 373i built in adapters.  I can't find drivers anywhere - has anyone found working NIC drivers for this server?

Thanks

---

### Post by bmartin on 2007-08-20
The toolboxes at HP assume you're using RHEL or SLED and provide an RPM only. Those jerks.

Anyways, [here]("http://h18004.www1.hp.com/support/files/server/us/download/27391.html")'s the RPM with the source code. To use this RPM, you need the **alien** package.
```
sudo apt-get install alien
```. Then you can use alien --to-tgz (FILE) to convert it to a tarball... or you could use --to-deb to make it a DEB archive...

Or... I attached the source code that was in the RPM to begin with at the bottom of this post. You'll have to compile it (it uses the normal compilation method) and possibly run **modprobe bnx2** after installation to insert the kernel module.

If this is all foreign to you, let me know and I can be more verbose. I gave you instructions in case you want to learn, or if you don't trust me. I don't take it personal. I prefer doing things myself for both of those reasons.

---

### Post by eisublime on 2007-08-20
Great thanks.  I since I haven't got a working NIC, apt-get doesn't work out so well, and make doesn't work - I guess because a fresh install doesn't come with gcc?  Sorry, it's been a while since I've done much with Linux and I'm really rusty - do I just need to download and install gcc and I should be good to go, or will I be missing anything?

---

### Post by bmartin on 2007-08-20
sudo apt-get install build-essential linux-headers-`uname -r`

Sorry, I failed to read that last remark. I don't know what to do if you can't use Apt. You need build-essential and the headers to do pretty much anything.

---

### Post by bmartin on 2007-08-20
OK... hmmm... well, I could compile this for you... but I need to know what kernel you're going to be using this on. If I compile it with the wrong kernel headers, it's pretty useless to you. Then you'll have to use **insmod** to insert it.

On that computer, what's the output of **uname -r**?

---

### Post by eisublime on 2007-08-20
actually - I forgot that i could use apt to install off of the installation cd.  I'm using the 64bit version of the OS, and using alien, it's telling me that that isn't supported by that driver - i'm seeing if there's a different one now.

---

### Post by eisublime on 2007-08-20
It doesn't seem to matter which rpm I download from HP's site, I keep getting:
dpkg-gencontrol: error: current build architecture amd64 does not appear in package's list (i386)
when I run alien -k *packagename.rpm*.  Is there anything else i can do, or should i switch to the 32 bit version?

---

### Post by bmartin on 2007-08-20
The RPM file merely contains the source code found In my first post, I attached the source code. It appears at the bottom of my post. Just grab that.

That doesn't solve the problem of compiling the source code, though. I don't know whether using the 32-bit version would help with this issue, but it does simplify some other issues that would make more sense on a desktop PC (as opposed to a server).

If you have an older Ethernet card lying around, you could try sticking that into the server so you have some kind of connection to use. Without something that you can plug in and use the internet, it's painfully difficult to try to build anything from source code.

---

### Post by eisublime on 2007-08-21
Yeah, if I download the source that you gave me and unzip it to /home/username/downloads/drivers/ and run make on it it says 
make -C SUBDIRS=/home/username/downloads/drivers/bnx2-1.5.10d modules
make: *** SUBDIRS=/home/username/downloads/drivers/bnx2-1.5.10d: No such file or directory.  Stop
make: *** [default] Error 2

am I missing something there?

Thanks very much for sticking with me on this.

---

### Post by eisublime on 2007-08-21
Ok, it looks like I need to look at the error messages that I'm getting a little bit better - then I would have realized that the linux-headers didn't install.  Once I installed those, it looks like I was able to compile the driver, and make install seemed to run correctly as well, as did modprobe.  Now how do I get the NIC to work?

Thanks so much for your help.

---

### Post by eisublime on 2007-08-21
ah hah!  I had to edit /etc/modules to have
alias eth0 bnx2
alias eth1 bnx2

in it.  once I did that, I was able to ifconfig eth0 up and it looks like its working.  Thanks so much for your help!

---

### Post by bmartin on 2007-08-21
If those are the correct drivers, the **modprobe bnx2** command should've installed the necessary driver and it should be working. I'm not really familiar with your ethernet controller. If you use the newer Gutsy kernel (which would require a network connection to download... you could try the newest release), it might have support for the device, but that's a gamble. I'm very surprised it didn't work upon installation.

---

### Post by eisublime on 2007-08-21
Oh I see.  Did you extract that source code from the bnx2-1.5.10d-2.src.rpm file, or did you have a different one.  I only ask because the file you gave me didn't have the -2 at the end, it was just bnx2-1.5.10d.tar.bz2, so I'm wondering if it was that driver or not.

---

### Post by bmartin on 2007-08-21
I used alien to make a tgz archive, then kept extracting those archives until I found the source code.

---

### Post by eisublime on 2007-08-21
Ok, I started over, and just compiled the source, installed the driver, and ran modprobe to insert the kernel module.  Turns out, that after that, i just had to up the interface and reboot the machine (probably could have just restarted networking) and it was working.  Thanks very much for your help!

---

### Post by bmartin on 2007-08-21
:popcorn: You're welcome!... and that's awesome. I'm glad I was able to help.

I'm having a good day, too. My girlfriend (who just graduated w/ her MS in Aerospace Engineering this month) landed a job that pays "pretty well" and has great job security... although she went to the 4th-best engineering school in the country and probably deserves more pay. I might be moving soon and **finally** buying a house... which is pretty much the reason I got my MS. Woohoo!!! :KS

Sorry, the KDE star is just really cute. It almost makes me want to use KDE (I use Fluxbox).

---

### Post by eisublime on 2007-08-21
Well congrats, that's cool.

I have one more question - /etc/modules doesn't have bnx2 listed in it, is there someplace that lists all the installed drivers, or modules that are in use or any of those types of things?  I know my terminology is probably messed up, but you get the idea for what I'm looking for...

---

### Post by bmartin on 2007-08-21
**lsmod** lists all the kernel modules that are loaded into memory
**cat /proc/modules** lists something that's a little more verbose

Beware that every time you get a new kernel, you'll need to repeat the process to install a new kernel module. If you want to load the same kernel every time, you can modify your GRUB menu.list file (/boot/grub/menu.lst) to load whatever kernel you're currently running.

If you always run this kernel, you'll never have to recompile your kernel module. Debian automatically regenerates a portion of your menu.lst file every time a new kernel is installed.

---

