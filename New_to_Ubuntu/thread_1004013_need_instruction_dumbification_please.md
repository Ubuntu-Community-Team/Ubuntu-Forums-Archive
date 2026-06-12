---
title: "need instruction dumbification please"
date: 2008-12-06
forum: New to Ubuntu
---

### Post by SRG8 on 2008-12-06
okay so i feel really dumb about this but i got instructions on how to fix a bug with the alsa sound or something and skype which was great except i didn't know how to follow the instructions, real newb here and terminal is definetely not a strong point. So if someone is kind enough to dumbify these instructions even more would be greatly appreciated.

heres the link:

[https://bugs.launchpad.net/ubuntu/+source/ia32-libs/+bug/273693/comments/6](https://bugs.launchpad.net/ubuntu/+source/ia32-libs/+bug/273693/comments/6)

---

### Post by kansasnoob on 2008-12-06
This is a long read, but really necessary and I think it will answer most of your questions. Note where it says:

> Q. I can't get Skype/WINE/an OSS application/XYZ working correctly with PulseAudio, what can I do?
A. Some applications require some extra configuration, and some applications don't work with PulseAudio - please refer to Appendix C for information on specific applications.

But apply all appropriate Pulse Audio fixes (appropriate to your version of Ubuntu). In other words read it all!

[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

---

### Post by 2hot6ft2 on 2008-12-06
That is funny to read...:o The commands are in terminal.

1. Create /etc/ld.so.conf.d/alsa32.conf with the following contents:
/usr/lib32/alsa-lib
translation:

sudo gedit /etc/ld.so.conf.d/alsa32.conf
then copy and paste this into it
/usr/lib32/alsa-lib
save and close

2. Create /etc/ld.so.conf.d/alsa64.conf with the following contents:
/usr/lib/alsa-lib
translation:

sudo gedit /etc/ld.so.conf.d/alsa64.conf
then copy and paste this into it
/usr/lib/alsa-lib
save and close

3. sudo ldconfig
this one is pretty obvious in terminal use
sudo ldconfig

4. Open /usr/share/alsa/pulse.conf in the editor and remove the "/usr/lib/alsa-lib/" prefix from the libasound_module_conf_pulse.so file.
translation:

sudo gedit /usr/share/alsa/pulse.conf
this time delete
/usr/lib/alsa-lib/
from the line that says
/usr/lib/alsa-lib/libasound_module_conf_pulse.so

Save and close, done

Just checked and the folders do exist so that should do it according to those instructions.


More pulse audio info here [http://forumubuntusoftware.info/viewtopic.php?f=46&t=2179&start=0&st=0&sk=t&sd=a](http://forumubuntusoftware.info/viewtopic.php?f=46&t=2179&start=0&st=0&sk=t&sd=a)

---

### Post by adult swim on 2008-12-06
i would try kansasnoobs advice **first** but if you get stuck heres the directions you were asking for
1) from a terminal, run ```
gksudo gedit /etc/ld.so.conf.d/alsa32.conf
``` paste in ```
/usr/lib32/alsa-lib
``` save and close the file
2) from a terminal, run ```
gksudo gedit /etc/ld.so.conf.d/alsa64.conf
``` paste in ```
/usr/lib/alsa-lib
``` save and close the file
3) in the terminal run ```
sudo ldconfig
```
4) mine is a bit different so i cant really confirm but ill draw you a picture of what the instructions say.  run from a terminal ```
gksudo gedit /usr/share/alsa/pulse.conf
``` and then remove the highlighted text in the picture.  close and save the file.

---

### Post by ugm6hr on 2008-12-06
I have no idea what this does, but I have prepared a walk-through of exactly what to do (as described in your link).  I have given things to enter in Terminal within the Code boxes, and entries within files as quotes.

```
gksudo gedit /etc/ld.so.conf.d/alsa32.conf
```

This will open a new text file.  Copy and paste the following into the file and click Save from the menu:

> /usr/lib32/alsa-lib

```
/etc/ld.so.conf.d/alsa64.conf
```

This will open a new text file.  Copy and paste the following into the file and click Save:

> /usr/lib/alsa-lib

```
sudo ldconfig
```
Enter your password and press Enter

```
gksudo gedit /usr/share/alsa/pulse.conf
```

Use the "Find and Replace option" as follows:
Find: /usr/lib/alsa-lib/libasound_module_conf_pulse.so
Replace: libasound_module_conf_pulse.so

According to the instructions, there should only be 1 instance.  Then click Save.

As explained, I don't understand what is being done here - so everything done at own risk.

EDIT: In fact, I'm clearly way to slow!

---

### Post by SRG8 on 2008-12-06
K THNX A LOT that read although long (you werent kidding=P) was actually very helpful.
I tried first shot what they recommended for skype and now its working beautifully again so thanks for all the help =D

---

