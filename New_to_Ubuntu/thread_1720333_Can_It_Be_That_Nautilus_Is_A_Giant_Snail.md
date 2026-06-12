---
title: "Can It Be That Nautilus Is A Giant Snail?"
date: 2011-04-03
forum: New to Ubuntu
---

### Post by widda on 2011-04-03
I think I have searched everywhere except applying under the  Freedom of Information Legislation 
I have a PC 80Gb /1.5 GbRAM /2.8Ghz Dell,/ Lucid Lynx /Gnome,clean install over XP.
And a Vaio 120Gb ext USB drive containing copies of all my files from recently dead Dell laptop Lucid Lynx Gnome.
I of course want to transfer them back to new PC, so I can keep working.
BUT I can't, TOO SLOW
BUT, I used to use this drive in conj. with now-dead lappy.
A lot of talk about the forums suggests it's just a wee bug that may get attended to one day...
BUT this doesn't make sense. There's no OS without a functioning file manager, is there???
Unless I do it file by file, I get things like this (see **attachment**), which promises approximately 2 years transfer time for 1 folder of 4Mb. I have serious doubts that it would happen in that time, it goes a little darkscreen in first 10 minutes, looks preoccupied.
Now if my car will not go faster than 1 x.p.h., there is a FINITE number of possible causes.
There must be in this case a FINITE number of possibilities.    ?
I will explore them all.
Thanks anyone...

---

### Post by matt_symes on 2011-04-03
Hi

I love that screen shot. That amount of time would tax my patience.

Have you tried copying the from the terminal ?

Are there any errors in your ~/.xsession-errors file concerning nautilus ?

> clean install over XP

This is a Wubi install or install to partition ? 

You have checked the drive for errors ? What is the file system on the drive ?

You have checked the drive SMART status ?

That's where i would start to look.

Kind regards

---

### Post by grahammechanical on 2011-04-03
If your screen is going darkscreen then something is using up all your RAM and CPU power. Do not blame the file manager. It is just a program. Yesterday I used Nautilus to burn a 4GB ISO image to DVD. It did it in minutes. And that included blanking the disc before transferring the data. And it was not a simple action of copying one large file.

From the image you post I would say that the copying process has not even started. 

Regards.

---

### Post by widda on 2011-04-03
For 'Giant Snall' read 'Giant Sna**i**l'

---

### Post by widda on 2011-04-03
> **matt_symes said:**
> Hi

I love that screen shot. That amount of time would tax my patience.
**It's great hey!**
Have you tried copying the from the terminal ?
**No I will look into that**
Are there any errors in your ~/.xsession-errors file concerning nautilus ?
**Never heard of but will look**


This is a Wubi install or install to partition ? 
**I had a wubi install beside shipped XP, but wiped the lot for iso cd install, here is snapshot afterward **
You have checked the drive for errors ? **Dont know what that means**What is the file system on the drive ?** I know NTFS and FAT and will try find**
 
You have checked the drive SMART status ?
**Dont know what that means**

That's where i would start to look.

Kind regards
**thanks**, **widda**

---

### Post by matt_symes on 2011-04-03
Hi

> **grahammechanical said:**
> If your screen is going darkscreen then something is using up all your RAM and CPU power. Do not blame the file manager. It is just a program. Yesterday I used Nautilus to burn a 4GB ISO image to DVD. It did it in minutes. And that included blanking the disc before transferring the data. And it was not a simple action of copying one large file.

From the image you post I would say that the copying process has not even started. 

Regards.

This is an excellent suggestion as well.

Kind regards

---

### Post by widda on 2011-04-03
> **grahammechanical said:**
> if your screen is going darkscreen then something is using up all your ram and cpu power. Do not blame the file manager. From the image you post i would say that the copying process has not even started. 
**ok , ram and cpu i can do 'top' command**
regards.
**w**

---

### Post by widda on 2011-04-03
oh, prob with top command, may take 3 weeks for terminal to open. will try

---

### Post by widda on 2011-04-03
here's top shot
for me, not informative, the top cpu percentage doesnt change much

---

### Post by widda on 2011-04-03
but when I thought I had killed the file transfer, by x-ing the window, it didnt. a thing popped up saying Cant Do this File - Skip?, I said Skip.
so presumably it's still going on.
dont know how to find file transfer monitor again

---

### Post by widda on 2011-04-03
or how to stop it and use terminal (after I study up how)
or whether I should !
it's still going here's another copy error

---

### Post by widda on 2011-04-03
Xsession file errors

/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_AU.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
GNOME_KEYRING_CONTROL=/tmp/keyring-Mgkpr1
GNOME_KEYRING_CONTROL=/tmp/keyring-Mgkpr1
SSH_AUTH_SOCK=/tmp/keyring-Mgkpr1/ssh
GNOME_KEYRING_CONTROL=/tmp/keyring-Mgkpr1
SSH_AUTH_SOCK=/tmp/keyring-Mgkpr1/ssh

(polkit-gnome-authentication-agent-1:1292): GLib-GObject-WARNING **: cannot register existing type `_PolkitError'

(polkit-gnome-authentication-agent-1:1292): GLib-CRITICAL **: g_once_init_leave: assertion `initialization_value != 0' failed
** (nm-applet:1294): DEBUG: old state indicates that this was not a disconnect 0
Unable to find a synaptics device.
Initializing nautilus-open-terminal extension
** Message: Initializing gksu extension...
Initializing nautilus-gdu extension
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/blueman/plugins/AppletPlugin.py", line 105, in _load
    self.on_load(applet)
  File "/usr/lib/python2.6/dist-packages/blueman/plugins/applet/PulseAudio.py", line 115, in on_load
    if int(version.split(".")[2]) < 15:
ValueError: invalid literal for int() with base 10: '21-63-gd3efa-dirty'
WARNING: Application calling GLX 1.3 function "glXCreatePixmap" when GLX 1.3 is not supported!  This is an application bug!
Starting gtk-window-decorator
I/O warning : failed to load external entity "/home/stan/.compiz/session/10ba8d53b25ee79b37130182301137129400000011990036"
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

WARNING: Application calling GLX 1.3 function "glXDestroyPixmap" when GLX 1.3 is not supported!  This is an application bug!
** (nm-applet:1294): DEBUG: foo_client_state_changed_cb
** (nm-applet:1294): DEBUG: foo_client_state_changed_cb
** (update-notifier:1546): DEBUG: Skipping reboot required
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

[Info  20:13:16.959] Initializing DBus
[Info  20:13:17.185] Initializing Mono.Addins
[Info  20:13:17.815] Starting new FSpot server (f-spot 0.6.1.5)

(f-spot:1773): Gtk-WARNING **: gtk_menu_attach_to_widget(): menu already attached to GtkMenuItem
[Info  20:13:19.179] Hack for gnome-settings-daemon engaged

(f-spot:1773): GdkPixbuf-WARNING **: GdkPixbufLoader finalized without calling gdk_pixbuf_loader_close() - this is not allowed. You must explicitly end the data stream to the loader before dropping the last reference.
value = f-spot version 0.6.1.5 len = 22
value = 2011:04:03 20:13:56 len = 19
Saved 14740 bytes
value = f-spot version 0.6.1.5 len = 22
value = 2011:04:03 20:13:56 len = 19
value = f-spot version 0.6.1.5 len = 22
value = 2011:04:03 20:13:56 len = 19
Saved 14740 bytes
[Info  20:13:56.405] Exiting
[Info  20:15:26.243] Initializing DBus
[Info  20:15:26.453] Initializing Mono.Addins
[Info  20:15:26.706] Starting new FSpot server (f-spot 0.6.1.5)

(f-spot:1806): Gtk-WARNING **: gtk_menu_attach_to_widget(): menu already attached to GtkMenuItem
[Info  20:15:27.621] Hack for gnome-settings-daemon engaged

(f-spot:1806): GdkPixbuf-WARNING **: GdkPixbufLoader finalized without calling gdk_pixbuf_loader_close() - this is not allowed. You must explicitly end the data stream to the loader before dropping the last reference.
[Info  20:15:32.971] Exiting
[Info  20:15:48.580] Initializing DBus
[Info  20:15:48.774] Initializing Mono.Addins
[Info  20:15:49.030] Starting new FSpot server (f-spot 0.6.1.5)

(f-spot:1822): Gtk-WARNING **: gtk_menu_attach_to_widget(): menu already attached to GtkMenuItem
[Info  20:15:50.003] Hack for gnome-settings-daemon engaged

(f-spot:1822): GdkPixbuf-WARNING **: GdkPixbufLoader finalized without calling gdk_pixbuf_loader_close() - this is not allowed. You must explicitly end the data stream to the loader before dropping the last reference.
value = f-spot version 0.6.1.5 len = 22
value = 2011:04:03 20:17:03 len = 19
Saved 17973 bytes
value = f-spot version 0.6.1.5 len = 22
value = 2011:04:03 20:17:03 len = 19
value = f-spot version 0.6.1.5 len = 22
value = 2011:04:03 20:17:03 len = 19
Saved 17973 bytes
[Info  20:17:03.645] Exiting
[Info  20:20:29.643] Initializing DBus
[Info  20:20:29.853] Initializing Mono.Addins
[Info  20:20:30.147] Starting new FSpot server (f-spot 0.6.1.5)

(f-spot:1856): Gtk-WARNING **: gtk_menu_attach_to_widget(): menu already attached to GtkMenuItem
[Info  20:20:31.219] Hack for gnome-settings-daemon engaged

(f-spot:1856): GdkPixbuf-WARNING **: GdkPixbufLoader finalized without calling gdk_pixbuf_loader_close() - this is not allowed. You must explicitly end the data stream to the loader before dropping the last reference.
error checking orientation
error checking orientation
error checking orientation
error checking orientation
error checking orientation
error checking orientation
error checking orientation
value = f-spot version 0.6.1.5 len = 22
value = 2011:04:03 20:21:35 len = 19
Saved 10940 bytes
value = f-spot version 0.6.1.5 len = 22
value = 2011:04:03 20:21:35 len = 19
value = f-spot version 0.6.1.5 len = 22
value = 2011:04:03 20:21:35 len = 19
Saved 10940 bytes
[Info  20:21:35.718] Exiting
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

---

### Post by The Cog on 2011-04-03
Lovely screenshot.

I think you may have trouble with that external drive. You say it contains files from the dead Dell - is it the drive from the dead Dell (that you've moved to a caddy) or was it external to the Dell? If it's **from** the Dell, then I think a dead drive is the problem and a new drive in the Dell might bring it back to life.

Two things might prove/disprove the idea that it's a faulty drive problem:

1: Run the command ```
tail -f /var/log/messages
```to display new messsages as they're logged. Then try the file copy again and see if lots of disk error messages come out.

2: Look at the disk smart data and see if there are errors or problems recorded there. In Xubuntu it's System->Disk Utility but I can't remember the exact menu path to it in Ubuntu.

---

### Post by widda on 2011-04-03
> **The Cog said:**
> Lovely screenshot.

I think you may have trouble with that external drive. You say it contains files from the dead Dell - is it the drive from the dead Dell (that you've moved to a caddy) or was it external to the Dell? If it's **from** the Dell, then I think a dead drive is the problem and a new drive in the Dell might bring it back to life.

Two things might prove/disprove the idea that it's a faulty drive problem:

1: Run the command ```
tail -f /var/log/messages
```to display new messsages as they're logged. Then try the file copy again and see if lots of disk error messages come out.

2: Look at the disk smart data and see if there are errors or problems recorded there. In Xubuntu it's System->Disk Utility but I can't remember the exact menu path to it in Ubuntu.
It's an external and was external to dead laptop. It's a Vaio 120Gb. haven't got yet how to find its FAT or NTFS (many things to look at, I'm gettin there)
I downloaded some SMART by terminal, and queried it with a command but it didnt recognise. Thanks for help

---

### Post by widda on 2011-04-03
firmware issue for the Vaio drive?

---

### Post by widda on 2011-04-03
this from error messages looks relevant but i dont know what to do with it
" usb 2-2: reset high speed USB device using ehci_hcd and address 2"

---

### Post by The Cog on 2011-04-03
There's your problem. I don't know what it is exactly, but that's your problem. USB resets like that make me think hardware problems.

It might be the disk drive, but I have a feeling that it might be a USB controller compatibility issue. At this stage, all I could suggest is trying a different USB cable (that did it for me once), a different USB port, or using a different computer to extract the files from the drive.

---

### Post by widda on 2011-04-03
[QUOTE=The Cog;10632506... USB resets like that make me think hardware problems.

It might be the disk drive, but I have a feeling that it might be a USB controller compatibility issue. At this stage, all I could suggest is trying a different USB cable (that did it for me once), a different USB port, or using a different computer to extract the files from the drive.[/QUOTE]

*Thanks TC, that reminds* me that my system slowed to unusable last week when I plugged printer in, and then recovered dramatically when I plugged it in to another port.
Anyway, i'll start googling usb controller compatibility.
Also the ext drive came with a double usb plug, and i'm using a single (tho twas ok on lappie.)

---

### Post by widda on 2011-04-03
Breaking News

---

### Post by Dutch70 on 2011-04-03
Nice...looks like it might actually finish in your lifetime.

btw, just wondering if, in case your hard drive is failing, it's still under warranty? Just something to think about.

---

### Post by JRV on 2011-04-03
Could it be this problem?

Run "top" from the command line.

If "gvfsd-metadata" is hogging your processor do this:

```

rm -rf /home/USERNAME/.local/share/gvfs-metadata
pkill gvfsd-metadata 
```

---

### Post by widda on 2011-04-03
hi there Dutch70, no, I could yet pre-decease the copying of Music Folder. It bailed out at some unknown time, 5 percent done. I just started copy again and as usual it leapt away enthusiastically for 5 seconds and then slowed to close to zero. But I have found the monitor applet at least.
I still haven't got the cp or cp-r in terminal to work. I guess I'm not putting in the right names /filepaths for the directories. And I need to look up USB compatibility issues also.

---

### Post by widda on 2011-04-03
> **JRV said:**
> 

...Run "top" from the command line.
If "gvfsd-metadata" is hogging your processor do this ...

No JRV, gvfsd isnt there at all, and nothing is hitting more than 5% of CPU or RAM.

I have a soft spot for Minnesota I because of a certain artist whom I expect to be seeing in a double act with BB King this month in Adelaide, not to mention the movie Fargo.

---

### Post by widda on 2011-04-04
For anyone's info, I have been watching closer and I think one thing that's happening during transfers is that when it gets to a file it is having an issue with, it stops (or privately bangs its cpu on the file futilely for ages) and then finally activates a notice asking if I want to Skip the file, at that point I hit Skip and we're off again.  Maybe there's a setting somewhere that says it should try for 500 times before prompting, some big loop like that? Also I suspect some of the prompts are false.
Anyway I'm hauling my files back into PC, keeping transfers down to 40 Mb where possible. Not fast, but do-able.
 Also someone said on here a good kickstart for USB is running dmesg a few times and restarting a few times.
I think its faster now because I'm no longer flogging a lame horse, but instead slowing down on the keystrokes, not gridlocking it with a backlog of little tasks. Still lame though, but only in this matter of transfers.

---

### Post by widda on 2011-04-04
O, and the error is always same

Error splicing file: Input/output error
 I'll chase it all down, but I must see daylight or at least starlight soon

---

### Post by widda on 2011-04-04
***950 Mb/s is happening! after I took the external drive out of back-of-box USB slot and put it in a 4-way hub already cabled to adjacent USB slot. So drive has changed USBslots and gone 5 feet away.  I'm delirious about the Mb/sec!

Annoyingly, the b'band usb modem, which was already in the 4-hub that I moved the extdrive to, went  unstable immediately, and net now is dropping out or in about every 3min - And always drops out if I try to get a web page, so unusable. More to those usb's than meets the eye. ***
That was all written off line, but net is back behaving normally, so any hubsharing issue was temporary (if real). 
I'll mark this filetransfer via usb issue SOLVED, which seems be so - it's quite valuable to know that of all the hidden complex things that might have been, it was seemingly "try a different USB slot"!
And we did get a great screenshot out of it.

---

