---
title: "Uninstall Programs?"
date: 2010-05-01
forum: New to Ubuntu
---

### Post by Hydrokys on 2010-05-01
Completely new to linux and was wondering how i go about removing some programs that came with 10.04 and what startup applications do i absolutely need?

---

### Post by sadaruwan12 on 2010-05-01
You can use the Ubuntu software center to remove programs it's under Applications -> Ubuntu Software Center.

Once it opens select Installed Software and select the once you want to remove and click the remove button.

In Linux or in Ubuntu only the essential programs are run at the start up so you don't need to manually remove or disable anything it's very different to windows and if some ting needs to be run at boot time OS will let you know what.

Don't try to remove any startup programs it might screw your system up.

---

### Post by oldos2er on 2010-05-01
There are several services I disable after install Ubuntu; Bluetooth Manager, Evolution Alarm Notifier, GNOME Login Sound, Personal File Sharing, Remote Desktop, and Visual Assistance. I also turn off Avahi daemon, brltty, pcmciatuils, and speech-dispatcher. I've never had a problem with my system because of this. But if you're going to run a program e.g. sysv-rc-conf, it's best to do some research first.

---

### Post by aysiu on 2010-05-01
Before actually *removing* anything, you may just want to try going to System > Preferences > Startup Applications and unchecking a bunch of things you think you don't need, and then logging out and logging back in again to see if there's anything missing.

---

### Post by j_Antonio on 2010-11-11
> **aysiu said:**
> Before actually *removing* anything, you may just want to try going to System > Preferences > Startup Applications and unchecking a bunch of things you think you don't need, and then logging out and logging back in again to see if there's anything missing.

You can go to System > Administration > Synaptic Package Manager.

There you got a search bar to filter your results, in this case the program you want to uninstall. Select it then select it and mark it  as complete removal.
:guitar:

---

### Post by Rubi1200 on 2010-11-11
Before removing a program ALWAYS check its properties to see what the dependencies are.

In Synaptic, highlight the program and click on Properties > Dependencies.

If there is something you are not sure about, ask here first please.

Thanks.

---

### Post by 3rdalbum on 2010-11-11
Don't remove any preinstalled software if you are new to Linux. I've known newbies who have deleted Python because they think "I'm not a programmer, I don't need a programming language", and half their system depends on  Python.

---

### Post by cloyd on 2010-11-11
One thing to remember in Ubuntu . . . it isn't such a hog as Windows. I have several things I don't think I'll ever use that were there with the original install . . . but I have no reason to try to get rid of them. On the other hand, if I install a program and don't like it, I usually uninstall it as soon as possible. But for most of us, the default installations don't take up that much room. Unless you are very limited on disc space, I wouldn't worry about it.

---

### Post by mfstutz on 2011-06-20
I have the same question, only for a different purpose.

>>> Which programs CAN be deleted? <<<

>>> How could you predict that uninstalling something through Synaptic will trash your system (render it unusable) <<<

>>> Is there another tool which will uninstall stuff "more safely"? <<<

I'm trying to set up a kiosk where I place a computer that only has a web browser which points to a specific set of websites.  In order to remove the temptation for others to muck around with the computer I have used synaptic to uninstall everything other than the web browser & WiFi stuff.  

Deleting multiple programs at the same time, upon reboot I end up with an unusable system, (& having to reinstall from scratch, since I don't know how to recover) as the process apparently trashes some graphics driver or something essential.  The exact symptom is a message saying, "Ubuntu is running in a low-graphics mode", then upon clicking the "OK" button, I get a series of options with "Cancel" and "OK".  Long story short, none of the options work to get to a GUI interface & I have zero command line skills in unix.

I've reinstalled 3 times now (lengthy process, for some reason) & could use some help.

---

### Post by Christmas on 2011-06-20
> **mfstutz said:**
> 
>>> Which programs CAN be deleted? <<<

That depends. Usually anything can be deleted :) It's recommended not to remove system packages, or packages that are vital for the desktop environment to run. If for example you remove everything GNOME though, you could just press Alt+Ctrl+F1, login with your user and then install that back with something like **sudo apt-get install ubuntu-desktop** or **sudo apt-get install gnome**. Then to start up GNOME again type **sudo /etc/init.d/gdm restart** and eventually press Alt+Ctrl+F7 to go back in graphical mode.

> **mfstutz said:**
> 
>>> How could you predict that uninstalling something through Synaptic will trash your system (render it unusable) <<<

Again, you'll just have to know what are you doing, Synaptic ain't going to tell you what's dangerous for you to uninstall, or what you need/don't need. Usually a Google search before starting removing packages will clear that for you.

> **mfstutz said:**
> 
>>> Is there another tool which will uninstall stuff "more safely"? <<<

I don't know.

---

### Post by mfstutz on 2011-06-21
Reporting Progress . . . any further help appreciated.

Uninstalled and rebooted without incident:
gbrainy (Mark for Complete Removal == Complete)
gnome-games-common           (Complete)
openoffice.org-core          (Complete)
openoffice.org-common        (Complete)
openoffice.org-style-human   (Complete)
--reboot ok--
empathy-common               (Complete)
gwibber-service              (Complete)
tsclient                     (Complete)
vinagre                      (Complete)
ftp                          (Complete)
rdesktop                     (Complete)
--reboot ok--
transmission-common          (Complete)
evolution                    (Complete)
evolution-common             (Complete)
evolution-data-server        (Complete)
evolution-data-server-common (Complete)
--synaptic froze for a while, but came back--
--reboot results in "Ubuntu is running in low-graphics mode--

Would REALLY like to not have to reinstall & go through this process again.  Will try some of the commands in previous response from Christmas unless someone thinks they have some more precise "rescue" information


SYSTEM:
===========================================
Compaq Presario CQ56 (from Best Buy, USA)
replaced and formatted drive
Installed Ubuntu10.04 Desktop
===========================================

---

### Post by mfstutz on 2011-06-21
Full message on reboot:
Ubuntu is running in low-graphics mode
Your screen, graphics card, and input device settings could not be detected correctly.  You will need to configure these yourself. (OK)

Comes up with radio buttons of various options.  Selecting the "Run for one session" option produces another dialogue box: "Stand by for one minute while the display restarts..." . . . which never goes away.

Clicking "OK" (Cancel is grayed) results in a blank screen with a flashing dash in upper right corner.

At this point, the only remedy seems to be the power button for 5 seconds to reboot.  (which takes me back to "Ubuntu is running in low-graphics mode)

Restart X sends me back to the (terminal) "Standby" message

Reconfigure graphics is equally "useful" in that it takes me to another dialogue box which has 3 radio buttons (1.Use default, 2.Create new config and 3.Use backed-up config), none of which do anything when you click "OK" (Cancel takes you back to the first "5-option" dialogue.

Troubleshoot the error allows you to look at a log (since I can't cut & paste to another computer, I'll give exerpts from the (WW) entries:
-- (WW) The directory "usr/share/fonts/X11/cyrillic" does not exist.
-- (WW) Falling back to old probe method for vesa
-- (WW) Falling back to old probe method for fbdev

Review the startup errors produces blank dialogue box.

Edit the configuration file does nothing.

Archive configuration and logs seems to back the stuff up, but doesn't help me get back to a GUI.

Exiting to console sticks me into a command line login . . . where, of course, I'm lost.

. . . would still like some help here if someone could jump in . . . please . . .

---

### Post by mfstutz on 2011-06-21
sudo apt-get install gnome . . . fails

The following packages have unmet dependencies:
gnome: Depends: swfdec-mozilla but it is not going to be installed E: Broken packages

sudo apt-get install ubuntu-desktop . . . fails

Massive spew . . . but of course, since this is failing on initial boot, there's no network to get anything . . . and obviously it isn't searching the install CD sitting in the CD drive.

---

### Post by wildmanne39 on 2011-06-21
> **mfstutz said:**
> sudo apt-get install gnome . . . fails

The following packages have unmet dependencies:
gnome: Depends: swfdec-mozilla but it is not going to be installed E: Broken packages

sudo apt-get install ubuntu-desktop . . . fails

Massive spew . . . but of course, since this is failing on initial boot, there's no network to get anything . . . and obviously it isn't searching the install CD sitting in the CD drive.If you can get into recovery with networking you can run this command to see if it can fix broken packages.
```
sudo apt-get -f install
```
```
sudo apt-get update && sudo apt-get upgrade
```
this link will help with getting into recovery.
[https://wiki.ubuntu.com/RecoveryMode](https://wiki.ubuntu.com/RecoveryMode)

---

### Post by mfstutz on 2011-06-21
Unable to get to recovery console (read & followed link instructions) however can get to a command line (by using "Exit to console login" . . . however no network.  Any way to start up the wireless from a command line?  (It probably would still have the connection information.)

---

### Post by arpanaut on 2011-06-21
Might I suggest that rather than tearing down a full install, but to start from a minimal install and build what you need.

for Kiosk mode it is not so much to rmoveing all the programs but to set up a limited user and only allow access to exactly what is desired for said user.

Check this link, I didn't read all but it appears that he has a ready made kiosk install
[http://jacob.steelsmith.org/content/ubuntu-kiosk-based-10041](http://jacob.steelsmith.org/content/ubuntu-kiosk-based-10041)

Google "Ubuntu Kiosk"  lots of info to be had.

I think you are making this harder on yourself than it needs to be.

---

### Post by mfstutz on 2011-06-21
Thank you for your help.  I'm taking a different tactic: instead of "Stripping down Desktop" I'm going to try mini.iso & build up from there.  Fun project for tonight!  Thanks!

---

