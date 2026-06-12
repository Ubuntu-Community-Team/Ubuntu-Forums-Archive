---
title: "Removing Virus From External Hard Drive"
date: 2009-07-31
forum: New to Ubuntu
---

### Post by SpideyNYC on 2009-07-31
Greetings.  I am in desperate need of some help.  A nasty little virus infected some files and I NEED to salvage whatever I can.  The files were infected on a Windows PC.  Before reinstalling XP, I copied the files to my external hard drive.  What I would like to do is hook up the drive to Ubuntu and scan it with an anti virus.  Afterwards, transfering the clean files back to that Windows machine.  My question is, how do I go about doing this?  My Ubuntu experience is basically zero so please be very specific please.  Personally, I use a Mac and have both Ubuntu and XP on my computer via VMWare.  A million thanks for your time and consideration.

---

### Post by lisati on 2009-07-31
There are virus scanners available that are Linux-friendly. You might want to check out something like clamav or AVG free.

---

### Post by credobyte on 2009-07-31
BitDefender ( [https://help.ubuntu.com/community/BitDefender](https://help.ubuntu.com/community/BitDefender) ).

---

### Post by vinutux on 2009-07-31
Antivir..is another good chioce....

**[http://www.free-av.de/en/download/download_servers.php]("http://www.free-av.de/en/download/download_servers.php")**

---

### Post by SpideyNYC on 2009-07-31
Thanks for the advice.  I downloaded bitdefender but got the following error when running the exe file...

[/home/peterparker/Desktop/bitdefender_antivirus(2).exe]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
zipinfo:  cannot find zipfile directory in one of /home/peterparker/Desktop/bitdefender_antivirus(2).exe or
          /home/peterparker/Desktop/bitdefender_antivirus(2).exe.zip, and cannot find /home/peterparker/Desktop/bitdefender_antivirus(2).exe.ZIP, period.


Any ideas?

---

### Post by vinutux on 2009-07-31
> **SpideyNYC said:**
> Thanks for the advice.  I downloaded bitdefender but got the following error when running the exe file...

[/home/peterparker/Desktop/bitdefender_antivirus(2).exe]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
zipinfo:  cannot find zipfile directory in one of /home/peterparker/Desktop/bitdefender_antivirus(2).exe or
          /home/peterparker/Desktop/bitdefender_antivirus(2).exe.zip, and cannot find /home/peterparker/Desktop/bitdefender_antivirus(2).exe.ZIP, period.


Any ideas?

exe is windows executable...find something like deb, tar.gz.....deb is the installabel binary format here

---

### Post by vinutux on 2009-07-31
Here is the link of bitdiffender linux version**[http://www.bitdefender.com/PRODUCT-80-en--BitDefender-Antivirus-Scanner-for-Unices.html]("http://www.bitdefender.com/PRODUCT-80-en--BitDefender-Antivirus-Scanner-for-Unices.html")**

---

### Post by SpideyNYC on 2009-07-31
Tried Bitdefender twice and it downloads an exe file to my desktop.  So I don't know.  Also tries Antivir and a .tar.gz file was downloaded and opened successfully.  I then double cliked the install file and some crazy text file opened.  Can anyone shed some light?

---

### Post by aesis05401 on 2009-07-31
Hello,

There are a couple ways to accomplish what you would like.  Since you are very new to Ubuntu we will use the graphical tools to grab a program. 

1. Click the 'Applications' menu (top left menu bar on default setup)
2. Click Add/Remove
3. Change 'Show' option box to 'All Available Applications'
4. Type 'Virus Scanner' into the search box (this is a graphical frontend for clamAV)
5. Click the check-box next to Virus Scanner and then 'Apply Changes'
6. Input your password to install.

If no Virus Scanner entry comes up from the search do the following:
1. Open 'System' menu from the top of the screen
2. Click 'Administration'
3. Click 'Software Sources'
4. Check all the boxes on the first screen (Ubuntu Software tab)
5. Go back to 'Add/Remove Programs and try again.

Does this work for you?

Edit: Now I see the front-end I know you might be a little scared ;)  This program is only a user interface for a powerful tool, so don't worry.  After choosing System or Single user you have to click 'quit.'  On the next screen that appears go to the help menu and choose update virus signatures. 

Let us know how it works out.

---

### Post by SpideyNYC on 2009-07-31
Ok first off thanks so much.  I got the virus scanner working however I can not get the signature updated.  It says that there's a newer version available but it doesn't give me the option to download it.

---

### Post by aesis05401 on 2009-07-31
K, We can fix this pretty fast - but first I want to point out that virus scanners are not this community's specialty ;)  Usually software from within the Add/Remove menu is pretty up to date.  I have just completed the steps I am about to give you so as not to give bad advice a second time ;)

I just visited the program maintainer's page and he says the Ubuntu repository is using an old version.  Here is a link to the updated version: [http://sourceforge.net/projects/clamtk/]("http://sourceforge.net/projects/clamtk/")

The file you are downloading is a .deb file - this stands for debian which is the parent distribution of Ubuntu.  Sometimes deb files do not have options set to make menu items and whatnot, but it appears that this package does install a menu item under 'Applications/Accessories.'

So once this package is downloaded:
1. Double click the file
2. Package Installer should open
3. Click 'Install Package' or 'Reinstall Package' (the button text changes depending on whether it thinks there is a previous version on your machine).
4. Open 'Applications/Accesories'
5. Open Virus Scanner
6. Help Menu/Update
7. Choose folder to scan

This worked on my machine.  The signature download was very fast, but the package you are downloading was just updated on the sixteenth of this month, so there wasn't much to pull.

---

### Post by aesis05401 on 2009-07-31
I should mention now that the files which get flagged will need to be deleted manually afterwards. This is the same thing Windows AV do automatically, but on Linux there is a philosophy of not opening certain cans of worms.

Anyhow, Clam will give you a list of everything that needs to go.  The scanning engine is mainly designed to detect Windows malware and it is reputedly pretty good at it :)

---

### Post by hellmet on 2009-07-31
AVG is quite good. Download this .deb here : [http://www.avg.com/filedir/inst/avg85flx-r287-a2632.i386.deb](http://www.avg.com/filedir/inst/avg85flx-r287-a2632.i386.deb)

This will install itself like .exe from Windows, except that you won't have to Next-Next-Install. Its easier.
Also, AVG's interface is less scary to a new Linux user.

---

### Post by theozzlives on 2009-07-31
> **aesis05401 said:**
> I should mention now that the files which get flagged will need to be deleted manually afterwards. This is the same thing Windows AV do automatically, but on Linux there is a philosophy of not opening certain cans of worms.

Anyhow, Clam will give you a list of everything that needs to go.  The scanning engine is mainly designed to detect Windows malware and it is reputedly pretty good at it :)

I use clamav, but it quarantines the files (if you tell it to), not clean them. you go:
```
sudo apt-get install clamav
mkdir /tmp/virus
clamscan -ri --move=/tmp/virus /media/disk (or where ever your drive mounts to)
```

---

### Post by desperado665 on 2009-07-31
> **theozzlives said:**
> I use clamav, but it quarantines the files (if you tell it to), not clean them. you go:
```
sudo apt-get install clamav
mkdir /tmp/virus
clamscan -ri --move=/tmp/virus /media/disk (or where ever your drive mounts to)
```

Suppose I wanted to boot a livecd and use clamav to scan a mounted windows partition and quarantine all infected files. How would I do this?

---

### Post by SpideyNYC on 2009-07-31
Can anyone help me update the signatures for the virus scanner?  Thanks ever so much

---

### Post by jacklinux on 2009-07-31
if you know WHAT was infected then just remove those however, if the files are not important then format it. Wipe it clean and use again.

---

### Post by Liolikas on 2009-07-31
> **SpideyNYC said:**
> Can anyone help me update the signatures for the virus scanner?  Thanks ever so much

Help>Update Signatures

---

### Post by SpideyNYC on 2009-07-31
Thanks for all the feedback.  Since I am familiar with AVG I decided to try that. The .deb downloaded successfully, however, I can not install it.  I get a message saying same version is already installed.  I did try AVG earlier so maybe I installed it and didn't realize.  How can I be certain?

---

### Post by Liolikas on 2009-07-31
sudo avggui

> 
Launcher

Making a launcher to start AVG

Code:

sudo rm -r /usr/share/applications/avggui.desktop
sudo nano /usr/share/applications/avg.desktop

add:
Code:

[Desktop Entry]
Name=AVG Antivirus
Comment=Antivirus
Exec=gksudo avggui &
Icon=/opt/grisoft/avggui/prog/pixmaps/avgico_big.png
Terminal=false
Type=Application
Categories=Application;System;

save and exit.

You can now start AVG by going to Applications tab ---> System Tools.

I think AVG stopped making Linux versions.

---

### Post by SpideyNYC on 2009-07-31
Those codes are french to me.  This is my first time using Linux

---

### Post by Liolikas on 2009-07-31
..whatever forget them...
Just try command:
```

sudo avggui

```

---

### Post by SpideyNYC on 2009-07-31
Says command not found

---

### Post by Liolikas on 2009-07-31
So you do not have avg. At all forget avg. Avg decided not to make Linux version because we have no viruses. For simple task like nuke windows virus in external driver Clam AV should be more than enough. ;)

---

### Post by SpideyNYC on 2009-07-31
OK I got it.  Thanks a bunch

---

### Post by hellmet on 2009-07-31
Good to know Linux helped you. Please help the community back, by posting what worked for you in the end.

---

### Post by Liolikas on 2009-07-31
I think he found Clam AV in package manager installed it and nuked small wind0ze virus in external hdd.

---

### Post by lisati on 2009-07-31
> **Liolikas said:**
> ..whatever forget them...
Just try command:
```

sudo avggui

```

I think the latest Linux version of avg free doesn't have a gui. At least it didn't when I temporarily had it on my Ubuntu box a few weeks back.

---

### Post by aesis05401 on 2009-07-31
> **Liolikas said:**
> I think he found Clam AV in package manager installed it and nuked small wind0ze virus in external hdd.

Just to clarify if others are reading this thread for advice - the ClamTk package we tried to grab from repos earlier in this thread is very out of date.  The maintainer has posted a note @ sourceforge telling anyone who wants it on Ubuntu from the repos will need to work to get the package updated.  

I can confirm that the repo version installs and loads, but will not update signatures or operate properly after that.  The .deb from sourceforge operates as intended - so anyone looking to use the little clamtk frontend program should get it from the sourceforge page.

---

