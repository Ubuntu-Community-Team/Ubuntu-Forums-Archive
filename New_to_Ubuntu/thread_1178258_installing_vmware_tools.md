---
title: "installing vmware tools"
date: 2009-06-04
forum: New to Ubuntu
---

### Post by hehe299792458 on 2009-06-04
I've been trying to install VMware tools inside Ubuntu 9.04, but I keep getting the following error message:

> apple@ubuntu:~$ cd '/home/apple/vmware-tools-distrib' 
apple@ubuntu:~/vmware-tools-distrib$ sudo '/home/apple/vmware-tools-distrib/vmware-install.pl' 
[sudo] password for apple: 
The following VMware kernel modules have been found on your system that were 
not installed by the VMware Installer.  Please remove them then run this 
installer again.

vmxnet
vmmemctl
vmci
vmblock

I.e. - 'rm /lib/modules/2.6.28-11-generic/misc/<ModuleName>.{o,ko}'

Execution aborted.

apple@ubuntu:~/vmware-tools-distrib$ 




What can I do to fix this?

---

### Post by wanchai on 2009-06-04
Well, have you tried to remove the modules as the the error message actually suggests?
In your /lib/modules/2.6.28-11-generic/misc you will find a bunch of modules whose names start with vm. Remove those. They will be rebuilt when you install VMWare tools. You need to go through this every time you upgrade the kernel.

---

### Post by hehe299792458 on 2009-06-04
> **wanchai said:**
> Well, have you tried to remove the modules as the the error message actually suggests?
In your /lib/modules/2.6.28-11-generic/misc you will find a bunch of modules whose names start with vm. Remove those. They will be rebuilt when you install VMWare tools. You need to go through this every time you upgrade the kernel.

when I try to delete those modules, I get a permission denied error.

---

### Post by wanchai on 2009-06-04
are you trying to delete as root, i.e. sudo rm?

---

### Post by hehe299792458 on 2009-06-05
thanks. I forgot that.

However, after I installed it, nothing happened. I could find any mention of the program, and I didn't gain the features that vmware tools provided for windows (i.e. automatically switching the mouse between guest and host os, display res resize, etc). I just pressed enter when it prompted me to. Did I do something wrong?

---

### Post by wanchai on 2009-06-06
It's true that there is not much to see, for example, there is no tray icon as in a Windows guest. If it compiled everything and if there were no errors about inserting kernel modules, you should be fine.

You can check the kernel modules by running *lsmod | grep vm*. This should give you a list of modules. In my Debian guest I see vmblock, vmmemctl, vmhgfs, vmci, vmxnet.

You can get the VMWare toolbox by runnung *sudo vmware-toolbox*. Check *ls -l /usr/bin/vmware** to see what else is installed.

The features that you mentioned all work for me. I can also copy and paste between guest and host, and I am using the shared drive feature as well. I'm using Ubuntu 9.04 as a host, and various Windows flavors plus Debian 4 as guests. Some of these features depend on the preferences you're setting in VMWare Workstation (are you actually using VMWare Workstation or something else?). I've attached a screenshot of my settings, you'd have switch on one of the autofit features if you need automatic resizing.

---

### Post by AnimalMagic on 2009-06-06
You also need to install a mouse driver... Can't remember the details, but there is a posting on here somewhere...

Found this (I think its the right one...) 
> 
sudo apt-get install xserver-xorg-input-vmmouse


---

### Post by wanchai on 2009-06-06
I don't have xserver-xorg-input-vmmouse installed. Neither in the guest nor in the host. And the package information ([http://packages.ubuntu.com/jaunty/xserver-xorg-input-vmmouse](http://packages.ubuntu.com/jaunty/xserver-xorg-input-vmmouse)) seems to indicate that this is needed only in some specific cases where you want to boot an OS either on a physical machine or in a virtual machine.

hehe299792458, I think you should describe your setup (guest OS, host OS, VMWare product and version, your preference settings) and your problem in more details. Maybe then we can help you better.

---

### Post by hehe299792458 on 2009-06-06
Vmware Fusion 2.04

Host: Mac OS X 10.5.7; UMBP T9600 4GB 320GB 

Guest: Ubuntu 9.04; NAT Networking; 20Gb SCSI; 1CPU 512MB


My problem: I'm trying to install VMWare tools, but when I finished installing (I just pressed enter whenever prompted) nothing changed. I didn't seem to gain any of the features of VMware tools.

---

### Post by wanchai on 2009-06-07
Let's check whether your VMWare tools installation was successful. It's normal that you don't really see anything after it's installed. The features you mentioned also depend on the preferences selected in VMWare. This is the case at least in VMWare Workstation, however I'm not familiar with Fusion, don't have a Mac unfortunately.

Please run the following in your guest OS:

[FONT="Courier New"]**lsmod | grep vm **[/FONT]
This should list the kernel modules installed by VMWare tools.

[FONT="Courier New"]**ps -e | grep vm **[/FONT]
This should list the processes related to VMWare tools.

[FONT="Courier New"]**ls -l /usr/bin/vmware* **[/FONT]
This should list the VMWare tools applications, for example vmware-toolbox which you might be familiar with from your Windows guest.

---

### Post by hehe299792458 on 2009-06-07
I couldn't copy the text so here's a screenshot

---

### Post by wanchai on 2009-06-07
This looks good. Your VMWare tools are installed properly and you have the same modules and the same processes running that I have in my system.

By the way, there is a typo in your last line, it should have been /usr and not /user.

Please compare the VMWare settings that I sent you earlier with the ones that you have. Maybe there something in there, maybe we're comparing apples and oranges since we're using different VM products. And I will set up a VM with Ubuntu 9.04 as a guest and see how that works. Will get back to you later.

---

### Post by hehe299792458 on 2009-06-07
> **wanchai said:**
> This looks good. Your VMWare tools are installed properly and you have the same modules and the same processes running that I have in my system.

By the way, there is a typo in your last line, it should have been /usr and not /user.

Please compare the VMWare settings that I sent you earlier with the ones that you have. Maybe there something in there, maybe we're comparing apples and oranges since we're using different VM products. And I will set up a VM with Ubuntu 9.04 as a guest and see how that works. Will get back to you later.

thanks for noticing the typo. Here's a screenshot of the final command correctly inputted

---

### Post by wanchai on 2009-06-07
Now I have a VM with Ubuntu 9.04 and it shows the same problems as the OP described.

AnimalMagic was right about the mouse driver (sorry, but when I'm running into problems, I find too many posts where people suggest to install this and that without giving reasons, without describing in which cases this might apply, etc. Since the first few posts here were about rather trivial problems I hoped that there was just something simple missing).

In my Debian install, the VMWare tools installed the mouse driver, in Ubuntu they didn't. The VMWare tools distribution contains mouse drivers for different Xorg versions, but none is put into /usr/lib/xorg/modules/input. Doing this manually didn't quite work because the hal fdi files and maybe some other things need to be changed as well...

The shortest way to fix the mouse problem is, as AnimalMagic pointed out, to install xserver-xorg-input-vmmouse. I tried it, and it works.

This solved the auto grab/ungrab of the mouse, but the auto screen resize is still a problem.

---

### Post by hehe299792458 on 2009-06-07
> **wanchai said:**
> Now I have a VM with Ubuntu 9.04 and it shows the same problems as the OP described.

AnimalMagic was right about the mouse driver (sorry, but when I'm running into problems, I find too many posts where people suggest to install this and that without giving reasons, without describing in which cases this might apply, etc. Since the first few posts here were about rather trivial problems I hoped that there was just something simple missing).

In my Debian install, the VMWare tools installed the mouse driver, in Ubuntu they didn't. The VMWare tools distribution contains mouse drivers for different Xorg versions, but none is put into /usr/lib/xorg/modules/input. Doing this manually didn't quite work because the hal fdi files and maybe some other things need to be changed as well...

The shortest way to fix the mouse problem is, as AnimalMagic pointed out, to install xserver-xorg-input-vmmouse. I tried it, and it works.

This solved the auto grab/ungrab of the mouse, but the auto screen resize is still a problem.


hmmm... so could you suggest a version of ubuntu that is proven to work with vmware?

---

### Post by wanchai on 2009-06-08
I think you should stick with the version that you have right now. You already succeeded in installing VMWare tools and you have all necessary modules inserted in the kernel. That's good because in some cases this requires fixes in the code. In particular, the vmhgfs module used for sharing directories between host and guest doesn't compile out of the box.

The fix for your mouse problem is easy:
[FONT="Courier New"]**sudo apt-get install xserver-xorg-input-vmmouse**[/FONT]

In order to be able to automatically resize the screen and copy&paste between guest and host you need the application vmware-user to run. Go to System, Preferences, Startup Applications and add a new one with the command [FONT="Courier New"]**/usr/bin/vmware-user**[/FONT].

Then log out from Ubuntu and log in again. This will restart the X server and that's all that's needed to get the new mouse driver running. It also starts a new session that will launch vmware-user. You should then have all the vmware-tools features.


Thanks to AnimalMagic and:
[http://www.nileshk.com/node/122](http://www.nileshk.com/node/122)
[http://blogs.vmware.com/teamfusion/2009/04/ubuntu-904-on-vmware-fusion-2.html](http://blogs.vmware.com/teamfusion/2009/04/ubuntu-904-on-vmware-fusion-2.html)
[http://blogs.vmware.com/workstation/2009/04/ubuntu-904-jaunty-jackalope-on-vmware-workstation-652.html](http://blogs.vmware.com/workstation/2009/04/ubuntu-904-jaunty-jackalope-on-vmware-workstation-652.html)

---

### Post by AnimalMagic on 2009-06-08
> **hehe299792458 said:**
> hmmm... so could you suggest a version of ubuntu that is proven to work with vmware?

I run 8.10 64bit as host and guest with no issues (on dell machines). 

9.04 runs fine as a guest, once you get past the initial issues. Anytime the kernel is updated and you have to re-run the vmware tools config, you have to manually delete the vmware files in your earlier post, but otherwise it works fine. All my guests run fullscreen so I haven't experienced any resizing issues...

I believe there is a user fix to run vmware on 9.04 as host, but I haven't done this - I'm quite happy with 8.10 :-)

---

### Post by wanchai on 2009-06-08
I've been using every Ubuntu version since 6.10 as host. As far as I remember, there were always one or two little issues that could be fixed after googling a bit. Currently I am using 9.04 as a host. VMWare Workstation 6.5.2 installs without any problems and runs fine. However there is problem with Compiz which didn't exist in 8.10. This is a known bug in VMWare that will hopefully be fixed in the next version of VM Workstation.

see here for details:
[http://communities.vmware.com/message/1205368#1205368](http://communities.vmware.com/message/1205368#1205368)
[http://forum.compiz-fusion.org/showpost.php?p=69879&postcount=8](http://forum.compiz-fusion.org/showpost.php?p=69879&postcount=8)

---

### Post by hehe299792458 on 2009-06-08
> **wanchai said:**
> I've been using every Ubuntu version since 6.10 as host. As far as I remember, there were always one or two little issues that could be fixed after googling a bit. Currently I am using 9.04 as a host. VMWare Workstation 6.5.2 installs without any problems and runs fine. However there is problem with Compiz which didn't exist in 8.10. This is a known bug in VMWare that will hopefully be fixed in the next version of VM Workstation.

see here for details:
[http://communities.vmware.com/message/1205368#1205368](http://communities.vmware.com/message/1205368#1205368)
[http://forum.compiz-fusion.org/showpost.php?p=69879&postcount=8](http://forum.compiz-fusion.org/showpost.php?p=69879&postcount=8)

but which versions have you been using for guest?

---

### Post by AnimalMagic on 2009-06-08
FWIW I've used very release since 7.04 as guest without issues. Initially with Windows XP as host, but over the last couple of years it's been Ubuntu as host.

---

### Post by wanchai on 2009-06-08
My guest OS are Windows 2000 Prof, XP Prof, 2000 AS, 2003 EE as well as Debian 4 and 5.

Anyhow, you should be almost done with your Ubuntu 9.04 guest. Once you've done the two minor adjustments described in post #16, everything should be ok.

---

### Post by hehe299792458 on 2009-06-09
> **wanchai said:**
> My guest OS are Windows 2000 Prof, XP Prof, 2000 AS, 2003 EE as well as Debian 4 and 5.

Anyhow, you should be almost done with your Ubuntu 9.04 guest. Once you've done the two minor adjustments described in post #16, everything should be ok.

ok. Thanks a lot!. I missed those tips somehow. They did work

---

### Post by pangloss on 2009-07-03
> **wanchai said:**
> 
In order to be able to automatically resize the screen and copy&paste between guest and host you need the application vmware-user to run. Go to System, Preferences, Startup Applications and add a new one with the command [FONT="Courier New"]**/usr/bin/vmware-user**[/FONT].


This works, but only masks the underlying problem. See ~/.xsession-errors for details, but the essence is that both /usr/share/gnome/autostart/vmware-user.desktop and /etc/xdg/autostart/vmware-user.desktop are malformed for Gnome environments. Changing both copies of vmware-user.desktop from

```
Desktop Entry
Encoding=UTF-8
Exec=vmware-user
Name=VMware User Agent
X-KDE-autostart-phase=1
NoDisplay=true
```

to 

```
Desktop Entry
Type=Application
Name=VMware User Agent
Exec=vmware-user
Icon=system-run
Comment=VMware User Agent
X-GNOME-Autostart-enabled=true
```

will allow vmware-user to autostart.

Source: [http://communities.vmware.com/thread/181894]("http://communities.vmware.com/thread/181894")

---

### Post by AlexanderDGreat on 2009-07-12
Hi,

I was also having trouble with VMware Tools on my Ubuntu 9.04 (guest), Vista32 (host), first I ran this:
[INDENT]sudo apt-get install xserver-xorg-input-vmmouse open-vm-tools
[/INDENT]But this only fixed mouse support.

So I went to this site: [http://ubuntuguide.net/install-vmware-tools-on-ubuntu-904](http://ubuntuguide.net/install-vmware-tools-on-ubuntu-904)

They gave these 2 commands:
[INDENT][COLOR=#C20CB9]**wget**[/COLOR] http:[COLOR=#000000]**//**[/COLOR]chrysaor.info[COLOR=#000000]**/**[/COLOR]scripts[COLOR=#000000]**/**[/COLOR]ubuntu904vmtools.sh
[/INDENT][INDENT][COLOR=#C20CB9]**sudo**[/COLOR] [COLOR=#C20CB9]**bash**[/COLOR] .[COLOR=#000000]**/**[/COLOR]ubuntu904vmtools.sh
[/INDENT]After I tried it, my VMware Tools works perfectly!

My Vmware Workstation is 6.5.2 build 156735.

---

