---
title: "I installed third party software and now I can't find it."
date: 2010-09-23
forum: New to Ubuntu
---

### Post by greenmaji on 2010-09-23
After installing AVG anti-virus for linux/FreeBSD it didn't show up in the applications menu or in search files (other then the .deb) and Im at a loss as to what I can do to find the application.

suggestions?

Thanks in advance :P

---

### Post by Rubi1200 on 2010-09-23
If I am not mistaken it is a command line only application.

Try from the terminal (Applications > Accessories)

---

### Post by mprice on 2010-09-23
Here is some information to make a launcher for avg so you can just run it from the menu.

[https://help.ubuntu.com/community/Antivirus/Avg]("https://help.ubuntu.com/community/Antivirus/Avg")

---

### Post by greenmaji on 2010-09-23
:( Im kinda clueless how to use applications from the command line

I entered the exact lines you bracketed and got a command not found error

---

### Post by Rubi1200 on 2010-09-23
In the terminal:

```
avg
```

Also take a look at the link posted by mprice

---

### Post by greenmaji on 2010-09-23
> **mprice said:**
> Here is some information to make a launcher for avg so you can just run it from the menu.

[https://help.ubuntu.com/community/Antivirus/Avg]("https://help.ubuntu.com/community/Antivirus/Avg")

I don't have the first file.. avggui..

I downloaded and installed the .deb with the installer application now there is only a text file left that is compressed on my computer.. do I need to download something again to the desktop for the tutorial to work correctly?

---

### Post by mprice on 2010-09-23
Ok open up the terminal then paste this in there:

```
sudo rm /usr/share/applications/avggui.desktop
``` hit enter then copy this into the terminal:

```
gksudo gedit /usr/share/applications/avg.desktop
``` hit enter and then this should open up gedit. Once that opens up copy this into gedit which should be completely blank:

```
[Desktop Entry]
Name=AVG Antivirus
Comment=Antivirus
Exec=gksudo avggui &
Icon=/opt/grisoft/avggui/prog/pixmaps/avgico_big.png
Terminal=false
Type=Application
Categories=Application;System;
```

Save the file and close out gedit. Now go to Applications>System Tools>AVG Antivirus and click on it. This should open up AVG now if not then we will retrace the steps and find out what happened.

---

### Post by greenmaji on 2010-09-23
rm: cannot remove `/usr/share/applications/avggui.desktop': No such file or directory

---

### Post by mprice on 2010-09-23
Well then apparantly it doesnt exist so....go on to the next step to create your own then. Let me know if that works.

---

### Post by sandyd on 2010-09-23
> **mprice said:**
> Well then apparantly it doesnt exist so....go on to the next step to create your own then. Let me know if that works.
avg hasn't had a gui since v8.
use bitdefender

---

### Post by greenmaji on 2010-09-23
> **sandyd said:**
> avg hasn't had a gui since v8.
use bitdefender

thanks I will try that :popcorn:

---

### Post by greenmaji on 2010-09-23
LOL bitdefender's install is a .exe and umbutu won't let me do it...

its not in the repository or in synamtaic without any filters

nevermind.. I figured it out

---

### Post by 3rdalbum on 2010-09-23
Why do you want antivirus on an Ubuntu system anyway? There are no viruses that cam affect Linux. And you are obviously not running a mail server or anything.

---

### Post by beew on 2010-09-24
> **greenmaji said:**
> LOL bitdefender's install is a .exe and umbutu won't let me do it...

its not in the repository or in synamtaic without any filters

nevermind.. I figured it out

That is because you got the wrong (Windows) version. Check instead
[URL="http://www.bitdefender.com/business/antivirus-for-unices.html"]http://www.bitdefender.com/business/antivirus-for-unices.html
[/URL]

Not everything is in Ubuntu repositories, especially when it is closed source like BD. :)

---

### Post by greenmaji on 2010-09-24
> **3rdalbum said:**
> Why do you want antivirus on an Ubuntu system anyway? There are no viruses that cam affect Linux. And you are obviously not running a mail server or anything.

There are windows machines on my LAN and we might share a NTFS partition on this hardrive.

---

### Post by manny43 on 2010-09-24
> **greenmaji said:**
> After installing AVG anti-virus for linux/FreeBSD it didn't show up in the applications menu or in search files (other then the .deb) and Im at a loss as to what I can do to find the application.

suggestions?

Thanks in advance :P
Sometimes you have to restart system and then it shows up.

---

### Post by Zero++ on 2010-09-24
You could also try clam AV or Avast. I use both to scan for virus on my repair box. Chuck un an NTFS drive with a virus: backup, scan, fix! Another trick is portable apps. They run just fine in WINE and they have anti-virus and anti spyware options.

---

### Post by greenmaji on 2010-09-27
thanks guys.. I got bitdefender working with adding its repositlory in synaptic and getting a temperary key in termanal.. it got me to were I could put in my one year key..

I updated it and ran my first scan... typicaly nothing but it works fine..

thanks for the help peps :popcorn::guitar:

---

