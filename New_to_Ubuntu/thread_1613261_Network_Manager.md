---
title: "Network Manager"
date: 2010-11-04
forum: New to Ubuntu
---

### Post by BSMD1 on 2010-11-04
Hey everybody, I've just upgraded to the newest version of ubuntu. The reason was I was having multiple issues, but the main thing that got me to switch was that I wasn't able to locate the network manager. I accidentally removed the appllet and uninstalled it with the notion that I was going to be able to reinstall it without an internet connection (stupid).
 
BUT ANYWAY. So I got everything set up nice and neat on my new system. I was even able to connect to the internet and download all my updates and reorganize my bookmarks and addons on firefox through the network manager appllet! Once I did a manadatory restart, though, I once again can't find it. I've stayed up all night to do all this, and I can honestly say this is my worst stupid moment yet (I mean, I'm usuing a windows box to write this message for god's sake). Please help. And also I've looked around for the network manager program with no success in locating it. I used to be more technologically inclined, but ubuntu spoiled me.
 
Thanks in advance...

---

### Post by Hippytaff on 2010-11-04
It's not in System -> Preferences?

---

### Post by BSMD1 on 2010-11-04
Well I checked that just now and in system>Preferences>startup Applications I found it but I'm not sure how to activate it. The ubuntu help and guidelines sometimes seem a little opaque

---

### Post by coffeecat on 2010-11-04
The Network Manager applet is attached to the Notification Area applet which is, itself, easy to miss. The notification area is just three tiny horizontal lines on the panel. If you're using the default dark ambiance theme you need good eyes and a magnifying glass.

Make sure you have notification area on the panel. If not, add it. (Right-click on panel > Add to panel).

If the Network manager still doesn't appear, have a look in System > Preferences > Startup Applications. Is it listed under the Startup Programs tab? Is it ticked? If no to both, this is what you need to add it:

Name: Network Manager

Command: nm-applet --sm-disable

Comment (optional): Control your network connections

---

### Post by BSMD1 on 2010-11-04
I did just that but when i went to use it, the error message "Failed to execute child process nm-applet (no such file or directory)"

---

### Post by coffeecat on 2010-11-04
> **BSMD1 said:**
> I did just that but when i went to use it, the error message "Failed to execute child process nm-applet (no such file or directory)"

That sounds as though it *may* be a missing or corrupted executable belonging to network manager. It's strange that it should happen after an ordinary update on a new system, but whatever. Since you won't have working networking you can't reinstall with freshly downloaded packages, so I suggest this. It assumes you are using 10.10/Maverick. If you are using 10.04/Lucid post back before trying this.

Boot into another system. It can be Windows - it doesn't matter what the OS is. Download these two packages if you are running a 32-bit system:

[http://archive.ubuntu.com/ubuntu/pool/main/n/network-manager/network-manager_0.8.1+git.20100810t184654.ab580f4-0ubuntu2_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/n/network-manager/network-manager_0.8.1+git.20100810t184654.ab580f4-0ubuntu2_i386.deb)
[http://archive.ubuntu.com/ubuntu/pool/main/n/network-manager-applet/network-manager-gnome_0.8.1+git.20100809t190028.290dc70-0ubuntu3_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/n/network-manager-applet/network-manager-gnome_0.8.1+git.20100809t190028.290dc70-0ubuntu3_i386.deb)

Or these two if a 64-bit system:

[http://archive.ubuntu.com/ubuntu/pool/main/n/network-manager/network-manager_0.8.1+git.20100810t184654.ab580f4-0ubuntu2_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/main/n/network-manager/network-manager_0.8.1+git.20100810t184654.ab580f4-0ubuntu2_amd64.deb)
[http://archive.ubuntu.com/ubuntu/pool/main/n/network-manager-applet/network-manager-gnome_0.8.1+git.20100809t190028.290dc70-0ubuntu3_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/main/n/network-manager-applet/network-manager-gnome_0.8.1+git.20100809t190028.290dc70-0ubuntu3_amd64.deb)

Transfer the two files to your Ubuntu system however you want - probably with a USB stick - and then simply install them by double-clicking on each in turn. Now reboot and see if the network-manager applet appears in your panel

---

### Post by BSMD1 on 2010-11-04
Sorry for the long wait, I had to get some sleep (like I said I was up all night)
I tried to install the files, but another ubuntu error popped up saying I need proper installation files. So I did as it said and installed two files I needed. But now for one it said "error dependency is not satisfiable: libgconf2-4" and the same error message for the next one but instead saying I needed libnm-util1. Here's the kicker, I obtained both of those files as well, but it said those versions were already installed!
 
crap...

---

### Post by coffeecat on 2010-11-04
Yes, there are masses of dependencies for network manager, and if one of those is corrupted then it will be like searching for a needle in a haystack.

Question: you say this was a fresh install which went wrong after a routine update? Am I correct? I haven't had any problem with network manager after any update with either Lucid or Maverick. And nor have most people judging by the lack of such threads. Which makes me wonder if your original install medium was faulty. It only needs one damaged file somewhere to cause weird and unpredictable problems.

Did you check the md5sum of the ISO download you used, and did you burn the CD at a low speed?

---

### Post by BSMD1 on 2010-11-04
The installation went off without a hitch, and I burned the image at average speed. But I had the same problem with my previous version of ubuntu. I thought everything would've been fine, seeing that I was actually able to use the network manager prior to restarting the system to finalize the updates. Should I go ahead and reinstall? Or would that be putting a band-aid over cancer?

---

### Post by coffeecat on 2010-11-04
> **BSMD1 said:**
> But I had the same problem with my previous version of ubuntu.

That's very unlucky. Perhaps you could clarify a few things first. Your previous version of Ubuntu, was it installed from the same downloaded ISO, or do you mean it was a previous release of Ubuntu? In short, which version were you running before and which version now, and if they were different, did you do a version upgrade?

If you did do both installs from the same ISO, it is just possible that the ISO was corrupted. Not enough to prevent it from working, but enough to cause it to write a bad file somewhere in the system which only manifested after a routine update. Hence the importance of always checking the md5 hash sum for every ISO you download. That's even before you burn it to disc.

---

### Post by BSMD1 on 2010-11-04
I upgraded from 8.10 to 10.10. So yes, it was two different ISO's

---

### Post by coffeecat on 2010-11-04
And did you check the md5sum?

---

### Post by gamebusterzade on 2010-11-04
now this may not matter but how are u trying to connect

hardwire or WiFi

(had to hardwire temprarily to get WiFi to work becuse of bad drivers)

---

### Post by BSMD1 on 2010-11-04
No, I've been reading up on how to do so, and I have the md5sum help up on my terminal right now. But I wouldn't know what to do.

---

### Post by BSMD1 on 2010-11-04
I connect through wlan, I haven't had any problems up until recently, and this is the first time something like this has occured

---

### Post by gamebusterzade on 2010-11-04
i would first try hardwire first

if that doesn't work then see if there is a *.tar(or similar filetype) for the network manager some where 
  
if the above fall im hopeless in helping u

---

### Post by BSMD1 on 2010-11-04
Yes, I tried hardwiring it yesterday, didn't work. But I think i'll try it again later.
I'm not sure how getting different copies of the files will work, but i'm trying it right now.

---

### Post by BSMD1 on 2010-11-04
If all else fails, could I know of some alternative programs to connect to networks?

---

### Post by cpmman on 2010-11-04
Wicd is in the Software Centre/repositories.

---

### Post by BSMD1 on 2010-11-04
Are there any type of specifics I have to enter about my router to be able to connect?

---

### Post by coffeecat on 2010-11-04
> **BSMD1 said:**
> No, I've been reading up on how to do so, and I have the md5sum help up on my terminal right now. But I wouldn't know what to do.

Here you go. How to MD5SUM:

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

And md5sums for 10.10:

[http://releases.ubuntu.com/10.10/MD5SUMS](http://releases.ubuntu.com/10.10/MD5SUMS)

---

