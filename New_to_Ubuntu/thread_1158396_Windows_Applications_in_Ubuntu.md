---
title: "Windows Applications in Ubuntu"
date: 2009-05-13
forum: New to Ubuntu
---

### Post by carl_76 on 2009-05-13
Hi.

I am considering running Ubuntu as my main OS on the laptop I just bought.  I know that some of my old windows applications can be run through a windows emulator or virtual machine.  I looked at some of the options available and it appears that all open Windows as a window in Ubuntu.  And, any Windows applications I run will appear as a window inside the Windows window.  

Is there an a way of running Windows applications so that they appear as a window in the Ubuntu task bar even though they're running through a Windows emulator or virtual machine?  

Thanks in advance for any help.

---

### Post by aeiah on 2009-05-13
virtualbox allows for seamless window integration. its probably better than when i tried it, but when i tried it i basically had a normal ubuntu desktop with a windows taskbar on top of my windows panel, and Windows programs floating around just like they were native linux applications. of course, where possible the best solution is to use wine. it isnt as heavy on your resources as running a whole windows operating system in the background and usually integrates into the look and feel of the ubuntu desktop much better.

what applications are you hoping to run? have you considered linux alternatives? this is almost always the best solution.

---

### Post by Sir Jasper on 2009-05-13
Hi,

You can put icons for Windows programs, run via Wine, on a panel.

You could add a drawer or drawers to your panel and have many Windows shortcut icons in any drawer.

All my Windows programs are portable so I have a single icon which loads a PortableApps menu for all of the twelve Windows programs I use.

My regards

---

### Post by ugm6hr on 2009-05-13
> **aeiah said:**
> what applications are you hoping to run? have you considered linux alternatives? this is almost always the best solution.

Indeed.  If you intend to run multiple Windows applications, you need to consider whether there is much value in changing OS.

---

### Post by Bölvaður on 2009-05-13
No the window list is not really supposed to be snooping around in what you are doing in a virtual machine, nor is it supposed to support endlessly long list of operating systems. I know it is strange to hear but it might make more sense to you later on :)
On that you can run most windows applications as if nothing was out of the ordinary... I mean.. the os is just running on virtual machine and has no idea if it is running on real hardware or not. The only thing is there is poor 3d acceleration support as it is running on virtual hardware.. not your nvidia 39999 card ;)

**W**INE **I**s **N**ot an **E**mulator, nor have there ever been any windows emulators.
It on the other hand lets the window list see what is going on as it is just part of the desktop.

look up [www.winehq.org]("http://www.winehq.org")

---

### Post by WelshChris on 2009-05-13
VirtualBox is a good solution, if you have the disk space.  I have a Samsung NC10 - a netbook by some standards, although I've put a 500Gb hdd in here.  Virtualbox runs WinXP flawlessly, including MathCad, the reason why I went down this path.

When not in use, the virtual machine can be put into hibernation, and is ready to use reasonably quickly.

---

### Post by MontelEdwards on 2009-05-13
> **ugm6hr said:**
> Indeed.  If you intend to run multiple Windows applications, you need to consider whether there is much value in changing OS.
Well yeah, WINE is great... but it barely works good. The only thing i have got to work is like Microsoft Office, and Safari. I hate Virtualbox and would rather use VM Server but since you are new to Ubuntu I would reccomend Virtualbox. Dual-Booting I believe is your best option if you are not prepared to leave Microsoft completely.

---

### Post by carl_76 on 2009-05-13
> **aeiah said:**
> what applications are you hoping to run? have you considered linux alternatives? this is almost always the best solution.

Hi.

Thanks for all the answers.  I am looking for linux alternatives for all applications before I switch.  However, there are a few engineering applications that I need that will not run on any other OS.  I doubt I'll ever run more than two or three Windows programs at any time, and graphics performance isn't much of a consideration.

If I have a processor that supports hardware VMs, would KVM be a better solution from a performance perspective, assuming it allows seamless integration?

Thanks again.

---

