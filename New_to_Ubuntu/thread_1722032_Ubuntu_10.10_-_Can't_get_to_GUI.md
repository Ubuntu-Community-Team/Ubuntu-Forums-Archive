---
title: "Ubuntu 10.10 - Can't get to GUI"
date: 2011-04-05
forum: New to Ubuntu
---

### Post by maembe on 2011-04-05
Hi everyone,

I just installed Ubuntu 10.10 on my brand new laptop to dual boot between that and Windows 7, but for some reason, it goes straight to the command terminal screen instead of the gui.  I've tried typing startx but it just makes the screen go black and I have to shut it down with the power button.  I've also have tried a few other commands to no avail.  Before I installed I was able to get into the gui to test it out with the CD, so I'm not sure if it could be a graphics issue.

Anyone have any ideas?

Thanks for your help

---

### Post by Dutch70 on 2011-04-05
Hi and welcome to UF

You could try some of these settings...
[[COLOR="RoyalBlue"]http://ubuntuforums.org/showthread.php?t=1613132[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1613132")

Also, no need to do a hard reboot...
[[COLOR="RoyalBlue"]http://kember.net/articles/reisub-the-gentle-linux-restart/[/COLOR]]("http://kember.net/articles/reisub-the-gentle-linux-restart/")

---

### Post by maembe on 2011-04-05
> **Dutch70 said:**
> Hi and welcome to UF

You could try some of these settings...
[[COLOR=RoyalBlue]http://ubuntuforums.org/showthread.php?t=1613132[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1613132")

Also, no need to do a hard reboot...
[[COLOR=RoyalBlue]http://kember.net/articles/reisub-the-gentle-linux-restart/[/COLOR]]("http://kember.net/articles/reisub-the-gentle-linux-restart/")

I tried 'nomodeset' but it just says "nomodeset:  command not found
am I doing something wrong?

I did nomodeset for a single boot but it just gave me a long string of text in the command terminal, including "Fatal server error:
no screens found"
"xinit:  No such file or directory (errno 2):  unable to connect to X server
xinit:  No such process (errno 3):  Server error."


It didn't go to a black screen, just the command terminal.
Thanks for the restart guide.  Very helpful.  I can actually pull it out of the black screen and back to the terminal with just Alt+Sys req+R+E.

---

### Post by oldfred on 2011-04-05
nomodeset has to be on the linux line in grub menu.

On first boot after install, press e on getting the GRUB bootloader. 
Hold shift from BIOS boot to get menu if only one system installed.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode)
[https://bugs.launchpad.net/ubuntu/+source/casper/+bug/661939/comments/18](https://bugs.launchpad.net/ubuntu/+source/casper/+bug/661939/comments/18)

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/LiveCDBootOptions](https://help.ubuntu.com/community/LiveCDBootOptions)
[http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt](http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt)
noapic nolapic noapci noirqpoll nosmp irqpoll

Some other settings:
[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)
* Older Intel video card: i915.modeset=1 or i915.modeset=0
* nVidia: nomodeset
* Generic: xforcevesa or nouveau.modeset=0
* Radeon: radeon.modeset=0

---

### Post by maembe on 2011-04-05
Okay, so here's where I'm at now.  I thought I'd try to use kubuntu instead since it has a different gui.  I installed and it hung up on the install at 77%.  When I shut it down and restarted it worked!  However, I wanted to make sure I had everything so I decided to reinstall.  This time it installed all the way and now I'm having the exact same problem I had with Ubuntu.  I can't get to the gui.  I did get-apt upgrade and update to get a bunch of updates and tried the nomodeset and a bunch of other stuff but I can't figure this out.  Why would it work when I installed the first time but not now?

---

### Post by wep940 on 2011-04-05
Post back the output of:
 
lspci
 
so we can see what video adapter you have.

---

### Post by Dutch70 on 2011-04-05
If you're getting something like... maembe@ubuntu~$ or whatever it is, try typing...
```
sudo startx
```


If you're not getting that, try hitting (cntl+alt+F7) to get it, then enter the command above. 
[I](I'm going off memory here & it's not that great, but you may have to hit cntl+alt+F2 and then cntl+alt+F7) 
[/I]

If you do get to the GUI, run the following in a terminal.
```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by maembe on 2011-04-05
> **wep940 said:**
> Post back the output of:
 
lspci
 
so we can see what video adapter you have.

00:1c.5 PCI bridge:  Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 (rev 05)
00:1d.0 USB Controller:  Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge:  Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge:  Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 SATA controller:  Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus:  Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
00:1f.6 Signal processing controller:  Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 05)
02:00.0 Network controller:  Realtek Semiconductor Co., Ltd. Device 8176 (rev 01)
03:00.0 Ethernet controller:  Atheros Communication AR8152 v1.1 Fast Ethernet (rev c1)
ff:00.0 Host bridge:  Intel Corporation Core Processor QuickPath Architecture Generic Non-core REgisters (rev 02)
ff:00.1 Host bridge:  Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
ff:02.0 Host bridge:  Intel Corporation Core Processor QPI Link 0 (rev 02)
ff:02.1 Host bridge:  Intel Corporation Core Processor QPI Physical 0 (rev 02)
ff:02.2 Host bridge:  Intel Corporation Core Processor Reserved (rev 02)
ff:02.3 Host bridge:  Intel Corporation Core Processor Reserved (rev 02)



lspci -v | less gets me:

VGA compatible controller:  Intel Corporation Core Processor Integrated Graphics Controller (rev 02) (prog-if 00 [VGA controller])
Subsystem:  Toshiba America Info Systems Device fdd0
Flags:  bus master, fast devsel, latency 0, IRQ 10
Memory at d0000000 (64 bit, non-prefetchable) [size=4M]
Memory at c0000000 (64 bit, prefetchable) [size=256M]
I/0 ports at 5050 [size=8]
Expansion ROM at <unassigned> [disabled]
Capabilities:  <access denied>
Kernal modules:  i915

---

### Post by maembe on 2011-04-05
> **Dutch70 said:**
> If you're getting something like... maembe@ubuntu~$ or whatever it is, try typing...
```
sudo startx
```
If you're not getting that, try hitting (cntl+alt+F7) to get it, then enter the command above. 
[I](I'm going off memory here & it's not that great, but you may have to hit cntl+alt+F2 and then cntl+alt+F7) 
[/I]

If you do get to the GUI, run the following in a terminal.
```
sudo apt-get update && sudo apt-get upgrade
```

I already did the apt-get upgrade and updates.

startx just makes the screen go blank

---

### Post by Dutch70 on 2011-04-05
Have a look at this... it's lucid, but I don't think it matters.
[[COLOR="RoyalBlue"]http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/[/COLOR]]("http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/")

Edit: Just noticed that's the same link oldfred gave you. 

Also, if you were logged in long enough to run all the updates, you probably got a kernel update that could be the problem. Try to login to the older kernel. If you don't see your grub menu, try hitting the escape key while booting, to bring it up.

---

### Post by maembe on 2011-04-05
> **Dutch70 said:**
> Have a look at this... it's lucid, but I don't think it matters.
[[COLOR=RoyalBlue]http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/[/COLOR]]("http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/")

Also, if you were logged in long enough to run all the updates, you probably got a kernel update that could be the problem. Try to login to the older kernel. If you don't see your grub menu, try hitting the escape key while booting, to bring it up.

I don't know how to log in to an older kernel, but I did the i915modeset thing and when I type startx, instead of just going to a black screen I get a bunch of text.  One of the things that stands out is 
"Fatal server error: 
no screens found"

There is also:
(EE) open /dev/fb0:  No such file or directory
(EE) intel(0):  No kernel modesetting driver detected.
(EE) Screen(s) found, but none have a usable configuration.

xinit:  No such file or directory (errno 2):  unable to connect to X server
xinit:  No such process (errno 3):  Server error.

---

### Post by maembe on 2011-04-06
Well, after some more research, I'm writing this to you with the rekonq browser that came installed with kubuntu :guitar:

I'm going to find out what commands I used so I can post them here to help others, but essentially, it created two more ubuntu boot options in the grub so it looked like this:

Ubuntu kernel 2.6.25-28-generic
Ubuntu kernel 2.6.25-28-generic (recovery)
Ubuntu kernel 2.6.25-22-generic
Ubuntu kernel 2.6.25-22-generic (recovery)
Some Windows ones

The 28 one is the one that is working.  So now my question is can/should I hide the options that I don't need in the grub boot menu?

EDIT:  I think it may have been these commands that did it:
sudo apt-get install discover mdetect
sudo apt-get install x-window-system-core x-window-system xterm

I'm going to mark this as solved, but let me know if you don't think it was these.  Thanks for all of your help.  I have a lot more questions.

---

### Post by Dutch70 on 2011-04-06
The extra options in the boot menu are updated kernels. They will continue to increase every time a new kernel update comes out. It's best to keep at least 2, in case you have trouble with one of them. 

If you want to get rid of the older ones, go to synaptic and search for "image-2" and mark the oldest kernel for removal (be careful). Some new users like to use Ubuntu Tweak for this. I'm not sure if/how that works with KDE.

---

