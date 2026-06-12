---
title: "How to administer an Ubuntu PC?"
date: 2009-01-23
forum: New to Ubuntu
---

### Post by melrokz on 2009-01-23
Now, suppose i set up Ubuntu 8.10 in the PC's of my cyber-cafe. The PC configuration is P4 proc, 256MB RAM, Intel 845GL video card, 80GB HDD with Ethernet router - speed 2Mbps.

1. I'd like to give users a password, but prevent them from installing software or making system-wide changes. Apart from changing file permissions, is there any other way?

2. If i have to change file permissions, which all files and what permissions?

3. Ubuntu 8.10 can run on 256MB RAM?

4. Why are flash animations taking 100% CPU load?

5. How to lock disk drives? (ntfs, ext3, fat32)

6. How 2 install Openoffice 3 from the site?
   (Only the RPM version is available?)

---

### Post by taurus on 2009-01-23
1.  As long as the new users don't belong to group admin in /etc/group, then they can't install or change system files.  They can only modify files in their own $HOME.

2.  What files are we talking here?  Chances are you don't have to do anything.

3.  Gnome will run on 256MB of RAM but slow.  XFce4 is another option.  How large is your swap partition?

4.  Maybe because you have a slow machine.

5.  If you don't want people to access those partitions, either change permissions or mount them in such a way that only root can access them.

6.  Edit /etc/apt/sources.list and add this line to the end of it.

```
deb http://ppa.launchpad.net/openoffice-pkgs/ubuntu intrepid main
```

6a.  There is a .deb version if you look for it hard enough.

---

### Post by stchman on 2009-01-23
> **melrokz said:**
> Now, suppose i set up Ubuntu 8.10 in the PC's of my cyber-cafe. The PC configuration is P4 proc, 256MB RAM, Intel 845GL video card, 80GB HDD with Ethernet router - speed 2Mbps.

1. I'd like to give users a password, but prevent them from installing software or making system-wide changes. Apart from changing file permissions, is there any other way?

2. If i have to change file permissions, which all files and what permissions?

3. Ubuntu 8.10 can run on 256MB RAM?

4. Why are flash animations taking 100% CPU load?

5. How to lock disk drives? (ntfs, ext3, fat32)

6. How 2 install Openoffice 3 from the site?
   (Only the RPM version is available?)

1.  Go to System--->Administration--->Users from there you can create users and give/take user admin privileges.

2.  Be more specific.

3.  Yes, but barely.  I recommend minimum of 512MB.

4.  If you have small amounts of RAM and a slow processor.

5.  In the fstab mount them but do not give write privileges.

6.  There is a DEB version of OO3 available.

---

### Post by Bölvaður on 2009-01-23
> **melrokz said:**
> 
1. I'd like to give users a password, but prevent them from installing software or making system-wide changes. Apart from changing file permissions, is there any other way?

Any other way?
Normal setup with additional user (perhaps named customer, unprivileged) that has no rights will probably do just fine if I understand you, I do not see why anyone would need to change file permissions on other than files they own.


> **melrokz said:**
> 
2. If i have to change file permissions, which all files and what permissions?
Can you rephrase that please?


> **melrokz said:**
> 
3. Ubuntu 8.10 can run on 256MB RAM?

Yes but you may want to use different software than you would on more ram. Also you are forced to install via Alternate install disk, not livecd.
Software to think about: Openbox, and put Openbox/GNOME session as default.
... something eother than pidgin.. it takes about 40mb I think

> **melrokz said:**
> 
4. Why are flash animations taking 100% CPU load?

Probably because flash is very cpu heavy and poorly optimized format (flash kind of sucks kind of pretty hard). That can be clearly seen on pcs that do not have enough processing power. I do not know if installing flash 10 will help much, but atleast you can try it.

> **melrokz said:**
> 
5. How to lock disk drives? (ntfs, ext3, fat32)

Lock? Do you mean like not showing the user that there are anything else than /home/customer/ ?


> **melrokz said:**
> 
6. How 2 install Openoffice 3 from the site?
   (Only the RPM version is available?)
Never install anything from websites unless if it is last resort, this is linux we are uber secure as long as we dont install random stuff ;)
[http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml]("http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml")

in software sources add:

deb [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) intrepid main

the howto can be found if you google: "installing open office 3 ubuntu"
it is the second link.

---

### Post by melrokz on 2009-01-23
By file permissions, I mean the files used for installing software like apt and synaptic are to be locked down only to be used by giving root password.

---

### Post by cmay on 2009-01-23
i am no expert at this but given the ram and other specs and the suggestions to use something lighter as xubuntu i know there is a minimal official ubuntu.iso available  which can be useful since you can build it pretty much from base . then i would use open-box as desktop or lxde which is very light. the thing is that open box gives a pretty good option to how the menu configures by either a menu editor or by xml editing by hand . its easy to customize in my opnion. i have single computer where my guests can login automatic and use the two only menu options that is webbrowser and exit. i use jwm as desktop on that one bt can be done just as easy on open box.

---

### Post by dawynn on 2009-01-23
Ubuntu typically has everything set up already so that ordinary users can't damage system files.  I have a mostly default Ubuntu installation, and every time I need to change a system file, there's some kind of password protection involved.

I can freely access my $HOME directory without problems, but not system files.

---

### Post by melrokz on 2009-01-23
Could you plz give the download link 4 openoffice3 .deb version and the link to the installation instructions?

---

### Post by ugm6hr on 2009-01-23
[http://tombuntu.com/index.php/2008/10/14/install-openofficeorg-30-in-ubuntu-804-and-810/](http://tombuntu.com/index.php/2008/10/14/install-openofficeorg-30-in-ubuntu-804-and-810/)

---

### Post by dawynn on 2009-01-23
Something to consider for a Cyber Cafe -- if you're primary purpose for the machine is a web browser:

[http://kiosk.mozdev.org/](http://kiosk.mozdev.org/)

Poke around a bit and you'll see that they even have a CD built ready to go.

The idea of the project is to create a PC that is just a web browser.  It boots up straight to a web browser (FireFox) and any attempt to close the web browser just basically restarts the web browser.

There are instructions for how you can remaster the CD for your use (make whitelists and blacklists to suit your needs, establish the "home" page, etc).  As I understand it, they only start enough of X services to utilize the web browser -- so the requirements should be pretty small.

---

