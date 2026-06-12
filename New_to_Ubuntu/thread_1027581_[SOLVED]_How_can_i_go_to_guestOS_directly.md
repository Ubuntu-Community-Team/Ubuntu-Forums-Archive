---
title: "[SOLVED] How can i go to guestOS directly?"
date: 2009-01-01
forum: New to Ubuntu
---

### Post by eshant_engineer on 2009-01-01
before booting, is it possible to have option for OS which is installed in virtual hard-drive through virtualbox?

---

### Post by snova on 2009-01-01
Possibly, but I don't think so.

---

### Post by tylerspaska on 2009-01-01
I'm not sure about that either, but you could set up another user on your system and when that user profile loads you could have it automatically load your virtualbox session fullscreen.

---

### Post by pp. on 2009-01-01
> **eshant_engineer said:**
> before booting, is it possible to have option for OS which is installed in virtual hard-drive through virtualbox?

No.

In order to run the OS installed in a virtual hard drive you need to run an application which is called Virtualbox. The application needs the host OS to run.

Also, it's not possible to boot the computer from an OS installed on a virtual disk.

---

### Post by eshant_engineer on 2009-01-01
but other drives other then virtually made are not accessible....now is it possible to access other drives?

---

### Post by DGortze380 on 2009-01-01
> **eshant_engineer said:**
> but other drives other than virtually made are not accessible....now is it possible to access other drives?

What other drives? I think you're talking about a dual boot, google is your friend.

---

### Post by HotShotDJ on 2009-01-01
> **eshant_engineer said:**
> but other drives other than virtually made are not accessible....now is it possible to access other drives?There are several ways to accomplish this.  The easiest is to set up Shared Folders (Settings menu in VirtualBox).  If the instructions given within the Settings menu are not clear, you can refer to the VirtualBox User Manual (located at [http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads) ).  And, of course, if you are still not clear after that, I suggest you look at the Virtualization sub-forum right here in ubuntuforums: [http://ubuntuforums.org/forumdisplay.php?f=308](http://ubuntuforums.org/forumdisplay.php?f=308), starting with the Virtualization Mega-Thread.

---

### Post by scorp123 on 2009-01-01
> **eshant_engineer said:**
> is it possible to have option for OS which is installed in virtual hard-drive through virtualbox? You mean upon login? e.g. you login into Linux and taddaaa! instead of being in GNOME you're in your virtual OS?

I did something like that for a project. We needed OpenSolaris + Solaris + Linux + Windows ... all on the same machine. And at the same time (the guest OS'es would then be displayed fullscreen on attached Sun Ray ThinClients ... but that's another story)

So I used VirtualBox to implement this little miracle. More details can be found here:

"Poor Man's VDI"
[http://ebberstwork.blogspot.com/2008/10/poor-man-vdi_22.html](http://ebberstwork.blogspot.com/2008/10/poor-man-vdi_22.html)

This stuff here was originally written for **Solaris Express** and/or **OpenSolaris 2008.11** but looking at the files I'd say all of this should work on Ubuntu as well (OpenSolaris has so many similarities with Linux, even the config files are more or less in the same places).

So let me explain a little how I intended this to work:

UNIX-like operating systems such as Ubuntu Linux and OpenSolaris are multi-user Operating Systems, right? So in theory there can be multiple users logged into the system doing multiple things at the same time. And if VirtualBox is installed ... in theory all users could be accessing their VM at the same time. And each of them could have their own virtual machine with their own settings ...

So my goal was that users themselves could select which virtual machine they want to login to in future sessions so I don't end up having to write a custom login script for each of them.

My goal was to write one login script, that would nontheless load the right VM for each user.

So this is how I did it:

**1.)** **_Create a login script that loads the VM we want:_**

**/usr/bin/vbox_autovm**
```
#! /bin/bash
AUTOVM=`cat $HOME/.autovm`
if [ -z $AUTOVM ]
  then
    /usr/bin/zenity --error --text="You have not yet configured your ~/.autovm file. Please ask your administrator."
    exit 1
fi
/usr/bin/VBoxSDL -fullscreen -vm $AUTOVM
```

So you'd have to copy and paste the content above into the file location I mention above. And please pay attention to those backticks .... backticks " ` " and apostrophes " ' " are _NOT_ the same. Please really make sure you use copy & paste! So how to edit the file (just in case you or anyone else reading this don't know it ....):

**_GNOME:_**
[LIST][*]Applications > Accessories > Terminal
[*]Once the terminal opens type this into it:
```
gksu gedit /usr/bin/vbox_autovm
```
[*]copy & paste the few lines from above
[*]save and close the file
[*]issue this command to make the file executable:
```
sudo chmod 755 /usr/bin/vbox_autovm
```
[/LIST]

**_KDE:_**
```
kdesu kate /usr/bin/vbox_autovm
```

**_Terminal (multiple possibilities)_**
```
sudo vim /usr/bin/vbox_autovm
sudo nano /usr/bin/vbox_autovm
sudo pico /usr/bin/vbox_autovm
```


**2.)** **_offer VMs as available login option_**

With the same edit procedure as above, copy and paste the contents here and place this stuff into the file I indicate:

**/usr/share/xsessions/autoVM.desktop**
```
[Desktop Entry]
Encoding=UTF-8
Name=AutoVM
Comment=Launch your chosen ~/.autovm
Exec=/usr/bin/vbox_autovm
Icon=/usr/share/pixmaps/VBox.png
Type=Application
```
... after that you should get "AutoVM" as an available session type in your GDM (the GUI login window).


**3.)** **_define our "autoVM" so the two scripts above know what to start_**

This one is easy. Login to your normal desktop, eg. GNOME. Open a terminal window as described above, and just to make sure please open VirtualBox and take a look at the names of the virtual machines there. If I do that here I can see that I named my virtual Windows XP like this: **"WinXP_vb0000"**

Another way to make sure is via the terminal, e.g. if you issue this command: "**VBoxManage list vms**"

If I do that here (irrelevant parts left away):
```
> VBoxManage list vms

VirtualBox Command Line Management Interface Version 2.1.0
(C) 2005-2008 Sun Microsystems, Inc.
All rights reserved.

**Name:            [COLOR="Red"]WinXP_vb0000[/COLOR]**
Guest OS:        Windows XP

```

So that's the name of the virtual machine. So if I want to login directly into my virtual machine I'd have to execute this little command now:
```
echo WinXP_vb0000 > ~/.autovm
```

As an alternative: Open an editor and just put the name of your VM on one single line, then save the file as ".autovm". Voila done.

You can now login to your VM directly.

I suppose this is what you wanted?  :D  (if not sorry for wasting the space here .... )

---

