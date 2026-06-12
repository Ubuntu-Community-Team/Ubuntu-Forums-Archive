---
title: "Accidentally removed nm-applet from tray. Won't appear again."
date: 2008-09-19
forum: Networking &amp; Wireless
---

### Post by wat3r on 2008-09-19
Hello

As the title says, I accidentally removed the nm-applet from the tray. 

I have tried to run the command nm-applet, but it won't appear. I have tried several reboots, and I have tried starting it both via terminal and Alt+F2.

Just so I don't get any questions about this; I don't get any feedback when I run the command nm-applet. The system acts like it started without any problem, but it just isn't there.

---

### Post by PocketDog on 2008-09-19
You mean the icon's disappeared? Bring it back by right-clicking the panel > add to panel. It'll be in the list of options. If you've deleted the nm-applet entirely try **sudo apt-get install --reinstall network-manager** from a terminal, or search network-manager or just nm-applet in Synaptic

---

### Post by wat3r on 2008-09-19
I just removed the icon. When I right click and select 'Add to panel', the only manager in the list is a different one, which is just not as user friendly as nm-applet. The one I have in the list is called 'Network Monitor'.

Both network-manager and nm-applet are installed on the system. I tried reinstalling them just now, but didn't seem to fix anything.

The packages I reinstalled were
- network-manager
- network-manager-gnome

---

### Post by PocketDog on 2008-09-19
Just one more thing before I panic and run off, screaming: right click the task bar again, and re-add 'notification area'. That's where the network manager lives, if it's not on your task bar then the network manager won't be either

---

### Post by wat3r on 2008-09-20
You learn new things every day. The thing I learned today, was: The nm-applet lives inside the Notification Area. Thank you PocketDog :)

And just to clearify: I was not being sarcastic just now. It actually worked :p

---

### Post by PocketDog on 2008-09-20
Well that's a relief! I was worried I'd been completely and utterly wrong and, as usual, hopeless :lolflag: Glad I could help

---

### Post by iceback on 2008-09-22
I was in a boat similar to wat3r's, but reboot brought back the nm-applet to the panel, but none of the configuration returned.  Lost all my vpn definitions and can't find them nor remember how I instantiated them in the first place!  All I get from nm-applet(0.6.6) is "Manual Configuration..."

---

### Post by iceback on 2008-09-22
Reading on further lead me to [http://ubuntuforums.org/showthread.php?t=898105]("http://ubuntuforums.org/showthread.php?t=898105") and much happiness

Sorry for the noise

---

### Post by quixote on 2008-11-08
Thanks Pocketdog!  nm-applet disappearance was driving us crazy too.  Never occurred to either of us to fix the notification area.  We were looking for what was wrong with nm-applet!

---

### Post by nailhead33 on 2008-11-24
I've been fighting this stupid thing for two weeks now.  On the verge of rolling it all back to 8.04.  Who'da thunk that the network manager icon was in the notification area?

Thanks, dude.  Choirs of angels sing...

---

