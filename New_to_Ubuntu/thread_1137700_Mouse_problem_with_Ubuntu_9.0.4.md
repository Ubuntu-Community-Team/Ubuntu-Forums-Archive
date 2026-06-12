---
title: "Mouse problem with Ubuntu 9.0.4"
date: 2009-04-25
forum: New to Ubuntu
---

### Post by isher on 2009-04-25
Hello!

I'm totally new to Ubuntu and just installed Ubuntu 9.0.4 with Wubi.  Pretty soon after startup, I am able to click with my mouse, however after only 15 seconds or so, the clicking totally stops working. I have a wireless Logitech mouse.  Any ideas?
:confused:

Thanks for the help.

---

### Post by bennachie on 2009-04-25
I'm not sure that I completely understand the symptoms. Can you confirm that:

You have installed 9.04 under Wubi and booted into Ubuntu. I assume that you are using the Gnome desktop.

After doing so, you can move the cursor around and left click on panel and menu items, folders etc. The click is recognised, and the relevant action initiated.

After a short time, you can still move the cursor around, so mouse tracking continues to operate, but you lose the capacity to left click on any items. Can you still right click on them?

Everything works normally when you return to Windows.

---

### Post by isher on 2009-04-25
Thank you for your reply bennachie,

1.  Yes. Yes.

2.  Yes.

3. Both right and left click do not work after a short time.  The click function never comes back.

4. The mouse works fine when I boot back to XP.

---

### Post by pistos on 2009-04-25
This sounds a lot like the problem I am now having after upgrading to 9.04 from 8.10. I have a notebook computer, and my trackpad buttons stop responding after a few seconds, and the tracking gets really sluggish. However, if I boot up with a USB mouse plugged in, then the machine will function correctly. Weird. I suspect it is the graphics driver, believe it or not. I am using the open source radeon driver, since it is the only one besides the vesa driver which works with my notebook (has ATI Radeon 9700 Mobility chip set). If I knew how to do it, I would try the vesa driver to see my problems clear up that.

---

### Post by bennachie on 2009-04-25
Nobody seems to have had much trouble with wireless mice, from Logitech or anyone else. They should work out of the box. You can find a compatibility list here:

[http://www.linuxcompatible.org/compatlistcat26.html](http://www.linuxcompatible.org/compatlistcat26.html)

Are the batteries reasonably fresh?

You might also find some useful comments here:

[http://www.linuxquestions.org/hcl/showcat.php/cat/441](http://www.linuxquestions.org/hcl/showcat.php/cat/441)

---

### Post by isher on 2009-04-26
Yes, the batteries are fine.

I didn't find my mouse on either of those sites. It's the Logitech LX7 931395-0403

Could it be that Ubuntu doesn't have certain drivers, like for this mouse?

[B]
[/B]

---

### Post by NathanDS101 on 2009-04-26
Hmmm maybe its crashing or something do u have windows or vista does it work on any other op systems

---

### Post by isher on 2009-04-26
> **isher said:**
> Thank you for your reply bennachie,

1.  Yes. Yes.

2.  Yes.

3. Both right and left click do not work after a short time.  The click function never comes back.

4. The mouse works fine when I boot back to XP.

Yes, XP.

---

### Post by manojchandra on 2009-04-26
i am having similar problems with logitech cordless mouse. any solutions found yet?

---

### Post by barkpoint on 2009-04-26
> **manojchandra said:**
> i am having similar problems with logitech cordless mouse. any solutions found yet?

I am also having exactly the same problem with my logitech LX7 cordless mouse. It stops recognizing my click after a few seconds. I have been able to work around it by disconnecting the USB cord for the mouse and reconnecting it. I upgraded to 9.04 from 8.10.

---

### Post by jsge on 2009-04-27
I have the same problem here. I upgraded from 8.10 to 9.04 this past week-end and all worked fine.
This afternoon, Gnome looked to be frozen, the mouse cursor was flying but no mouse click possible.
I restarted the computer and now I do have mouse click issue. The problem is that I cannot make the focus to another app. I have to play from right clicking a few times and then, left click works....
The mouse works fine under older Ubuntu install. I wonder if there is not an issue with Gnome event?
Annoying....

---

### Post by manojchandra on 2009-04-27
> **barkpoint said:**
> I am also having exactly the same problem with my logitech LX7 cordless mouse. It stops recognizing my click after a few seconds. I have been able to work around it by disconnecting the USB cord for the mouse and reconnecting it. I upgraded to 9.04 from 8.10.

Yes, it worked for me. Thanks.

---

### Post by Zapster on 2009-04-28
Same problem here. I'm using a Logitech Cordless desktop bundle with keyboard and a cordless optical mouse (Cordless MouseMan Optical). Did someone already filed a bug in launchpad? I think this problem might affect many users.

BR
zap

---

### Post by svivian on 2009-04-28
I'm having similar problems. I have a wireless desktop bundle with one USB key for the keyboard and mouse. The keyboard is working perfectly but the mouse isn't! I've tried loads of stuff but nothing has worked yet...

---

### Post by person9 on 2009-04-29
I have a logitech cordless mouse as well. I just upgraded from 8.10 to 9.04 today, and now my mouse situation is all weird. Batteries are fine, but that's what I first suspected.

I plugged in my mouse and it was fine for an hour or so, then I realized I had to double- and triple-click things, then do so really fast in order for it to respond. It would do a lot of "hanging on" to things, like randomly highlighting text or getting "stuck" to a scrollbar when  i move my mouse away.

This, as well as sluggish tracking, are totally random and sporadic. It's happening as I speak. My laptop trackpad buttons are fine right now, yet when I began writing this post they weren't functional (although tracking was). 

Idk what's up but my trackpad and mouse DO function fine and they DID function fine with 8.10 a few hours ago, and they DO function fine in Vista. It's a mystery for now, I guess.

---

### Post by papaquack on 2009-05-03
Did anyone ever find a solution for this? Over the weekend I started experiencing the same symptoms. I had upgraded to Jaunty the day it came out without any problems, but two days ago my mouse started randomly not recognizing my left-clicks. Right-clicks and mouse movement was fine, but I had to unplug my USB cable and replug it back in to get my left-click back. I have a corded Logitech trackball (marble mouse). Any help would be appreciated. Thanks!!!

---

### Post by svivian on 2009-05-04
I backed up my files onto my Windows partition then wiped Ubuntu and installed Jaunty from scratch. Now everything works fine. :)

---

### Post by fofenk on 2009-05-08
i have the same problem too. i also tried kubuntu as well

---

### Post by Niniel on 2009-05-08
Could be a problem with xorg.conf since that stores some mouse configuration data. However, xorg.conf may be empty after the upgrade or changed. There should be a backup copy, however. So if your mouse used to work before, you could try to copy the mouse section from the backup to the current xorg.conf and then restart the x server (log out and back in).
Or it might be the other way around and deleting xorg.conf may fix your mouse issue. 
Might be worth a try (make sure to keep a copy somewhere just in case).

---

### Post by satellitepro on 2009-05-08
I've had USB mouse random freezes ever since installing jaunty. (MS optical wheel mouse)

I suspected this to be related to inserting another USB device (camera, mp3 player) but it has happened once or twice when nothing else is plugged in and doesn't always happen when a USB device is inserted.  If a USB device has been connected, that dies as well.

I'm recording instances more scientifically now to identify a common element.  However, I suspect it's a USB related thing - every time, my laptop's built in touchpad continues to work fine before and after the USB mouse freezes.

I'm no expert on log files, but I haven't managed to track down any logged errors to report. I'm confident that it's not a hardware problem, since Windows XP and Ubuntu 8.04 installed on the same laptop are free of this problem.

---

### Post by mariliasaca on 2009-05-10
I have a slightly different problem: I use a totally common usb mouse (with wire), with a Dell notebook, and it works fine. When I unplug it, touse the usb with something else, it never comes back. Only if I ctrl-alt-backspace (gnome rebooting). 
It happened after I upgraded to 9.04, it worked perfectly well with 8.10 I used before. 

Suggestions?

---

### Post by SteveWin1 on 2009-05-13
I have had the exact same problem since I upgraded to Ubuntu 9.04.  I use a wireless logitech mouse as well (seems to be a connecting theme).  When this problem occurs, I am also unable to use the mouse pad on my laptop as an alternative.  The left mouse button on both does nothing. Here's what happens...

While the mouse appears to be freely moving around the screen, it is actually getting stuck inside one control object (button, tab, edit box,menu item, slider bar, etc).  The mouse cursor appears to move around the screen just fine, but when I click, nothing happens (because the mouse is still clicking inside the area in which it is actually trapped -- not where the cursor appears to be).  If I hold the cursor over a hyperlink, the hyperlink is not underlined like normal and buttons that normaly light up when the cursor is over them fail to do so.  If the mouse is trapped in a slider bar, I can go back and move the slider bar around with the mouse and it works fine, but I cannot get the focus out of that control object by using the mouse and cannot use adjacent slider bars using the mouse.  The tab key can be used to move the focus around in dialog boxes or on webpages and you can type in other fields or use the arrow keys to move slider bars around, but as soon as you click the mouse, the focus goes right back to the box or slider bar or whatever has the mouse trapped.  If I click the right mouse button anywhere on the screen, the pop-up menu that would have come up if I had actually right clicked on the area where the mouse is trapped comes up with one corner of the box at the location of the traped (invisible) mouse and not where the mouse cursor apears to be.  You can then left click somewhere to get rid of that box and the problem is fixed temporarily (until a few more clicks lands the cursor back in jail somewhere).  The menu popping up seems to free the mouse cursor.  If the mouse gets stuck somewhere where nothing happens when you right click, I can also free the mouse by closing whatever window has the cursor trapped.  ALT + F4 or tabbing to a close button on a dialog box also frees the cursor.  Unfortunately, sometimes you're at the desktop when the cursor gets trapped in some random area and right click does nothing and there's no window to close.  In this instance unplugging the mouse and plugging it back in is a last resort and always works.  This also seems to correct this problem for a very long time, instead of just seconds to minutes.

I am fairly certain that this is the same problem that most of the people on this thread are having and I am also fairly certain that the problem is that the mouse is getting trapped, even though it appears to be moving freely around the screen, and can only be freed by causing another window to steal the focus (like a pop-up menu when right clicking), closing the window that has trapped the mouse, or unplugging the usb cord for the mouse.  Sometimes right clicking doesn't work, but using the keyboard button that does the same ting as the right mouse button (looks like a menu with a mouse cursor over it) DOES work and vice versa (not sure why). 

This problem is extremely frustrating.  I hope someone figures out what's wrong.  I keep hoping the new updates that ubuntu installs are going to fix the problem, but they haven't.  Logitech is a pretty common brand of mouse, so I think this bug would be worthwhile to address.

---

### Post by Telecaster72 on 2009-05-16
I have this problem as well, on a cordless Advent Mouse.
It happens less frequently in xfce but still occurs.
Now i am trying out KDE and noticed that when i boot up and log in, mouse acts p, but if i just log out and back in again it works without exception.
That's a workaround that works for me, but is not ok in the long run, so i want to fix this permanently, so i'll be following this thread.

---

### Post by csno1 on 2009-05-16
I've been experiencing the same problem too. I have an advent wireless mouse and since upgrading from 8.10 my mouse occasionally loses focus and randomly locks onto other windows and objects! This is quite annoying and frustrating! I've surfed the net but am yet to find anything resembling a solution, lets hope we all find one :)

---

### Post by gytsygregro on 2009-05-17
@Niniel
I am using a wired usb G-Mouse and updated to Ubuntu 9.04 from 8.10. I had similar symptoms (left mouse click not recognized, sometimes no mouse button recognition).
[s] Deleting the xorg.conf fixed it (do not forget to make a backup copy). [/s]

Thank you.

---

### Post by csno1 on 2009-05-17
Just done a clean install with Jaunty 9.04 but still the mouse focus problem still persists and bugs the hell out of me!

---

### Post by kevinkr on 2009-05-18
I am having the same problem with 9.04 and have had it with both a Logitech Optical Mouseman Wireless, and a brand new Microsoft Wireless Optical Mouse 2000.

The mouse just freezes with no warning, other usb devices seem to continue to work, but usually that is just the UPS which I will check next time it happens.

I have not been able to identify any specific cause, it just seems to be a function of mouse activity and time. 

Some sites and programs seem to result in a freeze. Certain features in eBay or Adobe Acrobat, but again it might be nothing more than the amount of time that has elapsed since the last freeze.

My mouse is never recognized except at boot. Disconnection kills it permanently - this was true with the Logitech which being ancient I believed had expired. It is also true with the MS wireless mouse as well.

I have tried a PS2 mouse I had on hand and had no problems during the short time I used it. (Not a long enough interval to be sure this is relevant.)

This behavior existed in 8.10 on my machine as well, but seemed far less frequent.

Wiping clean will probably mean an end to Ubuntu here - I have invested so much time and effort migrating from Windows and this is very disappointing to say the least. I don't really want to do it again near term, but this is getting to be unusable.

My machine is a 64 bit AMD Athlon based machine with NV4 chipset running 64 bit Ubuntu.. (PciE video card) I have the nvidia driver package installed.

---

### Post by kevinkr on 2009-05-18
Note that bug 374458 is definitely related although it pertains specifically to Kubuntu 9.04 which has kde desktop manager. I posted my mouse freeze issue to that bug report despite the fact that it was Kubuntu - I don't believe the desk top manager is playing a role here.

---

### Post by csno1 on 2009-05-21
Still do not know why my wireless mouse keeps latching onto windows and objects nevertheless I've just bought a wired USB mouse which has cured the mouse focus problem!

---

### Post by Telecaster72 on 2009-05-23
Same problem here with Advent mouse.
Found a workaround that works everytime but is a real hazzle.
I log in to KDE (has same mouse problems in gnome and xfce too), mouse acts weird, log out and back in again and it works flawless.
Pain in the neck though...

---

### Post by csno1 on 2009-05-24
I also logged-out/logged-in but it only cured the problem temporarily!

---

### Post by gytsygregro on 2009-05-28
After deleting the xorg.conf the mouse begun to have strange behaviour again.
Tried: dpkg-reconfigure -phigh x.server.org
Still no change.

Temporary work around: log in, log out.

---

### Post by G1zm0 on 2009-05-30
I had the same problems, running ubuntu 9.04 and logitech MX1000.
I fixed the problem by completly removing the 'lomoco' package with synaptic.
Until now everything works fine. I have my computer turned on now for about 6 hours, and the mouse is still working.

I haven't had the time to reboot, so I hope after reboot the problem won't come back.

---

### Post by kevinkr on 2009-05-30
I have used both logitech (mouseman optical wireless) and microsoft (wireless optical mouse 2000) USB mice in 9.04 and have a persistent mouse freeze issue. None of the suggestions here seem to work at all, what I have found that does is basically to either use a ps2 mouse or make sure that nothing else is on a USB port. Crashes still occur, but less frequently.

I've also found that when this occurs I must remove power to the PC completely to restore normal operation - this seems to indicate that something is not getting cleared/reset when the power is cycled. (This behavior does not happen in Win XP Pro - this machine is dual boot.)

An interesting issue with the USB support in Linux in general is that other than flash or hard drive based external storage devices it does not seem to understand how to enumerate USB plug and play USB devices at any time other than during boot up hardware detection.

In Windows you can unplug a malfunctioning peripheral and replug it and it will reenumerate. Both my mice receivers have reset buttons which work in Windows but do not in Linux. 

I use Ubuntu daily, but the lack of progress in addressing this problem is discouraging - there must be hundreds if not thousands of users having related problems.

---

### Post by jivbot on 2009-05-31
Same problem here. Mouse randomly freezes during normal operations. I can find no obvious reason and it appears to be a very common problem with 9.04

---

### Post by arkashkin on 2009-06-05
I have Dell Latitude D600 and I have the same bug. It happens with my laptop's mouse-pad and with a "Silver Line" usb mouse.

I made some script that unloads and loads again mouse's driver, and it helps me to restore a normal focus, here's the script:
> 
#! /bin/sh

if [ "`whoami`" != "root" ];
then
echo "Please run with SUDO"
exit 1
fi

echo "Removing mouse driver"
sudo rmmod psmouse
echo "Restoring mouse driver"
sudo insmod /lib/modules/`uname -r`/kernel/drivers/input/mouse/psmouse.ko

I hope some one will fix that bug soon...

---

### Post by Tom Collier on 2009-06-05
As an Ubuntu convert with a whole 48-hours of evaluation time under his belt...I have experienced strange mouse behavior, too.

This variant happens when I tried to use Evolution and it just started happening with F-spot photo manager.

Problem is left or right mouse click toggles the window title bar on then off (the part at the top of the window that contains the window title and the maximize/minimize icons). The contents of the window then jump up or down by the length of the title bar. The click then either has no effect, or launches the action above or below the target/focus.

It's like the old programmers' joke where you're supposed to click on a target to win a million dollars or something  like that, but the target disappears and jumps to another part of the screen on mouse_over.

I have an eeePC 1000 running Ubuntu 9.04 under Wubi with XP on the "other side." The behavior also occurs with the trackpad.  Mouse is a MS Mobile Wireless 3000.

I know nada about programming and am an uberNoobie.  But just thought I'd see if anyone else has experienced this variant of oddball mouse behavior under Jaunty.

---

### Post by joylessdave on 2009-06-06
i was having this problem with an upgrade from 8.10 to 9.04 

i was reading other posts  on the forum and disabling compiz was the suggestion on one of them

go to system | Preferences | appearance 
then go to the visual effects tab and select none

this seems to have solved the problem here (for now anyway)

---

### Post by Tom Collier on 2009-06-06
!!! Turning off visual effects solved the mouse behavior problem(s) I described in my previous post.  You guys are geniuses!  Thanks!

---

### Post by kevinkr on 2009-06-09
A few days ago I decided to connect a wired PS2 microsoft mouse to my desktop computer (Ubuntu 9.04/Win XP dual boot) in addition to the wireless USB mouse I normally use. The USB mouse just crashed, but the PS2 mouse is still working so it seems to point in the direction of a problem with USB mouse support.

The USB mouse never crashes in Windows XP. (In fact this installation of windows never crashes at all.)

One of the things I have noticed before is that USB mice cannot re-enumerate in Linux whereas they can in Windows. It would be great if this were to be fixed - it would make the mouse crash issue a minor deal if and when it were to occur.

---

### Post by balloooza on 2009-06-09
SAME PROBLEM HERE, my mouse will stop clicking
my solution: use the ps/2 adapter that same with the mouse (/keyboard) (did it, I only skimed the FOUR PAGES) I have a wireless desktop set, a problem with an easy fix like that is better than disecting the /etc directory

---

### Post by teejcee on 2009-06-09
I have experienced problems with a Logitech LX6 wireless mouse. It is mainly a problem with the scroll wheel but I have had a few random freezes also.

Try this...

```
sudo rmmod psmouse
sudo modprobe psmouse rate=100 proto=imps
```

This cured my problems but only temporarily. When I next re-boot, I'm back to square one.

If I could have a script run those commands at boot, I think I'd be ok, however, I don't know how to do that.

More research required.....

---

### Post by teejcee on 2009-06-09
OK...looks like I have an answer.....try this

```
sudo gedit /etc/modprobe.d/NAME.conf
```

...where NAME is the name of the file you are going to create. As I have an LX6 , I called it, ....wait for it.... lx6.conf

now put this line in the file...

```
option modprobe psmouse rate=100 proto=imps
```

Now save the file & exit gedit.

That's it...!!!

I have re-booted several times & my problems have ( for now at least ) disappeared.

---

### Post by dspisak on 2009-06-09
Hi.  I use a PS/2 mouse.  With 9.04 my computer hangs 1) when I move a window by grabbing the title bar with the mouse, 2)when moving the vertical scroll bar, 3) moving the mouse pointer slowly close to the scroll bar. Also, the keyboard and the clock (in the upper right corner) no longer function.  I have to reboot.

I am not running compriz. The freeze happens with other programs in addition to firefox.

I had absolutely no problems when running ubuntu 8.10, kernel 2.6.27-11. I will reinstall kernel 2.6.27-11 and see if the freeze thaws.


Here is my system:
MB - Asus M3A78-T, 0802 bios
CPU - AMD Phenom II x4 810, 3.18 GHz
RAM - 2 GB Crucial PC8500
On-board Video - ATI Radeon HD 3300
On-board Audio - ATI RS780 Azalia and/or ATI Technologies Inc SBx00 Azalia (Intel HDA)
OS - was ubuntu 8.10, kernel 2.6.27-11, is now 9.04, kernel 2.6.28-11

---

### Post by irvotheturbo on 2009-07-16
I've got the same problem here. I'm using upgraded Ubuntu 9.04 (from Hardy) with recent updates and a Logitech Cordless Mouse and Keyboard Receiver (oldy).
It used to work perfect, but just started to act up when I changed my videocard last week. I exchanged my spare NVidia GeForce2 MX for a new NVidia GeForce 7600 GS. Hardware Drivers installed the new NVIDIA v180 driver. I also installed CompizConfig Settings and turned Compiz on.

The thing that is happening to my mouse is very annoying and kind of like described above. I noticed when I scroll up with my mouse it sometimes locks up the window and clicking wherever or even typing (ALT+TAB or something else) doesn't seem to work any more. Most of the time scrolling down unlocks the focus on the window and starts working normally again. Still, sometimes it gets stuck for a longer time.
Also, when I have selected something and scroll up or down it pastes the selected bit wherever I'm editing something. Pretty frustrating! Scrolling over a link also makes the mouse click on a link in FF (or Epiphany), but they open up in a new tab so it must be the middle button...

Just went back to the old NVidia (v96) driver, but it doesn't seem to matter. Turning Compiz off doesn't matter either (have to turn it off to get Remote Desktop to work anyway).

Anyone? :confused:


My system:
Asus A7n8x Deluxe + XP3200+
Asus N7600GS Silent
Onboard nForce Soundstorm (OSS)
Running Ubuntu 9.04, kernel 2.6.28-11 (updated from 8.04 and 8.10)

---

### Post by raypsi on 2009-07-27
I got the no left click on my USB wireless mouse swapping the key from left to right don't help. And it's problematic sometimes it works sometimes it don't.

 when I click the key i get audio confirmation that it was clicked but nothing happens.

It all started after I updated Firefox to 3.0.12 

If I right click then left click it works more often than not.

I can't click off a window but if I alt F4 it the window closed then the left key works agin for awhile.

---

### Post by raypsi on 2009-07-27
> **joylessdave said:**
> i was having this problem with an upgrade from 8.10 to 9.04 

i was reading other posts  on the forum and disabling compiz was the suggestion on one of them

go to system | Preferences | appearance 
then go to the visual effects tab and select none

this seems to have solved the problem here (for now anyway)

nope not for me

---

### Post by raypsi on 2009-07-28
> **Tom Collier said:**
> !!! Turning off visual effects solved the mouse behavior problem(s) I described in my previous post.  You guys are geniuses!  Thanks!

been there done that still the same trouble

---

### Post by raypsi on 2009-07-28
> **csno1 said:**
> I also logged-out/logged-in but it only cured the problem temporarily!

yes log out log in seems to do it for now have, mouse will report

---

### Post by ipx on 2009-09-15
Man, this really annoys the cr*p out of me, are people still having this problem? Is there a solution?

- I didn't have lomoco installed
- Visual effects was already on none
- The "modprobe psmouse rate=100 proto=imps" didn't work

Ubuntu 9.04, Labtec Ultra-flat Wireless mouse/keyboard

EDIT: I tried upgrading to linux kernel 2.6.29-generic x64 with no success.
EDIT2: This is definately related to the wireless mouse for me, if i disconnect and use wired mouse it works like a charm.

Update: As I wrote in my newer post, I believe that you can reproduce the same problem by only keeping your mouse3 pressed all the time on a system without this problem. The window-focus-bug will occur in the same way as if you had this bug with your wireless mouse. Please give me feedback on this, as this might be very related to a fix.

---

### Post by soan on 2009-10-12
Having the same problem any ideas anyone? Fixes supplied did not work.

---

### Post by Stuart42 on 2009-10-12
I ended up plugging into a different USB port. Not sure why this helped...

---

### Post by soan on 2009-10-13
Tried the mouse on like 3 pcs, turned out to be the mouse. I always thought Logitech was good and now the 1st one I buy breaks on me... :-)
O'well glad it was not an Ubuntu issue.

---

### Post by kevinkr on 2009-10-13
In my case running 64 bit Jaunty it most definitely is Ubuntu. Every USB wireless mouse I have tried crashes within a few minutes of boot. I finally just gave up and plugged in a PS2 mouse - that works fine. I doubt this problem will ever get fixed.

Logitech Mouseman Wireless and Microsoft Wireless Optical Mouse (bought new after installation of Jaunty) both did it.

---

### Post by timjohn7 on 2009-10-27
Exactly the same problem with Labtec Wireless UltraFlat Desktop Mouse.  Works perfectly for ~20 minutes and then displays the "lost Focus" characteristics as described in various posts here.

It seems to happen in Opera 10 more than in other applications.  Could it be "mouse gestures"-related?

The pity is that the wireless keyboard works flawlessly, so I doubt whether there is an interference or usb issue.  I've changed batteries in the mouse, unplugged it and rebooted several times, but the problem re-occurs.  I've not yet tried the modprobe fix and compiz doesn't seem to make any difference.

It's almost as if the mouse instructions build up in a buffer which then tops out and the mouse doesn't catch up.

What is even stranger is that if I then plug in a standard PS2 mouse, it displays the same characteristics until rebooting.

This is all running on an AMD Sempron with 1 Gb RAM and Ubuntu 9.10 RC.

PLEASE HELP!

---

### Post by ipx on 2009-11-06
> **timjohn7 said:**
> Exactly the same problem with Labtec Wireless UltraFlat Desktop Mouse.  Works perfectly for ~20 minutes and then displays the "lost Focus" characteristics as described in various posts here.

It seems to happen in Opera 10 more than in other applications.  Could it be "mouse gestures"-related?

The pity is that the wireless keyboard works flawlessly, so I doubt whether there is an interference or usb issue.  I've changed batteries in the mouse, unplugged it and rebooted several times, but the problem re-occurs.  I've not yet tried the modprobe fix and compiz doesn't seem to make any difference.

It's almost as if the mouse instructions build up in a buffer which then tops out and the mouse doesn't catch up.

What is even stranger is that if I then plug in a standard PS2 mouse, it displays the same characteristics until rebooting.

This is all running on an AMD Sempron with 1 Gb RAM and Ubuntu 9.10 RC.

PLEASE HELP!

I have the exact same mouse with the exact same problem. I have found out that I can reproduce the exact same problem by keeping mouse3 pressed while I try to do other stuffs on my regular desktop with a corded mouse. The result is the same, it stucks on window-focuses, I have to right-click to get it o respond again etc. Could anyone with the same problem please also see if im onto something?

---

### Post by Jethro_uk on 2009-11-13
Right, this is getting silly. I have had this problem on TWO completely different machines now. One was a 8.10->9.04 upgrade. The other a completely fresh 9.04 install to a bare machine. Both machines have dual-boot XP, which (guess what ?) - works flawlessly. So it is clearly an Ubuntu/Linux issue.

Looking at the 8.10->9.04 machine, it worked flawlessly under 8.10. So it would suggest something changed in 9.04

The only clue I have, being a linux noob, is the xorg.conf now holds no mouse driver details, with a comment in the file that the HAL handles the mouse now. However I have no idea if this happened in 9.04, or has been the case for a while.

It is so intensely frustrating, as I *want* to use Ubuntu. However this problem, although subtle and perhaps uncommon, is enough to drive me to distraction. It renders the machine unusable.

---

### Post by Niniel on 2009-11-14
For me, the problems with my trackball have disappeared after one of the recent updates. 
So all that's still bugging me are the (FF-related?) freeze-ups.

---

### Post by markba on 2009-11-29
It's also on Karmic 9.10. My machine is a Packard-Bell laptop with a touchpad.

I've tried several things, at no result:
- downgraded (by a fresh install) to 9.04
- external mouse
- using 'acpi=off noapic nolapic' as kernel start parameters
- turn off visual effects

I can try to downgrade to 8.10 as many people in this thread encountered the problem *after* they upgraded from 8.10 to 9.04.

My guess is, it's a focus problem. You can gain back focus, at least temporarily by pushing Alt-F1 for activating menu's.

---

### Post by CylnZ on 2009-11-30
9.10, had never experienced this issue prior to this week. I thought it was a script/config problem with FF.  Nope. I can't necessarily recreate the issue on demand, but, it occurs mostly within FF. If I c+a+backspace and relog in, it works fine again for a while. Then, bam, I get to navigate via keyboard till I c+a+backspace and relog in, again. Have tried all the fixes in this thread and a couple others.

Since this has been an issue for several years, it looks like another "good luck" scenario.

---

### Post by triglav on 2009-11-30
> **markba said:**
> 
My guess is, it's a focus problem. You can gain back focus, at least temporarily by pushing Alt-F1 for activating menu's.

I agree. I have the same problem after installing 9.10 on Dell Inspiron 6000 laptop. 
However, I have no problems with 9.10 on my 4yr old desktop computer, so obviously, the bug is hardware dependent.

---

### Post by Jethro_uk on 2009-11-30
[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/41301](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/41301)

---

### Post by bill.ca on 2009-12-01
For what it's worth, I'm having the same problem as everyone else: I upgraded to 9.10 from 9.04 and everything worked fine for a couple of weeks.  Then, last week, I started having mouse problems.  As others have said, it is a "focus" problem, with the mouse not highlighting links or windows, and the mouse clicks not working.  I get this when I use just about any application.  Oh, and I also lose Alt + Tab at the same time.

Anyway, the only new thing I have to add to this discussion is that I downloaded the Fedora 12 Live CD to see if that worked any better and had exactly the same problems with it.  

I ran 9.04 for 6+ months without any problems, and I'm tempted to downgrade back to it.  My machine at work runs 9.04 and (fingers crossed) still works ok,  but several people on the Ubuntu and LinuxQuestions forums have said they've had problems doing trying to revert to 9.04.  Does anyone have any wisdom to offer here?

---

### Post by Jethro_uk on 2009-12-02
After a while playing with this problem, I have got it down to be an annoyance, rather than a showstopper.

Not being a Linux guru, my opinions are of limited value, but I firmly believe this is an X-Server/XOrg problem. I've seen it happen under GNOME and KDE, and with all combinations of window managers, and decorators.

There appears to be a connection with ALT-TAB ... as soon as the mouse focus issue happens, you lose ALT-TAB.

Anyway, I have discovered that if I activate ALT-TAB as soon as I login, it seems to "protect" my system, and I don't seem to lose mouse focus.

I have also discovered, that CTL-ALT-D (show desktop) seems to recover mouse focus ... once all windows are minimised to the taskbar, then ALT-TAB seems to work again, and mouse focus is restored. Hopefully this workaround will prove useful to people, and can remove the need to logout/login again, or to restart the machine with the loss of data that implies.

---

### Post by bill.ca on 2009-12-02
Jethro_UK - Unfortunately, your fixes don't work for me.  For the record, I tried updating to the newest nvidia driver today (190.42), but it didn't fix anything.  It was a vague hope...

---

### Post by Jethro_uk on 2009-12-03
> **bill.ca said:**
> Jethro_UK - Unfortunately, your fixes don't work for me.  For the record, I tried updating to the newest nvidia driver today (190.42), but it didn't fix anything.  It was a vague hope...

sometimes it takes more than one ctl-alt-D ... it's almost like the windows have to "cycle".

Have you tried Alt+F1, to try and bring up the apps menu. I've also found that works. The fact you experience the issue in another distro implies it's something very low-level.

---

### Post by Wafaa on 2010-02-07
> **teejcee said:**
> OK...looks like I have an answer.....try this

```
sudo gedit /etc/modprobe.d/NAME.conf
```...where NAME is the name of the file you are going to create. As I have an LX6 , I called it, ....wait for it.... lx6.conf

now put this line in the file...

```
option modprobe psmouse rate=100 proto=imps
```Now save the file & exit gedit.

That's it...!!!

I have re-booted several times & my problems have ( for now at least ) disappeared.
Thanks! 
My mouse kept randomly getting stuck and not responding to any click very frequenty on 9.10.  This made it work, and it hasn't gotten stuck since.

---

### Post by painki11er on 2010-07-14
I had this problem with ubuntu 9.04 then 9.10 and now 10.04. I managed to solve it though and now I want to share my solution. 

First of all I'm using a wireless mouse. The adapter was connected to a USB hub. It turned out that that was the cause. The problem has gone when I connected the adapter directly to USB port (usb mounted on a motherboard).

So if you're facing this kind of problem try switching ports of your mouse or wireless adapter etc.

---

