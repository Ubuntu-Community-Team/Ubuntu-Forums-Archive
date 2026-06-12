---
title: "Installing additional files from LiveCD"
date: 2010-05-31
forum: New to Ubuntu
---

### Post by tyler9 on 2010-05-31
After successfully installing Ubuntu 10.04 from the LiveCD, I now need to install and run the files that allow using a dial-up external modem. These files are on the 10.04 LiveCD but aren't installed by default.

If I understand correctly, these files [Software Packages] are on the LiveCD in:

[DVD drive]:\pool\main\w\wvdial\ wvdial_1.60.3_i386.deb
...and 
[DVD drive]:\pool\main\w\wvstreams\  [3 sw packages]

My question: how exactly do I get these required files from the LiveCD and run them from Ubuntu? Is it a matter of simply copying+pasting to the Ubuntu 10.04 desktop? Or do I need to install the files, and then run them? Is the Synaptic Package Manager required? I'd prefer a graphical tool, instead of a command-line terminal at this point. I do plan to familiarize myself with these features, but as a complete noob a graphical tool would be best.

Related question: 
I'm unable to use a mouse+keyboard simultaneously on the new Ubuntu PC--the motherboard has only one PS/2 port, many USB ports, but we haven't yet bought USB mouse or keyboard. 

As a workaround, I enabled the Ubuntu onboard keyboard, allowing mouse-clicks on the [virtual] keyboard keys. It seems to work fine.

But--when I tried to open the package manager, I got a password prompt. This creates a problem:  when this password box is onscreen, the onboard keyboard isn't accessible--it's dimmed out, unusable--I can't click the onboard keybd keys to enter password. Is this a bug? If so, I'll be glad to report it--will read forum sticky "beginner's guide to filing bug reports."

Anyway, apologies for these very basic questions--I'm a complete Ubuntu noob, and Ubuntu  seems fantastic; but with very spotty net access, I can't search for answers as much as I'd like. Normally I'd be able to search and I'm sure find the answer I need. Once I get dial-up working on Ubuntu 10.04, that'll solve the problem!

Thanks!

---

### Post by _duncan_ on 2010-05-31
You can add the live CD as a software source using Synaptic. Just click Settings > Repositories, then make sure the 'Cdrom with Ubuntu 10.04 Lucid Lynx checkbox is CHECKED in the 'Ubuntu Software' tab,

The extra .deb packages you need from the live CD will be made available to Synaptic for installation.

---

### Post by tyler9 on 2010-06-01
Thanks, _Duncan_.  I couldn't access Synaptic due to the Ubuntu onboard-keyboard password bug. I'll have a working keyboard tomorrow, so I'll be able to get to it.

After I install these required programs, I'll need to use command-line stuff to get it working, correct? This isn't a simple graphical UI-driven installation? I'm really beginning to wonder why this has to be so difficult.

---

### Post by Ozymandias_117 on 2010-06-01
Not a bug, it's supposed to make sure nothing is watching your keystrokes while you put in your password, so it knocks back every other program.

---

### Post by NUboon2Age on 2010-06-01
> **tyler9 said:**
> After successfully installing Ubuntu 10.04 from the LiveCD, I now need to install and run the files that allow using a dial-up external modem. These files are on the 10.04 LiveCD but aren't installed by default.

If I understand correctly, these files [Software Packages] are on the LiveCD in:

[DVD drive]:\pool\main\w\wvdial\ wvdial_1.60.3_i386.deb
...and 
[DVD drive]:\pool\main\w\wvstreams\  [3 sw packages]

My question: how exactly do I get these required files from the LiveCD and run them from Ubuntu? Is it a matter of simply copying+pasting to the Ubuntu 10.04 desktop? Or do I need to install the files, and then run them? Is the Synaptic Package Manager required? I'd prefer a graphical tool, instead of a command-line terminal at this point. I do plan to familiarize myself with these features, but as a complete noob a graphical tool would be best.


Yes, as the reply prior from _duncan_ explains, first add the LiveCD to the respositories in Synaptic.  Then just start Synaptic and do a search for wvdial and wvstream, mark them for install and then click 'Apply'.  That will handle all the installation for you (sweet!).

> 
Related question: 
I'm unable to use a mouse+keyboard simultaneously on the new Ubuntu PC--the motherboard has only one PS/2 port, many USB ports, but we haven't yet bought USB mouse or keyboard. 

As a workaround, I enabled the Ubuntu onboard keyboard, allowing mouse-clicks on the [virtual] keyboard keys. It seems to work fine.

But--when I tried to open the package manager, I got a password prompt. This creates a problem:  when this password box is onscreen, the onboard keyboard isn't accessible--it's dimmed out, unusable--I can't click the onboard keybd keys to enter password. Is this a bug? If so, I'll be glad to report it--will read forum sticky "beginner's guide to filing bug reports."


Well, I would consider it a usability/user-experience bug and the kind of thing that needs to be fixed or the workaround made more evident for new users so that they can have a mac-like user-friendly experience.  So from that point of view I think it'd be a very good to [add yourself to this bug report]("https://bugs.launchpad.net/ubuntu/+source/gksu/+bug/421660"), mark it as a bug that apply to you, subscribe to it and leave comments and as much info as you are able to (ie. Apport info if you can).

However there might be a workaround:

"Similar to the Accessibility options of the Login Manager, gdm, you can have an onscreen keyboard appear after you move the mouse in a special way. See: [https://help.ubuntu.com/community/Accessibility/OnboardAndMousetweaksAtGDM](https://help.ubuntu.com/community/Accessibility/OnboardAndMousetweaksAtGDM)

Here's the thread that might that came from which might be helpful:
[https://help.ubuntu.com/community/Accessibility/OnboardAndMousetweaksAtGDM](https://help.ubuntu.com/community/Accessibility/OnboardAndMousetweaksAtGDM)

---

### Post by NUboon2Age on 2010-06-01
> **tyler9 said:**
> Thanks, _Duncan_.  I couldn't access Synaptic due to the Ubuntu onboard-keyboard password bug. I'll have a working keyboard tomorrow, so I'll be able to get to it.

After I install these required programs, I'll need to use command-line stuff to get it working, correct? This isn't a simple graphical UI-driven installation? I'm really beginning to wonder why this has to be so difficult.

One way around this would be to go to a terminal and type 

```
sudo synaptic
```  It will ask you for the password and then bring up Synaptic.  Then you're off and running in GUI land.

---

### Post by NUboon2Age on 2010-06-01
> **Ozymandias_117 said:**
> Not a bug, it's supposed to make sure nothing is watching your keystrokes while you put in your password, so it knocks back every other program.

Excellent, excellent, excellent point.  But I still consider it a usability bug.  Maybe if the workaround was active by default I could be okay with it. So I still say bug report it.

---

### Post by _duncan_ on 2010-06-01
> **tyler9 said:**
> ...
After I install these required programs, I'll need to use command-line stuff to get it working, correct? This isn't a simple graphical UI-driven installation? ...

Not sure I got the question correctly. If you are referring to getting dial-up working via wvdial, then yes, since wvdial is a command-line dial-up tool.

Assuming you got the needed stuff from the live CD installed, I suggest marking this thread as SOLVED, and create a new thread with the appropriate title in case you need additional dial-up help.

---

### Post by GeorgeVita on 2010-06-01
> **_duncan_ said:**
> You can add the live CD as a software source using Synaptic...
@**tyler9**: If you face any problem on above method, try:

> **GeorgeVita said:**
> ..._**Update for Ubuntu [size=3]10.04[/size]**_
Although **wvdial** and dependencies are included into CD of **10.04** are NOT installed by default! [Bug#400573]("https://bugs.launchpad.net/bugs/400573")
You do not need to download them, just use the .iso or LiveCD or LiveUSB following the procedure below:

1. right click ubuntu-10.04-desktop-i386.iso and '**open with archive mounter**'
(or mount LiveCD/LiveUSB)
2. right click on icon created (from 1) to '**browse folder**'
3. create a folder on Desktop (ex. named 'wvdial')
4. copy into that folder all 4 .deb files that exist into .iso/LiveCD/LiveUSB
... **/pool/main/w/wvdial**
and **/pool/main/w/wvstreams**
5. use **System > Administration > Synaptic Package Manager**
and then from menu **File > Add downloaded packages** > double click Desktop and then the folder you created at point #3, click **open**, follow instructions to install

Regards,
George

---

### Post by tyler9 on 2010-06-03
_duncan_:
"You can add the live CD as a software source using Synaptic. Just click  Settings > Repositories, then make sure the 'Cdrom with Ubuntu 10.04  Lucid Lynx checkbox is CHECKED in the 'Ubuntu Software' tab"

_duncan_, I did this, but am getting dbox "An Error Occurred" with a list of "Failed to fetch http://...(url)" listings.

Wondering if Ubuntu was incorrectly trying to download from the web sources listed on this "Ubuntu Software" tab, I cleared all the other checkboxes [web sources], and left only the "Cdrom with Ubuntu 10.04 Lucid Lynx" checked. I made sure to click the "Reload" button--and get the same error message.

Is it possible the DVD Drive isn't mounted? I read the Help topic about mounting Media drives--it says when the DVD drive icon appears on the desktop [it is on my desktop], that means the drive has been mounted.

What might I be doing incorrectly here?

Thanks for tips--

---

### Post by bodhi.zazen on 2010-06-03
I believe you need to use the Alternate CD, and not the live or desktop CD, as a repository.

Another option would be Aptoncd

---

### Post by tyler9 on 2010-06-03
> **bodhi.zazen said:**
> I believe you need to use the Alternate CD, and not the live or desktop CD, as a repository.

Another option would be Aptoncd

Sorry but I don't understand. 

The files required for dial-up are not installed, but they are included on the LiveCD. 

But the user can't install dial-up using the files on the LiveCD? 

If that's the case, why are they on the LiveCD?

When I ordered the LiveCD, I didn't see any info about additional CDs needed for installation.

Can someone help with this?

Thanks for info--

---

### Post by _duncan_ on 2010-06-03
@tyler9

You're not doing anything wrong. Something seems to be broken with Synaptic in the current release. It has something to do with the way the live CD is being mounted.

You can still retrieve the files needed manually as suggested by GeorgeVita.

---

### Post by tyler9 on 2010-06-04
> **_duncan_ said:**
> @tyler9

You're not doing anything wrong. Something seems to be broken with Synaptic in the current release. It has something to do with the way the live CD is being mounted.

You can still retrieve the files needed manually as suggested by GeorgeVita.

Thank you, _duncan_--will do. 

GeorgeVita: I've read the threads--thanks for your tireless efforts on behalf of us dial-up users!

---

### Post by GeorgeVita on 2010-06-04
Hi **tyler9**,
just copy those files into a directory and use synaptic 'offline procedure' to install them:
> 5. use **System > Administration > Synaptic Package Manager**
and then from menu **File > Add downloaded packages** > double click Desktop and then the folder you created at point #3, click **open**, follow instructions to install

Regards,
George

---

### Post by tyler9 on 2010-06-04
I did the above and apparently successfully installed the four .deb files.

With the external modem connected to a USB port, confirming the modem's power light is on, I typed in the terminal window:
wvdial
...and I get "Cannot open /dev/modem. No such file or directory"

Thinking maybe the modem wasn't mounted, I typed:
mount /dev/modem
...and get "Can't find /dev/modem in /etc/fstab or /etc/mtab"

Wondering if I neglected to install a driver, I re-checked the modem's user's guide, which says: "You need a USB modem driver (CDC ACM) compiled into a Linux kernel 2.4.20 or higher or as a loadable module for your kernel. Installation of the modem under these kernels is fully automatic provided your kernel has the Plug and Play module enabled (default). You do not need to install any drivers off the USRobotics installation CD-ROM." 

Rechecking, I typed
man mount
...and as a new user, it would take days for me to understand the explanation. I'd simply like to get online, which will make my self-education in Linux and Ubuntu a bit less difficult.

Maybe I should use a graphical interface instead of command line? Would that mean I'd need to download gnome-ppp? Or maybe I haven't followed the correct sequence of required actions, and missed a prerequisite/prior action or something? As a noob, it's difficult for me to tell.

Thanks for tips--believe it or not, though I'm new to Linux/Ubuntu, I'm not new to using computers, though I'm beginning to feel like it....:)

---

### Post by _duncan_ on 2010-06-05
@tyler9

I haven't used wvdial in quite a while, so I'm hoping someone with more current knowledge would chime in. Anyway, it's been half a day, so for whatever it's worth, here are my thoughts:

1. you need to configure wvdial by typing in a terminal:
```
sudo wvdialconf
```

In theory, this will scan for a working modem in your computer, and if one is found, will create a template configuration file /etc/wvdial.conf.

Pay attention to the text displayed. If a modem is found, it will try to establish the best speed for the modem. It will also show the device name for the modem. For serial modems, it's usually /dev/ttyS0 or /dev/ttyS1.

In your case, I'm guessing it's something like /dev/ttyACM0. Not sure about this coz I haven't worked with USB modems before.

2. If a working modem is found, you need to edit the config file to put in your connection parameters: Do this:

```
gksudo gedit /etc/wvdial.conf
```

3. Look for entries like the following:
```
;Phone = ******
;Username = ******
;Password = ******
```

You need to edit these entries to your specific connection parameters. **Note that you also need to remove the semicolon from each of these lines to uncomment it.**

4. Just to be sure, add the following lines at the end:
```
Stupid Mode = yes
Carrier Check = no
```

5. Save the config file and exit.

6. To try dialing in again, do this:

```
sudo wvdial
```


I'm doing all these from rote memory since I don't have any dial-up modem to try it on. Come to think of it, I don't use wvdial even while I was on dial-up.:) There's a possibility some of my instructions are inexact or inaccurate.

---

### Post by tyler9 on 2010-06-06
> **_duncan_ said:**
> @tyler9
[...]
Come to think of it, I don't use wvdial even while I was on dial-up.:) There's a possibility some of my instructions are inexact or inaccurate.

Inexact or not, they worked!

Much thanks for your help--needed hand-holding--brain was overloaded+frazzled. And thanks to all posters in this thread!

---

