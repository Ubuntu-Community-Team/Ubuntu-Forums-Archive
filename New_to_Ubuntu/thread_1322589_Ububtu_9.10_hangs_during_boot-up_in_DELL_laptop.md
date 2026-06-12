---
title: "Ububtu 9.10 hangs during boot-up in DELL laptop"
date: 2009-11-11
forum: New to Ubuntu
---

### Post by karth83 on 2009-11-11
I was using Ubuntu 9.04 for few months without any serious problem. It is great OS.

I am using DELL XPS 1530 with Vista ans Ubuntu 9.04 as dual boot.
I was having Fedora and Kubuntu in my external USB HDD which I connect sometimes to my laptop.

I recently installed Ubuntu 9.10 in my external USB HDD. Shutdown is very fast and its working normally except the boot-up.

Sometimes it hangs during boot-up or takes more than 2 mintues to switch from the Initial ubuntu symbol to the Loading Ubuntu screen.

(New grub is installed by 9.10 and it has detected my other linux distributions in that drive.)

Please help me to solve this issue.

---

### Post by karth83 on 2009-11-11
Even Kubuntu 9.10 is not running in my laptop. It is hanging in boot-up or After loggin into the desktop. 

Older Ubuntu versions run in my laptop without any problem. I think problem is with V9.10.

---

### Post by witeshark17 on 2009-11-11
Just hangs, any more detail? Does anything work; how do you retry?

---

### Post by karth83 on 2009-11-12
Kubuntu desktop I have never seen till now. It never comes to desktop.
But ubuntu desktop comes up sometimes. Once it opens everything works fine.

If it hangs I have to power off, then try restarting 4 to 5 times and the desktop comes up.

---

### Post by witeshark17 on 2009-11-12
So you get past the Grub and BIOS into GUI well enough to know that it's not a basic boot issue?

---

### Post by Dullstar on 2009-11-12
> **karth83 said:**
> Even Kubuntu 9.10 is not running in my laptop. It is hanging in boot-up or After loggin into the desktop. 

Older Ubuntu versions run in my laptop without any problem. I think problem is with V9.10.

I don't think that if Ubuntu 9.10 doesn't work, Kubuntu would.  Instead, they'd probably both fail.  Unless Gnome can be incompatible with one machine and then KDE compatible on that same machine and vice versa.  Can anyone tell me if that's possible, actually?  It would probably come in handy if someone has a problem.

---

### Post by karth83 on 2009-11-12
After I select the Ubuntu 9.10 in the grub, it shows me a ubuntu logo screen.
Then it switches to Loding screen. It hangs in the screen where the "new brownish loading screen" comes (Out of 5 restarts it passes this screen only once and the login screen comes up. After that no problem in Ubuntu9.10, while Kubuntu9.10 Hangs after login screen as well). Ubuntu 9.04 and Kubutnu9.04 works very much fine in the same Harddisk (Multiple OS Harddisk).

---

### Post by monkey d luffy on 2010-02-01
I got exactly the same problem.
I find it strange because sometimes I am able to boot up.
I dont think it's because the dell laptop.

With me it hangs when the loading bar fades.
While normally it would boot at that time.

I'm also using ubuntu 9.10 (64bit).

---

### Post by monkey d luffy on 2010-02-01
I have solved this, updating ubuntu seemed to work.
It's still a bit strange though, I think it has something to do with compatibility since I have a lot of propieraty drivers.

---

### Post by ademey on 2010-02-11
I have a DELL vostro 1000 laptop with ATI Xpress 1150.

I get a very similar problem. Sometimes boot process is interrupted after ubuntu logo was shown. tty1 login (command line) is prompted. If you wait about a minute, graphical boot continues. No internet connection can be established (LAN is dead) 
What I usually do is force reboot when command-line login is prompted. Sometimes I have to repeat this cycle 4-5 times untill I get a sound boot-up with LAN working.

This problem is frustrating me for about 2 months now, and I can't find a fix on any of the fora nor through posting bug reports.
I am using ubuntu for about 2 years now, but I'm not an expert of what's underneath the GUI.

Any help?

---

### Post by ademey on 2010-02-20
Update: since some days I have wireless internet at home. If boot hangs at command line, startup continues after 1-2 minutes. I am already happy wireless works! But delayed startup is really frustrating...

I posted a bug but no replies: [Bug 498586] tty1 login prompted for a minute

---

### Post by mbickell on 2010-03-20
Same problem here.
Just recently installed 9.10 as a dual boot with win7 on my Dell laptop.
Now Ubuntu hangs at the loading screen (after the splash screen, as described in the previous posts).
I have tried disabling the splash screen, but this part of the boot loads fine, its just the loading screen which hangs.

If I press Ctrl-Alt-F1 after the system "hangs", and it takes me to the command prompt log in, but I don't know if there is anything I can do from there. Is there a command I can try that will update Ubuntu? Although I downloaded my Ubuntu about 4 days ago, so I don't suppose there will be any big updates.

Thanks!

---

### Post by ademey on 2010-03-28
Some new information...
It seems to be related to the ATI graphics driver that's auto-selected. If the vesa driver is specified in /etc/X11/xorg.conf, the problem is resolved. However, the vesa driver only supports 3:4 screen formats, so everything is stretched horizontally on the screen...

Open terminal 

sudo gedit /etc/X11/xorg.conf

Add the text below, save and close, then restart.

Section "Device"
   Identifier   "Configured Video Device"
   Driver      "vesa"
EndSection

---

### Post by hiva.mj on 2010-04-16
I´ve made a clean instalation of kubuntu 9.10 in a dell inspiron 1545 machine, with windows 7.
The instalation was quite easy without any problems. and the machine worked fine as long as i use ubuntu only, but the first time i use win7 and reboot the machine, i face an error 
"grub loading.
The symbol '  ' not founfd.
Aborted. Press any key ..'


and after that, I could not anymore use the laptop, cause after press any key, got the same message, then tried again and the system reboot, and shows the message again - infinite loop.
I´ve reinstalled kubuntu 9.10 with the live cd, and now it's working, but If i use win7 then i face the same problem, and I have to reinstall ubuntu again.
Are there any way to use both OSes without having this problem?

---

