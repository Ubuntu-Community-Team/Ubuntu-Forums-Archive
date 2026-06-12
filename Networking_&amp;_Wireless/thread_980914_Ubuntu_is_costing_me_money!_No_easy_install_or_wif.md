---
title: "Ubuntu is costing me money! No easy install or wifi capability"
date: 2008-11-13
forum: Networking &amp; Wireless
---

### Post by Simon Lemb on 2008-11-13
I have a Dell inspiron 1300, stock wifi card and after much publicity and excitement in the new freeware community I jumped on board.

The install partioning process wiped my harddrive...I mean EVERYTHING and now Ubuntu can't see my wireless router.


I have a million things to do today and the "easy operation" I read about doesn't seem to be strictly true!!


Sorry to moan, any ideas?

---

### Post by Simon Lemb on 2008-11-13
Really disappointed so far, can't ANYONE help?


I would never have tried to get onboard the community were it not for the reassurances that it was all intuitive and straightforward!


Any help would be GREATLY appreciated! :)

---

### Post by prshah on 2008-11-13
> **Simon Lemb said:**
> 
Any help would be GREATLY appreciated!

OK, there's lots we can do to help, but it's going to take time, which you don't seem to be able to spare right now. Maybe you should do this at a later time?

If you feel no time like the present; the first thing you need to do is get hold of the _Windows_ driver for WiFi. The notebook model you mentioned uses a Dell brand mini-pci WiFi card which have no linux drivers. However, you can comfortably use the Windows drivers in linux.

Post back for more details when and if you are ready, or you can just take a look at [http://ayao.livejournal.com/196297.html](http://ayao.livejournal.com/196297.html)

---

### Post by Simon Lemb on 2008-11-13
Blnk

---

### Post by superprash2003 on 2008-11-13
which ubuntu have you installed??

---

### Post by Simon Lemb on 2008-11-13
> **prshah said:**
> OK, there's lots we can do to help, but it's going to take time, which you don't seem to be able to spare right now. Maybe you should do this at a later time?

If you feel no time like the present; the first thing you need to do is get hold of the _Windows_ driver for WiFi. The notebook model you mentioned uses a Dell brand mini-pci WiFi card which have no linux drivers. However, you can comfortably use the Windows drivers in linux.

Post back for more details when and if you are ready, or you can just take a look at [http://ayao.livejournal.com/196297.html](http://ayao.livejournal.com/196297.html)
Thank you, I'll try and find a driver. I appreciate the response, it's driving me nuts!

I'm a freelance musician working on a deadline. :guitar:

---

### Post by Simon Lemb on 2008-11-13
> **superprash2003 said:**
> which ubuntu have you installed??

The latest version, I don't have the number to hand, sorry. I just downloaded it today. Sadly I have no programming knowledge....I just liked the idea of not being tied into microsoft! I didn't count on the partitioning going wrong. I also want to meet others in the community and see if I can offer anything myself.:)

---

### Post by Simon Lemb on 2008-11-13
> **prshah said:**
> OK, there's lots we can do to help, but it's going to take time, which you don't seem to be able to spare right now. Maybe you should do this at a later time?

If you feel no time like the present; the first thing you need to do is get hold of the _Windows_ driver for WiFi. The notebook model you mentioned uses a Dell brand mini-pci WiFi card which have no linux drivers. However, you can comfortably use the Windows drivers in linux.

Post back for more details when and if you are ready, or you can just take a look at [http://ayao.livejournal.com/196297.html](http://ayao.livejournal.com/196297.html)

I followed those links but really it seems way beyond my knowledge.

Can I cut and paste some code onto a usb key and put it somewhere on my laptop? :confused:

---

### Post by jonobr on 2008-11-13
HEllo


I think people are asking about what hardware you have and what your running.

In order to help, try posting your devices and system info

To show the version of Ubuntu you are on,
Go to Applications-> Acceessories->terminal
and type
cat /etc/lsb-release

POst results here

Then enter 
lspci -v | less


Same again post results here.
Im not a wireless expert, but there are some here who have had a lot of experience with this and there are a couple of threads on 1300's

You need to give them the info to help you.

Respectfully I (and IM sure anyone who notices your subject line) feels wants to help and doesnt want to see you going through this pain, however, like any leap into a new world, you should take it slowly.

---

### Post by Swagman on 2008-11-13
When you get your wireless issue sorted... open a terminal (Applications>Accessories > Terminal)

And install LMMS

ie:

```
 sudo apt-get install lmms
```

from a fellow :guitar: <---- Wrong way round !!

---

### Post by prshah on 2008-11-13
> **Simon Lemb said:**
> 
Can I cut and paste some code onto a usb key and put it somewhere on my laptop? :confused:

Unfortunately not. Here's a second best solution: a step-by-step guide to setup wireless using the Windows drivers, with expected outputs, so you can see whether things are going right or wrong.

[[SOLVED] How to activate WG311v3 (or any ndiswrapper or native) wireless]("http://ubuntuforums.org/showthread.php?t=756260")

If you run into trouble, post back the step you are stuck at, along with the output you get.

Note that you need to skip the commands summary at the beginning (for impatient users) and jump to the middle where commands and outputs (in blue) are matched together.

---

### Post by Simon Lemb on 2008-11-13
> **jonobr said:**
> HEllo


I think people are asking about what hardware you have and what your running.

In order to help, try posting your devices and system info

To show the version of Ubuntu you are on,
Go to Applications-> Acceessories->terminal
and type
cat /etc/lsb-release

POst results here

Then enter 
lspci -v | less


Same again post results here.
Im not a wireless expert, but there are some here who have had a lot of experience with this and there are a couple of threads on 1300's

You need to give them the info to help you.

Respectfully I (and IM sure anyone who notices your subject line) feels wants to help and doesnt want to see you going through this pain, however, like any leap into a new world, you should take it slowly.
Thanks jonobr, I appreciate the advice mate!

Here's the info:

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=8.10
DISTRIB_CODENAME=intrepid
DISTRIB_DESCRIPTION="Ubuntu 8.10"


00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)

Subsystem: Dell Device 01c9
Flags: bus master, fast devsel, latency 0
Capabilities: <access denied>
Kernel driver in use: agpgart-intel
Kernel modules: intel-agp

00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)

Subsystem: Dell Device 01c9
Flags: bus master, fast devsel, latency 0, IRQ 16
Memory at dff00000 (32-bit, non-prefetchable) [size=512K]
I/O ports at eff8 [size=8]
Memory at c0000000 (32-bit, prefetchable) [size=256M]
Memory at dfec0000(32-bit, non-prefetchable) [size=256K]
Capabilities: <access denied>
Kernel modules: intelfb

00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)

Subsystem: Dell Device 01c9
Flags: bus master, fast devsel, latency 0

---

### Post by Simon Lemb on 2008-11-13
> **prshah said:**
> Unfortunately not. Here's a second best solution: a step-by-step guide to setup wireless using the Windows drivers, with expected outputs, so you can see whether things are going right or wrong.

[[SOLVED] How to activate WG311v3 (or any ndiswrapper or native) wireless]("http://ubuntuforums.org/showthread.php?t=756260")

If you run into trouble, post back the step you are stuck at, along with the output you get.

Note that you need to skip the commands summary at the beginning (for impatient users) and jump to the middle where commands and outputs (in blue) are matched together.


I didn't realise there was more code....I'm cutting and pasting now between two computers. Sorry, I'm a total n00b.




00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
        Subsystem: Dell Device 01c9
        Flags: bus master, fast devsel, latency 0
        Capabilities: <access denied>
        Kernel driver in use: agpgart-intel
        Kernel modules: intel-agp

00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
        Subsystem: Dell Device 01c9
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at dff00000 (32-bit, non-prefetchable) [size=512K]
        I/O ports at eff8 [size=8]
        Memory at c0000000 (32-bit, prefetchable) [size=256M]
        Memory at dfec0000 (32-bit, non-prefetchable) [size=256K]
        Capabilities: <access denied>
        Kernel modules: intelfb

00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
        Subsystem: Dell Device 01c9
        Flags: bus master, fast devsel, latency 0
        Memory at dff80000 (32-bit, non-prefetchable) [size=512K]
        Capabilities: <access denied>

00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
        Subsystem: Dell Device 01c9
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at dfebc000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: HDA Intel
        Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=0b, subordinate=0b, sec-latency=0
        Capabilities: <access denied>
        Kernel driver in use: pcieport-driver
        Kernel modules: shpchp

00:1c.3 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 4 (rev 03)
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=0c, subordinate=0d, sec-latency=0
        I/O behind bridge: 0000d000-0000dfff
        Memory behind bridge: dfc00000-dfdfffff
        Prefetchable memory behind bridge: 00000000d0000000-00000000d01fffff
        Capabilities: <access denied>
        Kernel driver in use: pcieport-driver
        Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
        Subsystem: Dell Device 01c9
        Flags: bus master, medium devsel, latency 0, IRQ 16
        I/O ports at bf80 [size=32]
        Kernel driver in use: uhci_hcd
        Kernel modules: uhci-hcd

00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
        Subsystem: Dell Device 01c9
        Flags: bus master, medium devsel, latency 0, IRQ 17
        I/O ports at bf60 [size=32]
        Kernel driver in use: uhci_hcd
        Kernel modules: uhci-hcd

00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
        Subsystem: Dell Device 01c9
        Flags: bus master, medium devsel, latency 0, IRQ 18
        I/O ports at bf40 [size=32]
        Kernel driver in use: uhci_hcd
        Kernel modules: uhci-hcd

00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
        Subsystem: Dell Device 01c9
        Flags: bus master, medium devsel, latency 0, IRQ 19
        I/O ports at bf20 [size=32]
        Kernel driver in use: uhci_hcd
        Kernel modules: uhci-hcd

00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03) (prog-if 20)
        Subsystem: Dell Device 01c9
        Flags: bus master, medium devsel, latency 0, IRQ 16
        Memory at b0000000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>
        Kernel driver in use: ehci_hcd
        Kernel modules: ehci-hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3) (prog-if 01)
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=32
        Memory behind bridge: dfb00000-dfbfffff
        Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
        Subsystem: Dell Device 01c9
        Flags: bus master, medium devsel, latency 0
        Kernel modules: intel-rng, iTCO_wdt

00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03) (prog-if 8a [Master SecP PriP])
        Subsystem: Dell Device 01c9
        Flags: bus master, medium devsel, latency 0, IRQ 16
        I/O ports at 01f0 [size=8]
        I/O ports at 03f4 [size=1]
        I/O ports at 0170 [size=8]
        I/O ports at 0374 [size=1]
        I/O ports at bfa0 [size=16]
        Kernel driver in use: ata_piix
        Kernel modules: ata_piix

02:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
        Subsystem: Dell Device 01c9
        Flags: bus master, fast devsel, latency 64, IRQ 18
        Memory at dfbfc000 (32-bit, non-prefetchable) [size=8K]
        Capabilities: <access denied>
        Kernel driver in use: b44
        Kernel modules: b44

02:03.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
        Subsystem: Dell Device 0005
        Flags: bus master, fast devsel, latency 64, IRQ 17
        Memory at dfbfe000 (32-bit, non-prefetchable) [size=8K]
        Kernel driver in use: b43-pci-bridge
        Kernel modules: ssb

~
~

---

### Post by issih on 2008-11-13
Ok, lets try and do this with minimal pain, and move onto slightly more pain if that fails.

Either plug the laptop into the router with an ethernet cable and then run the following code in a terminal:
```
sudo apt-get install ndisgtk
```

Alternatively if you have no option to get online at all other than wireless throw the ubuntu install cd into the drive and then goto System->Administration->Software Sources. In there ensure that the box next to using the cd as a source is ticked, then run the command above.

Once that is done, you should have a new program installed, open it from System->Preferences->Windows Wireless Drivers

In there you need to select the *.inf file from the windows driver (N.B. it may be necessary to fiddle to get at this file, but it is doable)

All this is simply a gui front end to ndiswrapper, its just a bit more friendly for new users

Hope that helps

---

### Post by Simon Lemb on 2008-11-13
> **Swagman said:**
> When you get your wireless issue sorted... open a terminal (Applications>Accessories > Terminal)

And install LMMS

ie:

```
 sudo apt-get install lmms
```

from a fellow :guitar: <---- Wrong way round !!

Hi swagman! :guitar:

What's lmms? :confused:

---

### Post by jonobr on 2008-11-13
EEEKKK


Either you have big problems or your output was truncated:-)


Could you run the command again and make sure you got all the output.
Hit enter a few times to get it all.

If thats the complete list I did not see your wireless adaptor.
If thats the case, maybe from a terminal window if you could type dmesg (it will give a lot of output) and post here to see if there are problems noted in there.
ITs mostly gobbeldy gook and hard to read, but we could take a looksie

---

### Post by Simon Lemb on 2008-11-13
> **issih said:**
> Ok, lets try and do this with minimal pain, and move onto slightly more pain if that fails.

Either plug the laptop into the router with an ethernet cable and then run the following code in a terminal:
```
sudo apt-get install ndisgtk
```

Alternatively if you have no option to get online at all other than wireless throw the ubuntu install cd into the drive and then goto System->Administration->Software Sources. In there ensure that the box next to using the cd as a source is ticked, then run the command above.

Once that is done, you should have a new program installed, open it from System->Preferences->Windows Wireless Drivers

In there you need to select the *.inf file from the windows driver (N.B. it may be necessary to fiddle to get at this file, but it is doable)

All this is simply a gui front end to ndiswrapper, its just a bit more friendly for new users

Hope that helps
Hi issih, thanks man, all went well until I opened the windows wireless drivers gui....there's nothing in the box....do I need to get the *.inf file from somewhere?

---

### Post by Simon Lemb on 2008-11-13
> **jonobr said:**
> EEEKKK


Either you have big problems or your output was truncated:-)


Could you run the command again and make sure you got all the output.
Hit enter a few times to get it all.

If thats the complete list I did not see your wireless adaptor.
If thats the case, maybe from a terminal window if you could type dmesg (it will give a lot of output) and post here to see if there are problems noted in there.
ITs mostly gobbeldy gook and hard to read, but we could take a looksie


haha, I was typing it in manually until I found my usb key :lol:

there's the full output in another post i think....i'm on a tiny wee eeepc and typing/navigating forums is a pain in the ****... :)

---

### Post by jonobr on 2008-11-13
HI

OPen to correction, but pooching around I think the INF your looking for is bcmwl5a.inf for the card you have list in your output.

---

### Post by Simon Lemb on 2008-11-13
> **jonobr said:**
> HI

OPen to correction, but pooching around I think the INF your looking for is bcmwl5a.inf for the card you have list in your output.
sorry to sound slow....but where do I find this file and where do I need to install it?

---

### Post by jonobr on 2008-11-13
Hello

Anyone please correct me here, and Sdog, Im hoping IM leading you in the right direction.

(Using and acknowledging prshah previous information on using ndiswrapper)

I believe its wrapped up in R74092us.EXE
which can be found at 
[http://ftp.us.dell.com/network/R74092us.EXE](http://ftp.us.dell.com/network/R74092us.EXE)

Download it,
(it should end up in your desktop,)
Right click and select extract here.

(FEEL THE BURN>>>> FEEL THE LINUX BURN BABY)
:)

There are two similar files in the directory, I think the one you are looking for is in AR/bcmwl5a.inf (not IR) 

Open the terminal again and Execute the following commands
And replace names where necessary


pwd <Enter>
eg response = /home/simon

mkdir inf_file  <Enter> (creates an INF directory to hold your file)

sudo find . -name bcmwl5a.inf <Enter>  (find where its at)
(it should be around /home/simon/Desktop/R74092us/AR/bcmwl5a.inf)

Copy that file to the newly created directory

cp /home/simon/Desktop/R74092us/AR/bcmwl5a.inf /home/simon/inf_file <enter> (you copy and past where it found the file.)

cd /home/simon/inf_file <enter> (changes to that directory)
ls -l <enter>
Hopefully it will list the file and its there.

Now,  taking from  prshah most excellent post earlier,

sudo ndiswrapper -i /home/simon/Desktop/bcmwl5a.inf

ndiswrapper -l  <Enter> (verifies it has been found)
sudo ndiswrapper -m  <Enter> (adds to module library)
sudo modprobe ndiswrapper  <Enter> (load your wrapped device driver)

See if you get this far

---

### Post by Simon Lemb on 2008-11-13
Hi jonobr, thanks for the help....i've managed to get the bcmwl5a.inf file onto the laptop with ubuntu but when I go to the windows wireless drivers utility, it tells me it's an invalid driver! Any ideas?

---

### Post by jonobr on 2008-11-13
HI,

When you got it onto your system to you manage to exeucte all your commands? AT what point did it fail?
Im wondering if it was the other one (IR) as opposed to AR<
however, let me know at what point on the sequence of steps I gave you that it cwapped out

---

### Post by jimv on 2008-11-13
I think you need the .sys file with the same name from that file you downloaded.  So you need the .inf file and the .sys file.

I ran into this same problem when I started with Ubuntu.  I now keep the driver files stowed away on a thumbdrive in case I need them ;)

---

### Post by Simon Lemb on 2008-11-13
> **jonobr said:**
> HI,

When you got it onto your system to you manage to exeucte all your commands? AT what point did it fail?
Im wondering if it was the other one (IR) as opposed to AR<
however, let me know at what point on the sequence of steps I gave you that it cwapped out

Ok, I'm trying the one in the IR folder....

---

### Post by Simon Lemb on 2008-11-13
> **jimv said:**
> I think you need the .sys file with the same name from that file you downloaded.  So you need the .inf file and the .sys file.

I ran into this same problem when I started with Ubuntu.  I now keep the driver files stowed away on a thumbdrive in case I need them ;)

Thanks jimv....what do I need to do with the .sys file? :confused:

---

### Post by jonobr on 2008-11-13
Good catch Jimv

Out them into the same dir as the INF.

Use the same CP command, just this time copy from the location if the sys file

---

### Post by Simon Lemb on 2008-11-13
> **jonobr said:**
> Good catch Jimv

Out them into the same dir as the INF.

Use the same CP command, just this time copy from the location if the sys fileThanks jonobr :)

Is there any way you could describe what I need to do in simpler terms? At the moment, both the .sys and .inf files are on the desktop. Can you repeat the CP command, this is all very new to me.... :(

---

### Post by jonobr on 2008-11-13
Sure no problem,
We all hard to start somewhere.

Do me a flavour, open the terminal window,
(applications-> accessories-> terminal window

If you type the following commands and send the results to me, 
Ill give you the commands you need to run,

in the terminal window type
pwd then enter and post results
then ls -l *.inf (Or INF case matters!)
then ls -l *.sys

I also recommend you do research yourself to ensure your happy with the INF file I recommended, I dont want to mung up your machine (without your input of course:-) )

---

### Post by Simon Lemb on 2008-11-13
I suspect I've not done this right...

saul@saul-laptop:~$ pwd
/home/saul
saul@saul-laptop:~$ Is-I*.inf
bash: Is-I*.inf: command not found
saul@saul-laptop:~$ Is-I*.sys
bash: Is-I*.sys: command not found
saul@saul-laptop:~$

---

### Post by jonobr on 2008-11-13
my mistake I got you to list in the wrong directory,

execute the commands below in a terminal window.
Im preserving the naming convention i used in my last posts..

also, please please check this is the right INF for you.






Open the new terminal

mkdir inf_file <Enter> 
cd inf_file
cp /home/saul/Desktop/R74092us/AR/bcmwl5a.inf .  <- notice the '.' that means here (ie copy bcmw15a to here)

I cant recall where the sys file is , this is a guess
cp /home/saul/Desktop/R74092us/AR/bcmwl5.sys .



ls -l <enter>

Hopefully it will list the files and its there.


sudo ndiswrapper -i /home/saul/inf_file/bcmwl5a.inf

ndiswrapper -l <Enter> 
sudo ndiswrapper -m <Enter> 
sudo modprobe ndiswrapper <Enter> 

See if you get this far

---

### Post by jonobr on 2008-11-13
You know what,
I must be intimidating you a bit,
the cp , cd and mkdir commands can all be doing using the desktop and normal folders point - click windows style stuff.

Unix systems started off in the days when connection to the was done over unreliable telephone links,
as a result, a lot of the commands are very short so that you were sending as few characters as possible over the link, so
cp instead of copy
rm instead of delete (careful with this one, it doesnt ask if your sure!)
mkdir make directory
ls= list 
cd = change directory.

A lot of these can be done using the right click on the desktop,
you will see make folder, delete, copy paste and so on.
Like windows your home directory will be /home/saul
and when you login and use the console thats where you go first,

you can navigate using the gui, or the terminal.
In the terminal using commands is doing using relative or absolute pathnames,

so /home/saul is absolute.

if I was to be in desktop ( /home/saul/desktop)
i could cd /home/saul/documents (change directory to documents directory using absolute names, or or from /home/saul/dektop I could give relative
cd ../documents (.. = previous dir)

I could go on and on but there are tonnes of resources out there on this,
long story shortened, you can do the file manipulation using gui.

---

### Post by Simon Lemb on 2008-11-14
> **jonobr said:**
> Sure no problem,
We all hard to start somewhere.

Do me a flavour, open the terminal window,
(applications-> accessories-> terminal window

If you type the following commands and send the results to me, 
Ill give you the commands you need to run,

in the terminal window type
pwd then enter and post results
then ls -l *.inf (Or INF case matters!)
then ls -l *.sys

I also recommend you do research yourself to ensure your happy with the INF file I recommended, I dont want to mung up your machine (without your input of course:-) )
Thanks for all your help but this is all too technical for me. I'm going to install Windows 98 which is the only OS I have on disk. Maybe I'll come back to Ubuntu once it has these problems sorted....I just have too much work to do now.

Thanks again, I'm sorry I wasn't able to get it all to work.

Cheers,
Simon

---

### Post by jonobr on 2008-11-14
Hey,

Sorry to loose you, Im hoping when things settle down a bit on your end and you have some quite time, you can come back to the light:-)

I think the time/money pressure you were under , you have made the best decision for you.

Just know there are a whole bunch of people on this forum willing to assist you when you comeback.

I know once these teething problems are resolved, ubuntu will win you over with the software that costs an arm and a leg on windows but can usually be obtained on ubuntu.

Remember before you go, the solution is there, it has been done before,
the clock just beat us......

---

### Post by Simon Lemb on 2008-11-14
> **jonobr said:**
> Hey,

Sorry to loose you, Im hoping when things settle down a bit on your end and you have some quite time, you can come back to the light:-)

I think the time/money pressure you were under , you have made the best decision for you.

Just know there are a whole bunch of people on this forum willing to assist you when you comeback.

I know once these teething problems are resolved, ubuntu will win you over with the software that costs an arm and a leg on windows but can usually be obtained on ubuntu.

Remember before you go, the solution is there, it has been done before,
the clock just beat us......

Thanks again....Windows98 is not working either! I guess I should have got a computer degree first! Funny thing is, I've installed that OS many times before, I guess just not on this laptop. It's not seeing the wifi capability of the laptop and I'm getting frustrated.

I decided to start from scratch again with Ubuntu. I have installed it again (version 8.10) and have gone through this thread again with no success.

The problem is that nothing is triggering recognition of the wifi card. I am truly stuck now as I don't understand a lot of the short hand you are using. When you put an * does this mean I use a * or are you using shorthand for "number" or something?



All I want is a step by step guide using this small EEPC with a usb stick and the actual text I need to input into the Ubuntu laptop.


I don't understand any of the references so I really just need to be spoon fed through the whole sorry thing!

If anyone can help in this way I'd be HUGELY grateful!!

---

### Post by Simon Lemb on 2008-11-14
Ok, I've got the .inf and .sys files on the desktop. Using the gui for winwrapper (?) I have managed to install the .inf file and it says that hardware is present. This seems like a good sign. I still don't know what the .sys file is for, I'll go back and read again.

Am I on the right track?

---

### Post by jonobr on 2008-11-14
Hello


WEclome back, that was a quick turnaround:-)

Im kinda worried you had similar problems with the windows installation and that wifi card. Im wondering if you have problematic hardware.

Do you execute the last few , Im not sure where you are exactly at the moment...

sudo ndiswrapper -i /home/saul/inf_file/bcmwl5a.inf

ndiswrapper -l <Enter>
sudo ndiswrapper -m <Enter>
sudo modprobe ndiswrapper <Enter>

If you did all this could you try doing an ifconfig in the terminal window and post back what you see,

---

### Post by prshah on 2008-11-14
> **Simon Lemb said:**
> Ok, I've got the .inf and .sys files on the desktop. Using the gui for winwrapper (?) I have managed to install the .inf file and it says that hardware is present. This seems like a good sign. I still don't know what the .sys file is for, I'll go back and read again.
Am I on the right track?

Absolutely. You don't need to worry about the .sys file. The .inf tells ndiswrapper what to do with the .sys

Once you have "modularised" the windows driver (ndiswrapper -m) you no longer need the .sys and/or .inf files.

As suggested, just load the ndiswrapper module, and (with a little luck) your wifi should be working!```
sudo modprobe ndiswrapper
```

---

### Post by Simon Lemb on 2008-11-14
> **jonobr said:**
> Hello


WEclome back, that was a quick turnaround:-)

Im kinda worried you had similar problems with the windows installation and that wifi card. Im wondering if you have problematic hardware.

Do you execute the last few , Im not sure where you are exactly at the moment...

sudo ndiswrapper -i /home/saul/inf_file/bcmwl5a.inf


 

LOL, yeah, I'm on a mission now to get this thing working..! :mad: :lolflag:


I've got as far as entering:

sudo ndiswrapper -i /home/saul/inf_file/bcmwl5a.inf

and this is what I get:

saul@saul-laptop:~$ sudo modprobe ndiswrapper
[sudo] password for saul: 
saul@saul-laptop:~$ sudo modprobe ndiswrapper
saul@saul-laptop:~$ sudo ndiswrapper -i/home/saul/inf_file/bcmwl5a.inf
install/manage Windows drivers for ndiswrapper

usage: ndiswrapper OPTION
-i inffile       install driver described by 'inffile'
-a devid driver  use installed 'driver' for 'devid' (dangerous)
-r driver        remove 'driver'
-l               list installed drivers
-m               write configuration for modprobe
-ma              write module alias configuration for all devices
-mi              write module install configuration for all devices
-v               report version information

where 'devid' is either PCIID or USBID of the form XXXX:XXXX,
as reported by 'lspci -n' or 'lsusb' for the card
saul@saul-laptop:~$ 


Does this make any sense to you?

---

### Post by jonobr on 2008-11-14
Hello

I think you bunched up, check the command

sudo ndiswrapper -i/home/saul/inf_file/bcmwl5a.inf

should  have a space between the i and the /home/saul

---

### Post by jonobr on 2008-11-14
BTW,

Just checking with you the files are there.

Im assuming if you do an 
ls /home/saul/inf_file/*.inf

it will show the file

then 

ls /home/saul/inf_file/*.sys it will show the sys file
(ls means list)

In file manager you could just navigate there and it should show it

---

### Post by Simon Lemb on 2008-11-14
> **prshah said:**
> Absolutely. You don't need to worry about the .sys file. The .inf tells ndiswrapper what to do with the .sys

Once you have "modularised" the windows driver (ndiswrapper -m) you no longer need the .sys and/or .inf files.

As suggested, just load the ndiswrapper module, and (with a little luck) your wifi should be working!```
sudo modprobe ndiswrapper
```

Thanks prshah, I get the following:

module configuration already contains alias


Any ideas?

---

### Post by Simon Lemb on 2008-11-14
> **jonobr said:**
> Hello

I think you bunched up, check the command

sudo ndiswrapper -i/home/saul/inf_file/bcmwl5a.inf

should  have a space between the i and the /home/saul
Ok, I tried that and got the following:


saul@saul-laptop:~$ sudo ndiswrapper -i /home/saul/inf_file/bcmwl5a.inf
[sudo] password for saul: 
couldn't open /home/saul/inf_file/bcmwl5a.inf: No such file or directory at /usr/sbin/ndiswrapper-1.9 line 219.
saul@saul-laptop:~$ 


The .sys and .inf files are in a folder on the desktop called: 

tecpages.com-bcm4318

Do I need to include that in the code when I specify location (home/saul....etc)

Also I have a little symbol in the top right of the screen next to the two computers icon that says "new drivers available". This is for the Broadcom B43 wireless driver. It says: Tested by the Ubuntu developers fwcutter is a tool which can extract firmware from various source files. It's written for BCM43xx driver files. There is a button that says activate which I pressed but not much happened....

---

### Post by Simon Lemb on 2008-11-14
> **jonobr said:**
> BTW,

Just checking with you the files are there.

Im assuming if you do an 
ls /home/saul/inf_file/*.inf

it will show the file

then 

ls /home/saul/inf_file/*.sys it will show the sys file
(ls means list)

In file manager you could just navigate there and it should show it

It says:

No  such file or directory

---

### Post by jonobr on 2008-11-14
Hello


Wrong directories,


on your desktop navigate to the folder and select the inf and sys files.
hightlight one and then hold down control and select the other.
Right click and select copy.


ON the top menu, go to place, 
it should open an explorer screen locate the 
inf_file directory you created. enter it right clck and paste
If inf_file is  not there go to file and create folder 
call it inf_file

then paste in the folder

rerun the ndis commands

---

### Post by jonobr on 2008-11-14
any luck??

---

### Post by Simon Lemb on 2008-11-15
> **jonobr said:**
> Hello


Wrong directories,


on your desktop navigate to the folder and select the inf and sys files.
hightlight one and then hold down control and select the other.
Right click and select copy.


ON the top menu, go to place, 
it should open an explorer screen locate the 
inf_file directory you created. enter it right clck and paste
If inf_file is  not there go to file and create folder 
call it inf_file

then paste in the folder

rerun the ndis commands

Ok, I have turned the computer on afresh.

On the desktop is a folder called:

tecpages.com-bcm4318

I double click that folder and inside are two files:

bcmwl5.inf

bcmwl5.sys

I highlight them both and right-click "copy"

The only thing I can see that says "place" is the Places menu on the top taskbar. Is there anyway you can explain the actions I need to take in this simple way please?

I don't understand terms like "rerun ndis commands" I'm afraid...is it possible you would just write it out as I have done above. Sorry to be slow but as I say I have very little knowledge.

---

### Post by jonobr on 2008-11-15
HEllo



Its like windows, you need to take those two files you copies and paste them info the inf directory you created,
up the top where you saw place, open that menu,select home.
It will open an exporer type window.
look for inf_file directory there.
If its not there you need to create it.
in that window, go to file->new folder
create it with exactly the same name.


When it appears plaste the two file in that folder.

Once thats done you are back to running the ndiswrapper commands in the console windo

---

### Post by Simon Lemb on 2008-11-15
> **jonobr said:**
> HEllo



Its like windows, you need to take those two files you copies and paste them info the inf directory you created,
up the top where you saw place, open that menu,select home.
It will open an exporer type window.
look for inf_file directory there.
If its not there you need to create it.
in that window, go to file->new folder
create it with exactly the same name.


When it appears plaste the two file in that folder.

Once thats done you are back to running the ndiswrapper commands in the console windo

Thanks jonobr, ok....I hit "places" ... then "home folder" and inside that folder is a folder called "inf_file". Do I put the .sys and .inf files in there?

---

### Post by sirebral on 2008-11-15
> **Simon Lemb said:**
> 
02:03.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
        Subsystem: Dell Device 0005
        Flags: bus master, fast devsel, latency 64, IRQ 17
        Memory at dfbfe000 (32-bit, non-prefetchable) [size=8K]
        Kernel driver in use: b43-pci-bridge
        Kernel modules: ssb

~
~

I noticed your WiFi card.  Please check here: [http://ubuntuforums.org/showthread.php?t=881903&page=2](http://ubuntuforums.org/showthread.php?t=881903&page=2)

Last post.

---

### Post by Swagman on 2008-11-16
If the wifi didn't work when you reinstalled  windows I suggest you go looky in the BIOS to make sure it's enabled.

as for your question on what is lmms

[**Looky here**](http://lmms.sourceforge.net/screenshots.php)

---

