---
title: "Can't prevent Pidgin from auto-startup"
date: 2010-07-12
forum: New to Ubuntu
---

### Post by danielgrosvenor on 2010-07-12
Similar to [this user]("http://ubuntuforums.org/showthread.php?t=828834&highlight=prevent+pidgin+startup"), whenever I switch my laptop on Pidgin automatically starts up and appears on my taskbar.  As well as going into 'Preferences' in Pidgin itself, I've used both StartUp-Manager and Ubuntu Tweak to check there's nothing in the startup, and even disabled Ubuntu One from auto-startup in case this was somehow connected.

Is there some Terminal command I can use to tell it to stop auto-starting whenever I log in?

---

### Post by danielgrosvenor on 2010-07-12
To give some more info, based on the questions asked in that other thread:

etc/init.d contains no file with 'pidgin' in the title

Typing "ls ~/.config/autostart" into Terminal gives me the following:

devilspie.desktop                      print-applet.desktop
gnome-at-session.desktop               Screenlets Daemon.desktop
gnome-keyring-daemon.desktop.dpkg-bak  thunderbird %u.desktop
gnome-screensaver.desktop              'TweetDeck'.desktop
gnome-user-share.desktop               ubuntuone-launch.desktop
gwibber.desktop                        vino-server.desktop
libcanberra-login-sound.desktop

I'd already disabled Gwibber from auto-startup as I don't ever use it, but perhaps this indicated there's some trace of it still on the system.

---

### Post by Pizack on 2010-07-12
Without doing a lot of diagnostics, you could try to uninstall it, then re-install it. Might take out whatever is making it start.

---

### Post by davidmohammed on 2010-07-12
question - start ubuntu tweak  - in session control have you got "automatically save open applications when logging out" ticked - if so untick it.

---

### Post by jdorenbush on 2010-08-27
I'm having this same problem...

---

### Post by davidmohammed on 2010-08-27
ok - can I suggest you install ubuntu-tweak and see if my post above fixes this.

---

### Post by jdorenbush on 2010-08-27
> **davidmohammed said:**
> ok - can I suggest you install ubuntu-tweak and see if my post above fixes this.

I've already got Ubuntu Tweak installed and it isn't listed in my startup applications. My settings are as follows:
AT SPI Registry - OFF
Bluetooth Manager - OFF
Certificate and Key Storage - ON
Check for new hardware drivers - OFF
Disk Notifications - ON
Docky - ON
GNOME Login Sound - OFF
GNOME Panel - ON
GNOME Settings Daemon - ON
Gwibber - OFF
Indicator applet - ON
Network Manager - ON
Personal File Sharing - ON
PolicyKit Authentication Agent - ON
Power Manager - OFF
Print Queue Applet - OFF
PulseAudio Sound System - ON
Remote Desktop - OFF
Screensaver - ON
Secret Stroage Service - OFF
SSH Key Agent - OFF
Ubuntu One - OFF
Update Notifier - OFF
User folders update - OFF
Visual Assistance - OFF
Volume Control - ON

and my option to save apps when logging out under Session Control is UNCHECKED.

---

### Post by cgelici on 2011-03-27
I had the same problem with Pidgin AND Google Chrome. They would both start up automagically. No entry in startup items.

This is how I solved it (in my case) And it's kind of simple...

Login to your ubuntu machine. When Pidgin starts, close it. Then don't reboot or shutdown but choose Log off.

Then reboot and it should be fine now.

I guess it has something to do with session manager restoring the previous session state or something like that.

I use Backtrack 4 R2 (based on ubuntu 8.10)
I hope it works for you guys...

---

### Post by bhh1988 on 2011-10-22
One solution that will surely work is to write a script that kills pidgin and have it as a startup script. Add this command to a file and put the file on the list of applications to atuostart:

kill `ps -e | grep pidgin | head -n 1 | awk '{print $1}'`

(Note that the first and last ticks are back-ticks, not single quotes)

---

