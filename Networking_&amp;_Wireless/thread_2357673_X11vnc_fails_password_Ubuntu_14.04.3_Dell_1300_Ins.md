---
title: "X11vnc fails password Ubuntu 14.04.3 Dell 1300 Inspiron in Startup Apps"
date: 2017-04-04
forum: Networking &amp; Wireless
---

### Post by Shobuz99 on 2017-04-04
Hi Ubuntu community,

I have re-installed Ubuntu 14.04 and done updates. It is running the ABI 3.19.0-80.88 kernel and headers.
 4.4.0-71  did not install when the updates were run.
I believe this may have something to do with my not choosing some option during Ubuntu installation.

I also had backed up my previous version of 14.04.3 using Deja-Dup and put the whole backup in one folder.
This would mean that when I restored it after the fresh Ubuntu 14.04 install, that I could access all my files
I had on the drive, previously. This was my 2nd re-install of Ubuntu 14.04.

This also means that my folder structure kept expanding and the first "restore" folder was underneath 2 sub-folders:

```
 Home/robotics1/restore32217/home/robotics1/restore081516/home/robotics/~original Ubuntu 10.04/files 
```
This means there are 3 "/home/robotics1/" folders 2 of which are sub-folders.

Moving on - I installed X11VNC from the package install and proceeded to setup the server in Startup Apps as a command. 
My settings in the command field were as follows:
```
 x11vnc -rfbversion 3.6 -gui tray -rfbport 59xx -rfbauth /home/robotics1/.vnc/passwd -o -xkb -ultrafilexfer /home/robotics1/.vnc/x11vnc.log -forever -bg 
```
I saved the command, exited.
I used ```
 x11vnc -storepasswd 
``` and stored the password to the folder 
```
/home/robotics1/.vnc/passwd 
```
Then restarted Ubuntu.
When it finished booting, the gui tray icon for x11vnc appeared and hung.
I hovered over it and the message read:
```
 Not currently attached to x11vnc Last available info: tkx11vnc: no client information available from x11vnc ... 
```

So I exited x11vnc and ran it manually, selecting the port, input a password, rfbversion, ultrafilexfer, and the -xkb flags manually as well.

Then I tried connecting with vncviewer from a Windows Vista machine. It connected successfully without errors!

After that I concluded that the string of commands and switches in the Startup Apps command had syntax errors somewhere.

Then I went through about 10 different iterations of the command line, removing some settings and moving others in a different order.
I discovered that when I removed the ```
 /home/robotics1/.vnc/passwd  /home/robotics1/.vnc/x11vnc.log
```
and used the ```
 -nopw 
``` that it would connect successfully!

To me, this means I may have some sort of problem with the folders and/or paths? OR
There is something I'm missing in the syntax of the command line I use for Startup Apps for the passwd file.

Can someone help me sort this out?
Again, I also wonder if the constant re-install of Ubuntu 14.04 has caused me problems I haven't realized yet.

Thank you for your help and support.
Rick (shobuz99)

---

### Post by Shobuz99 on 2017-04-05
**Update to the first section of my post**:
The Software Pkg Updater just ran an update and told me about an EOL for some portion of the 14.04 LTS pkg on August 8th 2016. ???? I didn't know that.
Also, it asked me to install the 4.4.0-72 Linux headers and kernel, that weren't installed when I re-installed Ubuntu 14.04.3 LTS
So I did. Now I'm considering going back and revisiting what I should do in re: to x11vnc server and its command line in Startup Apps...
I sure would like some advice here, anyway.
Thank you for your continued support. I always appreciate it.

Rick (shobuz99)

---

### Post by Shobuz99 on 2017-04-05
Please close this thread. I've solved my problem with x11vnc; however, the re-install of 14.04 had to be done again.
And it only installed the 3.19.0-80 kernel.. not the 4.4.0-72 kernel.
I think the reason is that I chose version 14.04.5 re-install, instead of starting from 14.04.3, which initially gave me the two kernels 3.19 and 4.4.0
at original install. I still don't know why; but at this point it doesn't matter.

Thank you for your interest in my issue. 

Rick (shobuz99)

---

