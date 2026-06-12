---
title: "How do I reset onboard on-screen keyboard layout"
date: 2009-02-21
forum: New to Ubuntu
---

### Post by getut on 2009-02-21
Please help.. I am using onboard. The Ubuntu software that creates an on-screen keyboard.

Somehow or another I have gotten the thing into a non-standard layout. I would like to blow away the settings so that it starts with the default keyboard layout again but cannot find where to do this or how to switch back to default layout in any fashion.

The onboard wiki isn't any help either. It neither says where it stores its settings or how to change keyboard layouts. It says on the wiki that it can be done, but not actually how to do it.

I'm using onboard with a 3d mouse on a home theater machine. I'd really hate to have to reinstall just to fix onboard. I've even removed it with sudo apt-get remove --purge onboard and then reinstalled. But the old, bad settings remained.

---

### Post by jerrrys on 2009-02-23
"Somehow or another I have gotten the thing into a non-standard layout. I would like to blow away the settings so that it starts with the default keyboard layout again but cannot find where to do this or how to switch back to default layout in any fashion"

how bout just reboot your system?

---

### Post by jerrrys on 2009-02-23
nevermind

---

### Post by jerrrys on 2009-02-23
?? [http://www.linuxquestions.org/questions/ubuntu-63/where-does-ubuntu-store-application-files-705209/](http://www.linuxquestions.org/questions/ubuntu-63/where-does-ubuntu-store-application-files-705209/)

---

### Post by getut on 2009-02-23
No.. its not user bin. It would have to be somewhere that non-privileged user can write to because I don't have to "sudo" to run onboard.

Most apps save config in users home folder like so... firefox saves settings to .mozilla, wine saves to .wine etc. But I can't find where the settings for onboard are saved.

After a fresh install it looks like this (which is what I want).
[IMG]https://wiki.ubuntu.com/Accessibility/Projects/onBoard?action=AttachFile&do=get&target=onboard-alpha.png[/IMG]

Mine looks like this and I can't switch it back.
[IMG]https://wiki.ubuntu.com/Accessibility/Projects/onBoard/layouts?action=AttachFile&do=get&target=sok-scan-base.png[/IMG]

---

### Post by rust612000 on 2009-03-02
the grey, blue, and red squares are for different buttons, click on the red square and click settings there is a layout menu there see if that helps

---

### Post by pave_FM on 2009-03-11
Try:
Go to System-Preferences-Main Menu
In the left panel choose Preferences, than in the right panel choose onBoard Settings, than close. Go to the System-Preferences-onBoard Settings and in the Layouts tab choose Default, than close.
That's it.

---

### Post by nilsto on 2009-05-11
Did you solve the problem?

---

### Post by aixlo on 2009-11-13
Press Alt-F2 and run gconf-editor. Navigate to apps/onboard
disable scanning and change the layout_filename from scan.sok to default.sok
There you are done. 
;)

---

### Post by prinspatrick on 2010-11-06
just open onboard and click in the rectangle on the right bottom corner

then you can reach the settings

---

