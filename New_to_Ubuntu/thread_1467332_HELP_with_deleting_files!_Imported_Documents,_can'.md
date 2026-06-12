---
title: "HELP with deleting files! Imported Documents, can't delete b\c no room for trash!"
date: 2010-04-30
forum: New to Ubuntu
---

### Post by LinuxNeubie on 2010-04-30
I set up my partitions, after asking for help here, as /(root) 20gb | /home 5gb | /usr 2gb | /swp 4gb | /tmp .5 gb - well so I thought. After I had installed I looked and there were a LOT more partitions than I had installed and they didn't look like the sizes I had told it to use. I'm sure some of them the OS put in by default regardless of other partitions set up.

Forgetting that I had a game which put all the user files - like 5gb - in My Documents, when I imported them it totally filled up /home (at least that is what it looked like) but when I found the problem and went to delete them it couldn't because there wasn't any room for trash. I couldn't even load the web browser because there wasn't any room for anything to run. 

I could of course open a terminal but I wouldn't know what to do once I did. I suppose I could just delete all the partitions from Windows 7 and start again but figuring out, with assistance, how to do something is, I think, more important. 

Thanks in advance for your help!

---

### Post by 2hot6ft2 on 2010-04-30
Empty trash **(be careful with this command, use copy and paste to prevent errors).**
> **tuxxy said:**
> Try this

```
sudo rm -rf ~/.local/share/Trash/files/*
```
then
Open a folder and go to Edit > Preferences > Behavior > Trash
Check the box by Include a delete command that bypasses Trash.
Click Close.
Browse to the files you want to delete and right click on them and select Delete.
When you're done you can remove that option from the right click menu by repeating the process and clearing the box you checked.

---

### Post by LinuxNeubie on 2010-04-30
Command worked fine. Problem is, Nautilus can't run because there is ZERO space to make anything, so I can't even open the "Home" folder, or any other folder, unless that "edit" is somewhere else as well. I looked everywhere I could find.

---

### Post by JKyleOKC on 2010-04-30
Try pressing ctrl, alt, and F2 all at the same time (similar to Windows' famed three-finger salute). This should give you a black screen with a login prompt. Type your user name, hit enter, and you'll get a prompt for your password. Type the password but you won't see any indication that it's going in. This is a security feature; it's going in even though you can't see any effect from it. Then hit enter again, and you should get a greeting and command prompt. Type "ls -a" without the quotes, to get a directory listing of your home directory, and note the name of the folder where your game's files are stored.

Next, type "cd" followed by a space and the name of that folder. You should get a prompt that includes the folder name. Type the "ls -a" command again to verify that it's the right folder. If it is, type "rm *" to remove all of the files from it.

If there are sub-folders, they won't be affected, but this ought to clear up some space so that you can go back to the GUI and use Nautilus to finish the clean-up. To get back, use "ctrl-alt-F7" and you should be home free. If you still don't have enough space, repeat the whole operation with each of the sub-folders in that game folder until you do.

Hope this helps!

---

### Post by LinuxNeubie on 2010-05-01
Thanks Jim! For some reason I couldn't change to any directory which had a space in it, say My Documents, without putting "cd My*" which was fine in that instance because it was the only folder with "My" in the name. I managed to free up the space to allow Nautilus to load, then trashed it through the GUI, but wondered how to change at the command line when the directory\folder\file isn't the old joliet 8 character type? Thanks!

---

### Post by HermanAB on 2010-05-01
Quote strings that contains spaces.

---

### Post by jvc26 on 2010-05-01
> **HermanAB said:**
> Quote strings that contains spaces.

As in:

```
"/path/to/My Documents"
```

In case you wondered.

J

---

### Post by clhsharky on 2010-05-01
HI LinuxNeubie

I like making

/swp 'sightly larger than ram'
/'root'10GB min - 20GB
/home 'twice the size as root'
What ever is left storage.

Never ran out of space, or slow downs for lack of.
Easy to reinstall or to upgrade.

Sharky

---

### Post by LinuxNeubie on 2010-05-01
Sharky, how would you change-rearrange the partitions? or is it easier just to wipe\reinstall? I haven't installed anything yet other than what the OS installed by default and My Documents which was a mistake since I can just grab them whenever I want them.

---

### Post by JKyleOKC on 2010-05-01
If you don't have any extras or data installed, the simplest route is to simply re-install and tell the program to use the whole disk (if it's not a dual-boot installation). I normally set "/" to be 5 GB, /swap to be about 125% the size of my RAM (so that I can hibernate), and give the rest of the disk to /home since that's where all my data plus my configuration files will go. However you might be more comfortable with 10 GB for "/" especially if you plan to install additional programs; they will go into /usr most of the time, and that's part of "/" (as is /boot). On this machine, for instance, my "/" partition has only 1.7 GB free, but it hasn't grown appreciably in the past six months. However /home has 162 GB free!

---

