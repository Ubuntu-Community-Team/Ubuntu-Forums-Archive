---
title: "Recovering from a failed upgrade from 16.04 LTS to 18.04 LTS with no networking"
date: 2019-03-04
forum: Networking &amp; Wireless
---

### Post by rsteinmetz70112 on 2019-03-04
I'm upgrading the 4th of 7 computers from 16.04 LTS to 18.04 LTS. 

This upgrade failed badly. It appears that some packages may not have downloaded and many others are not configured. I started working through the mess with dpkg and now have a computer that boots into a terminal but there is no networking. Using dpkg, apt and apt-get I can install packages if I can download them but without networking I have to boot into a live session download the .debs reboot then try to install them, more often that not they fail due to unmet dependancies. 

I've tried setting up a chroot session from the live session but the chroot session does not have networking. Using both sessions I can download the .debs, place them on the local drive and install them in the chroot session, but discovering which one are not installed and getting networking up is proving to be difficult.

Is there a better approach, please don't suggest a clean install, if I did that I would lose all of the configurations and software I've installed on this computer. I really would have to do a lot more work since this isn't a simple desktop.

If I could get the networking going I thin dpkg and apt could probably fix everything that broken.

---

### Post by oldfred on 2019-03-04
Moved to network sub-forum.

Um time traveler from future 128.04 or typo? :)

Does live installer work with network?
Are you using Wireless or hardwired connection.
See this & post report:
[https://ubuntuforums.org/showthread.php?t=370108](https://ubuntuforums.org/showthread.php?t=370108)

Did you have lots of ppas or proprietary drivers installed? You have to turn all those off before upgrade and then reinstall with new version also.

Your backup procedure should allow you to fully restore your system without much if any reconfiguration. Most user settings are in hidden files in /home, so backup of /home covers that. If you made system settings changes those are in /etc. And if you export list of installed apps you can just reimport all your apps. 
I prefer clean installs as that removes a lot of cruft that accumulates. Logs, old kernels old apps, and other files just accumulate over time.

---

### Post by rsteinmetz70112 on 2019-03-04
> **oldfred said:**
> Moved to network sub-forum.

> Um time traveler from future 128.04 or typo? :)
Typo. I fixed it. 
> Does live installer work with network?
It seems to do a lot of downloads. I haven't actually tried it on this one.
> Are you using Wireless or hardwired connection.

Hard wired. The NIC is recognized but does not receive a IP address 
> See this & post report:
[https://ubuntuforums.org/showthread.php?t=370108](https://ubuntuforums.org/showthread.php?t=370108)
I'll take a look. I'll post info on the NIC but I don't think that's the problem. It works just fine in a live session from a DVD.
> Did you have lots of ppas or proprietary drivers installed? You have to turn all those off before upgrade and then reinstall with new version also.
I don't have any. I try to stay as vanilla as I can. I only make changes if absolutely necessary.

> Your backup procedure should allow you to fully restore your system without much if any reconfiguration. Most user settings are in hidden files in /home, so backup of /home covers that. If you made system settings changes those are in /etc. And if you export list of installed apps you can just reimport all your apps. 
I actually have a mirror of the installation on another machine. But that is 16.04 so I'd still have to upgrade it.
> I prefer clean installs as that removes a lot of cruft that accumulates. Logs, old kernels old apps, and other files just accumulate over time.
That's certainly one point of view. This particular computer is really a backup for testing so I'm using this opportunity to learn more about how Ubuntu is put together.

---

### Post by oldfred on 2019-03-04
I do not know wireless, my 12 yr old laptop which has 16.04 and is mostly retired just worked.

But generally hardwired works and if live installer works then install should also work. I thought the chroot inherited all the system settings from the boot version, but have not experimented with it.
I found this in my notes as part of chroot. Not sure this still is correct configuration file. I do have this file in my 18.04.
       sudo cp /etc/resolv.conf /mnt/etc/resolv.conf #(may or may not be necessary to establish an internet connection) 

What brand/model system?
What internet chip?

Some info on one type of chip issue and multiple commands to post info. Script requested above is more for Wi-Fi issues.
[https://ubuntuforums.org/showthread.php?t=1921452](https://ubuntuforums.org/showthread.php?t=1921452)

---

### Post by rsteinmetz70112 on 2019-03-04
I'll try that when I can get back to the computer. 

Since apt and dpkg work, I was thinking of downloading the Bionic repository on an external drive and see if that would fix it. I just need a big enough external drive.

---

### Post by rsteinmetz70112 on 2019-03-05
I think I've just about solved it. 

By opening a live session and setting up a ```
# chroot
``` session in it I was able to download .deb of packages not listed as installed then track the dependencies back using ```
# deb -i ./package name.deb
``` then if a package installed running```
# dpkg --configurte -a
```  and ```
# apt install -f
``` each step yielded the names of unconfigured packages and unmet dependencies.

I homed in onCODE]# debcong[/CODE] once I got debconf configured I was able to get the network up and running  in the chroot session. 
The ```
# dpkg --configure -a 
```and ```
# apt install -f 
``` fixed most of the packages. 

I've still got some loose ends, like I don't have a DNS server permanently configured, I have to add it to```
#vi /etc/resolv.conf
nameserver 8.8.8.8
``` after each reboot, but that a minor problem, Ill take care of as soon as I have the packages all upgraded.

---

