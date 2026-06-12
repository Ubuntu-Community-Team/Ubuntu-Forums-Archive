---
title: "Wont reboot"
date: 2011-07-19
forum: New to Ubuntu
---

### Post by DarrenMR415 on 2011-07-19
Did this last night, which Ive done once before without issue,

```
If you&#8217;re running Ubuntu 10.10 or 11.04 on laptop, you might get a  problem that
fn key combination to change screen brightness is not  working. Here&#8217;s a solution for 
nvidia laptop with this problem:

 First edit xorg.conf in terminal with the command:
 sudo gedit /etc/X11/xorg.conf And then find the Section &#8220;Device&#8221; and add the bold line.[INDENT]Section &#8220;Device&#8221;
Identifier    &#8220;Default Device&#8221;
Option     &#8220;NoLogo&#8221;     &#8220;True&#8221;
**Option &#8220;RegistryDwords&#8221;    &#8220;EnableBrightnessControl=1&#8243;**
EndSection
[/INDENT]And now your brightness control is working in next login!

```Now my laptop wont finish booting up.  It stops at the Ubuntu screen with the 5 red dots, and just sits there doing nothing.

---

### Post by _0R10N on 2011-07-19
Can you switch to any tty? If so, please post the output of /var/log/syslog

Regards!

---

### Post by Bucky Ball on 2011-07-19
Can you boot into the recovery kernel? If so you could choose root shell at the options, take that line out again and reboot.

---

### Post by DarrenMR415 on 2011-07-19
> **_0R10N said:**
> Can you switch to any tty? If so, please post the output of /var/log/syslog

Regards!

> **Bucky Ball said:**
> Can you boot into the recovery kernel? If so you could choose root shell at the options, take that line out again and reboot.

If there was an "Absolutely useless talk" subsection, I would have posted this there.  Can you please instruct on how to do these things?

---

### Post by _0R10N on 2011-07-19
What I suggested is that when you rich the screen where your system seems to halt, press CTRL+ALT+F1. Then type in your username and password, and execute:

```
cat /var/log/syslog
```

What Bucky Ball suggests is that you select other line to boot up from your grub list when the system starts.

Regards!

---

### Post by DarrenMR415 on 2011-07-19
> **_0R10N said:**
> What I suggested is that when you rich the screen where your system seems to halt, press CTRL+ALT+F1. Then type in your username and password, and execute:

```
cat /var/log/syslog
```What Bucky Ball suggests is that you select other line to boot up from your grub list when the system starts.

Regards!

I dont get far enough to choose from the grub list.

CTRL-ALT-F1 does nothing

---

### Post by _0R10N on 2011-07-19
Wait, if you get to the dots screen, then you had to pass the grub screen, since it's one of the first things required to start up you system. Maybe it has little delay, so you don't get to see it.

---

### Post by DarrenMR415 on 2011-07-19
Do you mean where it says press F2 to enter system menu, F12 for boot menu?

---

### Post by _0R10N on 2011-07-19
No, that's an option for entering your BIOS configuration. Could you post a pic of the last screen you get to see?

---

### Post by DarrenMR415 on 2011-07-19
Its hard to tell, but the cursor in the top left starts blinking at about 10 seconds into the video.  The the Ubuntu screen stays there.  I let it sit last night for atleast 20 minutes and nothing.  And the cannot reserve MMIO region thing has been there for a really long time.

[[IMG]http://i70.photobucket.com/albums/i120/icantthink4155/th_VIDEO0002.jpg[/IMG]]("http://s70.photobucket.com/albums/i120/icantthink4155/?action=view&current=VIDEO0002.mp4")

---

### Post by Bucky Ball on 2011-07-19
Do you get to a menu where you can choose which kernel to use (or another operating system if you have one installed). Second on the list should be the 'Recovery kernel'. 

If you don't get that screen, try hitting shift (or it could be escape) at boot. That should take you to a menu.

---

### Post by DarrenMR415 on 2011-07-19
That video is from hitting the power button until it locks up.  You see everything I see.  Suggest a point in which I should do these things.  


Edit: switched between hitting esc and shift and got it started in low graphics mode.  Any way to debug, or view a log or something?

---

### Post by DarrenMR415 on 2011-07-19
This seems to have fixed my issue.  I can restart without it locking up now.  But once again I cannot adjust the brightness.

---

### Post by Bucky Ball on 2011-07-19
```
Section “Device”
Identifier    “Default Device”
Option     “NoLogo”     “True”
**Option “RegistryDwords”    “EnableBrightnessControl=1&#8243;**
EndSection
```From your first post. Boot in low graphics and take that line in bold out again, exit, reboot.

---

### Post by DarrenMR415 on 2011-07-19
Its already gone.  I just want to adjust my stinking brightness, its way too bright for nighttime usage.

---

### Post by Bucky Ball on 2011-07-19
Not in Gnome right now but have you tried right clicking on the top panel and adding the brightness applet?

---

### Post by DarrenMR415 on 2011-07-19
> **Bucky Ball said:**
> Not in Gnome right now but have you tried right clicking on the top panel and adding the brightness applet?

Have that, has no effect.

---

