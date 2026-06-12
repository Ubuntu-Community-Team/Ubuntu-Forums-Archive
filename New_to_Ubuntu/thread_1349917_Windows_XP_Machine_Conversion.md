---
title: "Windows XP Machine Conversion"
date: 2009-12-08
forum: New to Ubuntu
---

### Post by tapupartforpres on 2009-12-08
Hello new and newbie here.

I have a 2.53 mhz, P4, 160 GB HD, with 768 RAM with Windows XP on it.  I wanted to set up a file server for home use and wanted to know the best way to do this.  I have 2 Windows machines and a Mac cpu on a wireless network.  My friend mentioned to set up an ubuntu server but didn't give any specifics.   Any ideas?

Thanks

---

### Post by teward on 2009-12-08
Setting up an Ubuntu server will completely wipe windows on your computer, and you can only use Ubuntu because if you don't the server goes down.

you technically don't even need to use Ubuntu Server Edition.


I set up a networked file storage on ym Desktop, using Ubuntu Desktop Edition 9.04.  I installed openssh-client, and its dependencies, got my Desktop to act as an SSH server, and now I use sftp to access the data through either my account, or a user with the name guestssh.


Regardless of what way, you're going to have to ditch the idea of ever using Windows on that computer again.

---

### Post by LeifAndersen on 2009-12-08
You're going tow ant some sort of LAMP setup.  Ubuntu Server can give you that out of the box, if your willing to play with the terminal.  So, what I would do if you're new to ubuntu, and don't want to learn the unix command line, is go to: [http://www.ubuntu.com/products/whatisubuntu/serveredition](http://www.ubuntu.com/products/whatisubuntu/serveredition) download and burn the iso.  Once you've installed it ```
sudo apt-get install ubuntu-desktop
``` from there, you're golden.  Put everything you want to be put on a semi-public html page in /var/www.

---

### Post by chillyomi on 2009-12-08
Well if I understand correctly then you need to download the iso for the Ubuntu Server edition you want I recommend Jaunty Jackalope or maybe you could try Karmic Koala im still getting used to it .

Then again if you don't want to lose windows then you could try dual-booting with GRUB

---

### Post by 3rdalbum on 2009-12-08
> **LeifAndersen said:**
> You're going tow ant some sort of LAMP setup.  Ubuntu Server can give you that out of the box, if your willing to play with the terminal.  So, what I would do if you're new to ubuntu, and don't want to learn the unix command line, is go to: [http://www.ubuntu.com/products/whatisubuntu/serveredition](http://www.ubuntu.com/products/whatisubuntu/serveredition) download and burn the iso.  Once you've installed it ```
sudo apt-get install ubuntu-desktop
``` from there, you're golden.  Put everything you want to be put on a semi-public html page in /var/www.

You want to run Apache, MySQL, and PHP as a FILE server?! And you want the poster to start out with a command-line and install the desktop on top of it?

Ubuntu Server and Ubuntu Desktop are the same thing; one has a GUI the other doesn't. Install the regular Ubuntu desktop edition, and follow what I just posted to this other person: [http://ubuntuforums.org/showpost.php?p=8465840&postcount=9]("http://ubuntuforums.org/showpost.php?p=8465840&postcount=9")

---

### Post by tapupartforpres on 2009-12-08
> **TrekCaptainUSA said:**
> Setting up an Ubuntu server will completely wipe windows on your computer, and you can only use Ubuntu because if you don't the server goes down.

you technically don't even need to use Ubuntu Server Edition.


I set up a networked file storage on ym Desktop, using Ubuntu Desktop Edition 9.04.  I installed openssh-client, and its dependencies, got my Desktop to act as an SSH server, and now I use sftp to access the data through either my account, or a user with the name guestssh.


Regardless of what way, you're going to have to ditch the idea of ever using Windows on that computer again.

That is a good idea.  But I think I want the full server addition.

---

### Post by tapupartforpres on 2009-12-08
> **chillyomi said:**
> Well if I understand correctly then you need to download the iso for the Ubuntu Server edition you want I recommend Jaunty Jackalope or maybe you could try Karmic Koala im still getting used to it .

Then again if you don't want to lose windows then you could try dual-booting with GRUB

Thanks for the reply.  What does Jaunty Jackalope or Karmin Koala do?  Will it dual boot?  I would like to keep Windows on there just in case.  But for the most part I would keep it booted in Ubuntu as a file server.  Some suggestions I see is that you need 2 hard drives to accomplish this.  What do you suggest?

---

### Post by tapupartforpres on 2009-12-08
> **3rdalbum said:**
> You want to run Apache, MySQL, and PHP as a FILE server?! And you want the poster to start out with a command-line and install the desktop on top of it?

Ubuntu Server and Ubuntu Desktop are the same thing; one has a GUI the other doesn't. Install the regular Ubuntu desktop edition, and follow what I just posted to this other person: [http://ubuntuforums.org/showpost.php?p=8465840&postcount=9](http://ubuntuforums.org/showpost.php?p=8465840&postcount=9)

So you think using Ubuntu Desktop is the way to go?  So it will install in Windows and then share it.  Will that work well using Windows and Mac clients?  So I will not have to reformat the drive.  So I just load on the desktop and follow your instructions?  Thanks for your help.

---

### Post by ECPCLINUX on 2009-12-08
Hi, I'm what I like to call a "Forever newbie" so maybe my way will help in some way. I was tired of having 4 external laying around my desk (5 if I count my wife's) and trying to figure out where our files were saved. Hence, I used some old parts I had laying around and made a home server. I honestly don't know if this is the best way nor the most efficient. But here goes what I did. After I dismantled our externals I installed them on the newly made, from old parts, computer. Installed Ubuntu Desktop x32 bit 9.10 edition. Once installed, I opened synaptic and installed Samba. Once Samba was installed I was able to share with Windows Vista, Ubuntu and 7. It got a bit more complicated with the secondary hard drives, but doable.

---

