---
title: "first switch from windows...questions"
date: 2009-07-18
forum: New to Ubuntu
---

### Post by allen blake on 2009-07-18
My monitor is working at 1280/1024 75 Hz.

This resolution is too small for my eyes.  I need to lower the resolution, however, when I lower the resolution, the monitor freaks out vertically, horizontally, scrolling left right, or up down, and I can't see anything, and I have to a hard reboot.

Under System/Preferences/Screen Resolution:
 Gateway 2000 18'
 
 Choices 1600/1200 75 Hz
             1280/1024 75 Hz
             1152/864 75 Hz
             1024/768 75 Hz, 70 Hz, 60 Hz, 43 Hz
             Etc.

When I click on "detect displays" it doesn't do anything.

What does "clone screens" mean?

I have found two other people that was having a similar problem in 2007, but no solutions.

---

### Post by nwadams on 2009-07-18
try 1024x768 with 60hz refresh rate

detect displays is supposed to detect the monitors you have connected.

clone screens makes both monitors show the same image (if you have two or more plugged in)

---

### Post by allen blake on 2009-07-18
Thank you for your quick response.  I attempted that setting ( I may have attempted it, previously, but wanted to make sure ), and same result.  Took me a while to get back here.  Sorry for the delay, but I had to do a hard reboot.

Additional symptom is that when the setting takes effect, the mouse moving up and down makes the part of the screen under the mouse pointer disappear/turn black.

I thought that was what "Detect Displays" meant, but when I click it, it does nothing, which may mean it is just leaving the monitor "as is"?  But, it just "appears" to do nothing.

---

### Post by CatKiller on 2009-07-18
> **allen blake said:**
> This resolution is too small for my eyes.

System &#8594; Preferences &#8594; Appearance &#8594; Fonts. Increase the font size.

You'll have a much better experience at a higher resolution with larger text than just making the resolution lower.

---

### Post by LewRockwell on 2009-07-18
system information?

ubuntu? kubuntu?

version?

enabled restricted drivers?

all updates accomplished?

.

---

### Post by allen blake on 2009-07-18
Thanks to all:

I apologize for not including my system information.

I am running Hardy Heron/8.04 with all updates except for the ones that popped up this morning.

Regarding restricted:  no, not enabled, I don't believe.  I disabled restricted libraries.  But, I did disable it AFTER this problem had arisen.  I had attempted to solve the resolution problem for a while before I restricted them.

Regarding simply changing font sizes, I have changed them in Firefox, and in system/appearance...

However, those changes only affect certain fonts.  The fonts in this text box I am typing at this moment, for example, as well as the text in discussion forum posts are not affected by changing font sizes in those areas.

Is there a third location to change font size that I am overlooking besides the two I have already altered?

If so, that would be a good intermediate fix, but I would still like to fix the actual problem that I am having with screen resolution.

Thank you for your time.

---

### Post by allen blake on 2009-07-18
Also, I forgot to ask, is there a similar tool to Belarc Advisor/Aida32 that will give me all the system info from this machine.  I built it from scrap parts, and don't know what most of the stuff is or came from, originally, although most of it was from a Gateway.  I used to use the previous tools on Windows machines to determine hardware/software version specs.

---

### Post by LewRockwell on 2009-07-18
I realize this sounds insanely simple but you may find that 9.04 operates exactly as you desire without headaches, heartaches, and other assorted problems

All the usual apply regarding acquiring and testing 9.04 on your system via utilization of the LiveCD test-drive function

.

---

### Post by allen blake on 2009-07-18
I had planned on trying it, too.  I thought 8.04 would have been the more stable.  It is the general consensus that 9.04 is more stable/bug-free than 8.04, then?

---

### Post by theozzlives on 2009-07-18
> **allen blake said:**
> I had planned on trying it, too.  I thought 8.04 would have been the more stable.  It is the general consensus that 9.04 is more stable/bug-free than 8.04, then?

Stable? In some ways yes, better yes (in my opinion). Some will disagree. 8.04 is just an LTS (Long Term Support) version. I did have to replace a video card on one of my computers with 9.04. 9.04 is faster and has a nice login screen. I'd try the live CD and decide for yourself.

---

### Post by CatKiller on 2009-07-18
> **allen blake said:**
>  However, those changes only affect certain fonts.  The fonts in this text box I am typing at this moment, for example, as well as the text in discussion forum posts are not affected by changing font sizes in those areas.

Is there a third location to change font size that I am overlooking besides the two I have already altered?

In Firefox, Edit &#8594; Preferences &#8594; Content &#8594; Fonts & Colors &#8594; Advanced. Uncheck "Allow pages to choose their own fonts, instead of my selections above."

> If so, that would be a good intermediate fix, but I would still like to fix the actual problem that I am having with screen resolution.Well, the actual problem is that the text is too small for you to read. And a higher resolution desktop does look better than a low resolution one.

But it would be nice to allow you to set your resolution as well.

> **allen blake said:**
> Also, I forgot to ask, is there a similar tool to Belarc Advisor/Aida32 that will give me all the system info from this machine.

The command-line option would be **lshw**, but it's not very pretty. You'll probably find **hardinfo** more to your liking. If it's not installed already you can install it through Synaptic. It's in the Universe repository.

EDIT: Posting the results of ```
lspci | grep VGA
``` would give information about your graphics hardware to help people here diagnose your problem.

---

### Post by barkej on 2009-07-18
I have no stability issues in 9.04. I would give the 904 livecd a whirl.

---

### Post by The Cog on 2009-07-19
Nah, this is the best way to do it...
Go System -> Preferences -> Appearance, choose the Fonts tab then click the Details... button. At the top of the page, there is an input for resolution in dots per inch. Try increasing the dots-per-inch setting - maybe double it. I attach two screenshots.

You will need to close the details window before the change takes effect, and you will need to restart firefox before the change happens in your web browser.

---

### Post by louieb on 2009-07-19
> **allen blake said:**
> ...However, those changes only affect certain fonts.  The fonts in this text box I am typing at this moment, for example, as well as the text in discussion forum posts are not affected by changing font sizes in those areas.


For Firefox get [No squint]("https://addons.mozilla.org/en-US/firefox/addon/2592") It's one of 1st add-ons I install. Lets you adjust font size on a site by site basis. 

another add-on that lets you changeg those weird  background and font colors that some site use is [web developer]("https://addons.mozilla.org/en-US/firefox/addon/60").

---

### Post by LewRockwell on 2009-07-19
just try 904 dude

let us know how it works!

.

---

### Post by allen blake on 2009-07-19
Thank you again.  I had been doing too many searches on the graphics issue.  I didn't take my blinders off to try to search on the font issue.  One track mind.  Will at least make my continued search on the graphics issue more tolerable.

Catkiller - Thanks, specifically, for that checked box in "advanced".  True fonts were actually, a separate problem.  More of a user issue, ignorant, and not paying attention to their actual solution.  One of the simpleton cures, - the screen resolution is the first thing that came to my mind to make it more immediately tolerable.  I do very much prefer the more elegant, and intended solution, which are the specific font adjustments, of course.  My appreciation for that quick fix.

Catkiller - With regard to:
 
lspci | grep VGA

I am on a Dell QuietKey keyboard, and it doesn't have the vertical separator key, so I attempted just "lspci" to see what I could get.  It worked, and I got the following result:

00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 01)
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
01:00.0 Ethernet controller: ADMtek NC100 Network Everywhere Fast Ethernet 10/100 (rev 11)
01:02.0 Modem: Broadcom Corporation BCM4212 v.90 56k modem
01:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VE (LOM) Ethernet Controller (rev 81)

(I knew a little UNIX about 20-25 years ago, but I didn't know it well enough to remember any of it, and wasn't sure if "code" was required.  I assumed that was just a notification for that text box, but what about that vertical separator?)

(And, while I am at it, how about another thing that is just kick ***, can an old guy say that?  Is 41 old?  Anyway, shout out to COPY and PASTE in the terminal window!  You rock.  DOS is?/was such a POS wrt that!  Maybe they have fixed that in later versions of Windows, and I'm unaware or I've just forgotten.)

I did "lshw", and will post those results in a separate reply.  Also, thank you for "hardinfo".  I have not added that, as of yet.  But, I will.  Continued thanks.

---

### Post by allen blake on 2009-07-19
CatKiller (and other benevolently interested parties):

1) What the hell is up with this warning?!  It just LISTS stuff, no?  Why should I have to be super to know this?  I have no special powers.  What does this mean.  Anyway.  Here it is

WARNING: you should run this program as super-user.

rogue                     
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 510MiB
     *-cpu
          product: Intel(R) Pentium(R) 4 CPU 2.00GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 15.2.4
          size: 2GHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm up pebs bts
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 8KiB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 512KiB
     *-pci
          description: Host bridge
          product: 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 01
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel module=intel_agp
        *-display
             description: VGA compatible controller
             product: 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: vga_controller bus_master cap_list
             configuration: driver=i810_smbus latency=0 module=i2c_i810
        *-usb:0
             description: USB Controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:1
             description: USB Controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:2
             description: USB Controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-pci
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 81
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master
           *-network:0
                description: Ethernet interface
                product: NC100 Network Everywhere Fast Ethernet 10/100
                vendor: ADMtek
                physical id: 0
                bus info: pci@0000:01:00.0
                logical name: eth0
                version: 11
                serial: 00:50:bf:b5:f2:10
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical
                configuration: broadcast=yes driver=tulip driverversion=1.1.15 latency=64 maxlatency=255 mingnt=255 module=tulip multicast=yes
           *-communication
                description: Modem
                product: BCM4212 v.90 56k modem
                vendor: Broadcom Corporation
                physical id: 2
                bus info: pci@0000:01:02.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: generic bus_master cap_list
                configuration: driver=serial latency=64
           *-network:1
                description: Ethernet interface
                product: 82801DB PRO/100 VE (LOM) Ethernet Controller
                vendor: Intel Corporation
                physical id: 8
                bus info: pci@0000:01:08.0
                logical name: eth1
                version: 81
                serial: 00:03:47:f4:5c:87
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical
                configuration: broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI firmware=N/A ip=192.168.1.100 latency=64 maxlatency=56 mingnt=8 module=e100 multicast=yes
        *-isa
             description: ISA bridge
             product: 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801DB (ICH4) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=ata_piix latency=0 module=ata_piix
        *-serial UNCLAIMED
             description: SMBus
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 01
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
        *-multimedia
             description: Multimedia audio controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=Intel ICH latency=0 module=snd_intel8x0

---

### Post by allen blake on 2009-07-19
The Cog - Thank you, I had already done that, but it only has an effect on certain text.  I was missing the "advanced" button in Firefox, as CatKiller guided me to.  Thank you for your assistance, though.

---

### Post by allen blake on 2009-07-19
LouieB - Thank you for those two jewels.  I will download them toot sweet.

Those suggesting 9.04 - I will definitely try that version.  I have already downloaded it, previously.  This machine was originally intended to be 9.04, but I ran into installation problems with 9.04.  I ran into the same/similar installation problems with 8.04, but I found out what they were ( RAM quantity - swapped with a Windows machine, and bingo ) and this version stuck.

I intend to build several of these machines, now, I hope.  9.04, and Mint, I will try next, for very little reason other than I've heard a few people say they were "cool".

I've also heard I should try Debian, etc.  As it is more of a "full" Linux, than is Ubuntu.  However, I have lived through enough "mine is better than yours" in the computer world to worry about that.  Amiga/AtariST, anyone?

Thanks all.

---

### Post by allen blake on 2009-07-19
One problem with using font adjustments instead of screen resolution is that I also don't have to worry about things like this:

Now that I have adjusted the font, I notice errors in formatting on this page, for example, the formatting for the search box in the upper right is messed up, and when I increase font size the word search and the box cover up the line below it.

  				 					 						Search 						 								 	 								 								 								 								 						go 					
  				 			
 		  	     

   	 		     Or,     [Sign in using your Launchpad ID]("http://ubuntuforums.org/launchpad_login.php")
 For example, this "Or, Sign in using your Launchpad ID" is covered by the "Search ------Box------- <Go Button>"

---

### Post by CatKiller on 2009-07-19
> **allen blake said:**
>  I am on a Dell QuietKey keyboard, and it doesn't have the vertical separator key

I don't know that much about keyboard layouts, but it's possible that you do still have the ability to generate that character, but it's just not printed on the keyboard. It's normally on the backslash, so possibly it's on the third level for that key. I believe that the key that's marked with the broken pipe (if you have that one) functions in the same way in a lot of cases. Otherwise there may be some way to generate it from other characters with the Compose key, but I don't what sequence that would be.

>  (I assumed that was just a notification for that text box)
 
That's right. It also makes large chunks of text easier to read, since it puts a handy scrollable box around it.

The vertical bar, which is often referred to as a pipe because of its function, serves to take the output from one command and pipe it into another as an input (using that most brilliant of inventions, the standard input and standard output). In this case, it takes the output from lspci, which lists all the devices connected to the PCI bus, and puts it through grep, which searches through that output to find the string ‘VGA.’

I don't know enough about Intel graphics to be able to speculate on that being the cause of your resolution problem.

> **allen blake said:**
>  1) What the hell is up with this warning?!  It just LISTS stuff, no?  Why should I have to be super to know this?

It just lists stuff, yes, but it might be trying to list stuff that you aren't able to read, such as bits and pieces from the /proc virtual subsystem. Without running the command as root (by using sudo), there's the possibility that while the information it returns is accurate it might not be complete, if the system is set up to prevent non-root users from reading the /proc entries. So it warns you about it. I don't think that Ubuntu is set up by default to prevent normal users from reading /proc, so I don't think there's a difference in this case, but there might well be on other systems.

Compare, for example, the disk usage tools that are available. Normal users are not able to see inside root's Home folder (/root) or /Lost+Found, and so they will necessarily miss any disk usage from anything in those directories. The totals won't add up, since the results are incomplete. Running the same query as root, which is able to look inside any directory, would be complete.

Websites that assume a certain resolution, or a certain font size/type, or a certain screen size, are really annoying. It limits the web. You'd hope that this forum would be able to do better, but I think they are limited in what they can do with the (non-Free) forum software. Perhaps a kind word to an appropriate email address would help, perhaps not.

---

### Post by allen blake on 2009-07-19
CakKiller:  Thanks again for the response.  I used the broken "pipe", and, indeed, the screen output was not broken, simply by using shift>backslash key.

I will go over your post with more of a fine-toothed comb tomorrow.  I have a honey-do list before bedtime, and then my mind will be free.

Quote:

Three little birds, outside my doorstep, singin' sweet songs, a large-font melody clear and true...this is my message to you-hooo-hoo.

(Wearing my silverfish-riddled  June 30th, 1996 "Don't want no rat race..." Bob Marley Festival t-shirt as I type, coincidentally.)

---

### Post by allen blake on 2009-07-24
Any more insight out there on why I can't change my resolution downward?

---

### Post by Zimmer on 2009-07-24
> **allen blake said:**
> Any more insight out there on why I can't change my resolution downward?

Have a look at the  xorg.log   and see if there are any messages for the display modes, or the virtual screen size reported for clues as to how to proceed . There may be a possibility of tweaking the xorg.conf to use the resolution you want..

---

### Post by allen blake on 2009-07-24
Thanks...took me a while to figure out how to open it.  I pico'ed it, and it appears to be empty.

This is all I get at the top (just the header, no?)

 GNU nano 2.0.7                       File: xorg.log

Thank you for the fresh commentary.

Sincerely,
Allen.

---

### Post by CatKiller on 2009-07-24
> **allen blake said:**
> GNU nano 2.0.7                       File: xorg.log

What you've done there is open a new file called xorg.log. The file you're after is at /var/log/Xorg.0.log.

---

### Post by LookTJ on 2009-07-24
> **CatKiller said:**
> What you've done there is open a new file called xorg.log. The file you're after is at /var/log/Xorg.0.log.and use ```
cat /var/log/Xorg.0.log | less
``` to view so you don't edit the log file.

---

### Post by CatKiller on 2009-07-24
Or just ```
less /var/log/Xorg.0.log
```

---

### Post by allen blake on 2009-07-25
Thanks, again, guys.  I thought I might have opened a new one (that's what I 'member good ol' DOS edit doing, when the file didn't exist...)

Found me a page that is giving me a lesson on the terminal commands.

With what you gave me here, I was able to successfully squeeze out the following:

--------------------

X.Org X Server 1.4.0.90
Release Date: 5 September 2007
X Protocol Version 11, Revision 0
Build Operating System: Linux Ubuntu (xorg-server 2:1.4.1~git20080131-1ubuntu9.2)
Current Operating System: Linux rogue 2.6.24-24-generic #1 SMP Tue Jul 7 19:46:39 UTC 2009 i686
Build Date: 13 June 2008  01:08:21AM
 
        Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
        to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri Jul 24 09:51:37 2009
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Configured Monitor"
(**) |   |-->Device "Configured Video Device"
(==) Automatically adding devices
(==) Automatically enabling devices
(==) No FontPath specified.  Using compiled-in default.
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
        Entry deleted from font path.
(==) FontPath set to:
        /usr/share/fonts/X11/misc,
        /usr/share/fonts/X11/100dpi/:unscaled,
:

---

### Post by CatKiller on 2009-07-25
Page Up/Page Down will scroll though the file. You can copy the whole text to a file on your Desktop with ```
cat /var/log/Xorg.0.log > ~/Desktop/xorg.log
``` (the | that you saw before pipes the output from one command to the input of another command, the > takes the output from one command and writes it to a file, and the ~ signifies your Home folder. If you want redirected output to append to a file instead of overwriting the file, you would use >> instead of >)

If you put the output between [CODE] tags when you post it here it will get a scrollable box around it.

---

### Post by sfantus1 on 2009-07-25
I had a similar problem 3 weeks   ago when my graphics card got toasted ... the problem for me was that i couldn`t rise my resolution :)  the problem proved to be the cable :| no one was able to tell me that this could be the problem.... but i had a non original cable ... and when i changed it with the original that came with the monitor everything worked great .... the monitor was detected the resolution detected everything ... I was so happy because i almost changed my card again to make it work

the problem happened also on ubuntu and windows vista fully updated (i dual boot)

---

### Post by allen blake on 2009-07-26
Here we go.  Thanks for the continued support.  Was out of town, briefly, sorry for the delay, if anyone was checking back.

```

This is a pre-release version of the X server from The X.Org Foundation.
It is not supported in any way.
Bugs may be filed in the bugzilla at [http://bugs.freedesktop.org/](http://bugs.freedesktop.org/).
Select the "xorg" product for bugs you find in this release.
Before reporting bugs in pre-release versions please check the
latest version in the X.Org Foundation git repository.
See [http://wiki.x.org/wiki/GitPage](http://wiki.x.org/wiki/GitPage) for git access instructions.

X.Org X Server 1.4.0.90
Release Date: 5 September 2007
X Protocol Version 11, Revision 0
Build Operating System: Linux Ubuntu (xorg-server 2:1.4.1~git20080131-1ubuntu9.2)
Current Operating System: Linux rogue 2.6.24-24-generic #1 SMP Tue Jul 7 19:46:39 UTC 2009 i686
Build Date: 13 June 2008  01:08:21AM
 
    Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sun Jul 26 09:26:52 2009
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Configured Monitor"
(**) |   |-->Device "Configured Video Device"
(==) Automatically adding devices
(==) Automatically enabling devices
(==) No FontPath specified.  Using compiled-in default.
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
    Entry deleted from font path.
(==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(==) |-->Input Device "Configured Mouse"
(==) |-->Input Device "Generic Keyboard"
(==) The core pointer device wasn't specified explicitly in the layout.
    Using the first core pointer device.
(==) The core keyboard device wasn't specified explicitly in the layout.
    Using the first keyboard device.
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x81dc500
(II) Module ABI versions:
    X.Org ANSI C Emulation: 0.3
    X.Org Video Driver: 2.0
    X.Org XInput driver : 2.0
    X.Org Server Extension : 0.3
    X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules//libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
    compiled for 1.4.0.90, module version = 1.0.0
    ABI class: X.Org Video Driver, version 2.0
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 8086,2560 card 8086,2560 rev 01 class 06,00,00 hdr 00
(II) PCI: 00:02:0: chip 8086,2562 card 107b,2000 rev 01 class 03,00,00 hdr 00
(II) PCI: 00:1d:0: chip 8086,24c2 card 107b,2000 rev 01 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,24c4 card 107b,2000 rev 01 class 0c,03,00 hdr 00
(II) PCI: 00:1d:2: chip 8086,24c7 card 107b,2000 rev 01 class 0c,03,00 hdr 00
(II) PCI: 00:1e:0: chip 8086,244e card 0000,0000 rev 81 class 06,04,00 hdr 01
(II) PCI: 00:1f:0: chip 8086,24c0 card 0000,0000 rev 01 class 06,01,00 hdr 80
(II) PCI: 00:1f:1: chip 8086,24cb card 107b,2000 rev 01 class 01,01,8a hdr 00
(II) PCI: 00:1f:3: chip 8086,24c3 card 107b,2000 rev 01 class 0c,05,00 hdr 00
(II) PCI: 00:1f:5: chip 8086,24c5 card 107b,2000 rev 01 class 04,01,00 hdr 00
(II) PCI: 01:00:0: chip 1317,0985 card 1113,ec02 rev 11 class 02,00,00 hdr 00
(II) PCI: 01:02:0: chip 14e4,4212 card 14e4,0002 rev 00 class 07,03,00 hdr 00
(II) PCI: 01:08:0: chip 8086,1039 card 107b,2000 rev 81 class 02,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Intel Bridge workaround enabled
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,1), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
    [0] -1    0    0x00000000 - 0x0000ffff (0x10000) IX[b]
(II) Bus 0 non-prefetchable memory range:
    [0] -1    0    0x00000000 - 0xffffffff (0x0) MX[b]
(II) Bus 0 prefetchable memory range:
    [0] -1    0    0x00000000 - 0xffffffff (0x0) MX[b]
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:30:0), (0,1,1), BCTRL: 0x0006 (VGA_EN is cleared)
(II) Bus 1 I/O range:
    [0] -1    0    0x0000d000 - 0x0000d0ff (0x100) IX[b]
    [1] -1    0    0x0000d400 - 0x0000d4ff (0x100) IX[b]
    [2] -1    0    0x0000d800 - 0x0000d8ff (0x100) IX[b]
    [3] -1    0    0x0000dc00 - 0x0000dcff (0x100) IX[b]
(II) Bus 1 non-prefetchable memory range:
    [0] -1    0    0xff800000 - 0xff8fffff (0x100000) MX[b]
(II) Bus 1 prefetchable memory range:
    [0] -1    0    0xe6a00000 - 0xe6afffff (0x100000) MX[b]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(0:2:0) Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device rev 1, Mem @ 0xf0000000/27, 0xffa80000/19
(II) Addressable bus resource ranges are
    [0] -1    0    0x00000000 - 0xffffffff (0x0) MX[b]
    [1] -1    0    0x00000000 - 0x0000ffff (0x10000) IX[b]
(II) OS-reported resource ranges:
    [0] -1    0    0x00100000 - 0x3fffffff (0x3ff00000) MX[b]E(B)
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [5] -1    0    0x00000000 - 0x000000ff (0x100) IX[b]
(II) PCI Memory resource overlap reduced 0xf8000000 from 0xfbffffff to 0xf7ffffff
(II) Active PCI resource ranges:
    [0] -1    0    0xff8fd000 - 0xff8fdfff (0x1000) MX[b]
    [1] -1    0    0xff8fe000 - 0xff8fefff (0x1000) MX[b]
    [2] -1    0    0xff8ffc00 - 0xff8fffff (0x400) MX[b]
    [3] -1    0    0xffa7f800 - 0xffa7f8ff (0x100) MX[b]
    [4] -1    0    0xffa7fc00 - 0xffa7fdff (0x200) MX[b]
    [5] -1    0    0x20000000 - 0x200003ff (0x400) MX[b]
    [6] -1    0    0xf8000000 - 0xf7ffffff (0x0) MX[b]O
    [7] -1    0    0xffa80000 - 0xffafffff (0x80000) MX[b](B)
    [8] -1    0    0xf0000000 - 0xf7ffffff (0x8000000) MX[b](B)
    [9] -1    0    0x0000d480 - 0x0000d4bf (0x40) IX[b]
    [10] -1    0    0x0000dc00 - 0x0000dc0f (0x10) IX[b]
    [11] -1    0    0x0000d800 - 0x0000d8ff (0x100) IX[b]
    [12] -1    0    0x0000e080 - 0x0000e0bf (0x40) IX[b]
    [13] -1    0    0x0000e400 - 0x0000e4ff (0x100) IX[b]
    [14] -1    0    0x0000e000 - 0x0000e01f (0x20) IX[b]
    [15] -1    0    0x0000ffa0 - 0x0000ffaf (0x10) IX[b]
    [16] -1    0    0x000001f0 - 0x000001f0 (0x1) IX[b]
    [17] -1    0    0x000001f0 - 0x000001f7 (0x8) IX[b]
    [18] -1    0    0x000001f0 - 0x000001f0 (0x1) IX[b]
    [19] -1    0    0x000001f0 - 0x000001f7 (0x8) IX[b]
    [20] -1    0    0x0000ec00 - 0x0000ec1f (0x20) IX[b]
    [21] -1    0    0x0000e880 - 0x0000e89f (0x20) IX[b]
    [22] -1    0    0x0000e800 - 0x0000e81f (0x20) IX[b]
(II) Active PCI resource ranges after removing overlaps:
    [0] -1    0    0xff8fd000 - 0xff8fdfff (0x1000) MX[b]
    [1] -1    0    0xff8fe000 - 0xff8fefff (0x1000) MX[b]
    [2] -1    0    0xff8ffc00 - 0xff8fffff (0x400) MX[b]
    [3] -1    0    0xffa7f800 - 0xffa7f8ff (0x100) MX[b]
    [4] -1    0    0xffa7fc00 - 0xffa7fdff (0x200) MX[b]
    [5] -1    0    0x20000000 - 0x200003ff (0x400) MX[b]
    [6] -1    0    0xf8000000 - 0xf7ffffff (0x0) MX[b]O
    [7] -1    0    0xffa80000 - 0xffafffff (0x80000) MX[b](B)
    [8] -1    0    0xf0000000 - 0xf7ffffff (0x8000000) MX[b](B)
    [9] -1    0    0x0000d480 - 0x0000d4bf (0x40) IX[b]
    [10] -1    0    0x0000dc00 - 0x0000dc0f (0x10) IX[b]
    [11] -1    0    0x0000d800 - 0x0000d8ff (0x100) IX[b]
    [12] -1    0    0x0000e080 - 0x0000e0bf (0x40) IX[b]
    [13] -1    0    0x0000e400 - 0x0000e4ff (0x100) IX[b]
    [14] -1    0    0x0000e000 - 0x0000e01f (0x20) IX[b]
    [15] -1    0    0x0000ffa0 - 0x0000ffaf (0x10) IX[b]
    [16] -1    0    0x000001f0 - 0x000001f0 (0x1) IX[b]
    [17] -1    0    0x000001f0 - 0x000001f7 (0x8) IX[b]
    [18] -1    0    0x000001f0 - 0x000001f0 (0x1) IX[b]
    [19] -1    0    0x000001f0 - 0x000001f7 (0x8) IX[b]
    [20] -1    0    0x0000ec00 - 0x0000ec1f (0x20) IX[b]
    [21] -1    0    0x0000e880 - 0x0000e89f (0x20) IX[b]
    [22] -1    0    0x0000e800 - 0x0000e81f (0x20) IX[b]
(II) OS-reported resource ranges after removing overlaps with PCI:
    [0] -1    0    0x00100000 - 0x1fffffff (0x1ff00000) MX[b]E(B)
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [5] -1    0    0x00000000 - 0x000000ff (0x100) IX[b]
(II) All system resource ranges:
    [0] -1    0    0x00100000 - 0x1fffffff (0x1ff00000) MX[b]E(B)
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [4] -1    0    0xff8fd000 - 0xff8fdfff (0x1000) MX[b]
    [5] -1    0    0xff8fe000 - 0xff8fefff (0x1000) MX[b]
    [6] -1    0    0xff8ffc00 - 0xff8fffff (0x400) MX[b]
    [7] -1    0    0xffa7f800 - 0xffa7f8ff (0x100) MX[b]
    [8] -1    0    0xffa7fc00 - 0xffa7fdff (0x200) MX[b]
    [9] -1    0    0x20000000 - 0x200003ff (0x400) MX[b]
    [10] -1    0    0xf8000000 - 0xf7ffffff (0x0) MX[b]O
    [11] -1    0    0xffa80000 - 0xffafffff (0x80000) MX[b](B)
    [12] -1    0    0xf0000000 - 0xf7ffffff (0x8000000) MX[b](B)
    [13] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [14] -1    0    0x00000000 - 0x000000ff (0x100) IX[b]
    [15] -1    0    0x0000d480 - 0x0000d4bf (0x40) IX[b]
    [16] -1    0    0x0000dc00 - 0x0000dc0f (0x10) IX[b]
    [17] -1    0    0x0000d800 - 0x0000d8ff (0x100) IX[b]
    [18] -1    0    0x0000e080 - 0x0000e0bf (0x40) IX[b]
    [19] -1    0    0x0000e400 - 0x0000e4ff (0x100) IX[b]
    [20] -1    0    0x0000e000 - 0x0000e01f (0x20) IX[b]
    [21] -1    0    0x0000ffa0 - 0x0000ffaf (0x10) IX[b]
    [22] -1    0    0x000001f0 - 0x000001f0 (0x1) IX[b]
    [23] -1    0    0x000001f0 - 0x000001f7 (0x8) IX[b]
    [24] -1    0    0x000001f0 - 0x000001f0 (0x1) IX[b]
    [25] -1    0    0x000001f0 - 0x000001f7 (0x8) IX[b]
    [26] -1    0    0x0000ec00 - 0x0000ec1f (0x20) IX[b]
    [27] -1    0    0x0000e880 - 0x0000e89f (0x20) IX[b]
    [28] -1    0    0x0000e800 - 0x0000e81f (0x20) IX[b]
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
    compiled for 1.4.0.90, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 0.3
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
    compiled for 1.4.0.90, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 0.3
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
    compiled for 1.4.0.90, module version = 1.0.0
    ABI class: X.Org Server Extension, version 0.3
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
    compiled for 1.4.0.90, module version = 2.1.0
    Module class: X.Org Font Renderer
    ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
    compiled for 1.4.0.90, module version = 1.13.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 0.3
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
    compiled for 1.4.0.90, module version = 1.0.0
    ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) Matched intel from file name intel.ids in autoconfig
(==) Matched intel for the autoconfigured driver
(==) Assigned the driver to the xf86ConfigLayout
(II) LoadModule: "intel"
(II) Loading /usr/lib/xorg/modules/drivers//intel_drv.so
(II) Module intel: vendor="X.Org Foundation"
    compiled for 1.4.0.90, module version = 2.2.1
    Module class: X.Org Video Driver
    ABI class: X.Org Video Driver, version 2.0
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
    compiled for 1.4.0, module version = 1.2.3
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 2.0
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
    compiled for 1.4.0, module version = 1.2.2
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 2.0
(II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
    i810-dc100, i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G,
    E7221 (i915), 915GM, 945G, 945GM, 945GME, 965G, G35, 965Q, 946GZ,
    965GM, 965GME/GLE, G33, Q35, Q33, Intel Integrated Graphics Device
(II) Primary Device is: PCI 00:02:0
(--) Assigning device section with no busID to primary device
(--) Chipset 845G found
(II) resource ranges after xf86ClaimFixedResources() call:
    [0] -1    0    0x00100000 - 0x1fffffff (0x1ff00000) MX[b]E(B)
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [4] -1    0    0xff8fd000 - 0xff8fdfff (0x1000) MX[b]
    [5] -1    0    0xff8fe000 - 0xff8fefff (0x1000) MX[b]
    [6] -1    0    0xff8ffc00 - 0xff8fffff (0x400) MX[b]
    [7] -1    0    0xffa7f800 - 0xffa7f8ff (0x100) MX[b]
    [8] -1    0    0xffa7fc00 - 0xffa7fdff (0x200) MX[b]
    [9] -1    0    0x20000000 - 0x200003ff (0x400) MX[b]
    [10] -1    0    0xf8000000 - 0xf7ffffff (0x0) MX[b]O
    [11] -1    0    0xffa80000 - 0xffafffff (0x80000) MX[b](B)
    [12] -1    0    0xf0000000 - 0xf7ffffff (0x8000000) MX[b](B)
    [13] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [14] -1    0    0x00000000 - 0x000000ff (0x100) IX[b]
    [15] -1    0    0x0000d480 - 0x0000d4bf (0x40) IX[b]
    [16] -1    0    0x0000dc00 - 0x0000dc0f (0x10) IX[b]
    [17] -1    0    0x0000d800 - 0x0000d8ff (0x100) IX[b]
    [18] -1    0    0x0000e080 - 0x0000e0bf (0x40) IX[b]
    [19] -1    0    0x0000e400 - 0x0000e4ff (0x100) IX[b]
    [20] -1    0    0x0000e000 - 0x0000e01f (0x20) IX[b]
    [21] -1    0    0x0000ffa0 - 0x0000ffaf (0x10) IX[b]
    [22] -1    0    0x000001f0 - 0x000001f0 (0x1) IX[b]
    [23] -1    0    0x000001f0 - 0x000001f7 (0x8) IX[b]
    [24] -1    0    0x000001f0 - 0x000001f0 (0x1) IX[b]
    [25] -1    0    0x000001f0 - 0x000001f7 (0x8) IX[b]
    [26] -1    0    0x0000ec00 - 0x0000ec1f (0x20) IX[b]
    [27] -1    0    0x0000e880 - 0x0000e89f (0x20) IX[b]
    [28] -1    0    0x0000e800 - 0x0000e81f (0x20) IX[b]
(II) resource ranges after probing:
    [0] -1    0    0x00100000 - 0x1fffffff (0x1ff00000) MX[b]E(B)
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [4] -1    0    0xff8fd000 - 0xff8fdfff (0x1000) MX[b]
    [5] -1    0    0xff8fe000 - 0xff8fefff (0x1000) MX[b]
    [6] -1    0    0xff8ffc00 - 0xff8fffff (0x400) MX[b]
    [7] -1    0    0xffa7f800 - 0xffa7f8ff (0x100) MX[b]
    [8] -1    0    0xffa7fc00 - 0xffa7fdff (0x200) MX[b]
    [9] -1    0    0x20000000 - 0x200003ff (0x400) MX[b]
    [10] -1    0    0xf8000000 - 0xf7ffffff (0x0) MX[b]O
    [11] -1    0    0xffa80000 - 0xffafffff (0x80000) MX[b](B)
    [12] -1    0    0xf0000000 - 0xf7ffffff (0x8000000) MX[b](B)
    [13] 0    0    0x000a0000 - 0x000affff (0x10000) MS[b]
    [14] 0    0    0x000b0000 - 0x000b7fff (0x8000) MS[b]
    [15] 0    0    0x000b8000 - 0x000bffff (0x8000) MS[b]
    [16] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [17] -1    0    0x00000000 - 0x000000ff (0x100) IX[b]
    [18] -1    0    0x0000d480 - 0x0000d4bf (0x40) IX[b]
    [19] -1    0    0x0000dc00 - 0x0000dc0f (0x10) IX[b]
    [20] -1    0    0x0000d800 - 0x0000d8ff (0x100) IX[b]
    [21] -1    0    0x0000e080 - 0x0000e0bf (0x40) IX[b]
    [22] -1    0    0x0000e400 - 0x0000e4ff (0x100) IX[b]
    [23] -1    0    0x0000e000 - 0x0000e01f (0x20) IX[b]
    [24] -1    0    0x0000ffa0 - 0x0000ffaf (0x10) IX[b]
    [25] -1    0    0x000001f0 - 0x000001f0 (0x1) IX[b]
    [26] -1    0    0x000001f0 - 0x000001f7 (0x8) IX[b]
    [27] -1    0    0x000001f0 - 0x000001f0 (0x1) IX[b]
    [28] -1    0    0x000001f0 - 0x000001f7 (0x8) IX[b]
    [29] -1    0    0x0000ec00 - 0x0000ec1f (0x20) IX[b]
    [30] -1    0    0x0000e880 - 0x0000e89f (0x20) IX[b]
    [31] -1    0    0x0000e800 - 0x0000e81f (0x20) IX[b]
    [32] 0    0    0x000003b0 - 0x000003bb (0xc) IS[b]
    [33] 0    0    0x000003c0 - 0x000003df (0x20) IS[b]
(II) Setting vga for screen 0.
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
    compiled for 1.4.0.90, module version = 1.0.0
    ABI class: X.Org Video Driver, version 2.0
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
    compiled for 1.4.0.90, module version = 1.1.0
    ABI class: X.Org Video Driver, version 2.0
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
    compiled for 1.4.0.90, module version = 0.1.0
    ABI class: X.Org Video Driver, version 2.0
(II) intel(0): Creating default Display subsection in Screen section
    "Default Screen" for depth/fbbpp 24/32
(==) intel(0): Depth 24, (==) framebuffer bpp 32
(==) intel(0): RGB weight 888
(==) intel(0): Default visual is TrueColor
(II) intel(0): Integrated Graphics Chipset: Intel(R) 845G
(--) intel(0): Chipset: "845G"
(--) intel(0): Linear framebuffer at 0xF0000000
(--) intel(0): IO registers at addr 0xFFA80000
(II) intel(0): 1 display pipe available.
(==) intel(0): Using EXA for acceleration
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"(II) Module "ddc" already built-in
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"(II) Module "i2c" already built-in
(II) intel(0): Output VGA using monitor section Configured Monitor
(II) intel(0): I2C bus "CRTDDC_A" initialized.
(II) intel(0): I2C bus "DVODDC_D" initialized.
(II) Loading sub module "sil164"
(II) LoadModule: "sil164"
(II) Loading /usr/lib/xorg/modules/drivers//sil164.so
(II) Module sil164: vendor="X.Org Foundation"
    compiled for 1.4.0.90, module version = 1.0.0
    ABI class: X.Org Video Driver, version 2.0
(II) intel(0): I2C bus "DVOI2C_E" initialized.
(II) Loading sub module "ch7xxx"
(II) LoadModule: "ch7xxx"
(II) Loading /usr/lib/xorg/modules/drivers//ch7xxx.so
(II) Module ch7xxx: vendor="X.Org Foundation"
    compiled for 1.4.0.90, module version = 1.0.0
    ABI class: X.Org Video Driver, version 2.0
(II) intel(0): I2C bus "DVOI2C_E" removed.
(II) intel(0): I2C bus "DVOI2C_E" initialized.
(II) Loading sub module "ivch"
(II) LoadModule: "ivch"
(II) Loading /usr/lib/xorg/modules/drivers//ivch.so
(II) Module ivch: vendor="X.Org Foundation"
    compiled for 1.4.0.90, module version = 1.0.0
    ABI class: X.Org Video Driver, version 2.0
(II) intel(0): I2C bus "DVOI2C_E" removed.
(II) intel(0): I2C bus "DVOI2C_B" initialized.
(II) Loading sub module "tfp410"
(II) LoadModule: "tfp410"
(II) Loading /usr/lib/xorg/modules/drivers//tfp410.so
(II) Module tfp410: vendor="X.Org Foundation"
    compiled for 1.4.0.90, module version = 1.0.0
    ABI class: X.Org Video Driver, version 2.0
(II) intel(0): I2C bus "DVOI2C_B" removed.
(II) intel(0): I2C bus "DVOI2C_E" initialized.
(II) Loading sub module "ch7017"
(II) LoadModule: "ch7017"
(II) Loading /usr/lib/xorg/modules/drivers//ch7017.so
(II) Module ch7017: vendor="X.Org Foundation"
    compiled for 1.4.0.90, module version = 1.0.0
    ABI class: X.Org Video Driver, version 2.0
(II) intel(0): I2C bus "DVOI2C_E" removed.
(II) intel(0): I2C bus "DVOI2C_E" initialized.
(II) intel(0): I2C bus "DVOI2C_E" removed.
(II) intel(0): I2C bus "DVODDC_D" removed.
(II) intel(0): I2C device "CRTDDC_A:ddc2" registered at address 0xA0.
(II) intel(0): EDID vendor "GWY", prod id 9003
(II) intel(0): Using EDID range info for horizontal sync
(II) intel(0): Using EDID range info for vertical refresh
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) intel(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x0.0   35.50  720 738 846 900  400 421 423 449 -hsync -vsync (39.4 kHz)
(II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) intel(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) intel(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) intel(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "1024x768"x0.0   44.90  1024 1032 1208 1264  768 768 776 817 interlace +hsync +vsync (35.5 kHz)
(II) intel(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) intel(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) intel(0): Modeline "1024x768"x74.9   82.00  1024 1088 1192 1360  768 771 775 805 -hsync +vsync (60.3 kHz)
(II) intel(0): Modeline "800x600"x74.9   49.00  800 840 920 1040  600 603 607 629 -hsync +vsync (47.1 kHz)
(II) intel(0): Modeline "640x480"x59.4   23.75  640 664 720 800  480 483 487 500 -hsync +vsync (29.7 kHz)
(II) intel(0): Modeline "1024x768"x59.9   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync (47.8 kHz)
(II) intel(0): Modeline "640x480"x74.8   30.75  640 664 728 816  480 483 487 504 -hsync +vsync (37.7 kHz)
(II) intel(0): Modeline "720x405"x69.6   26.50  720 744 808 896  405 408 413 425 -hsync +vsync (29.6 kHz)
(II) intel(0): Modeline "1280x1024"x74.9  138.75  1280 1368 1504 1728  1024 1027 1034 1072 -hsync +vsync (80.3 kHz)
(II) intel(0): Modeline "1600x1200"x75.0  204.75  1600 1720 1888 2176  1200 1203 1207 1255 -hsync +vsync (94.1 kHz)
(II) intel(0): EDID vendor "GWY", prod id 9003
(II) intel(0): Output VGA connected
(II) intel(0): Output VGA using initial mode 1280x1024
(II) intel(0): detected 128 kB GTT.
(II) intel(0): detected 892 kB stolen memory.
(==) intel(0): video overlay key set to 0x101fe
(==) intel(0): Will not try to enable page flipping
(==) intel(0): Triple buffering disabled
(==) intel(0): Using gamma correction (1.0, 1.0, 1.0)
(**) intel(0): Display dimensions: (360, 270) mm
(**) intel(0): DPI set to (112, 150)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
    compiled for 1.4.0.90, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "exa"
(II) LoadModule: "exa"
(II) Loading /usr/lib/xorg/modules//libexa.so
(II) Module exa: vendor="X.Org Foundation"
    compiled for 1.4.0.90, module version = 2.2.0
    ABI class: X.Org Video Driver, version 2.0
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"(II) Module "ramdac" already built-in
(II) intel(0): Comparing regs from server start up to After PreInit
(==) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
    [0] 0    0    0xffa80000 - 0xffafffff (0x80000) MS[b]
    [1] 0    0    0xf0000000 - 0xf7ffffff (0x8000000) MS[b]
    [2] -1    0    0x00100000 - 0x1fffffff (0x1ff00000) MX[b]E(B)
    [3] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [4] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [5] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [6] -1    0    0xff8fd000 - 0xff8fdfff (0x1000) MX[b]
    [7] -1    0    0xff8fe000 - 0xff8fefff (0x1000) MX[b]
    [8] -1    0    0xff8ffc00 - 0xff8fffff (0x400) MX[b]
    [9] -1    0    0xffa7f800 - 0xffa7f8ff (0x100) MX[b]
    [10] -1    0    0xffa7fc00 - 0xffa7fdff (0x200) MX[b]
    [11] -1    0    0x20000000 - 0x200003ff (0x400) MX[b]
    [12] -1    0    0xf8000000 - 0xf7ffffff (0x0) MX[b]O
    [13] -1    0    0xffa80000 - 0xffafffff (0x80000) MX[b](B)
    [14] -1    0    0xf0000000 - 0xf7ffffff (0x8000000) MX[b](B)
    [15] 0    0    0x000a0000 - 0x000affff (0x10000) MS[b](OprD)
    [16] 0    0    0x000b0000 - 0x000b7fff (0x8000) MS[b](OprD)
    [17] 0    0    0x000b8000 - 0x000bffff (0x8000) MS[b](OprD)
    [18] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [19] -1    0    0x00000000 - 0x000000ff (0x100) IX[b]
    [20] -1    0    0x0000d480 - 0x0000d4bf (0x40) IX[b]
    [21] -1    0    0x0000dc00 - 0x0000dc0f (0x10) IX[b]
    [22] -1    0    0x0000d800 - 0x0000d8ff (0x100) IX[b]
    [23] -1    0    0x0000e080 - 0x0000e0bf (0x40) IX[b]
    [24] -1    0    0x0000e400 - 0x0000e4ff (0x100) IX[b]
    [25] -1    0    0x0000e000 - 0x0000e01f (0x20) IX[b]
    [26] -1    0    0x0000ffa0 - 0x0000ffaf (0x10) IX[b]
    [27] -1    0    0x000001f0 - 0x000001f0 (0x1) IX[b]
    [28] -1    0    0x000001f0 - 0x000001f7 (0x8) IX[b]
    [29] -1    0    0x000001f0 - 0x000001f0 (0x1) IX[b]
    [30] -1    0    0x000001f0 - 0x000001f7 (0x8) IX[b]
    [31] -1    0    0x0000ec00 - 0x0000ec1f (0x20) IX[b]
    [32] -1    0    0x0000e880 - 0x0000e89f (0x20) IX[b]
    [33] -1    0    0x0000e800 - 0x0000e81f (0x20) IX[b]
    [34] 0    0    0x000003b0 - 0x000003bb (0xc) IS[b](OprU)
    [35] 0    0    0x000003c0 - 0x000003df (0x20) IS[b](OprU)
(II) intel(0): Kernel reported 112128 total, 1 used
(II) intel(0): I830CheckAvailableMemory: 448508 kB available
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenByBusid: Searching for BusID pci:0000:00:02.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: drmOpenMinor returns 8
drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
(II) [drm] loaded kernel module for "i915" driver.
(II) [drm] DRM interface version 1.3
(II) [drm] DRM open master succeeded.
(II) intel(0): [drm] Using the DRM lock SAREA also for drawables.
(II) intel(0): [drm] framebuffer mapped by ddx driver
(II) intel(0): [drm] added 1 reserved context for kernel
(II) intel(0): X context handle = 0x1
(II) intel(0): [drm] installed DRM signal handler
(==) intel(0): VideoRam: 131072 KB
(**) intel(0): Framebuffer compression disabled
(**) intel(0): Tiling enabled
(II) intel(0): Attempting memory allocation with tiled buffers.
(WW) intel(0): Failed to allocate texture space.
(II) intel(0): Attempting memory allocation with untiled buffers.
(II) intel(0): Success.
(II) intel(0): [drm] Registers = 0xffa80000
(II) intel(0): [drm] ring buffer = 0xf0000000
(II) intel(0): [drm] mapped front buffer at 0xf00e0000, handle = 0xf00e0000
(II) intel(0): [drm] mapped back buffer at 0xf27f0000, handle = 0xf27f0000
(II) intel(0): [drm] mapped depth buffer at 0xf31b4000, handle = 0xf31b4000
(II) intel(0): [drm] mapped classic textures at 0xf3b78000, handle = 0xf3b78000
(II) intel(0): [drm] Initialized kernel agp heap manager, 33554432
(II) intel(0): [dri] visual configs initialized
(II) intel(0): Page Flipping disabled
(==) intel(0): Write-combining range (0xf0000000,0x8000000)
(II) intel(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(WW) intel(0): EXA greedy migration mode enabled.
(II) EXA(0): Forcing greedy migration option
(II) EXA(0): Offscreen pixmap area of 30720000 bytes
(II) EXA(0): Driver registered support for the following operations:
(II)         Solid
(II)         Copy
(II)         Composite (RENDER acceleration)
(==) intel(0): Backing store disabled
(==) intel(0): Silken mouse enabled
(II) intel(0): Initializing HW Cursor
(II) intel(0): [DRI] installation complete
(II) intel(0): xf86BindGARTMemory: bind key 0 at 0x000df000 (pgoffset 223)
(II) intel(0): xf86BindGARTMemory: bind key 1 at 0x000e0000 (pgoffset 224)
(II) intel(0): xf86BindGARTMemory: bind key 2 at 0x00aa4000 (pgoffset 2724)
(II) intel(0): xf86BindGARTMemory: bind key 3 at 0x027f0000 (pgoffset 10224)
(II) intel(0): xf86BindGARTMemory: bind key 4 at 0x031b4000 (pgoffset 12724)
(II) intel(0): xf86BindGARTMemory: bind key 5 at 0x03b78000 (pgoffset 15224)
(II) intel(0): Fixed memory allocation layout:
(II) intel(0): 0x00000000-0x0001ffff: ring buffer (128 kB)
(II) intel(0): 0x00020000-0x00024fff: HW cursors (20 kB)
(II) intel(0): 0x00025000-0x0002cfff: logical 3D context (32 kB)
(II) intel(0): 0x000df000:            end of stolen memory
(II) intel(0): 0x000df000-0x000dffff: overlay registers (4 kB, 0x000000000e796000 physical
)
(II) intel(0): 0x000e0000-0x00aa3fff: front buffer (10000 kB)
(II) intel(0): 0x00aa4000-0x027effff: exa offscreen (30000 kB)
(II) intel(0): 0x027f0000-0x031b3fff: back buffer (10000 kB)
(II) intel(0): 0x031b4000-0x03b77fff: depth buffer (10000 kB)
(II) intel(0): 0x03b78000-0x05b77fff: classic textures (32768 kB)
(II) intel(0): 0x08000000:            end of aperture
(II) intel(0): Output configuration:
(II) intel(0):   Pipe A is on
(II) intel(0):   Display plane A is now enabled and connected to pipe A.
(II) intel(0):   Output VGA is connected to pipe A
(II) intel(0): [drm] dma control initialized, using IRQ 17
(II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
(II) intel(0): DPMS enabled
(II) intel(0): Set up overlay video
(II) intel(0): direct rendering: Enabled
(--) RandR disabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension XAccessControlExtension
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 9, (OK)
drmOpenByBusid: Searching for BusID pci:0000:00:02.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 9, (OK)
drmOpenByBusid: drmOpenMinor returns 9
drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
(WW) AIGLX: 3D driver claims to not support visual 0x23
(WW) AIGLX: 3D driver claims to not support visual 0x24
(WW) AIGLX: 3D driver claims to not support visual 0x25
(WW) AIGLX: 3D driver claims to not support visual 0x26
(WW) AIGLX: 3D driver claims to not support visual 0x27
(WW) AIGLX: 3D driver claims to not support visual 0x28
(WW) AIGLX: 3D driver claims to not support visual 0x29
(WW) AIGLX: 3D driver claims to not support visual 0x2a
(WW) AIGLX: 3D driver claims to not support visual 0x2b
(WW) AIGLX: 3D driver claims to not support visual 0x2c
(WW) AIGLX: 3D driver claims to not support visual 0x2d
(WW) AIGLX: 3D driver claims to not support visual 0x2e
(WW) AIGLX: 3D driver claims to not support visual 0x2f
(WW) AIGLX: 3D driver claims to not support visual 0x30
(WW) AIGLX: 3D driver claims to not support visual 0x31
(WW) AIGLX: 3D driver claims to not support visual 0x32
(II) AIGLX: Loaded and initialized /usr/lib/dri/i915_dri.so
(II) GLX: Initialized DRI GL provider for screen 0
(II) intel(0): Setting screen physical size to 350 x 262
(WW) Configured Mouse: No Device specified, looking for one...
(II) Configured Mouse: Setting Device option to "/dev/input/mice"
(--) Configured Mouse: Device: "/dev/input/mice"
(==) Configured Mouse: Protocol: "Auto"
(**) Option "CorePointer"
(**) Configured Mouse: always reports core events
(**) Option "Device" "/dev/input/mice"
(==) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Configured Mouse: Sensitivity: 1
(**) Option "CoreKeyboard"
(**) Generic Keyboard: always reports core events
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "us"
(**) Generic Keyboard: XkbLayout: "us"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(II) evaluating device (Generic Keyboard)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) evaluating device (Configured Mouse)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(--) Configured Mouse: PnP-detected protocol: "ExplorerPS/2"
(II) Configured Mouse: ps2EnableDataReporting: succeeded
(II) intel(0): EDID vendor "GWY", prod id 9003
(II) intel(0): Using hsync ranges from config file
(II) intel(0): Using vrefresh ranges from config file
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) intel(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x0.0   35.50  720 738 846 900  400 421 423 449 -hsync -vsync (39.4 kHz)
(II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) intel(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) intel(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) intel(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "1024x768"x0.0   44.90  1024 1032 1208 1264  768 768 776 817 interlace +hsync +vsync (35.5 kHz)
(II) intel(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) intel(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) intel(0): Modeline "1024x768"x74.9   82.00  1024 1088 1192 1360  768 771 775 805 -hsync +vsync (60.3 kHz)
(II) intel(0): Modeline "800x600"x74.9   49.00  800 840 920 1040  600 603 607 629 -hsync +vsync (47.1 kHz)
(II) intel(0): Modeline "640x480"x59.4   23.75  640 664 720 800  480 483 487 500 -hsync +vsync (29.7 kHz)
(II) intel(0): Modeline "1024x768"x59.9   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync (47.8 kHz)
(II) intel(0): Modeline "640x480"x74.8   30.75  640 664 728 816  480 483 487 504 -hsync +vsync (37.7 kHz)
(II) intel(0): Modeline "720x405"x69.6   26.50  720 744 808 896  405 408 413 425 -hsync +vsync (29.6 kHz)
(II) intel(0): Modeline "1280x1024"x74.9  138.75  1280 1368 1504 1728  1024 1027 1034 1072 -hsync +vsync (80.3 kHz)
(II) intel(0): Modeline "1600x1200"x75.0  204.75  1600 1720 1888 2176  1200 1203 1207 1255 -hsync +vsync (94.1 kHz)
(II) intel(0): EDID vendor "GWY", prod id 9003
(II) intel(0): EDID vendor "GWY", prod id 9003
(II) intel(0): Using hsync ranges from config file
(II) intel(0): Using vrefresh ranges from config file
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) intel(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x0.0   35.50  720 738 846 900  400 421 423 449 -hsync -vsync (39.4 kHz)
(II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) intel(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) intel(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) intel(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "1024x768"x0.0   44.90  1024 1032 1208 1264  768 768 776 817 interlace +hsync +vsync (35.5 kHz)
(II) intel(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) intel(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) intel(0): Modeline "1024x768"x74.9   82.00  1024 1088 1192 1360  768 771 775 805 -hsync +vsync (60.3 kHz)
(II) intel(0): Modeline "800x600"x74.9   49.00  800 840 920 1040  600 603 607 629 -hsync +vsync (47.1 kHz)
(II) intel(0): Modeline "640x480"x59.4   23.75  640 664 720 800  480 483 487 500 -hsync +vsync (29.7 kHz)
(II) intel(0): Modeline "1024x768"x59.9   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync (47.8 kHz)
(II) intel(0): Modeline "640x480"x74.8   30.75  640 664 728 816  480 483 487 504 -hsync +vsync (37.7 kHz)
(II) intel(0): Modeline "720x405"x69.6   26.50  720 744 808 896  405 408 413 425 -hsync +vsync (29.6 kHz)
(II) intel(0): Modeline "1280x1024"x74.9  138.75  1280 1368 1504 1728  1024 1027 1034 1072 -hsync +vsync (80.3 kHz)
(II) intel(0): Modeline "1600x1200"x75.0  204.75  1600 1720 1888 2176  1200 1203 1207 1255 -hsync +vsync (94.1 kHz)
(II) intel(0): EDID vendor "GWY", prod id 9003
(II) intel(0): EDID vendor "GWY", prod id 9003
(II) intel(0): Using hsync ranges from config file
(II) intel(0): Using vrefresh ranges from config file
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) intel(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x0.0   35.50  720 738 846 900  400 421 423 449 -hsync -vsync (39.4 kHz)
(II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) intel(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) intel(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) intel(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "1024x768"x0.0   44.90  1024 1032 1208 1264  768 768 776 817 interlace +hsync +vsync (35.5 kHz)
(II) intel(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) intel(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) intel(0): Modeline "1024x768"x74.9   82.00  1024 1088 1192 1360  768 771 775 805 -hsync +vsync (60.3 kHz)
(II) intel(0): Modeline "800x600"x74.9   49.00  800 840 920 1040  600 603 607 629 -hsync +vsync (47.1 kHz)
(II) intel(0): Modeline "640x480"x59.4   23.75  640 664 720 800  480 483 487 500 -hsync +vsync (29.7 kHz)
(II) intel(0): Modeline "1024x768"x59.9   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync (47.8 kHz)
(II) intel(0): Modeline "640x480"x74.8   30.75  640 664 728 816  480 483 487 504 -hsync +vsync (37.7 kHz)
(II) intel(0): Modeline "720x405"x69.6   26.50  720 744 808 896  405 408 413 425 -hsync +vsync (29.6 kHz)
(II) intel(0): Modeline "1280x1024"x74.9  138.75  1280 1368 1504 1728  1024 1027 1034 1072 -hsync +vsync (80.3 kHz)
(II) intel(0): Modeline "1600x1200"x75.0  204.75  1600 1720 1888 2176  1200 1203 1207 1255 -hsync +vsync (94.1 kHz)
(II) intel(0): EDID vendor "GWY", prod id 9003
(II) intel(0): EDID vendor "GWY", prod id 9003
(II) intel(0): Using hsync ranges from config file
(II) intel(0): Using vrefresh ranges from config file
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) intel(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x0.0   35.50  720 738 846 900  400 421 423 449 -hsync -vsync (39.4 kHz)
(II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) intel(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) intel(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) intel(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "1024x768"x0.0   44.90  1024 1032 1208 1264  768 768 776 817 interlace +hsync +vsync (35.5 kHz)
(II) intel(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) intel(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) intel(0): Modeline "1024x768"x74.9   82.00  1024 1088 1192 1360  768 771 775 805 -hsync +vsync (60.3 kHz)
(II) intel(0): Modeline "800x600"x74.9   49.00  800 840 920 1040  600 603 607 629 -hsync +vsync (47.1 kHz)
(II) intel(0): Modeline "640x480"x59.4   23.75  640 664 720 800  480 483 487 500 -hsync +vsync (29.7 kHz)
(II) intel(0): Modeline "1024x768"x59.9   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync (47.8 kHz)
(II) intel(0): Modeline "640x480"x74.8   30.75  640 664 728 816  480 483 487 504 -hsync +vsync (37.7 kHz)
(II) intel(0): Modeline "720x405"x69.6   26.50  720 744 808 896  405 408 413 425 -hsync +vsync (29.6 kHz)
(II) intel(0): Modeline "1280x1024"x74.9  138.75  1280 1368 1504 1728  1024 1027 1034 1072 -hsync +vsync (80.3 kHz)
(II) intel(0): Modeline "1600x1200"x75.0  204.75  1600 1720 1888 2176  1200 1203 1207 1255 -hsync +vsync (94.1 kHz)
(II) intel(0): EDID vendor "GWY", prod id 9003
(II) intel(0): EDID vendor "GWY", prod id 9003
(II) intel(0): Using hsync ranges from config file
(II) intel(0): Using vrefresh ranges from config file
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) intel(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x0.0   35.50  720 738 846 900  400 421 423 449 -hsync -vsync (39.4 kHz)
(II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) intel(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) intel(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) intel(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "1024x768"x0.0   44.90  1024 1032 1208 1264  768 768 776 817 interlace +hsync +vsync (35.5 kHz)
(II) intel(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) intel(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) intel(0): Modeline "1024x768"x74.9   82.00  1024 1088 1192 1360  768 771 775 805 -hsync +vsync (60.3 kHz)
(II) intel(0): Modeline "800x600"x74.9   49.00  800 840 920 1040  600 603 607 629 -hsync +vsync (47.1 kHz)
(II) intel(0): Modeline "640x480"x59.4   23.75  640 664 720 800  480 483 487 500 -hsync +vsync (29.7 kHz)
(II) intel(0): Modeline "1024x768"x59.9   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync (47.8 kHz)
(II) intel(0): Modeline "640x480"x74.8   30.75  640 664 728 816  480 483 487 504 -hsync +vsync (37.7 kHz)
(II) intel(0): Modeline "720x405"x69.6   26.50  720 744 808 896  405 408 413 425 -hsync +vsync (29.6 kHz)
(II) intel(0): Modeline "1280x1024"x74.9  138.75  1280 1368 1504 1728  1024 1027 1034 1072 -hsync +vsync (80.3 kHz)
(II) intel(0): Modeline "1600x1200"x75.0  204.75  1600 1720 1888 2176  1200 1203 1207 1255 -hsync +vsync (94.1 kHz)
(II) intel(0): EDID vendor "GWY", prod id 9003
SetClientVersion: 0 9
(II) intel(0): EDID vendor "GWY", prod id 9003
(II) intel(0): Using hsync ranges from config file
(II) intel(0): Using vrefresh ranges from config file
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) intel(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x0.0   35.50  720 738 846 900  400 421 423 449 -hsync -vsync (39.4 kHz)
(II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) intel(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) intel(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) intel(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "1024x768"x0.0   44.90  1024 1032 1208 1264  768 768 776 817 interlace +hsync +vsync (35.5 kHz)
(II) intel(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) intel(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) intel(0): Modeline "1024x768"x74.9   82.00  1024 1088 1192 1360  768 771 775 805 -hsync +vsync (60.3 kHz)
(II) intel(0): Modeline "800x600"x74.9   49.00  800 840 920 1040  600 603 607 629 -hsync +vsync (47.1 kHz)
(II) intel(0): Modeline "640x480"x59.4   23.75  640 664 720 800  480 483 487 500 -hsync +vsync (29.7 kHz)
(II) intel(0): Modeline "1024x768"x59.9   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync (47.8 kHz)
(II) intel(0): Modeline "640x480"x74.8   30.75  640 664 728 816  480 483 487 504 -hsync +vsync (37.7 kHz)
(II) intel(0): Modeline "720x405"x69.6   26.50  720 744 808 896  405 408 413 425 -hsync +vsync (29.6 kHz)
(II) intel(0): Modeline "1280x1024"x74.9  138.75  1280 1368 1504 1728  1024 1027 1034 1072 -hsync +vsync (80.3 kHz)
(II) intel(0): Modeline "1600x1200"x75.0  204.75  1600 1720 1888 2176  1200 1203 1207 1255 -hsync +vsync (94.1 kHz)
(II) intel(0): EDID vendor "GWY", prod id 9003
SetGrabKeysState - disabled
SetGrabKeysState - enabled
SetGrabKeysState - disabled
SetGrabKeysState - enabled
(II) intel(0): EDID vendor "GWY", prod id 9003
(II) intel(0): Using hsync ranges from config file
(II) intel(0): Using vrefresh ranges from config file
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) intel(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x0.0   35.50  720 738 846 900  400 421 423 449 -hsync -vsync (39.4 kHz)
(II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) intel(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) intel(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) intel(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "1024x768"x0.0   44.90  1024 1032 1208 1264  768 768 776 817 interlace +hsync +vsync (35.5 kHz)
(II) intel(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) intel(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) intel(0): Modeline "1024x768"x74.9   82.00  1024 1088 1192 1360  768 771 775 805 -hsync +vsync (60.3 kHz)
(II) intel(0): Modeline "800x600"x74.9   49.00  800 840 920 1040  600 603 607 629 -hsync +vsync (47.1 kHz)
(II) intel(0): Modeline "640x480"x59.4   23.75  640 664 720 800  480 483 487 500 -hsync +vsync (29.7 kHz)
(II) intel(0): Modeline "1024x768"x59.9   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync (47.8 kHz)
(II) intel(0): Modeline "640x480"x74.8   30.75  640 664 728 816  480 483 487 504 -hsync +vsync (37.7 kHz)
(II) intel(0): Modeline "720x405"x69.6   26.50  720 744 808 896  405 408 413 425 -hsync +vsync (29.6 kHz)
(II) intel(0): Modeline "1280x1024"x74.9  138.75  1280 1368 1504 1728  1024 1027 1034 1072 -hsync +vsync (80.3 kHz)
(II) intel(0): Modeline "1600x1200"x75.0  204.75  1600 1720 1888 2176  1200 1203 1207 1255 -hsync +vsync (94.1 kHz)
(II) intel(0): EDID vendor "GWY", prod id 9003
(II) intel(0): EDID vendor "GWY", prod id 9003
(II) intel(0): Using hsync ranges from config file
(II) intel(0): Using vrefresh ranges from config file
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) intel(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x0.0   35.50  720 738 846 900  400 421 423 449 -hsync -vsync (39.4 kHz)
(II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) intel(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) intel(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) intel(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "1024x768"x0.0   44.90  1024 1032 1208 1264  768 768 776 817 interlace +hsync +vsync (35.5 kHz)
(II) intel(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) intel(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) intel(0): Modeline "1024x768"x74.9   82.00  1024 1088 1192 1360  768 771 775 805 -hsync +vsync (60.3 kHz)
(II) intel(0): Modeline "800x600"x74.9   49.00  800 840 920 1040  600 603 607 629 -hsync +vsync (47.1 kHz)
(II) intel(0): Modeline "640x480"x59.4   23.75  640 664 720 800  480 483 487 500 -hsync +vsync (29.7 kHz)
(II) intel(0): Modeline "1024x768"x59.9   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync (47.8 kHz)
(II) intel(0): Modeline "640x480"x74.8   30.75  640 664 728 816  480 483 487 504 -hsync +vsync (37.7 kHz)
(II) intel(0): Modeline "720x405"x69.6   26.50  720 744 808 896  405 408 413 425 -hsync +vsync (29.6 kHz)
(II) intel(0): Modeline "1280x1024"x74.9  138.75  1280 1368 1504 1728  1024 1027 1034 1072 -hsync +vsync (80.3 kHz)
(II) intel(0): Modeline "1600x1200"x75.0  204.75  1600 1720 1888 2176  1200 1203 1207 1255 -hsync +vsync (94.1 kHz)
(II) intel(0): EDID vendor "GWY", prod id 9003
(II) intel(0): EDID vendor "GWY", prod id 9003
(II) intel(0): Using hsync ranges from config file
(II) intel(0): Using vrefresh ranges from config file
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) intel(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x0.0   35.50  720 738 846 900  400 421 423 449 -hsync -vsync (39.4 kHz)
(II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) intel(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) intel(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) intel(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "1024x768"x0.0   44.90  1024 1032 1208 1264  768 768 776 817 interlace +hsync +vsync (35.5 kHz)
(II) intel(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) intel(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) intel(0): Modeline "1024x768"x74.9   82.00  1024 1088 1192 1360  768 771 775 805 -hsync +vsync (60.3 kHz)
(II) intel(0): Modeline "800x600"x74.9   49.00  800 840 920 1040  600 603 607 629 -hsync +vsync (47.1 kHz)
(II) intel(0): Modeline "640x480"x59.4   23.75  640 664 720 800  480 483 487 500 -hsync +vsync (29.7 kHz)
(II) intel(0): Modeline "1024x768"x59.9   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync (47.8 kHz)
(II) intel(0): Modeline "640x480"x74.8   30.75  640 664 728 816  480 483 487 504 -hsync +vsync (37.7 kHz)
(II) intel(0): Modeline "720x405"x69.6   26.50  720 744 808 896  405 408 413 425 -hsync +vsync (29.6 kHz)
(II) intel(0): Modeline "1280x1024"x74.9  138.75  1280 1368 1504 1728  1024 1027 1034 1072 -hsync +vsync (80.3 kHz)
(II) intel(0): Modeline "1600x1200"x75.0  204.75  1600 1720 1888 2176  1200 1203 1207 1255 -hsync +vsync (94.1 kHz)
(II) intel(0): EDID vendor "GWY", prod id 9003
(II) intel(0): EDID vendor "GWY", prod id 9003
(II) intel(0): Using hsync ranges from config file
(II) intel(0): Using vrefresh ranges from config file
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) intel(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x0.0   35.50  720 738 846 900  400 421 423 449 -hsync -vsync (39.4 kHz)
(II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) intel(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) intel(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) intel(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "1024x768"x0.0   44.90  1024 1032 1208 1264  768 768 776 817 interlace +hsync +vsync (35.5 kHz)
(II) intel(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) intel(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) intel(0): Modeline "1024x768"x74.9   82.00  1024 1088 1192 1360  768 771 775 805 -hsync +vsync (60.3 kHz)
(II) intel(0): Modeline "800x600"x74.9   49.00  800 840 920 1040  600 603 607 629 -hsync +vsync (47.1 kHz)
(II) intel(0): Modeline "640x480"x59.4   23.75  640 664 720 800  480 483 487 500 -hsync +vsync (29.7 kHz)
(II) intel(0): Modeline "1024x768"x59.9   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync (47.8 kHz)
(II) intel(0): Modeline "640x480"x74.8   30.75  640 664 728 816  480 483 487 504 -hsync +vsync (37.7 kHz)
(II) intel(0): Modeline "720x405"x69.6   26.50  720 744 808 896  405 408 413 425 -hsync +vsync (29.6 kHz)
(II) intel(0): Modeline "1280x1024"x74.9  138.75  1280 1368 1504 1728  1024 1027 1034 1072 -hsync +vsync (80.3 kHz)
(II) intel(0): Modeline "1600x1200"x75.0  204.75  1600 1720 1888 2176  1200 1203 1207 1255 -hsync +vsync (94.1 kHz)
(II) intel(0): EDID vendor "GWY", prod id 9003
(II) 3rd Button detected: disabling emulate3Button

```

---

### Post by allen blake on 2009-07-31
Checking back in.  I see my post hasn't generated any ideas.

I just had to do a hard reboot, for another reason, too.

While when attempting to alter screen resolution lower, I have grown accustomed to circumventing hard boots:  Do not attempt to lower screen resolution lower, as a person should be allowed.

However, there is something that continues to be a hard boot fix only, still, unavoidably:

Firefox.

I have disabled Addblock, and Flashblock.

Still, I get horrendous gray screen of death far too frequently.  I have the new FF 3.5.  Latest Ubuntu updates.  WTF.

---

### Post by CatKiller on 2009-07-31
I haven't done much with Intel drivers, so I don't know if this bit is significant:

```
(WW) AIGLX: 3D driver claims to not support visual 0x23
(WW) AIGLX: 3D driver claims to not support visual 0x24
(WW) AIGLX: 3D driver claims to not support visual 0x25
(WW) AIGLX: 3D driver claims to not support visual 0x26
(WW) AIGLX: 3D driver claims to not support visual 0x27
(WW) AIGLX: 3D driver claims to not support visual 0x28
(WW) AIGLX: 3D driver claims to not support visual 0x29
(WW) AIGLX: 3D driver claims to not support visual 0x2a
(WW) AIGLX: 3D driver claims to not support visual 0x2b
(WW) AIGLX: 3D driver claims to not support visual 0x2c
(WW) AIGLX: 3D driver claims to not support visual 0x2d
(WW) AIGLX: 3D driver claims to not support visual 0x2e
(WW) AIGLX: 3D driver claims to not support visual 0x2f
(WW) AIGLX: 3D driver claims to not support visual 0x30
(WW) AIGLX: 3D driver claims to not support visual 0x31
(WW) AIGLX: 3D driver claims to not support visual 0x32
```

Windows are faded out when they are unresponsive. Sometimes they become responsive again when they've finished being busy. What are the other symptoms that mean you have to hard reset?

---

### Post by allen blake on 2009-08-08
Yes, sometimes when the screen grays, and becomes unresponsive, it will come back.  However, many times it does not.  I would say that about half of the time, it occurs when entering my inbox at Yahoo! mail.  Very irritating.

I click on the highlighted unread messages number "24",  then...gray screen of death.

The good news is that one of my recent upside down yield sign exclamation mark updates updated Firefox, and related modules.  Since then, I have had no gray screen of death.

Thank you for pointing out that xlog statement.  Until this moment, I didn't even know what xlog was.  This is a log that logs all errors?  I will Google for more information.

My latest issue (or at least my latest issue I have not been able to resolve, myself, yet) is that in SMPlayer, I can't see my second hard drive.

I have installed the hard drive, it shows under places, but when I try to load files from SMPlayer, and choose "computer", only my one hard drive appears, the second one is a no show despite its appearance under "Places".

Under Places>right click in drive directory>permissions

It won't let me change permissions, owner folder access create and delete, but file access --- and won't let me change it, or won't SAVE the change  Grouped as root,  folder access - none, file access ---,  others same as Group.

Crud.  I think I just found it.  The security thing, again.  I have to select which applications I allow to have access to this drive?

I will try.

Have a good one, and anyone with any insight into my video card issue, big kiss.

Take care Cat Killer, thanks again for your time.

---

### Post by allen blake on 2009-08-08
Well, no, I misunderstood what that meant.  Which is good.  It seemed an OVERLY secure procedure.

So, still looking for a resolution to SMPlayer recognizing my second drive in File>Open>Computer only shows the system drive, despite the second drive showing in "Places".

---

### Post by CatKiller on 2009-08-08
> **allen blake said:**
>  Until this moment, I didn't even know what xlog was.  This is a log that logs all errors? 

It logs X messages. There are different logs for different things. They are generally in /var somewhere.

There's a tool at System &#8594; Adimistration &#8594; Log File Viewer that shows lots of the default logs. I can't remember if it's enabled on the menu by default.

> **allen blake said:**
>  So, still looking for a resolution to SMPlayer recognizing my second drive in File>Open>Computer only shows the system drive, despite the second drive showing in "Places".

Drives need to be mounted in the [filesystem]("http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard") somewhere for you to be able to access the files on them. The two most common places for drives to be mounted are /mnt and /media. Automatically mounted drives (CD's or drives that you mount by double-clicking on them in Computer) are mounted in /media. Drives that are mounted in /media get an icon on the Desktop by default.

---

### Post by allen blake on 2009-08-09
It is designated as /media, from checking properties in "Places" where it shows up automatically.

Will the following be sufficient to mount it?

=====

Mounting Fat Partition
1) Create a folder on the desktop suppose fatdrive (this is just a foldeer name )
2) Open the terminal type the following command
3) sudo -s
4) give the password
5) mount -a /dev/< fat partition to be mounted > <desktop folder name> -t vfat umask 0022
6) fat drive would be mounted

=====

And, if it *IS* sufficient, what is the folder on the desktop for?!

---

### Post by allen blake on 2009-08-09
Some other questions:

/media/ Mount points for removable media such as [CD-ROMs]("http://en.wikipedia.org/wiki/CD-ROM") (appeared in FHS-2.3).

  /mnt/ Temporarily [mounted]("http://en.wikipedia.org/wiki/Mount_%28computing%29") filesystems.
-----

1) Regarding /media, it's recognizing an IDE 40 gig drive as removable media?

2) /mnt Temporary?  It's a fixed hard drive.  I am sure I don't have to remount it every time I boot, so what do they mean "temporary"?

T.I.A.

---

### Post by allen blake on 2009-08-09
For future reference, it does appear to be visible on the default installation as "System Log" under system>administration>system log

---

### Post by CatKiller on 2009-08-09
> **allen blake said:**
> what is the folder on the desktop for?!

What you've described is mounting the partition to the Desktop. That isn't what normally happens. The icon on the Desktop is a launcher that runs something like "nautilus /media/wherever".

> **allen blake said:**
> 
1) Regarding /media, it's recognizing an IDE 40 gig drive as removable media?

Removable in the sense that it isn't mounted at boot, and it won't be mounted next time. It's more-or-less a hack to get the behaviour described earlier, of having a handy icon on the Dekstop for ease of access.

> 2) /mnt Temporary?  It's a fixed hard drive.  I am sure I don't have to remount it every time I boot, so what do they mean "temporary"?

Historically, mounted partitions would fit into the standard structure as a special purpose filestsyem. You'd use filesystems that had differing desirable properties for /boot, /home, /etc, /var, and so on (desirable properties being "efficient for lots of tiny files," "efficient for large files," "efficient for data that changes frequently," that kind of thing). /mnt would be just a generic place to put data sources that you simply wanted to get data from. The combination of ext being "good enough" for most use cases and Linux *users* being less technically-minded than Unix *sysadmins* of the past has meant that this approach is less widespread than it used to be. You can still do it, but most people don't bother.

---

### Post by allen blake on 2009-08-12
Ok, well, I found a tutorial or two on mounting the drive automatically, and of course, ran into some problems.

=====
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2327    18691596   83  Linux
/dev/sda2            2328        2434      859477+   5  Extended
/dev/sda5            2328        2434      859446   82  Linux swap / Solaris

Disk /dev/sdb: 40.8 GB, 40822161408 bytes
255 heads, 63 sectors/track, 4963 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xea58cbf6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        4963    39865266    c  W95 FAT32 (LBA)
current@rogue:/$ gedit /etc/fstab
=====

This tutorial said to add the last line to my fstab file:

[http://mesanna.com/2009/02/02/how-to-mount-a-partition-automatically-in-ubuntu-linux/](http://mesanna.com/2009/02/02/how-to-mount-a-partition-automatically-in-ubuntu-linux/)

=====
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=75b0ab87-a4b5-48ba-8472-01feff89dac7 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=d4d64612-de09-46a5-8898-0afad13f06e9 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/sdb1    /media/datadrive vfat unmask=000 0 0
=====

So, I added it.

Then I had two problems.

1) I rebooted and loaded SMPlayer, to see if it was recognized, now.  The drive was not recognized, it was a no show.  So, I went to "Places" and clicked on "40.8 GB Media" and was told "Cannot mount volume.  You are not privileged to mount this volume."  Of course, before adding that line, I was privileged, via "Places" to do so.  I went back to delete the line I added to fstab and ran into my second WTF.

2) I was not allowed to delete the line that I had just added and saved.  I was allowed to save the initial change to fstab, but when I went back to fstab and delete and resave I got the following error:  "Could not save the file /etc/fstab.  You do not have the permissions necessary to save the file (despite the fact that I just did, previously).  Please check that you typed the location (I didn't type, just file>save) correctly, and try again.

I found others having this problem a long time ago, but doubt it's the same reason:

[http://ubuntuforums.org/showthread.php?t=624460](http://ubuntuforums.org/showthread.php?t=624460)

---

### Post by allen blake on 2009-08-12
[http://www.linuxcompatible.org/thread28820-1.html](http://www.linuxcompatible.org/thread28820-1.html)

This tutorial differed with the "unmask=000", so this is when I attempted to change 000, to "user,rw,exec" as a shot in the dark...

Couldn't save to see if that worked, though.

---

### Post by Bartender on 2009-08-12
I may have missed it somewhere in the six pages.  You asked about something that helps to identify your hardware.  This should help some.  Open a terminal and paste this in, then hit Enter.  You'll have to enter your password before it does its thing...

 ```
sudo apt-get install gnome-device-manager
```

---

### Post by allen blake on 2009-08-12
Thank you Bartender.  I will check that out, too, although I think I solved the hardware analysis tool search (I forget how, at the moment, but I had some help there.  I will check yours out, too.)

Here is some more information regarding my attempt to mount my added drive:

current@rogue:~$ mount -t vfat /dev/sdb1 /media/datadrive -o force
mount: only root can do that
current@rogue:~$ sudo mount -t vfat /dev/sdb1 /media/datadrive -o force
mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
current@rogue:~$ sudo mount -t fat32 /dev/sdb1 /media/datadrive -o force
mount: unknown filesystem type 'fat32'
mount: maybe you meant 'vfat'?
current@rogue:~$

---

### Post by Bartender on 2009-08-12
I'm more of a GUI-type guy, preferring that to staring at lines of text til my old eyes give out.  But it looks to me like the drive might be NTFS?  BASH didn't like the vfat command.

aysiu's website (psychocats) goes into more detail about correctly specifying the parameters.

---

### Post by allen blake on 2009-08-13
No.  It's FAT32.  Thanks for the suggestion, though.

---

### Post by CatKiller on 2009-08-13
> **allen blake said:**
> 
/dev/sdb1    /media/datadrive vfat unmask=000 0 0

I don't know where you got "unmask" from. It's **umask** (an abbreviation of [**u**ser **mask**]("http://en.wikipedia.org/wiki/Umask")).

> Could not save the file /etc/fstab.

I've never seen that before. I generally use **nano**, though.

```
sudo nano /etc/fstab
```

---

### Post by allen blake on 2009-08-13
Catkiller,

Did I mention that my eyes are bad?!  Ouch.  I just read it wrong, and then, when I tried to undo it (just to make sure I got my minimal functionality back that I had before the change), I got sidetracked into the "gedit" refusing to allow me permission to resave the document.

I appreciate your efforts in identifying that for me.

As soon as I get home, I will make that change, and see if it alleviates some issues.  I will also use the different editing tool.

Take care.

---

### Post by allen blake on 2009-08-14
Update:

I forgot to type SUDO when I gedited the second, (and third, fourth, and fifth times, apparently.)  When you suggested "nano", I saw "SUDO" as a precursor, and thought:  "Maybe I forgot to do that on the follup edits."

Apparently, I did forget.  I didn't use "nano", yet.  But, "gedit" allowed me to make the changes when I used it correctly.

Imagine that.

Also, making that "unmask" vs. "umask" change gave me "Places" access of that drive back.  It also put an icon on the desktop.

However, it didn't show up as a DRIVE in SMPlayer.  I was disheartened.  But, then I started to think that I should look in /media for the folder that I created.  It did show up there as an accessible folder, even though it didn't show up as a drive under "Computer" in the browsing function of SMPlayer.

I don't know if it is supposed to show up as a drive, ever, or only as that folder in /media, but whichever the case, I can access my files through SMPlayer, now.

Still haven't resolved the screen resolution issue, but at least I am now suffering with a little musical panache.

Thanks, again, all.

---

### Post by CatKiller on 2009-08-14
> **allen blake said:**
> But, "gedit" allowed me to make the changes when I used it correctly.

For reference, it's best to use [gksudo]("http://www.psychocats.net/ubuntu/graphicalsudo") for graphical applications. I don't think gedit is a problem, but it's a good habit to get into.

>  However, it didn't show up as a DRIVE in SMPlayer.

Linux (and other *NIX operating systems) have no concept of drives. If it's in the [filesystem]("http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard"), it can be accessed. If it isn't, then it can't. What you're mounting could be anything; partitions formatted any number of ways (ext, ReiserFS, FAT, NTFS, HPFS, btrfs, and so on) or an ISO image, or another computer through Samba or NFS. But it all gets mounted to somewhere on the filesystem tree and accessed just as if it was a local directory. And everything is a file. Files are files, directories are files, devices (like your mouse, sound card or printer) are files, and data about your processor or memory are files. It's all quite flexible.

---

### Post by allen blake on 2009-08-16
I'm sure I will continue to struggle with that, but what threw me off is that in the GUI, it was showing me a drive, under "Places", so I was expecting to see the same thing when I browsed.  But, not the case :)

Anyway, it's working, now.

I have another question (besides the original screen resolution issue, or course).

I got ahold of some nice Boston Acoustic speakers this weekend.  I had tiny ones that work off of an analog signal.  These BA speakers don't work off of an analog signal.  Digital only.

And, I can't get the Intel 82801DB-ICH4 integrated sound card to play digital.

I went to "alsamixer" via terminal, and didn't see an option to switch from analog to digital.

I see lots of people in the past with this problem when I goog.  However, I don't see a solution.

Any ideas on this one?

TIA

---

### Post by CatKiller on 2009-08-17
Sorry. When I was looking at speakers for my computer I did consider getting some that took an S/PDIF input. But then I got some different ones instead. So I've never configured the optical out, and so I don't know how it's done.

---

### Post by allen blake on 2009-08-17
Ok.  Thanks anyway.  You've been a big help both directly, and indirectly, on several issues, and I appreciate that.

Maybe someone else will have some experience with the digital speakers.

---

### Post by CatKiller on 2009-08-17
> **allen blake said:**
>  Maybe someone else will have some experience with the digital speakers.

Best to start a new thread on that. I doubt anyone who knows about sound problems is going to read 6 pages of posts on the off-chance that there's a sound problem that isn't mentioned in the first page.

My hazy suggestion is that you'll need to add an entry for your digital output in ~/.asoundrc (which probably doesn't exist by default) to tell it to also use that device but, as I say, it's not something that I've had to do. All of the outputs that I could use come up in the graphical tools. ALSA uses something like (hw:0) to refer to the first sound card it finds, and then (hw:0,0), (hw:0,1), and so on to refer to the individual outputs. To use the appropriate output you probably just need to pick the right one of these. Or I could be completely wrong.

Good luck!

---

