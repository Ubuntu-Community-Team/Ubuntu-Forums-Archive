---
title: "user account settings"
date: 2009-10-15
forum: New to Ubuntu
---

### Post by igapo on 2009-10-15
I am a teacher new to xubuntu.  My computers were set up for me and I would like to have my student account autohide the taskbar at the bottom.  Is there a way to access the "settings" as an administrator when I am logged in as a student?  Thanks.

---

### Post by mikewhatever on 2009-10-16
Hi there, I don't think autohiding the bottom panel is an admin task. It's a user setting, similar to changing the wallpaper. You should be able to access the setting by right clicking on the panel.

---

### Post by igapo on 2009-10-16
Thanks mikewhatever.  I have tried to right click, but all it does is say info about "xfce panel" without any settings option.  Because these are used by middle school students, all priveledges in student account have been restricted so minimal options are available.  Any additional thoughts would be greatly appreciated.

---

### Post by OffAxis on 2009-10-16
So 'Customize Panel' isn't an option by right clicking on the panel? The 'Autohide' checkbox is on Customize's pop-up menu.

It's also under **Applications-->Settings-->Panel** (Autohide checkbox)

If neither of those is an option, the actual setting is in **/home/<username>.config/xfce4/panel/panels.xml**
It's line 13. Change the value of 'Autohide' from 0 to 1.

If you manually edit the file like this, you CANNOT have panel running (any changes you make will be ignored and overwritten).
So you'll need to boot to a shell or drop to a shell / kill gdm, whatever to get the setting to stick.

---

### Post by mikewhatever on 2009-10-16
I am not very familiar with xfce, but the problem seems to be the fact that whoever set things up have also restricted students making changes to the interface. If that's the case, you can't customize the panel.

---

### Post by OffAxis on 2009-10-16
> whoever set things up have also restricted students making changes to the interface.
True, but if you've got an administrator account then you can pretty much legitimately do  do whatever you want (unless there's a startup script that pulls configuration values from a server you don't have access to. Then you'd have to do questionable things that wouldn't be worth it). 


There's also a kiosk mode that these machines may have been configured as.
You can read up on that here:

file:///usr/share/xfce4/doc/C/xfce4-panel.html#panel-kiosk

If kiosk mode IS configured then your group or admin username will need to be mentioned in the kioskrc file to be able to edit the panel (from that group or username login)

Otherwise, 
To expound on my previous post...

Logon to your student account

Drop to a shell (**Ctrl+Alt+F1**)

Stop gdm  
```
/etc/init.d/gdm stop
```

edit the file 
```
nano /home/<student account username>/.config/xfce4/panel/panels.xml
```

go to line 13 and change the autohide value to 1

Exit nano (**Ctrl+X, Y, Enter**)

Restart gdm

if you have an admin account it's
```
sudo /etc/init.d/gdm start
```

if not just
```
logout
```
and hit the reset button.

As mentioned before, this is a user setting, not a system-wide setting, so as long as kiosk mode doesn't hamper your efforts, chances are this panel property is modifiable.

---

### Post by igapo on 2009-10-16
Thanks Offaxis, My permissions have been denied access to the xfce4 settings you mentioned.  Would I have to use the gksudo command to get to it?  I found the xfce4 setting under /usr/bin but it will not let me do anything to it, I assume because the owner is "root." How do I access that with my admin priviledges?  Thanks.

---

### Post by Sarmacid on 2009-10-16
You need to use sudo as in```
sudo /etc/init.d/gdm stop
```

---

### Post by OffAxis on 2009-10-16
> xfce4 setting under /usr/bin
The bin folder contains the actual code for the shell commands; for example **ls** for *list contents.*

What you want is the configuration file, which should be housed in your account's home folder (in that hidden sub-folder previously mentioned).

If your student account does not have ownership over that configuration file just precede the command with **sudo **(**gksudo **is for graphical programs, sudo is for command line) to edit it as root.

```
sudo nano /etc/home/<student user name>./config/xfce4/panel/panels.xml
```

---

### Post by igapo on 2009-10-16
Very good directions, unfortunately, it did not work.  I rechecked the autohide settings and it is still 1 after a restart; I even checked the file manager panel.xml file just to be sure it was 1.  Let me back up a little and tell you what I've noticed:  (1)  in usr/bin/xfce4-settings-manager, I can open and customize "appearance, desktop, mouse, and all other items in the window except the "panel."  (2)  The panel on the desktop will not let me right click on any of the icons (open office and firefox) so I don't seem to be able to customize those items either.  Could it have anything to do with "authorizations" set as administrator?  My student desktop also looks different than the admin; there is not top panel, only a large bottom one that gets in the way of buttons, but I can slide it up and down.

Thank you so much for your patience and time!

---

