---
title: "remastersys"
date: 2008-12-27
forum: New to Ubuntu
---

### Post by cigtoxdoc on 2008-12-27
I am trying to use remastersys GUI version.  Even though I am only person using my pc and I tell remastersys to put the output file in my own director, it stikll locks things up with root ownership.  I have tried su chown  but I keep having to drill down to lower subdirectories to change their ownership to.

I just want an image I can burn to my DVD.  What am I missing that is making life so difficult?

John

---

### Post by LowSky on 2008-12-27
soory i'm a little buzzed at the moment, but remastersys was really easy to use, when I made a back up on my machine. I'm kinda confised on what your problem is?

if it askes for sudo access then do it.. you can t acces any root files unless you have root (sudo) access. The only folder you dont need root access to is your own home folder. Thats basic linux 101, sorry to make it sound angry (or drunk) but the rules that went with Windows don't apply here

---

### Post by cigtoxdoc on 2008-12-27
Even when opening nautilus with gksudo, I could not do anything it terms of burning an image until I changed the ownership of everything from root.  The there were files way down in the subdirectories that were corrupted, etc, and had to be changed manually.  Next I find that DVD Creator does not like DVD-RW media and I have to use Brasero.

Another problem is that I have many 0-byte files (e.g., sockets).  Do I delete them?

John

---

### Post by Fragadelic on 2008-12-31
You shouldn't use your own home directory for remastersys.

What version of remastersys are you using?

What you are speaking of was a bug from a very long time ago.

I'm the author of remastersys and I'd love to know where you are getting the old version from?

---

### Post by cigtoxdoc on 2009-01-03
Please excuse my delay in replying to your post as I was not in my office where the PC with the remastersys is located.

According to my Synaptic Package Manager, I am using version 2.0-10, and it appears that I obtained the software by adding a line in my sources.list that pointed to your website.  

John

---

### Post by Fragadelic on 2009-01-08
Since you run the script as root(sudo) of course everything will be root permissions when the directory is created in there.

Why don't you just let it be /home/remastersys like the default is - if you /home is on a separate partition, it will make no difference.

I made the default /home/remastersys since most folks will have the largest partition for /home if they have them separated in different partitions and if they are all 1 partition, no difference.

When you issue a mkdir -p command like remastersys does, it will change the permissions to root:root since it is the root user issuing the command.  This is why you should never do anything in your home folder as root like create directories or anything.

If you are completely stuck, use the original ubuntu cd live and then do the following:

cd (to the folder where you mounted your /home partition)
sudo su
chown -R user:user ./user - where user is your actual username
cd
umount /(wherever you mounted your folder)
exit


Now reboot and you should be back to normal.

I'll have to put a warning up about that I guess but in the 2 years I've had remastersys out there, this is a first for this issue.

---

