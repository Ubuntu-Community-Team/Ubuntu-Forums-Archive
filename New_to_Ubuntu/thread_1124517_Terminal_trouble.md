---
title: "Terminal trouble"
date: 2009-04-13
forum: New to Ubuntu
---

### Post by killjoy714 on 2009-04-13
im new to linux and the terminal thing. what commands are what. im curently trying to move files to a read only travel drive :(  i dont know what to do please help

---

### Post by Tony Flury on 2009-04-13
if the destination drive is read-only - you wont be able to move any file too it - either via the command line, or through Nautilus.

Why is the destination drive read-only ?

---

### Post by Copernicus1234 on 2009-04-13
I think he probably wants to know how to make it not read-only. :)

---

### Post by cariboo on 2009-04-13
If you need to move files to a directory you don't have read/write permissions to use sudo, eg:

```
sudo mv somefile /media/<device> 
```

Where <device> is the mount point of your usb device.

Jim

---

### Post by Hospadar on 2009-04-13
I'd suggest reading in to a nice CLI tutorial

A quick google turned this one up and it looks nice
[http://gd.tuwien.ac.at/linuxcommand.org/learning_the_shell.php](http://gd.tuwien.ac.at/linuxcommand.org/learning_the_shell.php)

---

### Post by Jakey_TheSnake on 2009-04-13
Well, "mv" is the move command, and "cp" is the copy command. You'll need to use "sudo" in front of your command wherever you need root permissions, though - so if you don't have read/write permissions on the USB drive you'd just have to stick "sudo" in front of below commands, but I'm going to assume you do. 

For example, if you wanted to move a file (help.txt) from your desktop to a USB stick you'd type:

```
mv /home/username/Desktop/help.txt /media/disk
```

Where the first path is the file you want to move, the second is your USB drive. You can find out its "mount point" by opening it from the "Places" menu on your taskbar (or panel, as we call them), and looking at the file path. 

Other useful things to know are:

Say you wanted to move all text files from your Desktop to the USB stick, you could use:

```
mv /home/username/Desktop/*.txt /media/disk
```
because * represents a wild card and can be anything. A useful shortcut is also "~/" which is the same as typing "/home/username/", so - combining the two above tricks - you can move ALL files from your desktop using:

```
mv ~/Desktop/* /media/disk
```

Also, note that when typing a location, you can press the Tab key, and it will be completed for you, i.e. if you had a folder called "OpenOfficeOrg3" on your desktop, and you had typed "~/Desktop/Ope" so far, and hit Tab, it would complete the file path for you. If you have two different filepaths which begin with what you have typed thus far, the Tab key will take you up to the point in which they differ (as it doesn't know which one you want). If you press Tab twice, then you get a list of possibles, so "~/Desktop/" then tab twice would show you everything on your desktop. 

The "cd" command takes you to another directory, so "cd ~/Desktop" would 'take' the terminal to your desktop. Not very well explained, if someone could articulate for me I'd be grateful. 

"apt-get" you will see around a lot, you will most likely use it for installing applications (from the Ubuntu repositories), such as "emesene" the IM client (that I use instead of MSN or Pidgin) or "bum" (boot-up manager). You will need to run it as root. So:

```
sudo apt-get install bum
```
will install boot-up manager on your system. However, if you're new then you can use a GUI (Graphical User Interface) to do that instead, it's called Synaptic Package Manager and can be found in the System > Administration menu. 

The "easter egg", if you will, of "apt-get" is the command "apt-get moo" (no need to run as root), and will display...well, find out for yourself ;) 

.deb files can be installed via the terminal like thus (let's assume we have a file called programX.deb on the desktop):

```
cd ~/Desktop/

sudo dpkg -i programX.deb
```
BUT it's much easier just to double-click them and use the installer :)


You will also find people will tell you to extract things using the terminal, most likely a .tar.gz file, and the command will look similar to this: 
```
tar -xvzf packedfile.tar.gz
```
BUT it is just as quick and easy to find the file, right-click it, and press "Extract Here". 

Now let's show you the use of such terminal commands, even if you don't need to know this kind of stuff yet. Press Alt+F2 and open up "gconf-editor". You can see all your configuration settings for things like compiz, and your programs, and panels using this. Using the "gconftool-2" command, we can back these up and load them at a later date. For example, to back up our panel settings we could use:
```
gconftool-2 --dump /apps/panel > ~/Desktop/paneldata.entries
```
which would create a file called "paneldata.entries" on your desktop. Now you can do something stupid, like delete one of your panels by accident, and then load the old configuration with:
```
gconftool-2 --load ~/Desktop/paneldata.entries
```
You can have a look through the gconf-editor and see what kind of things you could backup, and what would be useful to backup etc. The filepath after the "--dump" command you can see from the navigation menu on the left-hand side of gconf-editor. 

Well, I might have rambled, it may not have solved your problems, you may learn nothing whatsoever from this post: but I hope it will help some people discover basic terminal commands, and encourage them to learn more! 

Happy Ubuntu-ing ;)

---

