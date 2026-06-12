---
title: "How to change permissions"
date: 2010-05-18
forum: New to Ubuntu
---

### Post by expatCM on 2010-05-18
Ubuntu 10.04  I need to change permissions at /dev/bus/usb/001/002

I run the following command

sudo chmod a+w /dev/bus/usb/001/002

and the permissions change.

I then reboot and the changes are gone.

How do I execute the command so that the changes stay?

---

### Post by anewguy on 2010-05-18
Because you are making permission changes against a dynamic device, they are only valid for your session.  I suspect that what actually needs to happen is this:

- a rule needs to be created in the udev rules to specify that when the particular USB device is plugged in mount it with "xxx" permissions


However, before I can walk you through creating such a rule, we need to know the device you are plugging in and having problems with, so please do the following:

- post back the make/model of the actual USB device you are trying to access

- with the device plugged in to a USB port, go to a terminal window (Applications/Accessories/Terminal) and post back the output of:

sudo lsusb


That should give us more to go on.

Dave ;)

---

### Post by expatCM on 2010-05-18
What I am trying to do is to finish off a scanner install.  I get a message from xsane that no devices are available and yet lsusb shows

Bus 001 Device 002: ID 03f0:2305 Hewlett-Packard ScanJet 3970c

When I first installed the scanner (on earlier Ubuntu releases) I needed to change the permissions of the USB port and then it worked.  Well I think that is what I did but I really cannot remember ... 

sane-find-scanner -q gives me the following 

found USB scanner (vendor=0x03f0 [hewlett packard], product=0x2305 [hp scanjet], chip=RTS8822) at libusb:001:002

---

### Post by anewguy on 2010-05-18
I honestly don't know what the "a" does after chmod in your example, but here's what I would try.  Open a terminal window (applications/accessories/terminal) and do the following:

type:

cd /etc/udev/rules.d <press enter>

sudo gedit 10-HP3970C-permissions.rules <press enter>  This will call up the editor with a new blank file.  Add the following as single line to that new file:


SUBSYSTEMS=="usb" ATTRS{manufacturer}=="Hewlett-Packard" attrs{product}=="ScanJet 3970c" MODE:="0666" SYMLINK+="HP ScanJet 3970C"


Now save the file, exit the editor and exit the terminal.

Try your scanner again.

If that doesn't work let me know and I'll do some more research.

Dave ;)

---

### Post by Drenriza on 2010-05-18
```
sudo chmod 0777 /dev/bus/usb/001/002
```
 
the a changes the permissions for all or the 4th digit in the xxxx permissions.

---

### Post by expatCM on 2010-05-18
Thank you for the replies.

To answer about the "a", it basically means "all" or everyone.  The default permissions on the port are 0664 and the change should make this 0666.   The 0777 permissions modify this to add execute to all as well.

No progress though ....

10-HP3970C-permissions.rules does not exist but no problem.  Instead there is libsane.rules.  In those rules there is an item for the 3970 scanner.  So I edited the mode=0664 to mode=0666 and rebooted.   Same message that no devices found.

```
The individual rule after edit
# Hewlett-Packard ScanJet 3970c
SYSFS{idVendor}=="03f0", SYSFS{idProduct}=="2305", MODE="0666",

Your suggested edit (basically the same thing)
SUBSYSTEMS=="usb" ATTRS{manufacturer}=="Hewlett-Packard" attrs{product}=="ScanJet 3970c" MODE:="0666" SYMLINK+="HP ScanJet 3970C"

Sane-find-scanner -q
found USB scanner (vendor=0x03f0 [hewlett packard], product=0x2305 [hp scanjet], chip=RTS8822) at libusb:001:002
```

But nothing doing at all ....  I took a look at the permissions on the port after reboot and they were 0664.

So I then ran sudo chmod 0777 /dev/bus/usb/001/002 and checked the permissions.  They were 0777.  Then a reboot and .......   back to 0664.

So I guess the big question is what is setting permissions on the port since finding that may be helpful.

---

### Post by -humanaut- on 2010-05-19
Heres a simpler way to change file permission if you want to avoid the terminal hit alt+f2 type: gksu nautilus then right click on the files or programs you want to change permissions on go to properties and change the permissions.

---

### Post by anewguy on 2010-05-19
> **expatCM said:**
> 

10-HP3970C-permissions.rules does not exist but no problem. 



Please note - the file does not exist - you will be creating it.  This file is used at the level that Ubuntu actually mounts the USB device.  What I have found is that some USB devices don't get mounted via "normal" means, so they default to being owned by root.  This means you can see the device but you can't open it.  You can test this via "sudo xsane" from a terminal.  Please note - you should *not*run xsane as root - we are only doing this to test.  If you do the "sudo xsane" and it finds your scanner. you need to create the file.  After you create the file if it still doesn't work we can change if from the textual identification of the device to the USB manufacturer and product codes.

Dave ;)

---

### Post by expatCM on 2010-05-19
Sorry Dave, my brain started thinking faster than my eyes were reading.  I have done exactly what you stated now but sudo xsane gives the same message.

I set the owner:group as root:root since that is the same as the other rules.

I rebooted and checked the permissions.  What I found was as follows

/dev/bus/001  755

/dev/bus/001/001  664

/dev/bus/001/002  664

---

### Post by anewguy on 2010-05-19
I'll do a little more thinking on it.  I'm pretty sure you're going to need rules defined in udev, and in a separate rules file in /etc/udev/rules.d but the ones for sane may work as that.  I'm pretty sure it's just how it's getting mounted, and that is done by the udev rules.  I don't think you can ever make the chmod to a device permanent, especially for a USB device.  That's what the udev rules should do for you.

So.....I'll do a little more thinking. ;)

Dave ;)

---

### Post by anewguy on 2010-05-19
Searching the net, I did find [this]("http://sourceforge.net/projects/hp3900-series/") for controlling your scanner with your scanners' chipset.  Let me know if you need help with this.

Dave ;)

---

### Post by expatCM on 2010-05-19
I already have the sourceforge package installed.  

I think this is the thread that I followed the last time I installed this scanner and it worked.
[http://ubuntuforums.org/showthread.php?t=288751](http://ubuntuforums.org/showthread.php?t=288751)

Something about the USB permissions seems to have changed with the present Ubuntu release though since I did not experience any problems with 9.10.....

---

### Post by anewguy on 2010-05-19
Silly question, but since you are manually chmod'ing to 777, have you tried changing the udev rule to 777?

Also, you can add a script to be executed on a udev rule, so theoretically one could do the chmod there, but the problem is that the chmod requires root (and therefore sudo) but I don't know how to get sudo to work in a script.  Also, the device would absolutely have to be mounted to the same /dev node everytime for that to work.

I'll keep trying....

dave ;)

---

### Post by expatCM on 2010-05-19
Yes, tried that but no success.  The udev rules do not appear to have any bearing on the usb port permissions.

Something changes the port permissions back to 0644 after a reboot no matter what permissions are set on the port or what permissions are set in the udev rules.

---

### Post by anewguy on 2010-05-19
> **expatCM said:**
> Yes, tried that but no success.  The udev rules do not appear to have any bearing on the usb port permissions.

Something changes the port permissions back to 0644 after a reboot no matter what permissions are set on the port or what permissions are set in the udev rules.

Yeah, it appears the udev rules don't affect the port permissions, though I'm a little confused (maybe the difference between the device and the port, even though I didn't think there were any).

As for setting the permissions back on reboot, as I mentioned before it's a dynamic device so the permissions won't be permanent. 

I have a thread posted right now looking for some help on getting something to run.  Once I get an answer on that I'll have the answer for you (trying to get it to automatically do the chmod whenever you log in).

Dave ;)

---

### Post by anewguy on 2010-05-20
I suppose you already seen it, but does [this]("http://ubuntuforums.org/showthread.php?t=1285100") help any?  I notice they edit the file to only include the scanner model (obviously you would use your scanner model).  Please note the  GROUP="scanner", ENV{libsane_matched}="yes" string on the end of the rule statement.  Also, be sure you're a member of the appropriate groups (scanner and saned).

I would:

sudo mv /etc/udev/rules/libsane.rules ~/libsane.rules <press enter> (we are going to clear out the libsane rules since it is just a bunch of scanners, but we are storing a copy in your home folder in case we need to put it back)

sudo cp /etc/udev/rules.d/10-local-permissions.rules /lib/udev/rules.d/100-hp3970-permissions.rules<press enter>

sudo rm /etc/udev/rules.d/10-local-permissions.rules <press enter>

sudo gedit /lib/udev/rules.d/100-hp3970-permissions.rules <press enter>

the contents of the entire file should only be:

SUBSYSTEMS=="usb" ATTRS{idVendor}=="03f0", ATTRS{idProduct}=="2305", MODE="0666",
, GROUP="scanner", ENV{libsane_matched}="yes"

Be *sure* the file only contains that line and that the line looks EXACTLY like that (note ATTRS, *not* SYSFS).

Save the file

exit the editor

exit the terminal

go to system/administration/users and groups

click on manage groups

locate the saned group, click properties, then be sure your userid is listed and checked

locate (add if needed) the scanner group, click properties, then be sure your userid is listed and checked

Now try scanning.

Dave ;)




Dave ;)

---

### Post by expatCM on 2010-05-20
I think we are close but .....  sadly ......  not there yet.

Yes, I had seen the thread, thank you but it is not quite the same.  I cannot get xsane to recognize the scanner, even if I launch with sudo ...

I made some slight edits to the file names but followed your instructions as follows.
```
sudo mv /etc/udev/rules.d/025_libsane.rules ~/025_libsane.rules 

sudo cp /etc/udev/rules.d/10-HP3970C-permissions.rules /lib/udev/rules.d/100-HP3970C-permissions.rules

sudo rm /etc/udev/rules.d/10-HP3970C-permissions.rules

sudo gedit /lib/udev/rules.d/100-HP3970C-permissions.rules

```

I copy and pasted your device profile but I made one small edit, I removed a comma.  This is what I am using.
```
SUBSYSTEMS=="usb" ATTRS{idVendor}=="03f0", ATTRS{idProduct}=="2305", MODE="0666", GROUP="scanner", ENV{libsane_matched}="yes"
```

I added the group scanner.  I checked that I am a member of scanner and saned and that my identity is checked.

After a reboot I tested.  No change in status.

The port still shows permissions of 0644 BUT the group has now changed to scanner (so it was root:root and now is root:scanner).

I found this [link]("http://reactivated.net/writing_udev_rules.html#ownership"), I will not pretend that I understand it but after reading through it appears related?

---

### Post by anewguy on 2010-05-20
The link you posted is for doing what I was talking about - running a script file when the udev rule is executed.  The only problem I've had is that I haven't been able to get that to work yet.  I'm still working on that, and I have another approach I'm working on as well.  I'll keep you posted.

Dave ;)

---

### Post by expatCM on 2010-05-20
ok .... thank you :)

---

### Post by anewguy on 2010-05-20
Okay, I *think* I've got it for you, at least it's worked when trying with my USB devices.

The first thing we have to do is give you permission to run a specific file, which includes a sudo command, without it prompting you for a password or bombing out:

- open a terminal window

- cd /etc <press enter>

- sudo gedit sudoers <press enter> enter your password when prompted

go to the end of the file, press <enter>, then add the following new line:

dave ALL=NOPASSWD: /usr/local/bin/hp3970-chmod.sh

Replace "dave" at the beginning of that line with your userid.

Save the file and exit the editor.

- cd /usr/local/bin <press enter>

- sudo gedit hp3970-chmod.sh <press enter>

This will open up the editor with a blank screen because it's a new file.

Put the following in the file:

#! /bin/bash
sudo chmod 777 /dev/bus/usb/001/002


Save the file and exit the editor.

sudo chmod +x hp3970-chmod.sh <press enter>

- ls -al hp3970-chmod.sh <press enter>

It should now look similar to this:

dave@dave-desktop:/usr/local/bin$ ls -al hp3970-chmod.sh
-rwxr-xr-x 1 root root 50 2010-05-20 03:25 hp3970-chmod.sh
dave@dave-desktop:/usr/local/bin$ 

The important things are that it is owned by root and that the permissions match.


Okay, so now we've given you permission to run the script file, and we've created the script file.  Now we just need to add it to the udev rules line:

- cd /lib/udev/rules.d <press enter>


- sudo gedit 100-HP3970C-permissions.rules <press enter>

Change the file to read as follows (EDIT: I originally forgot to add the RUN):

SUBSYSTEMS=="usb" ATTRS{idVendor}=="03f0", ATTRS{idProduct}=="2305", MODE="0666", GROUP="saned", ENV{libsane_matched}="yes" RUN+="/usr/local/bin/hp3970-chmod.sh"

Then save the file and exit.  Note that we changed the group to saned.  I'm not sure if that will make a difference or not but I think it might be better.


Now, assuming you always leave your scanner plugged into the same port, just reboot.  After reboot:

- open a terminal window

- ls -al /dev/bus/usb/001/002 <press enter>

Hopefully it will show with all rights now.

Try to scan again and report back the results.  We may need to play with the group stuff again, I'm not sure.

Dave ;)

---

### Post by expatCM on 2010-05-20
really sadly .....  it is not there yet ...

ls -al /dev/bus/usb/001/002
crwxrwxrwx+ 1 root saned 189, 1 2010-05-20 18:53 /dev/bus/usb/001/002

I have confirmed the above string by looking at the port properties and it really is 0777 root:saned

I still get the same message that no devices available...  I also ran sudo xsane and that gives the same message as well.

What am I missing that is very much there on your machine ......

---

### Post by anewguy on 2010-05-20
> **expatCM said:**
> really sadly .....  it is not there yet ...

ls -al /dev/bus/usb/001/002
crwxrwxrwx+ 1 root saned 189, 1 2010-05-20 18:53 /dev/bus/usb/001/002

I have confirmed the above string by looking at the port properties and it really is 0777 root:saned

I still get the same message that no devices available...  I also ran sudo xsane and that gives the same message as well.

What am I missing that is very much there on your machine ......

What I don't get is that we have accomplished setting the privileges on the device as you requested but it still doesn't work.  I am curious to try something, but I have no idea if it will work:

- on the udev rule, remove the GROUP and the ENV so it is just:

SUBSYSTEMS=="usb" ATTRS{idVendor}=="03f0", ATTRS{idProduct}=="2305", MODE="0666", RUN+="/usr/local/bin/hp3970-chmod.sh"

Note this won't take effect until you reboot.

If that doesn't work yet, try changing the /usr/local/bin/hp3970-chmod.sh to the string you were using:

sudo chmod a+w /dev/bus/usb/001/002

Again, any changes made won't take effect until you reboot.  I can't see how that could make any difference, since we've actually given more privileges than that to the libusb device.

Also, just for kicks, post back the output of:

sudo lsusb

again.

Since we've accomplished the chmod, and you said that manually doing so worked before, do you remember what the udev rule in libsane udev looked like?

I'm still pondering......

As far as missing anything, I don't have the same scanner.  I've just been working with one of my USB devices to automatically get the chmod done to the port as you requested.  My scanner, HP 4200C (USB), works "out of the box" with Ubuntu.


dave ;)

---

### Post by anewguy on 2010-05-20
I just downloaded the sourceforge package and looked at the readme.  Which method did you use when you installed it?  Hopefully the sane backend method.

Dave ;)

---

### Post by expatCM on 2010-05-21
No joy.

The full output of sudo lsusb is as follows
```
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 058f:6362 Alcor Micro Corp. Hi-Speed 21-in-1 Flash Card Reader/Writer (Internal/External)
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 03f0:2305 Hewlett-Packard ScanJet 3970c
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

When I originally had this working I did not change any of the rules, it was simply what was installed.  The only thing I did was run the command to change the port permissions.

I used method #2 to install the sourceforge package. That is the default selection and I think it is the one that installed the backend package.

---

### Post by anewguy on 2010-05-21
Did you ever have this working in 10.04, or was it working in a previous release and now you're trying to get it to work in 10.04?

Dave ;)

---

### Post by anewguy on 2010-05-21
I think there may be a little more going on here - specifically, it appears that at least with 10.04 the backend for the hp3900 series is already included.  By running the script from the sourceforge download, it's possible that the libs got messed up.

I didn't actually install the package - I've just been looking in it.  In particular, I already have the libsane-hp3900.la, libsane-hp3900.so.1 (just a link to ->) libsane-hp3900-so.1.0.20.  It appears the script puts it's own copies of libsane-hp3900.la and libsane-hp3900.so.1 in /usr/lib/sane.  I'm wondering if the overwrite of libsane-hp3900.so.1 may have anything to do with it.

In addition, I haven't found a udev rule yet for the hp3900 series.  However, if you had to chmod the libusb port before we might as well leave the udev rule and associate changes to sudoers and /usr/local/bin that we made since it is just setting the permissions on the port.

So, open a terminal window and do the following:

- cd /usr/lib/sane

- ls -al libsane-hp3900* <press enter>

Then copy/paste that output back here.

Dave ;)

---

### Post by expatCM on 2010-05-21
No, 10.04 was a fresh install from earlier on this week.  I have never had it running with 10.04 but I have had it working with every version since 6.0x.

The output of ls -al libsane-hp3900* is as follows ... 

```
-rw-r--r-- 1 root root   1041 2010-05-17 14:54 libsane-hp3900.la
lrwxrwxrwx 1 root root     33 2010-05-17 14:54 libsane-hp3900.so -> /usr/lib/sane/libsane-hp3900.so.1
lrwxrwxrwx 1 root root     39 2010-05-17 14:54 libsane-hp3900.so.1 -> /usr/lib64/sane/libsane-hp3900.so.1.1.0
-rw-r--r-- 1 root root 424456 2010-04-15 14:25 libsane-hp3900.so.1.0.20
-rwxr-xr-x 1 root root 668648 2010-05-17 14:54 libsane-hp3900.so.1.1.0
```

---

### Post by anewguy on 2010-05-21
Judging by the dates/times on the files:

```
-rw-r--r-- 1 root root   1041 2010-05-17 14:54 libsane-hp3900.la
lrwxrwxrwx 1 root root     33 2010-05-17 14:54 libsane-hp3900.so -> /usr/lib/sane/libsane-hp3900.so.1
lrwxrwxrwx 1 root root     39 2010-05-17 14:54 libsane-hp3900.so.1 -> /usr/lib64/sane/libsane-hp3900.so.1.1.0
-rw-r--r-- 1 root root 424456 2010-04-15 14:25 libsane-hp3900.so.1.0.20
-rwxr-xr-x 1 root root 668648 2010-05-17 14:54 libsane-hp3900.so.1.1.0
```

I would appear that you installed the sourceforge stuff on 5/17 and it did:

- modify/overwrite libsane-hp3900.la 

- added libsane-hp3900.so

- modify/overwrite libsane-hp3900.so.1

- added libsane-hp3900.so.1.1.0[/code]

I also noted that one of the files, libsane-hp3900.so.1, is a link to /usr/lib64/sane/libsane-hp3900.so.1.1.0.  So there is the potential another thing has been added to the mix:

- since it is pointing to /usr/lib64, I have to ask if you have installed the 64-bit version of Ubuntu, since I have the 32-bit and don't have /usr/lib64.  It's possible the 64-bit stuff is conflicting somehow since it appears the sourceforge stuff is 32-bit.  I don't know enough about libs, etc., to know what kind of difference it can make.

Did you do a clean install or an upgrade?  If a clean install, is it possible for you to just wipe out what you have, reinstall Ubuntu and then just try the scanner without the sourceforge stuff installed?  I don't know, but you may still need to chmod the libusb port for it to work - if so, we can add the changes to sudoers, the script file and the udev rule back in so that happens automatically.

At this point, we do have it chmod'ing the port, so I have to believe the problem lies now with the backends, which are made up of the files above.

Dave ;)

---

### Post by expatCM on 2010-05-22
You really do have my total attention here ..........

After reading your last post I thought I would try something to confirm that this is a mess of my making.  I booted from the live CD and then opened the program Simple Scan.  The scanner worked.  Simple Scan does not work when I boot normally.

Yes, I am running the 64 bit version, I have done so for some years.  Even using the sourceforge package :)   But it is clear from your observations that this is the problem.

I was wondering is there any way of removing the sourceforge package without a reinstall of Ubuntu?  I am not exactly thrilled with the prospect of reinstalling....

---

### Post by anewguy on 2010-05-22
open Synaptic Package Manager

search string -> sane

mark it for removal (it should come up and want to delete several other packages as well)

apply

now search string -> sane  again

mark the following packages for installation:

sane

libsane

sane-utils

xsane

now search string -> hp

be sure the following are marked - if not, mark them for installation:

hplip

libhpmud0

hplip-data

now search string -> simple-scan

check "simple-scan" package - if it's not marked, mark it for installation

Now click apply and let it do it's thing.  When it finishes, I would reboot just for the heck of it, then try scanning again.

While I doubt it actually hurts anything, we can also try removing the automatic chmod later if you want to.

Dave ;)

---

### Post by expatCM on 2010-05-22
Well I am very happy to report that everything is working now .....  no deviations or interpretations, the scanner works.

Removing and reinstalling everything was not exactly hard and served the purpose.

Thank you very much for your assistance and for seeing this one through to the end.  I have learned a lot here and I really appreciate that opportunity.

---

### Post by anewguy on 2010-05-22
Glad I was able to help.  BTW - I'd try removing the udev rule file (back it up first) as I doubt it is needed now either.  If it doesn't work, just copy it back (with sudo......).

Dave ;)

---

### Post by Tony Flury on 2010-05-22
Dave,
If there was an award for the most perseverence and helpfulness in assisting someone to solve a problem - it would go to you - well done :-)

---

### Post by anewguy on 2010-05-22
Ah shucks - I was just trying to help someone since I get so much help myself!

BTW - the reason I had you uninstall sane (which probably uninstalled the other stuff) was that the /usr/lib/sane folder is what had the messed up files, so by removing sane it removed that folder.  Adding sane back in re-created the folder without the changes made by the sourceforge package.  All the other things I had you add or check to be sure were installed were because when I tested uninstalling sane on my PC and then reinstalled it so I could test to be sure it would do what I thought, uninstalling sane also removed a bunch of stuff on my PC so I had to add it back in.

I'm just glad we were able to get this figured out!

Best of luck!
Dave ;)

---

