---
title: "File Manager Autospawns at startup + gvfsd trash uses 100% of CPU"
date: 2010-12-29
forum: New to Ubuntu
---

### Post by notjingo on 2010-12-29
I have seen some of the same issues come up in other threads and have attempted without success the various fixed suggested in those threads.  I was advised to open a new thread for this issue since the other threads were marked as [solved].

I am running Ubuntu 10.04 64-bit. 
I am using gnome 1.2.28+1ubuntu3 and Nautilus 1:2.31.1-ubuntu2~ppa92

After logging in Nautilus spawns thousands of instances for a couple minutes. My panel fills up with "Starting File Manager" indicators, which never seem to finish loading. They fill the panel and then finally disappear, or I can close them with ```
 killall nautilus
```. Concurrently, gvfsd-trash is reported to be using up 100% of the CPU.

After I close nautilus, I can reopen it and everything is back to normally working fine, including the gvfsd-trash. When I first encountered this error, the "Starting File Manager" indicators would continue appearing periodically (although in fewer numbers), but still failing to open and then disappearing after a few minutes. Apparently this doesn't happen anymore and I only experience the symptoms right after I login.


I'm not sure if this problem started occurring after a specific update, but I don't recall changing any settings before it began to happen. I've read all the threads I can on this but no solutions have worked for me. This problem seems to be pretty widespread though, and across several versions of Ubuntu.

I have tried the following things:

[LIST]
[*]Uninstalled Ubuntu One client, as per this thread 
[http://www.browse24h.com/index.php?q...Y2MDM0Mg%3D%3D](http://www.browse24h.com/index.php?q...Y2MDM0Mg%3D%3D)
Did not help.

[*]I have made the following changes to /usr/share/applications/nautilus.desktop
```
X-GNOME-AutoRestart=false # changed from =true
AutostartCondition=GNOME /apps/nautilus/preferences/show_desktop
``` # added this line
As per this thread [http://ubuntuforums.org/showthread.p...+spawns&page=2](http://ubuntuforums.org/showthread.p...+spawns&page=2)
Also did not help.

[*]I do not have the line mentioned at the end of this thread either (in the xorg.conf)
[https://bbs.archlinux.org/viewtopic.php?id=69282](https://bbs.archlinux.org/viewtopic.php?id=69282)
[/LIST]

[*]This thread discusses the link with gvfsd-trash
[https://bugzilla.gnome.org/show_bug.cgi?id=553776](https://bugzilla.gnome.org/show_bug.cgi?id=553776)

While the error is occuring, the top three processes running by memory usage are gvfsd-trash, dbus-daemon, and nautilus.

I've noticed that my swap reports 0% usage at any given time, even when I've been running a lot of memory intensive programs. (although I have 6 gigs of ram which still should be a lot.) This may be unrelated, but perhaps there is an issue with the way I am mounting my drives and memory? This seemed to be implied in one of the threads I read.

I'm pretty new to Ubuntu so any guidance on this would be a great help. From the several forum threads I've seen around I know this is a pretty widespread issue and has happened to many users. Unfortunately most of those forum threads are inconclusive or their solutions have not worked for me. 

I'd also appreciate some instruction on how to grab diagnostics and system specs to post here for a better understanding of whats going on in the system.


EDIT: After I killall nautilus, and re-start it by entering ```
nautilus
``` in the terminal, it opens and works fine but I get the following message:
```

Initializing nautilus-gdu extension

(nautilus:2295): Gtk-WARNING **: Undo: missing action Undo

(nautilus:2295): Gtk-WARNING **: Redo: missing action Redo

(nautilus:2295): Gtk-WARNING **: Reset to Defaults: missing action Reset to Defaults

(nautilus:2295): GdkPixbuf-CRITICAL **: gdk_pixbuf_format_get_name: assertion `format != NULL' failed
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

```
It doesn't look like its related, but just thought I'd post it in case.

---

### Post by notjingo on 2011-01-04
Anyone?

---

### Post by ravi84m on 2011-01-04
I am having the same issue after a recent update.

---

### Post by notjingo on 2011-01-05
It seems like this issue keeps popping up. I've read a bunch of threads that had identified this bug, even from older versions of Ubuntu (8, 9) and had resolved it, but it seems it's back.

I think it initially started when I set my desktop to remember a session to reload on startup the programs I previously had open. Still haven't been able to resolve this...

---

### Post by altor on 2011-01-08
Try to completly remove ubuntuone:

```
1. Quit the Ubuntu One client
2. $ sudo rm -rf ~/.local/share/ubuntuone
3. $ rm -rf ~/.cache/ubuntuone
4. $ rm -rf ~/.config/ubuntuone
5. $ mv ~/Ubuntu\ One/ ~/Ubuntu\ One_old/
6. Open Applications->Accessories->Passwords and Encryption Keys, go to the Passwords tab, delete the Ubuntu One token
7. $ sudo apt-get purge ubuntuone-client* python-ubuntuone-storage*
```

Not sure but maybe helps

---

### Post by amjjawad on 2011-01-08
[http://ubuntuforums.org/showthread.php?t=1642561&highlight=100%25+CPU](http://ubuntuforums.org/showthread.php?t=1642561&highlight=100%25+CPU)

Hope this will help.

---

### Post by ravi84m on 2011-01-10
I solved my issue... First I insalled  Thunar ```
[https://help.ubuntu.com/community/DefaultFileManager](https://help.ubuntu.com/community/DefaultFileManager)
```[U]
Then reboot and revert back to nautilus.
[/U]

---

### Post by amjjawad on 2011-01-11
> **ravi84m said:**
> I solved my issue... First I insalled  Thunar ```
[https://help.ubuntu.com/community/DefaultFileManager](https://help.ubuntu.com/community/DefaultFileManager)
```[U]
Then reboot and revert back to nautilus.
[/U]

Well Done :)

[IMG]http://ubuntuforums.org/picture.php?albumid=2161&pictureid=7263[/IMG]

---

### Post by Anon Customer on 2011-01-13
Note the purging the elementary ppa helped for me on this issue:

[http://ubuntuforums.org/showthread.php?t=1600397](http://ubuntuforums.org/showthread.php?t=1600397)

---

### Post by notjingo on 2011-01-20
Wow this is driving me nuts. I am still unable to resolve this.

- I followed @altor's instructions to completely remove ubuntuone.
Problem persisted.

- @ravi84m. I set Thunar as the default file manager, then rebooted and reverted back to nautilus.
Problem persisted.

- @Anon Customer. I purged the elementary ppa.
Problem persisted.

Thanks for your input so far. Does anyone have any other ideas? What is even causing this?

---

### Post by notjingo on 2011-01-20
Wow this is driving me nuts. I am still unable to resolve this.

- I followed @altor's instructions to completely remove ubuntuone.
Problem persisted.

- @ravi84m. I set Thunar as the default file manager, then rebooted and reverted back to nautilus.
Problem persisted.

- @Anon Customer. I purged the elementary ppa.
Problem persisted.

Thanks for your input so far. Does anyone have any other ideas? What is even causing this?

---

### Post by notjingo on 2011-01-20
Wow this is driving me nuts. I am still unable to resolve this.

- I followed @altor's instructions to completely remove ubuntuone.
Problem persisted.

- @ravi84m. I set Thunar as the default file manager, then rebooted and reverted back to nautilus.
Problem persisted.

- @Anon Customer. I purged the elementary ppa.
Problem persisted.

Thanks for your input so far. Does anyone have any other ideas? What is even causing this?

---

### Post by notjingo on 2011-01-20
Wow this is driving me nuts. I am still unable to resolve this.

- I followed @altor's instructions to completely remove ubuntuone.
Problem persisted.

- @ravi84m. I set Thunar as the default file manager, then rebooted and reverted back to nautilus.
Problem persisted.

- @Anon Customer. I purged the elementary ppa.
Problem persisted.

Thanks for your input so far. Does anyone have any other ideas? What is even causing this?

---

### Post by notjingo on 2011-01-20
I tried every solution that was posted in this thread and still could not solve this problem.

**BUT THEN...**
I took a different approach. I went to* System-> Preferences->Startup Applications* and clicked on the "Options tab." Then, I clicked on "Remember Currently Running Applications." 

**PROBLEM GONE.**

I had a feeling that the problem began right after I had clicked that originally a while back. What must have been going on was that I had been viewing a non auto-mounting device at the time. So I'm assuming at startup, nautilus was trying to open this device in some way but it couldn't because it wasn't mounted, causing nautilus to freak out and retry a billion times. 

So ultimately for me it was a really simple solution... Let's see if it holds.

For now we can set this thread to [SOLVED].

---

### Post by dmuir on 2011-02-15
I removed python-nautilus, and the problem went away for me.
If it crops up again, run:
```
tail /var/log/messages
```

And it might give some hints as to why nautilus is crashing.

---

### Post by jeeves on 2011-09-26
I ran into the this same problem on 11.04 Natty with the classic gnome 2 desktop.  What touched it off was was monkeying with gconf-editor to make the trash bin visible on the desktop. 

I would repeatedly use **killall nautilus** to stop the runaway avalanche of spawning file browsers. Once I killed off all instances of nautilus, I attempted to launch it from the command line and got the following message:

[I]Eel:ERROR:eel-preferences.c:117:preferences_gconf_value_get_string: assertion failed: (value->type == GCONF_VALUE_STRING)
Aborted[/I]

**So the solution for me turned out to be to simply launch gconf-editor again and go to *Apps > nautilus > desktop* and undo the checkmark on "trash_icon_visible"**

---

