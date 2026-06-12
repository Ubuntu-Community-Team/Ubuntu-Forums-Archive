---
title: "Wicd won't start after system reboot"
date: 2008-01-22
forum: Networking &amp; Wireless
---

### Post by oldsmobile_mike on 2008-01-22
Should be an easy one, right?  I've installed wicd as a replacement to the default Network Manager application, and have had no problems connecting to either my wired network, or two different wireless networks (other than that I can't get WEP-128 or WPA to work, but I think that's related to the old card I'm using)...  Anyhow, WICD works fine if I start it by going to the Applications -> Internet menu, and I've added the required command under Sessions:

+ Add Startup Program
Name: Wicd
Command: /opt/wicd/tray.py
Comment: WICD network settings

but each time I restart my computer, there's no tray icon for wicd, and it doesn't automaticlly re-connect to my network.  I have to manually restart it each time.  Any suggestions?  Any way to start it automatically through the command line?

Thanks!

---

### Post by imdano on 2008-01-23
What version of wicd are you using?  Some older versions (I think 1.3.1 and earlier) are known to have this problem, thought it might be present in some newer versions too.  Also, when you start up the computer, what's the output of ```
ps -ef | grep tray.py
```

---

### Post by coreymc on 2008-01-23
Hi-

You can put a symbolic link in autostart.  Find where your tray.py file is stored (e.g., /opt/wicd/tray.py) and then:

ln -s /opt/wicd/tray.py .kde/Autostart/tray.py

This works fine for me running Gutsy with KDE.

Good luck.

---

### Post by oldsmobile_mike on 2008-01-23
> **imdano said:**
> What version of wicd are you using?  Some older versions (I think 1.3.1 and earlier) are known to have this problem, thought it might be present in some newer versions too.  Also, when you start up the computer, what's the output of ```
ps -ef | grep tray.py
```

mike@Sager-5600P:~$ ps -ef | grep tray.py
mike      5254  5178  0 22:06 ?        00:00:00 /usr/bin/python /opt/wicd/tray.py
mike      5697  5518  0 22:07 pts/1    00:00:00 grep tray.py


In the meantime I've added a shortcut to the toolbar at the top of the screen, so I can just click on my shortcut and then hit "connect", at which point the network icon appears in the tray, but it's still annoying...  :(

---

### Post by imdano on 2008-01-24
What version of wicd are you using?

---

### Post by oldsmobile_mike on 2008-01-24
> **imdano said:**
> What version of wicd are you using?

I'm using 1.3.1 which, according to Synaptic, is the latest version available.  That's interesting, since when I go to the wicd website and click on "screenshots", I see a screenshot mentioning version 1.3.3.  Don't know what to make of that one.  :confused:

---

### Post by BattleCat_uk on 2008-01-24
Hi Mike,

I'm using 1.3.1 too. Up until 5mins ago I was having the same problem as you. Was very annoying! 

Did the /opt/wicd/tray.py in the start up and when I rebooted the wcid icon was not visible.:confused: Had to manually start it each time...

In wicd try ticking 'Automatically connect to this network' then reboot. It was so obvious but I missed it. It just started to work!

Hope this helps,

Brad

---

### Post by imdano on 2008-01-24
Our repository is out of date, the newest version of wicd is actually 1.4.1.  You can download the latest .deb here: [http://sourceforge.net/project/showfiles.php?group_id=194573](http://sourceforge.net/project/showfiles.php?group_id=194573)

---

### Post by oldsmobile_mike on 2008-01-24
> **imdano said:**
> Our repository is out of date, the newest version of wicd is actually 1.4.1.  You can download the latest .deb here: [http://sourceforge.net/project/showfiles.php?group_id=194573](http://sourceforge.net/project/showfiles.php?group_id=194573)

Thanks!  That solved the problem of wicd not starting with the computer.  Now is there any way to get it to automatically connect with a wired network?  I don't see the option for that.

---

### Post by imdano on 2008-01-24
You can click the "Use as default profile" button in the wireless network expander, and then make sure "Use default profile to autoconnect" radio button is selected in the preferences menu.  With those options wicd will  try to connect through ethernet before wireless, but sometimes it doesn't work out that way (I think I've figured out why, and it'll be fixed in the next release).

---

### Post by oldsmobile_mike on 2008-01-25
> **imdano said:**
> You can click the "Use as default profile" button in the wireless network expander, and then make sure "Use default profile to autoconnect" radio button is selected in the preferences menu.  With those options wicd will  try to connect through ethernet before wireless, but sometimes it doesn't work out that way (I think I've figured out why, and it'll be fixed in the next release).

That worked!  Thanks!

---

### Post by xodeus on 2008-03-03
I have this startup problem with the latest version 1.4.2
I've putted in Sessions and it wont start. I've to start it manually at every boot.

---

### Post by oldsmobile_mike on 2008-03-03
> **xodeus said:**
> I have this startup problem with the latest version 1.4.2
I've putted in Sessions and it wont start. I've to start it manually at every boot.


Weird.  I've actually found 1.4.2 to be very stable.  I'm not at my Linux machine right now, but could you post the commands you used to add it to Sessions?  I'll compare when I get home and make sure you're using the same commands as I am.

---

### Post by xodeus on 2008-03-03
System >> Preferences >> Sessions >>> Startup Programs >>> + Add >>>

and see the screenshot

---

### Post by oldsmobile_mike on 2008-03-04
> **xodeus said:**
> System >> Preferences >> Sessions >>> Startup Programs >>> + Add >>>

and see the screenshot

Hummm...  that's the same thing I have, and it works perfectly for me.  What do you get if you try executing the tray.py app from the command line?  Does it start that way at all?  Maybe it would help if you completely remove the program and reinstall (sudo apt-get remove wicd, then manually delete the other directories & stuff that aren't removed by the uninstaller, then reinstall)

---

### Post by xodeus on 2008-03-04
this is strange but great. wicd starts automaticly now.

---

