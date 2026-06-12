---
title: "too many file manager opens at start up"
date: 2010-10-18
forum: New to Ubuntu
---

### Post by bernardstar on 2010-10-18
too many windows pop up showing my home directory at start-up

---

### Post by Autodave on 2010-10-18
> **bernardstar said:**
> too many file manager opens at start up, help pls

I am guessing that the reason no one has answered yet is that they have no idea what you are talking about.  Can you be more specific as to exactly what is opening on start up?

---

### Post by chaanakya_chiraag on 2010-10-18
What happens?  Do many windows pop up showing your home directory or something?  Have you told GNOME to remember your session and reopen the programs that were open when you logged out?

---

### Post by bernardstar on 2010-10-18
> **Autodave said:**
> I am guessing that the reason no one has answered yet is that they have no idea what you are talking about.  Can you be more specific as to exactly what is opening on start up?

when the computer start, many thunar is opening, about 31, this happens when im trying 2 make nautilus as default fm in xfce, i use
the script here [https://help.ubuntu.com/community/DefaultFileManager](https://help.ubuntu.com/community/DefaultFileManager)

---

### Post by bernardstar on 2010-10-18
yes it pop up many home directory, i try not 2 save session, but still the same

---

### Post by jtarin on 2010-10-18
Which desktop manager are you using? Gnome or XFCE?

---

### Post by bernardstar on 2010-10-18
> **jtarin said:**
> Which desktop manager are you using? Gnome or XFCE?

xfce

---

### Post by jtarin on 2010-10-18
The script your using is for someone that wants a different file manager in Gnome..not XFCE.
Just remove the tick where it says "allow xfce to manage the desktop'

---

### Post by drs305 on 2010-10-18
On my new installs nautilus auto-spawns - but many more than 31! It is pretty much continuous until I "killall nautilus" several times. 

In Gnome, I have to open up /usr/share/applications/nautilus.desktop as root and change the *true* value in this line to *false*.
> X-GNOME-AutoRestart=false 
Since you use XFCE I wouldn't think this line exists but it might or you might have a similar line for XFCE in the same file.

---

### Post by 3Miro on 2010-10-18
Try going to Thunar -> Preferences -> Advanced -> Volume Manager. Then tell Thunar to not automount/browse media when inserted. Maybe this will help the issue.

---

### Post by bernardstar on 2010-10-18
> **jtarin said:**
> The script your using is for someone that wants a different file manager in Gnome..not XFCE.
Just remove the tick where it says "allow xfce to manage the desktop'

wow it works, my problem is solved, thx

---

### Post by chaanakya_chiraag on 2010-10-19
Please mark your thread as solved by going to Thread Tools -> Mark Thread as Solved.  Thanks :)

---

### Post by notjingo on 2010-12-20
I am having the same or similar issue. After logging in Nautilus spawns thousands of instances for a couple minutes. They fill the panel and then finally disappear. After that periodically I'll see a "Starting File Manager" appear in the panel, then disappear. My desktop icons are gone, but funny enough Nautilus occasionally will still work and I am able to browse files.

What is going on???

I am using gnome 1.2.28+1ubuntu3 and Nautilus 1:2.31.1-ubuntu2~ppa92

This problem seems to have come out of nowhere but I'm not sure if it started occurring after an update. I've read all the threads I can on this but no solutions have worked.

I have uninstalled Ubuntu One client, as per this thread 
[http://www.browse24h.com/index.php?q=aHR0cHM6Ly9idWdzLmxhdW5jaHBhZC5uZXQvdWJ1bnR1Lytzb3VyY2UvZ2xpYjIuMC8rYnVnLzY2MDM0Mg%3D%3D](http://www.browse24h.com/index.php?q=aHR0cHM6Ly9idWdzLmxhdW5jaHBhZC5uZXQvdWJ1bnR1Lytzb3VyY2UvZ2xpYjIuMC8rYnVnLzY2MDM0Mg%3D%3D)
Did not help.

I have made the following changes to /usr/share/applications/nautilus.desktop

X-GNOME-AutoRestart=false    # changed from =true
AutostartCondition=GNOME /apps/nautilus/preferences/show_desktop    # added this line

As per this thread:
([http://ubuntuforums.org/showthread.php?t=1510116&highlight=nautilus+spawns&page=2](http://ubuntuforums.org/showthread.php?t=1510116&highlight=nautilus+spawns&page=2))
Also did not help.

I do not have the line mentioned at the end of this thread either (in the xorg.conf)
[https://bbs.archlinux.org/viewtopic.php?id=69282](https://bbs.archlinux.org/viewtopic.php?id=69282)

Edit: This thread seems to imply there is a connection with gvfsd-trash, which on my system is also suddenly taking up 80%+ of CPU resources. 
[https://bugzilla.gnome.org/show_bug.cgi?id=553776](https://bugzilla.gnome.org/show_bug.cgi?id=553776)

Please help!


EDIT: After trying to investigate more, it seems that there are a few related issues here. I still have not been able to solve this.

The top three processes running by memory usage are gvfsd-trash, dbus-daemon, and nautilus.

Gvfsd-trash is gvfsdtaking up almost 100% of system resources. Also my swap reports 0% usage. 

I'm pretty new to Ubuntu so any guidance on this would be a great help. From the several forum threads I've seen around I know this is a pretty widespread issue and has happened to many users. Unfortunately most of those forum threads are inconclusive or their solutions have not worked for me. I'd also appreciate some instruction on how to grab diagnostics and system specs to post that may help someone figure out what is happening on my system. Thanks again for any help!

---

### Post by jtarin on 2010-12-20
To begin with I would suggest you post this in a new thread of its own as this one has been marked solved and won't get as much attention by those that could help.You should also mention in that thread what version of Ubuntu you are using.

---

