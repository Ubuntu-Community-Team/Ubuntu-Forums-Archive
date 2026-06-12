---
title: "firefox"
date: 2011-08-20
forum: New to Ubuntu
---

### Post by gr8ansh4u on 2011-08-20
my firefox version is 3.6.18 and i want to update it to 6.0 which is the latest version...but my firefox is not updating itself...and i'm not able to find any option to update it...so i hav to download firefox 6.0..but it is in .tar.bz2 format...how to install it?

---

### Post by sanderd17 on 2011-08-20
[http://www.ubuntugeek.com/how-to-install-firefox-6-on-ubuntu.html](http://www.ubuntugeek.com/how-to-install-firefox-6-on-ubuntu.html)

But if you mess with custom ppas, there is a big chance that you won't be able to do _system_ upgrades anymore via the update manager.

---

### Post by 73ckn797 on 2011-08-20
> **sanderd17 said:**
> [http://www.ubuntugeek.com/how-to-install-firefox-6-on-ubuntu.html](http://www.ubuntugeek.com/how-to-install-firefox-6-on-ubuntu.html)

But if you mess with custom ppas, there is a big chance that you won't be able to upgrade anymore via the update manager.
This link will install the latest FF. I will caution that in the last several days FF6 was causing issues such as taking a long time to scroll down pages. The screen would grey out and I would have to wait. Once it came back any further activity caused the same delay. I removed the Firefox ppa and went back to the repo version. This problem was occurring on a laptop and desktop computer.

---

### Post by scottstensland on 2011-08-20
I'm not sure what version of ubuntu you're using 
from a terminal window (Ctrl-Alt-t) issue :

sudo apt-get update
sudo synaptic

search for firefox - it appears as first entry just called - firefox
right click and pick - Mark for Installation
then click that green Apply check mark to activate the install

---

### Post by gr8ansh4u on 2011-08-20
i'm using ubuntu 10.10...i'll try..

---

### Post by sanderd17 on 2011-08-20
> **73ckn797 said:**
> This link will install the latest FF. I will caution that in the last several days FF6 was causing issues such as taking a long time to scroll down pages. The screen would grey out and I would have to wait. Once it came back any further activity caused the same delay. I removed the Firefox ppa and went back to the repo version. This problem was occurring on a laptop and desktop computer.

This has to be an Ubuntu issue. I'm using FF6 on Arch, and there is not much difference from FF5 or FF4.

---

### Post by melrokz on 2011-08-20
I wonder why Firefox keeps releasing versions faster than I can check it out!!!

---

### Post by VeterinaryPathologist on 2011-08-20
Look at [this thread]("http://www.webgapps.org/tutorials/firefox/general/installing-other-versions") to update firefox. It worked for me

---

### Post by uRock on 2011-08-20
In a terminal, enter the following command. This command will add Mozilla's stable PPA, then the following two parts of the command will tell the package manager to check for and install updates, which will in turn upgrade your Firefox.```
sudo add-apt-repository ppa:mozillateam/firefox-stable && sudo apt-get update && sudo apt-get upgrade
```

---

### Post by 73ckn797 on 2011-08-20
> **sanderd17 said:**
> This has to be an Ubuntu issue. I'm using FF6 on Arch, and there is not much difference from FF5 or FF4.
I did not pursue a solution but wonder whether it could be a java issue. No real reason to think that but FF5 was fine.

---

### Post by beew on 2011-08-20
> **sanderd17 said:**
> [http://www.ubuntugeek.com/how-to-install-firefox-6-on-ubuntu.html](http://www.ubuntugeek.com/how-to-install-firefox-6-on-ubuntu.html)

But if you mess with custom ppas, there is a big chance that you won't be able to upgrade anymore via the update manager.

That is pure FUD. I have used tons of ppas and never had I have a major problem. There are minor ones but they are rare and can usually be solved easily.

---

### Post by beew on 2011-08-20
> **sanderd17 said:**
> This has to be an Ubuntu issue. I'm using FF6 on Arch, and there is not much difference from FF5 or FF4.

I think that has to be an issue with 73ckn797's setup. I am using FF6 on Ubuntu11.04 and 10.10 and there has not been a problem.

---

### Post by -kg- on 2011-08-21
I'm using FF6 on Kubuntu 11.04 and have experienced no problems.  For another thread on another site, I read and saved what was updated (updated from the 11.04 repos), and largely all it was was some bug fixes.

As of FF4, Mozilla has taken to changing the version number even for minor bug fixes.  A bit confusing, as the convention with most software is to only change the version number for major upgrades, but what do I know?  But I have not noticed any major changes between FF4, 5, or now, 6.

---

### Post by shibu_sawyer on 2011-08-21
I too had this doubt, and after a lot of googling i found it..
my old version was 3.6.17 and now i removed the old one and now i am using 5.0.1..

The crazy thing is,firefox not releasing .deb part of firefox,only tarballs are present,many don know how to use it.. so here it is..


A. Install Firefox in 5 easy steps
 1. Download

 Download the RC from the official channels page:
[www.mozilla.com/firefox/channels/](www.mozilla.com/firefox/channels/)

  This how-to supposes that the downloaded file is saved in the "Downloads" directory situated in your home directory.

  
 2. Extract

 The downloaded file is a compressed .tar.bz2 archive. 
 you can extract the archive from the command line:

cd ~/Downloads/

tar xjf firefox-5.0.tar.bz2

 For those interested, here are the tar  arguments used in the command:
 x : eXtract
 j : deal with bzipped file
 f : read from a file (rather than a tape device)

 The .tar.bz2 archive can now be deleted.

  


  
 3. Move to /opt

 External programs like LibreOffice, Google Chrome, Adobe reader, ... are all installed in the /opt directory. 

 If you already had a previous Firefox version installed in the /opt directory, remove it with the following command:

sudo rm -r /opt/firefox

 Now move the firefox directory – which was created in your Downloads folder during extraction – to /opt:

sudo mv firefox /opt/firefox

  
 4. Set up symbolic links
To Use Firefox 5 as you default browser:
 "Backup" the old Firefox launcher:

sudo mv /usr/bin/firefox /usr/bin/firefox-old

 Create a symbolic link pointing to the new Firefox version:

sudo ln -s /opt/firefox/firefox /usr/bin/firefox

 No need to update your icons/shortcuts, they should now launch the new version of Firefox.

 Your old Firefox version is still installed. If you want to use it, run firefox-old in a terminal or create shortcuts/icons referring to firefox-old.

  
 
 5. Updates & Final

 Firefox 5 will manage its own updates independently of your system's package manager, an download subsequent  beta releases.

 There will be no need to repeat the whole "procedure"... Enjoy Firefox..

by the way restart your system and click the firefox icon in the taskbar,.
restart requires coz when i launched without restarting, showed the old version again,when i restarted new version started working..

---

### Post by Untold on 2011-08-21
> **melrokz said:**
> I wonder why Firefox keeps releasing versions faster than I can check it out!!!


This link should answer

[http://www.omgubuntu.co.uk/2011/06/firefox-5-released-faster-release-cycle-less-features/](http://www.omgubuntu.co.uk/2011/06/firefox-5-released-faster-release-cycle-less-features/)

---

### Post by sanderd17 on 2011-08-21
> **beew said:**
> That is pure FUD. I have used tons of ppas and never had I have a major problem. There are minor ones but they are rare and can usually be solved easily.

Sorry, I don't want to spread FUD and now I see that I have chosen my words a bit wrong. I meant "system upgrades", not "program upgrades". I've had problems with system upgrades before due to custom ppas.

---

### Post by I2k4 on 2011-08-21
I've found that one of the nicer things about FireFox on Ubuntu is that it seems to have its own automatic .deb installation handler for all kinds of software (I don't get the same from using Chrome.)   Often times, FireFox will go to a website and automatically handle installation.  

If just using the older FireFox to download and install the new one doesn't work, the terminal 

sudo apt-get update

command seems to put references to the newest version into the Synaptic Package Manager, so I can selectively choose what to use from there.  I avoid all the other "apt-get" commands because some of them seem to trigger massive lengthy downloads and installations that can't be stopped that I don't need or want.

---

### Post by 73ckn797 on 2011-08-21
> **beew said:**
> I think that has to be an issue with 73ckn797's setup. I am using FF6 on Ubuntu11.04 and 10.10 and there has not been a problem.
This issue was occurring on 2 different computers.

It was apparently a strange glitch. I have re-enabled the ppa and re-installed FF6 on the laptop and now have no problem. There was one part of the package, xul-ext-ubufox, that was coming in as a broken package originally. Efforts to fix it failed. This new installation did not have this problem. Maybe there was a problem from the source, which I believe there was since it happened on both computers.

---

### Post by gr8ansh4u on 2011-09-02
really helpful
thanks .. :)

---

