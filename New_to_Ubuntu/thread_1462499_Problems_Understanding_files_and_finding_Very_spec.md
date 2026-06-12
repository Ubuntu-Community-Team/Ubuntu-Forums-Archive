---
title: "Problems Understanding files and finding Very specific files"
date: 2010-04-25
forum: New to Ubuntu
---

### Post by orphanlast on 2010-04-25
I'm somewhat confused with the FILE SYSTEM folder or generally about important files to the computer.

I'm not even sure what I'm looking at. And sometimes, if I'm saving something, it shows folders in this place that I can never access, even when I try to show hidden files.

It's not just that I don't know what I'm looking at, I just don't know what the practical use for any of these things are and I feel I need to know.

**bin** - I have no idea what this folder is for.

**boot** - I can only assume this helps the computer boot up or something.

**cdrom** - I take it this is where all the files from a CD go when it's inserted into the computer

**dev** - I'm sure this is an abbreviation for "Developer" (singular or plural) but my question is "What about developers?" 

**etc **- maybe this is like saying eccentric... a place for Miscellaneous folders go???

**Home** - This is my home folder that leads to all the usual other files (music, videos, etc)

**lib** - I'm hoping they're going to come out with a file named rep because this seems politically one-sided... lol. I really don't know what that is.

**Lost+found **- I can't even open this folder. I know what a physical lost and found happens to be, but I don't know why I would want a lost and found folder on my computer, and it serves even less of a practical use if I can't even open it.

**root** - I have no idea

**sbin** - I have no idea

**selinux** - I know what "linux" is but I don't know what "se" would happen to be

**srv **- I have no idea

**sys** - An abbreviation for "system" but all of these programs seem to be important to the computer in general. So I have no idea what part of the "System" it would be referring to.

**tmp** - I've found out that this is where all the temporary files go. So far, my only practical use for this sucker is to get a youtube video to fully buffer, go here, and copy and paste the video to another folder and TA DAH! I just downloaded a youtube video.

**usr** - I'm sure this is an abbreviation for "user" but I don't know what practical use this folder has

**var **- I have no idea.

I mentioned that if I was in a save menu or something, then some of the files don't even show up. Here's a good example. I have used Virtualbox and deleted some of my virtual computers but there's a small file fragment of them that still remain. When I go into the save window it shows that some of these old computer names are in /home/orphanlast(that's the name I placed for my computer)/.virutalbox/hardisk 

When I go /home/ I a set of files, but none of them say "orphanlast" but I'm sure that's okay. I've pressed CTRL+H but that doesn't show "orphanlast" either, and it also doesn't show anything called ".virtualbox".

So, right now, I'm forced to have all these irritating file fragments on my computer.

---

### Post by WinterWeaver on 2010-04-25
[http://ubuntu-tutorials.com/2006/12/20/explanation-of-the-ubuntu-linux-file-structure-ubuntu-all-versions/](http://ubuntu-tutorials.com/2006/12/20/explanation-of-the-ubuntu-linux-file-structure-ubuntu-all-versions/)

[http://www.tuxradar.com/content/take-linux-filesystem-tour](http://www.tuxradar.com/content/take-linux-filesystem-tour)

[http://tldp.org/LDP/intro-linux/html/sect_03_01.html](http://tldp.org/LDP/intro-linux/html/sect_03_01.html)

---

### Post by thomas144 on 2010-04-25
I think the WinterWeaver provided some good links. If you're anything like me, you'll only get less confused over time. "File System" is basically the home of all of Ubuntu's files. By the way, you need to be a super user (often called the root user) to access the /root and /lost+found folders. If your curiosity is too much to suppress, go to Applications>Accessories>Terminal. You will see a screen with some text. Type in
```
 
gksudo nautilus

```
and press Enter on your keyboard. You wil be able to read and write almost anything, but if you look and not touch, you should be okay. Don't forget to exit the file browser and Terminal when you're done. Doing these actions mean root privalages, so you have to be a little careful.

---

### Post by tica vun on 2010-04-25
/home/username is the one you're looking for. That's the directory you (the user) have full read+write permission for, ie your home folder. This is where you can save your stuff and where all your user-specific settings are saved by individual applications. You shouldn't concern yourself with the rest unless you're looking to edit a specific config file, most of which should be somewhere in in /etc (which, by the way, stands for "extended text-based config files"). Installed software goes in various places, the binaries are in /bin and /usr/bin, the configurations (as mentioned) in /etc/, other files in /usr. /var contains variable files - the files that are expected to change frequently - this means mainly system logs. /media is where mounted devices (flash drives, CDs, etc) show up by default. /boot is where the bootloader is installed. That basically covers it.

---

### Post by quadproc on 2010-04-25
> **orphanlast said:**
> I'm somewhat confused with the FILE SYSTEM folder or generally about important files to the computer.

I'm not even sure what I'm looking at. And sometimes, if I'm saving something, it shows folders in this place that I can never access, even when I try to show hidden files.
...

You have received some good explanation sfrom other posters about files and I would like to add one comment:

On Linux or Unix, every possible place for data is a file.  Therefore, files include disk files, CDROMs, USB flash memory drives, floppy disks, pipe files, terminal windows, keyboards, and even the system memory.  Plus many other possible file types.  This concept can be confusing at first because the traditional meaning of the word file suggests a more limited scope, but as you become familiar with the system you will see the usefulness of the Linux file concept.

Welcome!

quadproc

---

### Post by oldos2er on 2010-04-25
dev = device

usr = Unix System Resources

---

### Post by theozzlives on 2010-04-25
If I'm correct /selinux was a security feature developed by Red Hat. I'm not sure, but I think you have to manually activate it.

---

### Post by orphanlast on 2010-04-26
... huh... This is some really weird stuff... 

So even linux just plops all sorts of files in one place. It looks like the "home" folder is pretty much the equivalent to "Program Files" in that a giant mess of folders just gets plopped into there. The only true upside is that they are all hidden files. 

My question is, would it cause problems if I were to organise all these by placing them into an organised set of folders to my liking? Or would that screw up the path that these programs have been designed to follow through?

---

### Post by Merk42 on 2010-04-26
> **orphanlast said:**
> ... huh... This is some really weird stuff... 

So even linux just plops all sorts of files in one place. It looks like the "home" folder is pretty much the equivalent to "Program Files" in that a giant mess of folders just gets plopped into there. The only true upside is that they are all hidden files. 

My question is, would it cause problems if I were to organise all these by placing them into an organised set of folders to my liking? Or would that screw up the path that these programs have been designed to follow through?

/home is more equivalent to My Documents, or actually "Users" if referring to Windows 7.

It only contains the configuration files for applications, not the applications themselves.  That is really a key difference between Windows and Linux organization.  Windows organizes based on where they came from (ie all files related to a program are in the same folder), where as Linux organizes based on what they do (all configs are in the same folder)


Without a lot symlinks, yes it would break it, just as if someone wanted to reorganize Windows folders moving them all around.  Why do you want to anyway? You should only need to go into your /home folder for anything 99% of the time.

---

### Post by orphanlast on 2010-04-26
> **Merk42 said:**
>  Why do you want to anyway? You should only need to go into your /home folder for anything 99% of the time.

Whenever a program decides to just dump files into one place it usually gets to be a bit of a pain in the *** to go about finding out where everything is when you do need to go into there.

---

### Post by Drenriza on 2010-04-26
**bin** - Is a folder for binary commands avaliable to all users.
 
**boot** - Is the boot directory containing kernel and boot loader files.
 
**cdrom** - Is not used anymore in newer versions of ubuntu.
 
**dev** - Contains device files, and is where HDD, cd-rom, external drives is mounted.
 
**etc **- Is the system configuration files. Containing configuration files for the entire system. And all its programs.
 
**Home** - = your home folder in windows
 
**lib** - Contains shared program libaries and kernel modules
 
**Lost+found **- If the system is not properly shutdown. An File System Check will start at bootup.
**Fsck will go through the system and try to recover any corrupt files that it finds. The result of this recovery operation will be placed in this directory**
 
**root** - Is the administrators home folder
 
**sbin** - Contains system binary commands
 
**selinux** - Is a folder, that contains files that add more security to the OS. Not sure how tho.
 
**srv **- Contains files for web-services
 
**sys** - Contains some files that previously was contained in /proc. /proc contains information about the systems state and processes
 
**tmp** - Temporaly files folder
 
**usr** - Contains system commands and utilities.
 
**var **- Contains files that change constantly.
examples.
Printer jobs.
e-mails boxes.
proxy cache files
> **orphanlast said:**
> 
**bin** - I have no idea what this folder is for.
 
**boot** - I can only assume this helps the computer boot up or something.
 
**cdrom** - I take it this is where all the files from a CD go when it's inserted into the computer
 
**dev** - I'm sure this is an abbreviation for "Developer" (singular or plural) but my question is "What about developers?" 
 
**etc **- maybe this is like saying eccentric... a place for Miscellaneous folders go???
 
**Home** - This is my home folder that leads to all the usual other files (music, videos, etc)
 
**lib** - I'm hoping they're going to come out with a file named rep because this seems politically one-sided... lol. I really don't know what that is.
 
**Lost+found **- I can't even open this folder. I know what a physical lost and found happens to be, but I don't know why I would want a lost and found folder on my computer, and it serves even less of a practical use if I can't even open it.
 
**root** - I have no idea
 
**sbin** - I have no idea
 
**selinux** - I know what "linux" is but I don't know what "se" would happen to be
 
**srv **- I have no idea
 
**sys** - An abbreviation for "system" but all of these programs seem to be important to the computer in general. So I have no idea what part of the "System" it would be referring to.
 
**tmp** - I've found out that this is where all the temporary files go. So far, my only practical use for this sucker is to get a youtube video to fully buffer, go here, and copy and paste the video to another folder and TA DAH! I just downloaded a youtube video.
 
**usr** - I'm sure this is an abbreviation for "user" but I don't know what practical use this folder has
 
**var **- I have no idea.


---

### Post by redmk2 on 2010-04-26
> **orphanlast said:**
> I'm somewhat confused with the FILE SYSTEM folder or generally about important files to the computer.

> There is a basic standard layout for the file system on a Linux host.  See [**_here_**]("http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard").

I'm not even sure what I'm looking at. And sometimes, if I'm saving something, it shows folders in this place that I can never access, even when I try to show hidden files.

It's not just that I don't know what I'm looking at, I just don't know what the practical use for any of these things are and I feel I need to know.

**bin** - I have no idea what this folder is for.

Command **[COLOR="Blue"]bin[/COLOR]**ary executables. These are the command you can use on...the command line!> 

**boot** - I can only assume this helps the computer boot up or something.

Correct.  This is where the boot image and the OS kernel live.> 

**cdrom** - I take it this is where all the files from a CD go when it's inserted into the computer


Sort of.  This is the mount point for the CD-ROM device.
> 

**dev** - I'm sure this is an abbreviation for "Developer" (singular or plural) but my question is "What about developers?" 

Nope!  This is where all **[COLOR="blue"]dev[/COLOR]**ices are described. All Linux devices (e.g hard drives, dc-rom, NIC, etc.) are described in individual files.  They live in /dev. > 

**etc **- maybe this is like saying eccentric... a place for Miscellaneous folders go???


More like [COLOR="Blue"]**etc**[/COLOR]etera.  This is where the configuration files for the system reside.  
> 

**Home** - This is my home folder that leads to all the usual other files (music, videos, etc)


This is the home for **all **users. All have a directory under /home (i.e. /home/orphanlast or /home/red or /home/john) 
> 

**lib** - I'm hoping they're going to come out with a file named rep because this seems politically one-sided... lol. I really don't know what that is.


This is where the common libraries for all compiled programs live.
> 

**Lost+found **- I can't even open this folder. I know what a physical lost and found happens to be, but I don't know why I would want a lost and found folder on my computer, and it serves even less of a practical use if I can't even open it.

[QUOTE]
This is where the OS stores corrupted files if the system crashes and you need to recover data.  The super user ***root*** is the only user with rights to this.


**root** - I have no idea

[/QUOTE]
This is the home directory for the user ***root***.
> 

**sbin** - I have no idea


These are the system binaries, such as ***init, fstab, fdisk, mount, etc.***.
> 

**selinux** - I know what "linux" is but I don't know what "se" would happen to be


Secure Linux 
> 

**srv **- I have no idea


Tis is where you can mount external services.  I do not use this.  I use /smb for Samba and /export for NFS.  (/export is the original place that SUN used for NFS). 
> 

**sys** - An abbreviation for "system" but all of these programs seem to be important to the computer in general. So I have no idea what part of the "System" it would be referring to.


Most of this is for external "driver's" for system devices (i.e the drivers for the PCI bus are at [COLOR="blue"]**/sys**/bus/pci[/COLOR]> 

**tmp** - I've found out that this is where all the temporary files go. So far, my only practical use for this sucker is to get a youtube video to fully buffer, go here, and copy and paste the video to another folder and TA DAH! I just downloaded a youtube video.


...and the files are deleted upon your logout.  Hence the temporary moniker
> 

**usr** - I'm sure this is an abbreviation for "user" but I don't know what practical use this folder has


UNIX system resources!  These would be complete app's such as rhythmbox or zip.  These 2 are at /usr/bin.  

> 

**var **- I have no idea.


Variable files (i.e.files whose content continually changes)  this is where the log files are (/var/log) and the Gnome virtual file system configuration for Samba shares (/var/lib/samba).
> 

I mentioned that if I was in a save menu or something, then some of the files don't even show up. Here's a good example. I have used Virtualbox and deleted some of my virtual computers but there's a small file fragment of them that still remain. When I go into the save window it shows that some of these old computer names are in /home/orphanlast(that's the name I placed for my computer)/.virutalbox/hardisk 

When I go /home/ I a set of files, but none of them say "orphanlast" but I'm sure that's okay. I've pressed CTRL+H but that doesn't show "orphanlast" either, and it also doesn't show anything called ".virtualbox".

So, right now, I'm forced to have all these irritating file fragments on my computer.

If I understand this correctly...  Your files should be at /home/orphanlast (not in /home/).

---

### Post by Merk42 on 2010-04-26
> **orphanlast said:**
> Whenever a program decides to just dump files into one place it usually gets to be a bit of a pain in the *** to go about finding out where everything is when you do need to go into there.

Again, other than configuration which is in your home folder, **why** do you need to go in there?

---

### Post by oldos2er on 2010-04-26
> **orphanlast said:**
> Whenever a program decides to just dump files into one place it usually gets to be a bit of a pain in the *** to go about finding out where everything is when you do need to go into there.

What program, what files? Can you give an example?

---

### Post by durand on 2010-04-26
You really should not need to touch *anything* outside you /home/username directory unless you know exactly what you're doing. 99% of programs will either put a menu item in your applications menu or will be a commandline program, in which case you can run it from the terminal. (Applications > Accessories > Terminal). You really don't need to use the root user either, except for sudo (superuser do, temporarilly makes you root). If you move files around in the filesystem, ie /, you will cause all sorts of problems. If you do want to do that sort of stuff, it is possible by being careful and using symlinks. I'd suspect that that is what you really want. [http://en.wikipedia.org/wiki/Symlink](http://en.wikipedia.org/wiki/Symlink)

---

### Post by orphanlast on 2010-04-26
> **durand said:**
> You really should not need to touch *anything* outside you /home/username directory unless you know exactly what you're doing. 99% of programs will either put a menu item in your applications menu or will be a commandline program, in which case you can run it from the terminal. (Applications > Accessories > Terminal). You really don't need to use the root user either, except for sudo (superuser do, temporarilly makes you root). If you move files around in the filesystem, ie /, you will cause all sorts of problems. If you do want to do that sort of stuff, it is possible by being careful and using symlinks. I'd suspect that that is what you really want. [http://en.wikipedia.org/wiki/Symlink](http://en.wikipedia.org/wiki/Symlink)

Yeah... but if you're wanting to move stuff around and customize things in general -- you kinda gotta know where things are in general... or at least understand it.

---

### Post by Merk42 on 2010-04-26
> **orphanlast said:**
> Yeah... but if you're wanting to move stuff around and customize things in general -- you kinda gotta know where things are in general... or at least understand it.

But **why** do you want to move your filesystem files around?  Even if you used a bunch of symlinks and somehow got it to resemble the way Windows organizes them, what purpose would that serve? :confused:

---

### Post by orphanlast on 2010-04-27
No, no... I wouldn't want it to be anything like windows. I hate how programs just dump programs into one place. 

I just like having things organized. I don't HAVE to do it. I've lived with that sort of things with windows my whole life and I'm sure I can live with it on Ubuntu.

---

### Post by durand on 2010-04-27
> **orphanlast said:**
> No, no... I wouldn't want it to be anything like windows. I hate how programs just dump programs into one place. 

I just like having things organized. I don't HAVE to do it. I've lived with that sort of things with windows my whole life and I'm sure I can live with it on Ubuntu.

To be honest, the linux filesystem is actually very organised and logical, if you understand how it works. You seem to be suffering from a windows mentality. It's not that dumping programs is more disorganised in linux, it's just a different hierarchy.

---

### Post by QLee on 2010-04-27
[QUOTE=durand]To be honest, the linux filesystem is actually very organised and logical, if you understand how it works.[/QUOTE]

+1 I agree, it's not less "organised", it's just different and requires a bit of study and learning.


orphanlast, you might want to have a look at this document:
[http://tldp.org/LDP/Linux-Filesystem-Hierarchy/Linux-Filesystem-Hierarchy.pdf](http://tldp.org/LDP/Linux-Filesystem-Hierarchy/Linux-Filesystem-Hierarchy.pdf)

---

### Post by egalvan on 2010-04-27
> **thomas144 said:**
> 
 , **you need to be a super user (often called the root user) to [COLOR="Red"]access[/COLOR] the /root and /lost+found folders.**

No, root is NOT needed to access these folders.
files can be READ (accessed safely) without root privileges 
root is needed to CHANGE (write, delete) or EXECUTE.


>  You wil be able to read and write almost anything, but if you** look and not touch**, you should be okay.
 Don't forget to exit the file browser and Terminal when you're done.
 Doing these actions mean root privalages, **so you have to be a little careful**.

MUCH safer to** not use root**, then you don't have to worry about not "touching"

.

---

### Post by orphanlast on 2010-04-28
Actually, I don't know why you guys say that I'll never really go into this thing because if I want something new in my menus then I have to constantly go to SYSTEM>PREFERENCES>MAIN MENU and then if I need to manually add an application to the menus then I need to select NEW ITEM, type in its name and sometimes I can just type in its name again in the COMMAND field, but that's only on a rare occasion. Normally I have to click BROWSE where I've confronted with all of these files... I'm constantly using this folder. The most irritating thing is that some of these files aren't named the same thing as the name of the actual program they represent.

---

