---
title: "Skype on 8.4 again."
date: 2010-02-04
forum: New to Ubuntu
---

### Post by sarum on 2010-02-04
Hi, I've been trying to install Skype. I just want to make 'phone calls without a video cam thing that seems to cause much comment on this forum.
So far I've downloaded from Software Scources.....deb...skype.com etc;etc...That worked OK. Then from Synaptic Packages - Skype, I got:-

skype:
  Depends: libasound2 (>1.0.16) but 1.0.15-3ubuntu4 is to be installed
  Depends: libgcc1 (>=1:4.3) but 1:4.2.4-1ubuntu4 is to be installed
 Depends: libqt4-dbus (>=4.4.3) but it is not installable
 Depends: libqt4-network (>=4.4.3) but it is not installable
 Depends: libqtcore4 (>=4.4.3) but it is not installable
 Depends: libqtgui4 (>=4.4.3) but it is not installable
  Depends: libstdc++6 (>=4.3) but 4.2.4-1ubuntu4 is to be installed
I have followed instructions from 'Begining Ubuntu' by Thomas & Sicam.
Many thanks to anyone who can suggest where I'm going wrong..........sarum.

---

### Post by steveneddy on 2010-02-04
This is probably the easiest way of performing this task besides installing the ppa:

[http://www.ehow.com/how_5665129_install-skype-ubuntu.html](http://www.ehow.com/how_5665129_install-skype-ubuntu.html)

---

### Post by rajeev1204 on 2010-02-04
Skype seems to be missing now from medibuntu.Strange.

BUt a google search for medibuntu skype returns some page 

[http://packages.medibuntu.org/hardy/skype.html](http://packages.medibuntu.org/hardy/skype.html)

But the packages link on the site goes here [http://packages.medibuntu.org/hardy/index.html](http://packages.medibuntu.org/hardy/index.html)

And there is no skype there.

---

### Post by rajeev1204 on 2010-02-04
> **sarum said:**
> Hi, I've been trying to install Skype. I just want to make 'phone calls without a video cam thing that seems to cause much comment on this forum.
So far I've downloaded from Software Scources.....deb...skype.com etc;etc...That worked OK. Then from Synaptic Packages - Skype, I got:-

skype:
  Depends: libasound2 (>1.0.16) but 1.0.15-3ubuntu4 is to be installed
  Depends: libgcc1 (>=1:4.3) but 1:4.2.4-1ubuntu4 is to be installed
 Depends: libqt4-dbus (>=4.4.3) but it is not installable
 Depends: libqt4-network (>=4.4.3) but it is not installable
 Depends: libqtcore4 (>=4.4.3) but it is not installable
 Depends: libqtgui4 (>=4.4.3) but it is not installable
  Depends: libstdc++6 (>=4.3) but 4.2.4-1ubuntu4 is to be installed
I have followed instructions from 'Begining Ubuntu' by Thomas & Sicam.
Many thanks to anyone who can suggest where I'm going wrong..........sarum.


Well, run an apt-get update first.Then try from the skype website 

[http://www.skype.com/intl/en/download/skype/linux/choose/](http://www.skype.com/intl/en/download/skype/linux/choose/)

If that fails, try the medibuntu links and search for 2 bpackages ,skype and skype-common.

Strangely i cant seem to find them now.

---

### Post by chaanakya_chiraag on 2010-02-04
Try this: open up a terminal (Applications->Accessories->Terminal) and type in the following:
```
sudo aptitude install skype
```
entering **your login password** when it asks you.  **NOTE: IT WILL NOT SHOW YOUR PASSWORD BEING TYPED**.  This is normal :)  Now for an explanation:
sudo - gives you root privileges
aptitude - used for installing programs
install - self-explanatory; installs packages
skype - name of package
It might ask you if you want to do a certain operation.  If it does, please post the output onto this forum and I can try to figure out what exactly is happening :)
- Chiraag

---

### Post by chaanakya_chiraag on 2010-02-04
Also, can you post the exact source you added?  It might be the wrong source...

---

### Post by kostkon on 2010-02-04
> **rajeev1204 said:**
> Skype seems to be missing now from medibuntu.Strange.

BUt a google search for medibuntu skype returns some page 

[http://packages.medibuntu.org/hardy/skype.html](http://packages.medibuntu.org/hardy/skype.html)

But the packages link on the site goes here [http://packages.medibuntu.org/hardy/index.html](http://packages.medibuntu.org/hardy/index.html)

And there is no skype there.
Medibuntu has stopped offering Skype.

---

### Post by rajeev1204 on 2010-02-04
> **kostkon said:**
> Medibuntu has stopped offering Skype.

Legal issues iam sure.

---

### Post by LowSky on 2010-02-04
The skype package on Skype.com is for newer versions of Ubuntu and probably desn't support 8.04 infact it says so right there when downloading.

You need to either upgrade Ubuntu to a newer version or wait for the next LTS, or find an older verison of Skype that may not work ad isn't supported

---

### Post by L Campbell on 2010-02-04
> **LowSky said:**
> The skype package on Skype.com is for newer versions of Ubuntu and probably desn't support 8.04 infact it says so right there when downloading.

You need to either upgrade Ubuntu to a newer version or wait for the next LTS, or find an older verison of Skype that may not work ad isn't supported

YIKES !! You are right.

I was just about to try to use Skype (in 8.04.4) and couldn't find it.

Another VoiP phone that I have used is Gizmo but it, too, is not available for 8.04.4

What do we do now for a VOIP phone?        :-)

---

### Post by kostkon on 2010-02-04
> **rajeev1204 said:**
> Legal issues iam sure.
No. Check [the announcement]("https://launchpad.net/medibuntu/+announcement/4539") and [the bug report]("https://bugs.launchpad.net/medibuntu/+bug/494564") that accompanies it.

---

### Post by sarum on 2010-02-04
Thankyou for your reply. Easy to copy/paste; so I am trying your's first:-
[sudo] password for cjf: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
The following packages are BROKEN:
  skype 
0 packages upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 20.2MB of archives. After unpacking 26.2MB will be used.
The following packages have unmet dependencies:
  skype: Depends: libasound2 (> 1.0.16) but 1.0.15-3ubuntu4 is installed.
         Depends: libgcc1 (>= 1:4.3) but 1:4.2.4-1ubuntu4 is installed.
         Depends: libqt4-dbus (>= 4.4.3) which is a virtual package.
         Depends: libqt4-network (>= 4.4.3) which is a virtual package.
         Depends: libqtcore4 (>= 4.4.3) which is a virtual package.
         Depends: libqtgui4 (>= 4.4.3) which is a virtual package.
         Depends: libstdc++6 (>= 4.3) but 4.2.4-1ubuntu4 is installed.
Resolving dependencies...
Unable to resolve dependencies!  Giving up...
Abort.
also:-deb [http://download.skype.com/linux/repos/debian/](http://download.skype.com/linux/repos/debian/) stable non-free
I hope this is of use....sarum

---

### Post by chaanakya_chiraag on 2010-02-04
ok, so your repo is fine ... I think.  Wait, I know the download page on skype's website offers one version for Hardy and below and another for Intrepid and above...maybe that's the problem...only the intrepid and above version is in the repos, in which case you can't install it because it requires updated packages.
[EDIT]Now they don't even have a 8.04 and below version on the website!!  That must be your problem ... the version on Skype's repo is too new for Hardy.  I would look for PPAs containing the latest packages for those libraries.

---

### Post by sarum on 2010-02-04
Yes, I think this is the problem. I've installed 'medibuntu-keyring' and after 'sudo aptitude install skype' I still get unable to install, or words to that effect. I shall try older versions 'till I get one that works.
Thankyou all for your help.

---

### Post by chaanakya_chiraag on 2010-02-05
By the way, have you tried the static version instead of the dynamic version/Ubuntu version?  It might work that way.

---

### Post by chaanakya_chiraag on 2010-02-05
The static version is [here]("http://www.skype.com/go/getskype-linux-beta-static").  Alternatively, you can also install the package skype-static from the skype repo/medibuntu repo.

---

### Post by rajeev1204 on 2010-02-05
> **sarum said:**
> Yes, I think this is the problem. I've installed 'medibuntu-keyring' and after 'sudo aptitude install skype' I still get unable to install, or words to that effect. I shall try older versions 'till I get one that works.
Thankyou all for your help.

Remove skype completely from system, avoid medibuntu and download direct from skype.com .

---

### Post by L Campbell on 2010-02-07
> **rajeev1204 said:**
> Remove skype completely from system, avoid medibuntu and download direct from skype.com .


Thanks for your suggestion here however, when I go to the Skype website, I only see Skype for 8.10 and I have 8.04.4.

I tried Skype 'help' but could not find an answer there.

Have you tried Skype on 8.04.4?

TIA.

---

