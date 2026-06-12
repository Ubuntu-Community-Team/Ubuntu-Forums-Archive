---
title: "No Connection Switch 14.04.1 LTS  MAJOR BUG"
date: 2015-01-11
forum: Networking &amp; Wireless
---

### Post by MikeMecanic on 2015-01-11
[B]Last update: 12:41PM ET
Was there when I installed last night but only for 10 to 20 minutes.  Dont have an on board WIFI.  The wireless keyboard is unstable.

[/B]Error code: DNS_PROBE_FINISHED_NO_INTERNET  No connection switch beside the clock and I don't know why it indicates connected while its not, don't even know how it connects:  This ,morning I don.t even have the clock (time and date setting:  Dead windows), On reboot it came back but still don.t have the connection switch: i**nvisible**. I switch the keyboard from default English (us) to french it gives weird stuff:** doesn.t work**.  Will have to re-install again I guess, unless someone knows about it!?  Thanks God it takes only 20 minutes.  **No option to lock the task bar like in Windows??**?   **Plus, I don't find anywhere a check box saying: _show the network activity in the task bar._**

I installed 2 Firewalls after ISO CD installation of 14.04.1 LTS and the connection switch disappear.  Plus, if I delete the Ethernet connection 1, on reboot it doesn't come back **(empty space no connection at all).**

[https://wiki.ubuntu.com/UncomplicatedFirewall](https://wiki.ubuntu.com/UncomplicatedFirewall)
[https://help.ubuntu.com/community/Gufw](https://help.ubuntu.com/community/Gufw)

[B]
Do I need the first one? [/B]And the second one should be included by default.  Like to see which ports are opens.  Remind me the Norton Suite full package in Windows.  Feel more secure.
All the best in 2015,

---

### Post by ajgreeny on 2015-01-11
Lets' start with ufw first; the package gufw is just a gui for uncomplicated firewall, so you can't have the second without the first.

I don't know exactly what you mean by the first query unless you mean there is no network icon showing in your panel.  If that is what is missing check that you have nm-applet running with command **ps aux | grep nm-applet** in terminal which should give you two lines of output; something similar to
```
ps aux | grep nm-applet
*username*    2230  0.0  0.2 880908 17816 ?        Sl   16:08   0:00 nm-applet
*username*   14145  0.0  0.0  18940   920 pts/0    S+   20:17   0:00 grep --color=auto nm-applet
```The numbers will be different and your username will be where I show *username*.

If you get just one line of output the nm-applet is not running and it may need to be added to the startup applications list to ensure it starts when you login to a new session.

---

### Post by MikeMecanic on 2015-01-11
In deed there is no icon and that's what I get

guest-D+  2820  0.0  0.4 591536 18164 ?        Sl   16:36   0:00 nm-applet
michel    7135  0.0  0.4 591404 18016 ?        Sl   17:07   0:00 nm-applet
michel   14320  0.0  0.0  15964   928 pts/0    S+   19:11   0:00 grep --color=auto nm-applet

[B]
To kill the network process I have to unplugged the wire (RJ-45).
To connect on boot up, I have to fool around with the on/off switch in the Network windows (the one below airplane mode set off).  The desktop becomes unstable until connection occurs.[/B]

---

### Post by wildmanne39 on 2015-01-11
I am afraid this is what happens when you start removing things randomly. You need to completely wipe your drive then install fresh not leaving any thing behind, if you followed this method then ignore this post please.

---

### Post by MikeMecanic on 2015-01-11
In deed, I format only the root and bootable partition.  In fact out of the 3 installations options, I choose the first one that leave intact the files on the 3rd partition.  The things is that there are  3 options and they should all work.  It work from 12.04 LTS to 14.04 LTS. Plus, I have a 100Gig of rare stuff that comes from BT Junkies Data Base.  I need an external drive to store them and proceed the you want me to.

---

### Post by MikeMecanic on 2015-01-11
Regarding the keyboard:  I change french (deleted) to french (Canada) and I add Canadian multilingual and the problem was resolved.  The keyboard is stable now.  **The only problem remaining is the menu bar:  No access the the Network Switch (invisible).  **For the Firewall, the terminal was telling me that it was already installed.  But I overwrite it because I didn't know that the terminal is now protected:  We don't see the password when we type it.  **THIS IS A BIG PLUS REGARDING INTRUSION A BONUS I SHOULD SAY.**

---

### Post by Bucky Ball on 2015-01-11
Have you checked, as suggested, that nm-applet is starting at boot? Not sure where it is in regular Ubuntu, but in xfce4 it is called 'Session & Startup'. What you want will be something similar. Go there and make sure nm-applet is set to start with your session at boot. If it's not there, add it (it may already be there but disabled).

---

### Post by MikeMecanic on 2015-01-12
**I try boot repair:** [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)


sudo add-apt-repository ppa:yannubuntu/boot-repair
sudo apt-get update
sudo apt-get install -y boot-repair && boot-repair

Those commands work fine but it Didn"t work: the icon or switch was still invisible..
  So, I finally did a quick re-install: **cd iso boot up, 1st option**.  Solved

---

