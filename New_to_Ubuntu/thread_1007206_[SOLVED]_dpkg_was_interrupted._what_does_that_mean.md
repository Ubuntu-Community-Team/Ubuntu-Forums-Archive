---
title: "[SOLVED] dpkg was interrupted. what does that mean? what do i do?"
date: 2008-12-10
forum: New to Ubuntu
---

### Post by danny_galaga on 2008-12-10
i was trying to download limewire, when my poxy internet connection seized up. so i canned the download (actually i think it was halfway through trying to install the package). so now when i open synaptic package manager to try and continue the limewire install i get this:


E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

is this an easy fix?

i cant believe ive screwed up my pc again. im really annoyed because last time it was such a mess, i had to reisntall. but this time around i was going to make an iso, but i never quite figured out how to do that either! which means if i have to reinstall, i have to download all the updates, just for 8.04...

HELP!

---

### Post by bluefrog on 2008-12-10
have you tried the suggested fix?

in a terminal (apps/accessories/terminal)
sudo dpkg --configure -a

---

### Post by danny_galaga on 2008-12-10
yes. but now if i try to open the package manager, it tells me another is open. i cant see anything else open. iv even tried restarting, in case there is something running that i cant see...

right now there is a big red warning sign where the updates star usually is. if i go in there and try and download updates, it tells me something about another manager running in interactive mode?  and now i cant close the update manager...

edit:

this is what i get if i do the sudo dpkg --configure -a thing:



dpkg: dependency problems prevent configuration of limewire-basic:
 limewire-basic depends on sun-java6-jre | icedtea-java7-jre | sun-java6-jdk | icedtea-java7-jdk | sun-java5-jre | sun-java5-jdk; however:
  Package sun-java6-jre is not installed.
  Package icedtea-java7-jre is not installed.
  Package sun-java6-jdk is not installed.
  Package icedtea-java7-jdk is not installed.
  Package sun-java5-jre is not installed.
  Package sun-java5-jdk is not installed.
dpkg: error processing limewire-basic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 limewire-basic

---

### Post by sayakb on 2008-12-10
Try:
```
sudo apt-get install -f && sudo dpkg-configure -a
```

---

### Post by danny_galaga on 2008-12-10
well, i did that and it seems to be doing the right thing in the terminal. but then it gives a warning and before i can read it, up pops a DOS looking disclaimer for sun microsystems. at the bottom of the disclaimer is <ok> 

i dont know if im supposed to do anything there, but typing 'ok' doesnt do anything. or hitting enter. i still have the warning symbol where the updates symbol should be...

edit: hovering the cursor over the warning symbol tells me:

"An error occurred. please run Package manager from the right-click menu or apt-get in a terminal to see what is wrong. The error message was: 'Error:BrokenCount > 0'This usually means that your installed packages have unmet dependencies"

---

### Post by plucky on 2008-12-11
> i dont know if im supposed to do anything there, but typing 'ok' doesnt do anything. or hitting enter. i still have the warning symbol where the updates symbol should be...

You need to accept the Sun License before the Java will install so use <tab>  and <Enter> or point and click with the mouse the **OK** button.

> "An error occurred. please run Package manager from the right-click menu or apt-get in a terminal to see what is wrong. The error message was: 'Error:BrokenCount > 0'This usually means that your installed packages have unmet dependencies"

Open the Synaptic package manager and find and fix broken packages.Probably the Sun Java install.

Good Luck

---

### Post by JoshuaRL on 2008-12-11
Yeah, I'll be another voice for Synaptic.  Once I stopped an unsuggested "distro upgrade" in Linux Mint because, well, because I was being stupid.  It was late, I was tired.  Stuff was borked bad.  And Synaptic fixed it.  Took a little time, but it fixed everything though.

---

### Post by danny_galaga on 2008-12-11
> **plucky said:**
> You need to accept the Sun License before the Java will install so use <tab>  and <Enter> or point and click with the mouse the **OK** button.



Open the Synaptic package manager and find and fix broken packages.Probably the Sun Java install.

Good Luck

hmmm, now it wont get me to that stage. this is what it tell me:


E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?



as far as im aware, there is no other process using it, whatever 'it' is...

---

### Post by JoshuaRL on 2008-12-11
And you tried a restart?  Could you try again and when the desktop loads go directly to Synaptic?

---

### Post by danny_galaga on 2008-12-11
ok, did a restart. went to synaptic, and i get this:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.


it just feels like im going around in circles. but for arguments sake, if i were to run 'dpkg --configure -a' , do i just type

 sudo dpkg --configure -a

into the terminal?

---

### Post by JoshuaRL on 2008-12-11
Yep, that'd be the one.  Post the output back here please.

---

### Post by danny_galaga on 2008-12-11
danny@danny-desktop:~$ sudo dpkg --configure -a
dpkg: dependency problems prevent configuration of limewire-basic:
 limewire-basic depends on sun-java6-jre | icedtea-java7-jre | sun-java6-jdk | icedtea-java7-jdk | sun-java5-jre | sun-java5-jdk; however:
  Package sun-java6-jre is not installed.
  Package icedtea-java7-jre is not installed.
  Package sun-java6-jdk is not installed.
  Package icedtea-java7-jdk is not installed.
  Package sun-java5-jre is not installed.
  Package sun-java5-jdk is not installed.
dpkg: error processing limewire-basic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 limewire-basic

---

### Post by Michael.Godawski on 2008-12-11
Can you please post your sources.list

```
cat /etc/apt/sources.list
```

found a similar issue here:
[http://forums.debian.net/viewtopic.php?t=26790&highlight=&sid=553c2303d7095dd979cad7c463490acc](http://forums.debian.net/viewtopic.php?t=26790&highlight=&sid=553c2303d7095dd979cad7c463490acc)
perhaps it will help somehow.

---

### Post by danny_galaga on 2008-12-11
like so:


danny@danny-desktop:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) intrepid main restricted
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) intrepid universe
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) intrepid universe
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) intrepid-updates universe
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) intrepid multiverse
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) intrepid multiverse
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) intrepid-updates multiverse
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse

# deb [http://apt.wicd.net](http://apt.wicd.net) hardy extras
deb [http://www.remastersys.klikit-linux.com/repository](http://www.remastersys.klikit-linux.com/repository) remastersys/

---

### Post by JoshuaRL on 2008-12-11
Try taking the # out from in front of the backports and partner repositories.  Save and do an update && upgrade.  See if that helps.

---

### Post by danny_galaga on 2008-12-11
sorry, i dont even know what that means? do i just run that list again? and manually take all '#' that i see?

---

### Post by JoshuaRL on 2008-12-11
I'm sorry man.  Sometimes I forget to explain stuff.
```

gksu gedit /ect/apt/sources.list

```
Then go down to almost the bottom.  This part:
> 
## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

See the bottom two lines with the web address?  Take the # away from in front of those.  Do the same for this part too:
> 
## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

After that, run the following commands and please post the output here:
```

sudo dpkg --configure -a
sudo apt-get -f
sudo apt-get update
sudo apt-get upgrade
sudo apt-get autoclean

```

---

### Post by gandaran on 2008-12-11
danny_galaga
don't uncomment the backports repository, it won't fix your problem and mite even add to your problems as you'll be updating to testing sofware
I suspect all your problems are due to a broken java install, if you have dificulty installing java using the command line then just use synaptic package manager, run the  sudo dpkg --configure -a command then open synaptic, scroll down to sun-java6-plugin check-mark for install and hit the apply button, if you still get any errors post them.

---

### Post by OldTimeTech on 2008-12-11
Also after the gedit, you need to save what you have changed before you go to the commands in terminal.

---

### Post by danny_galaga on 2008-12-12
> **gandaran said:**
> danny_galaga
don't uncomment the backports repository, it won't fix your problem and mite even add to your problems as you'll be updating to testing sofware
I suspect all your problems are due to a broken java install, if you have dificulty installing java using the command line then just use synaptic package manager, run the  sudo dpkg --configure -a command then open synaptic, scroll down to sun-java6-plugin check-mark for install and hit the apply button, if you still get any errors post them.

well, waddaya know! that did the trick. pure and simple. thanks for that (",)

edit: just in case anyone else follows this, what gandaran meant to type is:

in a terminal, run 'sudo dpkg --configure -a'

then open synaptic, scroll down to sun-java6-plugin check-mark for install and hit the apply button.

i found it quite hard to spot 'sun-java6-plugin' at first, but it was there (",)

---

### Post by skathmandoo on 2008-12-19
> **danny_galaga said:**
> well, waddaya know! that did the trick. pure and simple. thanks for that (",)

edit: just in case anyone else follows this, what gandaran meant to type is:

in a terminal, run 'sudo dpkg --configure -a'

then open synaptic, scroll down to sun-java6-plugin check-mark for install and hit the apply button.

i found it quite hard to spot 'sun-java6-plugin' at first, but it was there (",)


WOW! i had the exact problem. thanks to u guys its solved (hopefully). thank god for this thread & forum!

---

