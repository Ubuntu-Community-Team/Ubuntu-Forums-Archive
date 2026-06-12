---
title: "Integrating a 2nd hard drive."
date: 2010-11-24
forum: New to Ubuntu
---

### Post by s1wood on 2010-11-24
I'm running out of space on my rather small primary drive so I have just inserted another old drive I was previously using in a caddy. This was Linux formatted and has a certain amount of stuff stored on it. It is working perfectly well as a storage device but I would like to integrate it with the main drive, to be able to use panel launchers and to download and run programs and so on. 
How do I do this? The only way I can think of is to move the stuff and do an Ubuntu install on it:  will the two then work together (like a Windows C & D drive) or will they want to dual-boot? I feel there must be a more elegant solution.  I'm using Meerkat.

regards,

Susan

---

### Post by yankysunny on 2010-11-24
So u have a Ubuntu installed at one machine which is on low disk space and u want to use another hd with it?
If i understood correctly then wht is " to be able to use panel launchers and to download and run programs and so on." U mean to say that you want to install ubuntu on this machine?

---

### Post by eriktheblu on 2010-11-24
There is no need to reinstall, and I am a bit confused by what you're saying about panels and downloads. 

The Linux file system is quite different from Windows in that it allows you to designate any disk or disk partition to any point in the file system you choose. 

What are the sizes of your drives?

Assuming your new drive is larger, I would make that a data drive and keep the smaller one for the OS. Simply move the contents of /home to the new drive, then edit /etc/fstab (ok, editing fstab is not that simple) to reflect the new destination. There are a few online guides for this such as [https://help.ubuntu.com/community/Partitioning/Home/Moving]("https://help.ubuntu.com/community/Partitioning/Home/Moving")

With two HDDs I recommend dividing your swap space over both disks for improved performance.

---

### Post by s1wood on 2010-11-24
Actually the two disks are the same size - only 20Gb each. I don't have a lot of data, I was OK on one disk till I installed Virtualbox to run Windows on, which takes up more space than I had expected. I might invest in a bigger disk some day but that will still give me the same problem.

The 2nd drive appears on my desktop as a storage device and it won't allow me to create panel launchers for more direct access to its folders, nor do I get an option to install new programs to it which is what I want to do.  GParted shows it as sdb2 and it is formatted in FAT32.

I have looked at that guide and it is a bit beyond my capabilities, I am not very good with the terminal unless given very simple instructions and that looks too risky for experimentation.

I would like to move Virtualbox, but I have no idea if it would work on the 2nd disk and I don't get an option to install it there and start again (not that I want to do another Windows install anyway!). I probably should have thought of all this before I installed the disk but I can't be the only person to have this problem.

regards,

Susan

---

### Post by yankysunny on 2010-11-24
I think that you want direct access for the folders on the external disk. You can create the launcher which can directlt point to folder you want to access. 

I am not pretty sure that you can install the softwares on other disk as many config files are stored on /etc and bin files at /bin and may be other files.

I think moving your VirtualBox image would be good option. There must be a folder HardDisks and machins in the ./VirtualBox folder in your home folder. You can move the contents of the folder and then when you start the virtual box point them the image disk. It may take of couple of Gbs from the old disk

---

### Post by s1wood on 2010-11-25
I think I've got the answer - the format wasn't appropriate! 
I moved my stuff and reformatted the drive to Ext 2 and now it seems to be doing what I want. NB I tried Ext3/4 but they denied me permissions.
I can create panel launchers from this drive now - they aren't working but that's another thread. 
Being able to install programs to the new drive would be nice but, to be honest, I'm not expecting to want any new ones for a while so Virtualbox may as well stay wher eit is.

Thanks for the advice.

Susan

---

