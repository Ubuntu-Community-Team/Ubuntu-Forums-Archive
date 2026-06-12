---
title: "Upgrading to Natty Narwhal, impressions and comments of beginner.."
date: 2011-05-02
forum: New to Ubuntu
---

### Post by NeverUsedItBefore on 2011-05-02
Hi,
Well I upgraded to Natty Narwhal as a big popup appeared saying about it.

Couple of things about the upgrade process itself:

1) Remember its not fire and forget. After a while a screen appears asking if you accept some license arrangements with microsoft. So don't think you can go away from your computer and expect it will be upgraded straightaway.

Thoughts on this from absolute beginner.
 - It will be better for everyone to get the nasty popups out the way at the start, or at least give a warning they will be coming. It's quite a long upgrade especially if you take into account downloading it, surely it's best to make it easier to run?

2) Towards the end of the process, another popup appears.
It says something about a GNU GRUB. As a absolute begginner, and to make things easier, this popup should perhaps say something like:
"We find some existing settings on your existing version of Ubuntu. Would you like to keep them or not?"
Mention of grubs to me means something that I can squish or celebrities eat them in the jungle. Anyway, my advise is to select that you want to keep your existing settings.
(Advise only based on what worked for me, no warranty :-)

3) Problems with older systems/boot menu.
Note that for older computers with the previous graphics card installation (I suppose it's called 'ATI' or something), if you have the following hardware: Radeon 9200 SE, LG Flatron L1919S Monitor, the next time you boot (especially a brand new boot as opposed to restart), you can get the monitor erroring out: "OUT OF RANGE" 46.4khz 43 Hz.
To solve this error you need to install the startup manager, see the help page here:
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

This line is your friend:
sudo apt-get install startupmanager

This can be run in Applications - Accessories - Terminal

Once installed in can be run from System - Administration - Startup Manager.
I suggest setting in Display Section - resolution as 1024 x 768, color depth 24 bits
In advanced menu setting Bootloader menu resolution as 1024 x 768.

Also, I have been advised the following keys may help if you cannot boot:
Esc
Ctrl + Alt + F1 (like Ctrl Alt Del in Windows I think)
Ctl+Alt+Numpad (apprently this steps thru different resolutions).

Oh and one more thing, probably you need to select Ubuntu Classic when booting, you can find a new menu on the shutdown button (System Settings), Login Screen - select Ubuntu classic as default selection.

4) For Dual Boot users
Unfortunately not all hardware or all games is supported in ubuntu. Sometimes people advise
then the user of WINE, but I was told not to do this.
So some people like me are keeping windows on the computer as well as
Ubuntu.

After having installed the upgrade on a dual boot system, by default the
screen for selecting operating system is not appearing!
This is surprising and somewhat worrying, you may think Windows has disappeared!
And it's not great if you have problems, because you can only boot to
Ubuntu and if this isn't working......

Luckily it hasn't (disappeared), and you can re-enable the selection 
in the start up manager (tick - show boot splash in the misc section).

NOTE: Sometimes the monitor problems went away by either waiting for
a bit, or pressing all the buttons on the side of the monitor!
Bit of a disappointment that the first problem I have within 5 minutes of having natty, we find ourselves back at the gold old unix command line! :-)

---

