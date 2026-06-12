---
title: "Misc lowlevel stuff"
date: 2010-11-09
forum: New to Ubuntu
---

### Post by fhaber on 2010-11-09
A couple of short ones, from a desultory UNIX user trying Ubuntu again.  Yes, I'm really a newbie, as far as modern Linux distros are concerned. I'm actually enjoying Gnome's simplicity, and sudo-ing everthing is becoming second nature.  Pointers to my reeducation accepted with gratitude.

Currently running UStudio 10.10 with Vesa 12x10 video, since the  nV96 driver seems broken in Maverick. 

o In gnome/grub2, how do you TEMPORARILY keep the gui from autospawning when you ctrl-alt-bksp? Object: to install a driver. Desired: convenient revert to normal behavior.

o  Is the "recovery console" from login a "runlevel 1/gelded" or a real root  bash shell with pathing and customizations?  Could I, say, install a new graphics driver from there?   How do I keep this window from being tiny and illegible in the upper left?  Will all this change when I finally get accelerated video? 

o  How do you run MC, Alsamixer and other console apps and keep the Gnome terminal  hotkeys from intercepting the app's keys?  Should I be using xterm for  this? Is there a "naked" launcher shell for a GUI-desktop launch of older character apps with elaborate navigation hotkeys?

---

### Post by Zill on 2010-11-09
> **fhaber said:**
> A couple of short ones, from a desultory UNIX user trying Ubuntu again.  Yes, I'm really a newbie, as far as modern Linux distros are concerned. I'm actually enjoying Gnome's simplicity, and sudo-ing everthing is becoming second nature.  Pointers to my reeducation accepted with gratitude.

Currently running UStudio 10.10 with Vesa 12x10 video, since the  nV96 driver seems broken in Maverick... 
It *may* be that your UNIX experience is making the task seem harder than it should be. ;-)  Installing nvidia drivers in Ubuntu is *usually* quite straightforward.  Simply select "Hardware Drivers" from the System, Administration menu and driver options should be given.  Select the Recommended option and then hit Activate to install the driver, followed by a reboot.  If this fails for any reason please advise, together with your actual graphics card model number.

> **fhaber said:**
> ...How do you run MC, Alsamixer and other console apps and keep the Gnome terminal  hotkeys from intercepting the app's keys?  Should I be using xterm for  this? Is there a "naked" launcher shell for a GUI-desktop launch of older character apps with elaborate navigation hotkeys?
You can always use Ctrl-Alt-F1 to bring up a VT using the straight CLI.  Use Ctrl-Alt-F7 to return to the GUI.

---

### Post by fhaber on 2010-11-09
>actual graphics card model number

MX-420.  The latest trial driver comes as a .run-file, and must be installed from a clean terminal with the GUI shut down (not a recovery console).

>Ctrl-Alt-F1-6

Super!  Full screen, crisp, decent fonts. Thanks

---

### Post by Zill on 2010-11-09
> **fhaber said:**
> >actual graphics card model number

MX-420.  The latest trial driver comes as a .run-file, and must be installed from a clean terminal with the GUI shut down (not a recovery console)...
Forgetting a downloaded "trial driver" for now, what happens when you click on the System, Administration, Hardware Drivers menu item?  You may(!) see a list of available nVidia drivers.  Select the recommended driver, click "Activate", then reboot.

---

### Post by fhaber on 2010-11-10
Nope, as I said, the nVidia 96-series driver for older Geforce 3/4 cards is broken for Maverick.

The Hardware Drivers widget finds nothing.  The .18 drivers are in the repository. nVidia has a .19 for trial, but I have to change the boot runlevel of the machine, ideally temporarily.  Know what to edit?

---

### Post by anewguy on 2010-11-10
I could be incorrect here, but I think I remember reading that Ubuntu doesn't really use the run levels, particularly as you are accustomed to from your previous Unix experience (I remember those days!).

Instead, perhaps you can add some detail as to WHY you would need a different run level.  It's quite possible there is a simpler solution.  EDIT:  I should add, as an example, that if the nVidia driver requires X not to be running, all of that can be accomplished without the need for any run level changes.

Dave ;)

---

### Post by endotherm on 2010-11-10
can't help with the third, but if you want to kill x and keep it off for the remainder of the boot, use Ctrl + Alt + F1 to show TTY1, login as a sudo capable user, and enter this:
```
sudo service gdm stop
```you may have to kill X afterward, but I think it is closed automatically. otherwise if it still shows in ps, use kill/killall/stopx to end it. 

then install your driver and either reboot or startx.

it is my recollection that rescue mode is runlevel 3, so it is a full shell, but there are some things it won;t do unless you get back up to 5. i don;t play with run levels often.

---

### Post by Zill on 2010-11-10
> **fhaber said:**
> Nope, as I said, the nVidia 96-series driver for older Geforce 3/4 cards is broken for Maverick...
It seems that this is active [bug #626974]("https://bugs.launchpad.net/ubuntu/maverick/+source/xorg-server/+bug/626974") and it looks like an updated deb will be introduced into the Ubuntu repositories very shortly.  This is the preferred method of software installation as it ensures that driver updates track kernel updates.

However, as an interim measure you could try installing the PPA driver by adding [ppa:dajhorn/nvidia-96]("https://launchpad.net/~dajhorn/+archive/nvidia-96/") to your system's Software Sources.  Click on the line entitled "Technical details about this PPA" to see the line needed to paste into the /etc/apt/sources.list file, together with the associated Signing key.  Then just install the package in the usual way.

---

### Post by fhaber on 2010-11-10
Ah, thanks for the pointer to the bugtracking on Launchpad. I see that things are in flux.  I think I can wait until the official package filters from Debian ==>Ubuntu.

I have another little nit to drive you guys crazy.  I see Ubuntu has, uh, idiosyncratic methods to change keyboard bindings.  I'm running pretty vanilla, with USA-bog-standard 104/5 key on a desktop.  The sole changes I really need are 

o swap ctrl with capslock 

o enable ctrl-alt-bkspc to kill the GUI (which autospawns, of course).

How do I get the above changes to stick in an altF1-6 console session.  I'm going nuts, since ctrl is standard-mapping there and I lean heavily on things like the joe/jstar editor.

-crippled by my long and chequered history, apparently

---

### Post by Zill on 2010-11-11
fhaber:  I appreciate that your background makes you want to emulate UNIX as much as possible but I suggest that, unless you are still using UNIX systems, it is better to "adapt" to the Linux/Ubuntu way of doing things. :-)  IMHO this will cause far fewer problems in the long run.  However, to answer your queries as best I can:

1)  Open the Keyboard option from the System, Preferences menu then select the Layouts tab. Click on the "Options" button then the "Ctrl key position" pull-down and you should be able to select the "Swap Ctrl and CapsLock" option.

2)  From the same Keyboard Layout Options, you should also be able to open the "Key sequence to kill the X server" pull-down and then select the "Control + Alt + Backspace" option.

3)  My understanding is that these changes will only apply to Gnome (GUI) sessions, so when you are logged in to a TTY via Alt-F1 etc, I do not think they would have any effect.  However, I am happy to be proved wrong on this. :-)

FWIW, Ubuntu is primarily GUI based and, as you seem to rely heavily on CLI applications, it may not be the best distro for you.  You may find another distro that is better suited to your requirements.  However, if you do wish to embrace "the Ubuntu way of doing things" you will find plenty of help and support from the good folk on these forums. ;-)

---

### Post by fhaber on 2010-11-12
Thanks, everyone.

I can report that the test 96.19 driver from that PPA works well in Gnome, 12x10x(truecolor)x60Hz. And like all nvidia drivers, it makes console screens ugly VGA, and boot recovery consoles nearly unusable, with wordwrap. (You just knew I had to complaing about something, right (g)?)

For this reason, and simply because I'm trying an **audio** subdistro (Ubuntu Studio), I'm going to **have** to get used to Ubuntu's ways.  Expect more off-the-wall questions from this quarter, and thanks very much again for your help, people.

---

### Post by Zill on 2010-11-12
fhaber:  I am pleased that you have now got the graphics driver working OK.  I think, in time, you will get to know and love Ubuntu as much as we do!

Regarding your comments about console screens, I hardly ever use the Ctrl-Alt-Fx TTYs.  *Most* things can be done directly via the GUI but if I do choose to use the CLI then the Gnome terminal is quite adequate.

Similarly, I can't remember when I last needed a recovery console!

So, enjoy the Ubuntu learning curve - you won't regret it. :-)

---

