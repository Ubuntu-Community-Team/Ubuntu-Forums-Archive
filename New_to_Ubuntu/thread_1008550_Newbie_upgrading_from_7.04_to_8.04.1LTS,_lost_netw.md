---
title: "Newbie upgrading from 7.04 to 8.04.1LTS, lost network connection"
date: 2008-12-11
forum: New to Ubuntu
---

### Post by stpike on 2008-12-11
I am trying to upgrade from 7.04 to 8.04LTS in a dual boot system(XP on the other half of the disk). I used the System->Administration->Update Manager to go to 7.10 first and was unsuccessful.  Then I re-installed 7.04 and lost my network connection.  

I have the 8.04LTS ISO disk in my desire to just load that version cleanly but it states that partition 3(sda) which contains 7.04 at 27% of the (4.6GB) is 'Too small size' for 8.04.01 at 73% (12.2GB).

I have a Lenovo T60 with an 80GB hardrive and originally used the 7.04 ISO to split the disk in half for Ubuntu.  That worked fine then.

What should I do to get to install the 8.04LTS Ubuntu?

Thank you

---

### Post by cmay on 2008-12-11
can you put the disk of the hardy upgrade version in and then just run it from there. it works on my hardy to intrepid. other wise you may have to install all over again using the iso of the hardy after formatting the partions on the hard disk. you need to back up everthing either way i guess just to be safe.

---

### Post by albinootje on 2008-12-11
The easiest and fastest approach is to backup /etc and /home to some external usb-disk, and then do a fresh install of Hardy Heron.

After the installation you would put the data from /home back.
(a copy of /etc is handy for the config of X, and when you perhaps
have a customized /etc/network/interfaces for wireless)

What you need to know here :

* Backing up means also backing up hidden files and directories!
  for example dot-mozilla dot-mozilla-thunderbird in your home-dir(s)
  ( like .mozilla/ )
  Make sure you use a copy process or backup-program which supports this,
  or use archiving-software to zip the content.

* Before you start firefox for the first time after the install,
  copy .mozilla/ back from the backup in your home-directory,
  and adjust the permissions like :
  sudo chown -R username:username /home/username/
  where "username" is the name of your user in the new install

---

### Post by stpike on 2008-12-11
I can install the Hardy Heron ISO disk and it boots and loads fine, when I try to install it, it reports that SDA3 is too small. (The message received is in my original request for help)

I am a beginner with Ubuntu and Linux.  How would I reformat the 40GB partition that was created for the Feisty Fawn (7.04) I originally and sucessfully loaded?

Thanks

---

### Post by Michael.Godawski on 2008-12-11
To resize partitions I would use the Gparted live cd
[http://gparted.sourceforge.net/index.php](http://gparted.sourceforge.net/index.php)

tutorial:
[http://gparted.sourceforge.net/larry/resize/resizing.htm](http://gparted.sourceforge.net/larry/resize/resizing.htm)

---

### Post by albinootje on 2008-12-11
If you have internet connection you can install gparted while using the Hardy Heron install cdrom. Just open a terminal, and type in :

sudo apt-get update
sudo apt-get install gparted

and then :
sudo gparted

---

### Post by sneeks on 2008-12-11
As above,use gparted to partition the drive,then all should be well..

---

### Post by ajgreeny on 2008-12-11
Gparted is already on the live CD so no need to install it first.

I think you need to backup everything first as albinootje said and then start again from scratch, by deleting the current ubuntu partitions and then installing, but using the Manual partitioning when you get to that point in the install.  This will allow you to make new root and swap (and home) partitions as you want in the free space from where you deleted the old ubuntu.  It's not as difficult as it sounds, and as long as you have backed up properly you will always have that if anything goes wrong.

---

