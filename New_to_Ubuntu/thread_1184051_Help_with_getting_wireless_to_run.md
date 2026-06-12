---
title: "Help with getting wireless to run"
date: 2009-06-10
forum: New to Ubuntu
---

### Post by Beau Higgins on 2009-06-10
I have installed Ubuntu on a Compaq Presario V6000 running Vista. The wireless modem is a Broadcom, and I have gone through the steps in the help file at least to the best of my ability. I got as far as the find the ".inf" file and install the ndisgtk package part. I downloaded the driver for Broadcom, but it's an .exe file. Things I looked at on the web suggested using Wine or cabextract to open up the .exe file and get the .inf file, but I can't seem to install either program. I have installed the Jaunty Jackalope (9.04) version of Ubuntu. As you can probably gather, I am extremely new to Linux, not great with Windows but at least fair-to-middling (as a user!) with Mac. Any pointers, suggestions, input would be extremely appreciated.

---

### Post by TrakerJon on 2009-06-10
Well, windows drivers are probably not going to work for starters.

Try this...

Procedure to enable WPA Wireless in Ubuntu

Sometimes wireless adapters (usually internal ones) don&#8217;t want to work right after the initial Ubuntu operating system install, even if the system recognises the hardware. The following should help if you&#8217;re in that situation.

If you have wired Internet connectivity update the software sources list from a terminal windows with **sudo apt-get update**

**sudo apt-get install wpasupplicant** (may already be installed)
[B]
sudo apt-get install network-manager-gnome network-manager[/B] (may already be installed)
[B]
sudo gedit /etc/network/interfaces[/B] Comment out the lines without &#8220;lo&#8221; entries (using #) and save the file, if you have just installed Ubuntu this may not be necessary.

Create a file by: **sudo gedit /etc/default/wpasupplicant**, add entry ENABLED=0 and save the file.

**sudo touch /etc/default/wpasupplicant**

Reboot your system.

When prompted to connect to a wireless network, select the desired one and enter in the key if necessary.

---

### Post by superprash2003 on 2009-06-11
if you still have problems, post output of **lshw -C network** from the ubuntu terminal

---

