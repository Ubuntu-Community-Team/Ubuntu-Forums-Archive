---
title: "Keyring Problem in KDE"
date: 2007-07-23
forum: Networking &amp; Wireless
---

### Post by Ice_Dragon on 2007-07-23
I hope this is the right place.  I'm having a problem with my WEP keyring in KDE.  If I log in with a GNOME session, it asks for my password and everything is fine.  However, whenever I log into KDE, I have to type the WEP key myself.  If I go to the keyring manager, it just says "Keyring daemon is not running".  Also, if I log into GNOME and then switch to KDE, it works.  Any help would be appreciated.

---

### Post by audax321 on 2007-07-23
When you log in to KDE try running the following command:

```

/usr/bin/gnome-keyring-daemon

```

That should get the keyring daemon running under KDE. If it works, you'll probably want to make it start whenever you log into KDE (I would use the script I'm pasting below to prevent multiple instances of it).

```

#!/bin/sh
# Starts gnome-keyring-daemon only if another instance is not already running.

if [ "$(pidof gnome-keyring-daemon)" = "" ]; then
	gnome-keyring-daemon
fi

```

Hope that helps.

---

### Post by Ice_Dragon on 2007-07-24
Where am I supposed to put the script?  Sorry, I'm new to this.

---

### Post by audax321 on 2007-07-26
I haven't used KDE in years, but I'll try to help you out. What you want to do is copy that into a text file and save it in KDE's autostart folder. I think the folder you want to save it to is:

```

 /home/your_username/.kde/Autostart

```

unless of course that has changed.

Make sure the script is executable:

```

chmod +x /home/your_username/.kde/Autostart/name_of_script

```

That should do it. Now when you log-in to KDE the script should execute automatically.

---

