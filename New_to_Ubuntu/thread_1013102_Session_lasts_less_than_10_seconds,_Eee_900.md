---
title: "Session lasts less than 10 seconds, Eee 900"
date: 2008-12-16
forum: New to Ubuntu
---

### Post by MadCatmkII on 2008-12-16
Hello

I recently installed xubuntu 8.10 on an Eeepc 900. I installed the array kernel and the eee-control applet-thinga-majig. After that all seemed quite well, so I removed the standard kernels. And still all seemed well. But today when I started my eee and logged in I was met by a garbled background and a dialog with the following text:

> Your session only lasted less than 10 seconds.

And it suggests I might be out of diskspace, and gives me a look at the xsession error-log, posted below:

> 
/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=sv_SE.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to
/etc/X11/xinit/xinput.d/default.
/usr/bin/startxfce4: X server already running on display :0
Agent pid 5116
** Message: Querying XF86Misc extension
** Message: XF86Misc extension found
** Message: Querying Xkb extension
** Message: Xkb extension found
** Message: Querying XINPUT extension
** Message: XINPUT extension found
** Message: Querying Xkb extension
** Message: Xkb extension found
** Message: another SSH agent is running at: /tmp/ssh-PNwJEN5115/agent.5115

** (update-notifier:5150): WARNING **: already running?


** (nm-applet:5154): WARNING **: <WARN>
applet_dbus_manager_start_service(): Could not acquire the
NetworkManagerUserSettings service as it is already taken.  Return: 3


(nm-applet:5154): GLib-GObject-CRITICAL **: g_object_unref: assertion
`G_IS_OBJECT (object)' failed

(xfwm4:5132): libxfcegui4-WARNING **: ICE I/O Error

(xfwm4:5132): libxfcegui4-WARNING **: Disconnected from session manager.
Segmentation fault
Agent pid 5116 killed


I checked and I have almost 13gb free on disk. I also tried to do a restore-session xfix, suggested in another thread about 10 second sessions, but no go. I also checked the ownership of ICEauthority file and the dmrc file, but I own both it seems. Overall it seems this error can mean all sorts of things :confused:

Please help me and my poor eee!

---

### Post by taurus on 2008-12-16
Just to double check, what's the output of this command from a terminal?

```
df -h
```

---

### Post by MadCatmkII on 2008-12-16
I'm posting from another computer, so I'd rather not type out the output of all sex mount-points, but sda1 uses 18% and has 12gb free (I misremembered) while the rest uses 0% (3) or 1% (2)

Edit:

Apologies for being a wee bit rude. I just discovered that if I shut the computer down and start it up again and login I can use it as long as I don't click ok in the dialog. However when I do X restarts and logging on after that only gives another restart of X. 

output from df:

> 
/dev/sda1              15G  2,5G   12G  18% /
tmpfs                 501M     0  501M   0% /lib/init/rw
varrun                501M  108K  501M   1% /var/run
varlock               501M     0  501M   0% /var/lock
udev                  501M  2,7M  498M   1% /dev
tmpfs                 501M     0  501M   0% /dev/shm


---

### Post by curtistee on 2008-12-17
Thanks for the workaround; much appreciated.
I'm seeing the same thing on my Shuttle XPC (with plenty of free disk space). I'd much rather see a "proper" solution, however.

---

### Post by uniqueumang on 2008-12-17
I had same problem problem at university when 7.04 was released. University ssupport staff asked me to delete all the hidden files from user directory and that solved the problem. you have to log into command prompt (ctrl+alt + f1).Those hidden files are recreated when you log on. so its no biggie.


/* I am currently in windows so can't tell the exact command */

---

### Post by uniqueumang on 2008-12-17
As I promised , I can tell the exact command now . 
** WARNING :: If you do not follow properly , You may end up loosinmg all your files and folder from your home directory .

1ST STEP : PRESS CTRL + ALT+ F1
2ND STEP: ENTER CREDENTIALS
3RD STEP: cd ~/             
4TH STEP : rm -rf .??*   
5TH STEP: PRESS CTRL + ALT + F7

That's it. Login normally. :)

---

### Post by MadCatmkII on 2008-12-17
Thanks, I'll test that once I get home! Just for curiosity I'll delete the hidden files one by one and see which one solves the problem.

---

### Post by MadCatmkII on 2008-12-17
Removing the hidden files didn't help. But since the university support example included recursive removal, I decided to start axing hidden folders as well. After having removed .cache and trying to login it now just sits there, furiously blinking the HDD LED at me. At least I think it was the .cache directory, I can't switch over to the terminal to look at my bash-history.

I'm pretty much ready to use the standard windows solution (reinstall), but any further suggestions would still me nice.

---

### Post by uniqueumang on 2008-12-18
Oh !! I actually re contacted university but they are not happy to help as it is outside uni computers problem. 

If there is nothing important , then probably reinstall. if something is important , then copy with shell , and then reintall. 


I think I was able to also login in KDE. Well uni computers got both gnome and kde. I am not sure how to install KDE from bash. I also installed KDE last year and it was 500mb . 

Anyway Best of luck.

---

### Post by M0GEJ on 2008-12-20
I am having the same problem with my laptop at the moment. Have tried-
> **uniqueumang said:**
> As I promised , I can tell the exact command now . 
** WARNING :: If you do not follow properly , You may end up loosinmg all your files and folder from your home directory .

1ST STEP : PRESS CTRL + ALT+ F1
2ND STEP: ENTER CREDENTIALS
3RD STEP: cd ~/             
4TH STEP : rm -rf .??*   
5TH STEP: PRESS CTRL + ALT + F7

That's it. Login normally. :)
but can't get past entering in my "credentials". Any other ideas?

---

