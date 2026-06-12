---
title: "Uhh Virtualbox installed but where?"
date: 2009-01-05
forum: New to Ubuntu
---

### Post by stmdk on 2009-01-05
I'm using 8.04.  I apologize for being a Windows junkie that expects a little convenience and obvious direction.

Nothing but problems installing virtualbox.  I tried installing OSE but that didn't work.  I can't understand the point of having a package installer that leads you to believe everything installs fine but leaves out important steps that I can only discover on a forum.  

Anyway I gave up on the OSE after scouring through forums with no solutions.  I discovered another way that I though would work.

I installed virtualbox using this guide by downloading the deb and double clicking on it.

[http://ubuntuforums.org/showthread.php?t=770745](http://ubuntuforums.org/showthread.php?t=770745)

Everything installed fine.  There were no errors.  It shows up in the groups, where I added the user access.  

However, where is it?  How do I run it?  It's not in the applications menu. It just installs and then leave me with a mystery.

Someone has got to explain to me why things install but they're not added to the menu.  You would think that it would be a convenient part of install process to tell you how to run it or ask you if you want it added to a launch menu. Again, I'm sorry, I'm used to the user friendliness of Windows.  


I know it's in here somewhere but I cannot find it.

---

### Post by adult swim on 2009-01-05
is it in applications>system tools?  if not you can run by pressing alt+f2 and entering in ```
VirtualBox
```

you can add it to the menu if you right click up where it says applications and then select edit menu.  on the left make sure that applications is selected and on the right choose new item.  make it like the following (the command option is the only one that has to be exactly like below)
type: application
name: VirtualBox (can be anything  you want really)
Command: VirtualBox (has to be the command to launch virtualbox)
comment: VirtualBox (again can be whatever you want to put in)

---

### Post by tuxxy on 2009-01-05
You should be using the PUEL version and you start Virtualbox you could either open a terminal and enter 

```
VirtualBox
```

If you would like a menu icon then right click your menu and select edit, now create a new entry in the menu you like and use that command to run it.

---

### Post by RomeReactor on 2009-01-05
Hi. Sometimes the menus don't refresh immediately, and recently installed applications don't show up until after a while, or by restarting the panels. VirtualBox should show up in 'Applications->System Tools->Sun xVM VirtualBox'.

EDIT: By the way, you can get version 2.1.0 [here]("http://www.virtualbox.org/wiki/Linux_Downloads").

---

### Post by Vadi on 2009-01-05
Either in Applications-Accessories-Virtualbox or Applications-System Tools-Virtualbox.

At any rate, alt+f2 should fine it.

---

### Post by stmdk on 2009-01-05
Wow, you guys are fast.  Thanks.

When I type in virutalbox I get...


The program 'virtualbox' is currently not installed.  You can install it by typing:
sudo apt-get install virtualbox-ose
bash: virtualbox: command not found

BUT...it figures I find a solution as soon as I'm pulling my hair out..

I went to the menu editor and looked.  The System Tools is checked.  The VirtualBox is also within checked.  However neither show up in the application menu when I click on it.  So I unchecked them both and then exited the editor.  Went back in and rechecked them and now they show up fine.  

Wierd.  Is there a known bug with adding new items to the menu or did I miss a step?

Sorry if I sounded upset but when things don't work like they should (or at least what you expect they should)  you get a little frustrated...If this were Windows I would have already punched the monitor but I'm trying to learn this OS and I can't get too upset because I know I'm a newb and probably missing something obvious.


Thanks for the quick replies though! :D

Now I just gotta figure out why it won't communicated with the Innotek server so I can get rid of this darn name/email popup.

---

### Post by pyromanic123boom on 2009-01-05
Right..It should be in Applications-->System Tools--> Virtual Box, but it doesn't show up in the menus until you install the deb twice.

I have installed virtualbox on two systems, and both times, I had to install twice to make it appear in the menus. Sure, you can use ALTF2 or make a launcher, but I wanted in my applications menu.

---

### Post by adult swim on 2009-01-05
good that it worked for you.  remember one thing though, things are always case sensitive.  VirtualBox is not the same as virtualbox

---

### Post by stmdk on 2009-01-05
I didn't need to install twice but I had to do that little check cycle in the menu editor to get it to show.

At first, I thought I needed to reboot but when I came back in it still wasn't there and then I was like WTH!

It's working though and now I know to look out for it in the future.

---

### Post by linux6994 on 2009-01-05
Look under system tools or other, you will be able to find it there. When it opens up you will be able to define your virtual machines. The machine will boot via a virtual bios that you set up like any other. The best way is to set the virtual disks as expanding vice static that way it will grow as needed.

The disks will reside in a hidden directory in your /home directory in .virtualbox View hidden files to see it. Once your machine(s) are created you can copy the .virtualbox directory out for safe keeping in case things get messed up when playing. (Have done it many times)

I have found that the best way to use virtualbox is via the PEUL version that allows USB use easier that the OSE.
[http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

Download and install the Intrepid or Hardy file which ever you are running and allow the installer to install it. 

To use USB devices do the following
sudo gedit /etc/fstab
then add 
none /proc/bus/usb usbfs devgid=125 (what ever group id is),devmode=664 0 0
to the last line in the file
save and reboot.

Then when virtualbox opens select USB and add a filter. You will be able to connect whichever USB device you wish. I connect my iphone which syncs with itunes in XP. Device version upgrades will fail at the end ie.. 2.1 to 2.2 but normal syncing works fine.

Hopefully not to much info at once.

---

### Post by stmdk on 2009-01-05
Unfortunately I have no USB.  The darn ports shorted out one month into deployment (I'm in Iraq).  

The reason I'm using Ubuntu on this laptop is because the USB ports blew.  I discovered that Windows will NOT run if the USB ports are screwed up on a laptop that doesn't have a BIOS option to disable them.  XP wont even install.  Ubuntu is flexible though.  When it can't start the ports, it just gives up on them and drives on with other stuff.

I needed VirtualBox to run some apps that can only be run on XP.

---

### Post by linux6994 on 2009-01-05
stmdk - thank you for your service! Get home safe.

---

