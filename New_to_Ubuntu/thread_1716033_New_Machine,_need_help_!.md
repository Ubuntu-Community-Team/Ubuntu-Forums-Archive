---
title: "New Machine, need help !"
date: 2011-03-27
forum: New to Ubuntu
---

### Post by COMPUTIAC on 2011-03-27
[SIZE=3]Hello, got a new HP pavilion P6720f, Win7 64 bit.

  I want to put all my Ubuntu 10.10 things on here. How do I 
accomplish this ?

 I do have the disks I burned for 10.04 and 10.10 . 

 Doing the dual boot is no problem, I need to know how to transfer things like bookmarks, Tweak, and so on.

Thank's
[/SIZE]

---

### Post by fabricator4 on 2011-03-27
> **COMPUTIAC said:**
> [SIZE=3]Hello, got a new HP pavilion P6720f, Win7 64 bit.

  I want to put all my Ubuntu 10.10 things on here. How do I 
accomplish this ?

 I do have the disks I burned for 10.04 and 10.10 . 

 Doing the dual boot is no problem, I need to know how to transfer things like bookmarks, Tweak, and so on.

Thank's
[/SIZE]

Just copy everything in /home/username including all the hidden directories.  This will get everything that is able to be copied.  You might have to be careful with mail files, since the default mail program may run at boot and hold the files open.  The safe way seems to boot off live CD (or another partition) and do the copy.  The file permissions should copy over also,(assuming your username is the same on the new machine) but if they don't the worst that you'll have to do is recursively take ownership of everything in the directory.

Chris.

---

### Post by fabricator4 on 2011-03-27
For other system tweaks and so on, you should be able to copy the relevant config files for each program if they exist outside of you the /home directory.  A little research may be required for each program in this case, but most things really should be in the /home/username directory.

Chris.

---

### Post by COMPUTIAC on 2011-03-27
Hello fabricator4,  so you are saying to put in the 10.04 disk in the old machine, then copy the home folder to that ?

  If so, how do I get them to the disk ?

---

### Post by mastablasta on 2011-03-28
you ut an empty disk in computer burn the home/user folder to it. don't forget to add the hidden files (ctrl + h to show them in nautilus)
 
Linux mint has a nice backup tool (can alos be used in Ubuntu) to help you do this - back up all files in Home and programmes and then you simply move them to your new install and extract them. or use the same tool to put them back where they belong.
 
PPA for the tool: [https://launchpad.net/~webupd8team/+archive/mintbackup](https://launchpad.net/~webupd8team/+archive/mintbackup)
 
and here is some instructions on how to use it: [http://community.linuxmint.com/tutorial/view/2](http://community.linuxmint.com/tutorial/view/2)
 
the isntructions are written fi you do a Linux Mint upgrade (i.e. fresh install but want the old data) But it can be usefull in your case as well since you will also do a fresh install and use old data/settings for it.

---

### Post by kiran1247 on 2011-03-28
Hello COMPUTIAC - 

3 months back only I brought one new HP laptop  , and successfully installed "Ubuntu10.10" without any issues.

Now using/working Ubuntu without any issues.

Thanks
Kiran

---

### Post by fabricator4 on 2011-03-28
> **COMPUTIAC said:**
> Hello fabricator4,  so you are saying to put in the 10.04 disk in the old machine, then copy the home folder to that ?

  If so, how do I get them to the disk ?

Kind of.  Boot off the LiveCD, then copy the files to a USB stick or an external HDD, or burn to a DVD.  It depends on how much data you have, and what is easiest for you.

I like DVD backups because they are semi-permanent snapshots.  Most often when I change machines or hard drives I like to make a set (or two sets in some cases).  Once I've finished loading the data back I give it or the other set to my brother for safekeeping - off-site backups! :-)

I've only had to go to the second backup set once, when the first one got lost.  

There's also [Ubuntu One]("https://wiki.ubuntu.com/UbuntuOne/Tutorials/FileSharing") if you've got plenty of internet bandwidth and not too much data.

If none of these backup/restore options work for you, then you could get a crossover network cable and join the two machines together, then configure Samba to share folders to transfer files over.  If you haven't done this before there will be a little learning curve, but valuable experience.

Chris.

---

### Post by COMPUTIAC on 2011-03-28
Hello fabricator4, you are saying to put the live CD in the old machine ? Why ?

  I have 10.10 installed on it already.    I do have DVDs to use.

I can save Thunderbird in this manner also ?  With all settings ?

  Sorry for all the questions, just don't want to mess this up.

How do I make the font larger in FF 4.0 


        Thank's

---

### Post by fabricator4 on 2011-03-28
> **COMPUTIAC said:**
> Hello fabricator4, you are saying to put the live CD in the old machine ? Why ? 

Because you many not be able to copy all open files.  Try it and see if it works, if it does then there's not need to use a separate boot.

> 
I can save Thunderbird in this manner also ?  With all settings ?


Well, that's the problem.  Thunderbird may have open files.  This is more likely to be a problem for the system that you are replacing the files onto.

You should be able to stop any daemons that Thunderbird has running, but you might have to do a bit of research to find out what they are.

> 
How do I make the font larger in FF 4.0 


Well, apart from changing the preferences, I find the <ctrl><scroll-wheel> zoom to be very handy on sites with tiny or huge fonts.

Chris.

---

### Post by COMPUTIAC on 2011-03-28
Hello fabricator4, so if I boot with 10.04 this will leave all or most of the programs closed, and I will have a better chance of copying them without any problems ?

  I can copy bookmarks the same way ?

---

### Post by fabricator4 on 2011-03-28
> **COMPUTIAC said:**
> Hello fabricator4, so if I boot with 10.04 this will leave all or most of the programs closed, and I will have a better chance of copying them without any problems ?

  I can copy bookmarks the same way ?

Yes, and everything you really need is in /home/username

Just make sure you copy all the hidden files and directories.  I think you'll find all the firefox setup and favourites are in /home/username/.mozilla

In addition, if both machines are 10.10 then I suggest you copy all the .deb files in /var/cache/apt/archives/ as well.  These are the install files for all the updates and all the programs you added.  You'll still have to install them, but at least you won't have to download them again.

Chris.

---

### Post by COMPUTIAC on 2011-03-28
Hello fabricator4, I should install 10.04 on the new machine, update to 10.10,
  first,

 then insert the disk I just burned from the old machine, to add all the settings and stuff ?

  Thank's for your time and patience with me.

---

### Post by fabricator4 on 2011-03-28
> **COMPUTIAC said:**
> Hello fabricator4, I should install 10.04 on the new machine, update to 10.10,
  first,

 then insert the disk I just burned from the old machine, to add all the settings and stuff ?


No, just install 10.10 on the new machine.  There's no need to mess around with 10.04 if you want to run 10.10 on the new machine.

As soon as you do the install, copy the /home/username directory over (you use the same login name on both computers) and the copy the .deb installation files over.  Now you an can run update manager, and install any programs you need.

Chris.

---

### Post by COMPUTIAC on 2011-03-28
Hello fabricator4, I have the old machine running now. It is off-line.  How can I copy all the folders at once ?

  There is 68 of them after doing Ctrl+h

Can I close the home folder and still copy everything ?  or do I have to send each one to the burner ?

Where do I find the .deb installation files ?

---

### Post by fabricator4 on 2011-03-28
> **COMPUTIAC said:**
> 
Can I close the home folder and still copy everything ?  or do I have to send each one to the burner ?

Copy all of them in one operation in Brasero.  Once the burn has started you don't need the file manager window.

For the most reliable disk burn, use the slowest possible speed.

Chris.

---

### Post by COMPUTIAC on 2011-03-28
Hello, I close the home folder or not ?

---

### Post by fabricator4 on 2011-03-28
> **COMPUTIAC said:**
> Hello, I close the home folder or not ?

Yes, you can close the home folder in File Manager once the Brasero burn has started.

---

### Post by COMPUTIAC on 2011-03-28
Hello, I found a copy I made a couple weeks ago from Clonezilla.

  Can I just use this ?

---

