---
title: "cant get ubuntu 3D games to work"
date: 2009-03-27
forum: New to Ubuntu
---

### Post by sabith on 2009-03-27
when i try to run 3D games apps/games nothing happens???
this is my graphix 


description: VGA compatible controller
product: Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller
vendor: Intel Corporation
physical id: 2
bus info: pci@0000:00:02.0
version: 03
width: 32 bits
clock: 33MHz
capabilities: msi pm bus_master cap_list
configuration: latency=0
*-display:1 UNCLAIMED
description: Display controller
product: Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller
vendor: Intel Corporation
physical id: 2.1
bus info: pci@0000:00:02.1
version: 03
width: 32 bits
clock: 33MHz
capabilities: pm bus_master cap_list
configuration: latency=0


also when i try to run glxgears this error message comes up

tyler@tyler-laptop:~$ sudo glxgears
[sudo] password for tyler:
X Error of failed request: BadRequest (invalid request code or no such operation)
Major opcode of failed request: 143 (GLX)
Minor opcode of failed request: 19 (X_GLXQueryServerString)
Serial number of failed request: 10
Current serial number in output stream: 10
tyler@tyler-laptop:~$ tyler@tyler-laptop:~$ sudo glxgears
bash: tyler@tyler-laptop:~$: command not found
tyler@tyler-laptop:~$ [sudo] password for tyler:
bash: [sudo]: command not found
tyler@tyler-laptop:~$ X Error of failed request: BadRequest (invalid request code or no such operation)
bash: syntax error near unexpected token `('
tyler@tyler-laptop:~$ Major opcode of failed request: 143 (GLX)
bash: syntax error near unexpected token `('
tyler@tyler-laptop:~$ Minor opcode of failed request: 19 (X_GLXQueryServerString)
bash: syntax error near unexpected token `('
tyler@tyler-laptop:~$ Serial number of failed request: 10
bash: Serial: command not found
tyler@tyler-laptop:~$ Current serial number in output stream: 10
bash: Current: command not found
tyler@tyler-laptop:~$ tyler@tyler-laptop:~$
bash: tyler@tyler-laptop:~$: command not found
tyler@tyler-laptop:~$ glxgears
X Error of failed request: BadRequest (invalid request code or no such operation)
Major opcode of failed request: 143 (GLX)
Minor opcode of failed request: 19 (X_GLXQueryServerString)
Serial number of failed request: 10
Current serial number in output stream: 10
tyler@tyler-laptop:~$


also recovery mode and fix x doesnt solve my problem

PLEASE HELP!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

---

### Post by Xero Xenith on 2009-03-27
Go into System-Preferences-Appearance, Visual Effects tab. What is selected there now? Try setting it to Extra, and move a window around. What happens?

If you can't set it to Extra, or if moving a window after setting it to Extra doesn't make it go nice and wobbly, you don't have the 3D drivers installed.

---

### Post by sabith on 2009-03-27
the screen flashes then it says desktop effects could not be enabled

---

### Post by sabith on 2009-03-27
how do i install 3D drivers

---

### Post by mahimahi42 on 2009-03-27
I had this problem on my Wubi installation.

Trying looking at your graphics card's manufacturer's webpage for any 3D drivers. If there aren't any, try Google. If that fails, I don't know what to tell you.

---

### Post by sabith on 2009-03-27
does not tell me how to install to linuex

---

### Post by mahimahi42 on 2009-03-27
Try just installing the one(s) available, and do a Google search on how to enable/update them.

---

### Post by Paul T. on 2009-03-27
Have you tried system > administration > hardware drivers
see if driver for graphics card is listed.

---

### Post by sabith on 2009-03-27
i think i am going to switch back to vista

---

### Post by sabith on 2009-03-27
no its not listed only the network driver

---

### Post by Paul T. on 2009-03-27
Came across this link:

[http://hardware4linux.info/component/16922](http://hardware4linux.info/component/16922)

Don't give up so quickly with Ubuntu, can be nore challenging to get things working, but also more satisfying when you do!! :P

---

### Post by mahimahi42 on 2009-03-27
Yeah, once you get Ubuntu to your specs, Vista will be like a bad dream =)

---

### Post by sabith on 2009-03-27
i think ubuntu is faster anyway

still cant get 3D to work =(

---

### Post by loomsen on 2009-03-27
Well, try and start the game u want to run in a terminal window...

It will give u human readable what actually is wrong.

---

### Post by sabith on 2009-03-27
how

---

### Post by sabith on 2009-03-27
i want to play sabre apps/games/sabre
how do i do that in a command

---

### Post by Chemical Imbalance on 2009-03-27
try this in terminal:

glxgears

It will show you whether or not 3D accel is enabled

If it isn't installed or asks you to install something, run this:

sudo apt-get install mesa-utils

then run glxgears after it installs

---

### Post by loomsen on 2009-03-27
well, the binary will be named like the installer pkg usually

try sabre in a terminal

---

### Post by loomsen on 2009-03-27
Just installed it, the cmd is 

```

XRunSabre
```

---

### Post by sabith on 2009-03-27
it worked =) how come it does not work when i try to runit by pressing  app/games/sabre
when i do that it does nothing

---

### Post by loomsen on 2009-03-27
Can't tell you that, maybe it needs to be run in a terminal... There are some apps which need to be run inside a terminal window.

---

### Post by sabith on 2009-03-27
then why does it even have a shortcut in games why dont they tell me those things
no wounder people are having a lot of problems with ubuntu

---

### Post by loomsen on 2009-03-27
> **sabith said:**
> then why does it even have a shortcut in games why dont they tell me those things

So, whom would u actually want to blame for exactly what?

And whom did u pay money for exactly which part of your software, so that you could claim support?

Thats the difference. You left windows, bear in mind.

There is nothing like a central coordination for every single app any developer in the world wrote some time...


So, whom exactly would u expect to tell you?

You actually have to be willing to put forth in effort here n there too.
Especially if it's an app which needs 8bit mode and prlly was written 1993 (that is 16 years from now)

---

### Post by sabith on 2009-03-27
i tried to run xmoto and got this error

tyler@tyler-laptop:~$ xmoto
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  11
  Current serial number in output stream:  11
tyler@tyler-laptop:~$ 

i get the Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
on other games too how do i fix this

---

### Post by loomsen on 2009-03-27
[You probably won't get it to work at all...](http://ubuntuforums.org/showthread.php?t=816249)

---

### Post by qwertyuiop96 on 2009-03-27
Try setting the visual effects to "none".  I had A similar problem, and that solved it, although it is annoying to switch back and forth...

---

### Post by sabith on 2009-03-27
Hi its already on none

---

### Post by sabith on 2009-03-28
i try to run them and i get this

tyler@tyler-laptop:~$ xmoto
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  11
  Current serial number in output stream:  11
tyler@tyler-laptop:~$ 

please help

---

### Post by sabith on 2009-03-28
when i try to enable desktop effects it says desktop effect could not be enabled plus when i try to run games in the terminal because when i click on them regularly nothing happens so i open up a terminal and typ the game
billard-gl witch is a pool game i get this

tyler@tyler-laptop:~$ billard-gl

 BillardGL (C) 2001, 2002 Tobias Nopper, Stefan Disch, Martina Welte

X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  12
  Current serial number in output stream:  12
tyler@tyler-laptop:~$ 

wierd i am very new to linux please help me solve this issue so i canplay 3Dgames on my new os

  HELP

---

### Post by overdrank on 2009-03-28
Please do not create multiple threads on the same issue. Threads merged

---

### Post by Chemical Imbalance on 2009-03-28
> **sabith said:**
> when i try to enable desktop effects it says desktop effect could not be enabled plus when i try to run games in the terminal because when i click on them regularly nothing happens so i open up a terminal and typ the game
billard-gl witch is a pool game i get this

tyler@tyler-laptop:~$ billard-gl

 BillardGL (C) 2001, 2002 Tobias Nopper, Stefan Disch, Martina Welte

X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  12
  Current serial number in output stream:  12
tyler@tyler-laptop:~$ 

wierd i am very new to linux please help me solve this issue so i canplay 3Dgames on my new os

  HELP

Again, please run glxgears in terminal and tell us if it works.

---

### Post by sabith on 2009-03-28
sorry just trying to get the problem resolved

---

### Post by sabith on 2009-03-28
tyler@tyler-laptop:~$ glxgears
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  10
  Current serial number in output stream:  10
tyler@tyler-laptop:~$ 


thats what happened

---

### Post by Chemical Imbalance on 2009-03-28
This sounds like this bug:

[https://bugs.launchpad.net/ubuntu/+source/mesa/+bug/293012](https://bugs.launchpad.net/ubuntu/+source/mesa/+bug/293012)

There may be some solutions that work for you in the comments on that page.

---

### Post by sabith on 2009-03-28
been to that site already sorry still cant figure this out

---

### Post by sabith on 2009-03-28
i dont understand what to do to fix the bug can u help explain it to me  i 
AM NOT TECH SAVY

---

### Post by sabith on 2009-03-28
Tried reinstalling server did not work

---

### Post by Chemical Imbalance on 2009-03-28
You could try downloading the Jaunty beta livecd and see if glxgears runs correctly in the terminal using a live session.

[http://mirrors.gigenet.com/ubuntu/9.04/](http://mirrors.gigenet.com/ubuntu/9.04/)

---

### Post by sabith on 2009-03-28
Ok ill try it

---

### Post by sabith on 2009-03-28
which version it has a whole list of them

FOOTER.html                                        26-Mar-2009 20:59                  21
HEADER.html                                        26-Mar-2009 20:59                4437
MD5SUMS                                            26-Mar-2009 21:00                 413
MD5SUMS-metalink                                   26-Mar-2009 20:59                 298
MD5SUMS-metalink.gpg                               26-Mar-2009 20:59                 189
MD5SUMS.gpg                                        26-Mar-2009 21:00                 189
ubuntu-9.04-beta-alternate-amd64.iso               24-Mar-2009 06:55           728612864
ubuntu-9.04-beta-alternate-amd64.iso.torrent       26-Mar-2009 20:43               28032
ubuntu-9.04-beta-alternate-amd64.jigdo             26-Mar-2009 20:43              134323
ubuntu-9.04-beta-alternate-amd64.list              24-Mar-2009 06:55               95312
ubuntu-9.04-beta-alternate-amd64.metalink          26-Mar-2009 20:59               16326
ubuntu-9.04-beta-alternate-amd64.template          24-Mar-2009 06:55             1994925
ubuntu-9.04-beta-alternate-i386.iso                24-Mar-2009 06:57           721971200
ubuntu-9.04-beta-alternate-i386.iso.torrent        26-Mar-2009 20:43               27791
ubuntu-9.04-beta-alternate-i386.jigdo              26-Mar-2009 20:43              136139
ubuntu-9.04-beta-alternate-i386.list               24-Mar-2009 06:57               96331
ubuntu-9.04-beta-alternate-i386.metalink           26-Mar-2009 20:59               16213
ubuntu-9.04-beta-alternate-i386.template           24-Mar-2009 06:57             2008234
ubuntu-9.04-beta-desktop-amd64.iso                 24-Mar-2009 00:39           729899008
ubuntu-9.04-beta-desktop-amd64.iso.torrent         26-Mar-2009 20:46               28090
ubuntu-9.04-beta-desktop-amd64.list                24-Mar-2009 00:39                3526
ubuntu-9.04-beta-desktop-amd64.manifest            24-Mar-2009 00:24               33913
ubuntu-9.04-beta-desktop-amd64.metalink            26-Mar-2009 20:59               16100
ubuntu-9.04-beta-desktop-i386.iso                  24-Mar-2009 00:39           730886144
ubuntu-9.04-beta-desktop-i386.iso.torrent          26-Mar-2009 20:46               28129
ubuntu-9.04-beta-desktop-i386.list                 24-Mar-2009 00:39                3499
ubuntu-9.04-beta-desktop-i386.manifest             24-Mar-2009 00:17               34824
ubuntu-9.04-beta-desktop-i386.metalink             26-Mar-2009 20:59               15987
ubuntu-9.04-beta-server-amd64.iso                  24-Mar-2009 07:27           616796160
ubuntu-9.04-beta-server-amd64.iso.torrent          26-Mar-2009 20:59               23769
ubuntu-9.04-beta-server-amd64.jigdo                26-Mar-2009 20:59               95320
ubuntu-9.04-beta-server-amd64.list                 24-Mar-2009 07:27               67908
ubuntu-9.04-beta-server-amd64.template             24-Mar-2009 07:27             1762724
ubuntu-9.04-beta-server-i386.iso                   24-Mar-2009 07:28           600475648
ubuntu-9.04-beta-server-i386.iso.torrent           26-Mar

---

### Post by Chemical Imbalance on 2009-03-28
ubuntu-9.04-beta-desktop-i386.iso 24-Mar-2009 00:39 730886144

---

### Post by sabith on 2009-03-28
ok ill get back to you when i try to run glxgears and ill tell u what happened

---

### Post by sabith on 2009-03-28
it worked the glxgears does but does this this mean i cant use ubuntu 8.10 should i get the previous version or shouldi just install the beta and wait for the official version??????????????????

---

### Post by Chemical Imbalance on 2009-03-28
If you have the room, just install Jaunty onto a seperate partition and keep Intrepid on the other just in case.  That's good news your problem seems fixed in Jaunty.

---

### Post by sabith on 2009-03-28
should i get rid of vista
and jounty is slow but that might be because of the live session disk

---

### Post by Chemical Imbalance on 2009-03-28
> **sabith said:**
> should i get rid of vista
and jounty is slow but that might be because of the live session disk

I definitely recommend you keep Vista until you are confident with linux.

Yes, live sessions are slow bc you are reading from a cd.

---

### Post by loomsen on 2009-03-28
I'd seriously recommend reading my post... Your hardware is outdated, you can stop trying, it WON'T work.

Stop buggin him u other :D

Keep Vista btw...

---

### Post by Chemical Imbalance on 2009-03-28
> **loomsen said:**
> I'd seriously recommend reading my post... Your hardware is outdated, you can stop trying, it WON'T work.

Stop buggin him u other :D

Keep Vista btw...

At least he has opengl support on Jaunty now.  That stands for something at least.  I agree, keep vista installed for now.

---

### Post by orethrius on 2009-03-28
> **loomsen said:**
> I'd seriously recommend reading my post... Your hardware is outdated, you can stop trying, it WON'T work.

Stop buggin him u other :D

Keep Vista btw...

You know, X.Org 1.6 hasn't been backported to Intrepid yet, so it may well be the issue with 1.52 manifesting itself.  What I find humorous is that this apparently isn't widely known to Jaunty testers.  ;)

My own rig does much the same thing, and [the recommended Launchpad reading](https://bugs.launchpad.net/ubuntu/+source/mesa/+bug/293012) seems to indicate the same thing for many laptop models.  What's interesting here is that it appears to affect Intel chipsets, and not just ATi / nVidia; this indicates an issue with X.Org itself, *not* the proprietary drivers.

EDIT: I noticed that Chemical Imbalance saw the Launchpad issue; many people see it, and think nothing of it.  This may be a wider problem than initially thought, but it's comforting to know that Jaunty should fix it. :)

---

### Post by sabith on 2009-03-29
MY ISSUE IS RESOLVED I WENT AND REINSTALLED Ubuntu 8.10 Intrepid Ibex 
AND EVERYTHING IS WORKING TO SPEC NOW THE PROBLEM WAS THAT I HAD A PROGRAM CALLED 
COMPIZ THAT WAS CONFLICTING WITH MY DRIVER AND SO WAS THE THEAM I DOWNLOADED 

I DOWNLOADED COMPIZ AND IT STOPPED WORKING IF YOU HAVE TOO MANY PROGRAMMS INSTALLED ON LINUX THEY START TO CONFLICT WITH EVERYTHING THAT IS THE PROBLEM WITH LINUX

BUT I LIKE IT BETTER THAN VISTA AND MAC AND THAT IS SAYING SOMETHING

SO THANKS ANYWAY FOR EVERYBODYS HELP AT UBUNTU FORUMS

---

### Post by 3rdalbum on 2009-03-29
> **sabith said:**
> I DOWNLOADED COMPIZ AND IT STOPPED WORKING IF YOU HAVE TOO MANY PROGRAMMS INSTALLED ON LINUX THEY START TO CONFLICT WITH EVERYTHING THAT IS THE PROBLEM WITH LINUX

You downloaded Compiz? **Ubuntu comes with Compiz preinstalled.** If you followed an old document about "How to install Compiz on Ubuntu 7.04", then your attempt to follow those instructions and "install Compiz" caused your 3D acceleration to stop working.

Your assertion of "if you have too many programs installed on Linux they conflict with eachother" is wrong. Completely wrong. Linux works perfectly well no matter how many programs you have installed. Linux, like any operating system, has problems if you replace core parts of the system with older versions. In fact, Linux moves much quicker than Windows - a document from a year ago about "how to do x on Windows" will still work on Windows, but a year-old document of "how to do x on Linux" may either be completely useless and unnecessary, or could break parts of your system.

I'm glad you like Ubuntu, anyhow.

---

### Post by sabith on 2009-03-29
ok

---

