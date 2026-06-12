---
title: "Enabling Video Driver"
date: 2011-02-06
forum: New to Ubuntu
---

### Post by joe1363 on 2011-02-06
Hello all. 
I recently dual booted ubuntu 10.10 on my old laptop in hopes of it being faster and more stable than the Windows XP currently on my computer. It generally is, but I'm having some problems that I think can be fixed by enabling my video card.

From searching online, this should be done by going to /System/Admin/Additional drivers. However, after searching for available drivers it shows a blank list and tells me that there aren't any proprietary drivers in use.  Here are my system specs:

Fujitsu Lifebook N3510
  Intel(R) Pentium(R) M processor 1.73GHz, 2GB RAM
ATI Technologies Inc M22 [Mobility Radeon X300]  
 
It's an old machine and that video card is not longer supported by AMD (I've checked their site and couldn't find anything) so I know there may be problems.

I'm not sure what to do here, any suggestions? Let me know if I left out any important information. Thanks.

---

### Post by joe1363 on 2011-02-06
After doing some research I see the possibility that I won't be able to get this working due to ATI dropping support on it. It looks like another option would be to go with an open source driver from ubuntu. 

I read that it should be the default video driver for ubuntu, yet I can't seem to find it on my computer (as I mentioned before the list of additional drivers is empty). Can someone tell me the name of the driver, a way to install this driver, and/or how to check if it is on my computer?

---

### Post by 123456789123456789123456 on 2011-02-06
incorrect

from my reasearch try this, go to synaptic package manager, search for ati.
if all of the ati drivers are not currently installed, install them from what you see.  then do a search for enabling ati drivers, after running the enable code from terminal, restart the computer, the ubuntu installation should then reconize the video card, and run correctly.

---

### Post by waynefoutz on 2011-02-07
You're right. You are stuck with the open source drivers, but the ones installed out of the box aren't the cutting edge drivers that will give you the best results.

Try this:

to add this repository, in the terminal type:

```
sudo add-apt-repository ppa:xorg-edgers/ppa
```

then:

```
sudo apt-get update
```

Next, go to Administration/Update Manager, and install the updates. You should see MAJOR improvements. You should also get full 3d.

---

### Post by clhsharky on 2011-02-07
joe1363

Please read xorg-edgers/ppa first.


waynefoutz

> ** Please do not publish instructions for how to install from this archive without linking to this page! Anyone using packages from this archive is expected to read this page first and it is recommended to check back occasionally for notice on problems that may arise. **
[https://edge.launchpad.net/~xorg-edgers/+archive/ppa](https://edge.launchpad.net/~xorg-edgers/+archive/ppa)


123456789123456789123456

The ati drivers in synaptic package manager are not for his
> ATI Technologies Inc M22 [Mobility Radeon X300] 
chip, there for  ati HD cards.


Sharky

---

### Post by waynefoutz on 2011-02-07
> **clhsharky said:**
> joe1363

Please read xorg-edgers/ppa first.


waynefoutz


[https://edge.launchpad.net/~xorg-edgers/+archive/ppa](https://edge.launchpad.net/~xorg-edgers/+archive/ppa)




Thank you for pointing that out. I'll remember that in the future. That being said, this will work fine on Joe's radeon card.

---

### Post by joe1363 on 2011-02-07
Thanks for the input everyone. Unfortunately, I spent well over an hour and a half downloading the ATI packages before seeing the rest of the replies (I have slow dsl). 

As for the open source driver, I read the xorg-edgers/ppa and I'm not too sure where I'm at with that. After looking at the package details on the [https://edge.launchpad.net/~xorg-edgers/+archive/ppa]("https://edge.launchpad.net/%7Exorg-edgers/+archive/ppa") page, it seems I do have a lot of those packages, but a lot of them failed to build. Should I run the the ppa-purge anyway to be safe?

---

### Post by waynefoutz on 2011-02-07
If they failed to build yes. They should have done nothing more than replace the files that Ubuntu installed out of the box. The out of the box open source drivers are the only thing that card will work on. The PPA is nothing more than cutting edge updates of the out of box open source drivers.

---

### Post by joe1363 on 2011-02-07
I really don't want to mess anything up so can you confirm everything that I need to put into the terminal to remove and reinstall xorg? I tried putting in "sudo ppa-purge xorg-edgers" but that got me the message of "sudo: ppa-purge: command not found." After looking around, I think this might be the process:

sudo apt-get --purge remove xserver-xorg-video-nouveau

sudo add-apt-repository ppa: xorg-edgers/ppa

sudo apt-get update


Is this right?

---

### Post by realzippy on 2011-02-07
[I]I tried putting in "sudo ppa-purge xorg-edgers" but that got me the message of "sudo: ppa-purge: command not found."
[/I]
 You need the package **ppa-purge** to run the command "ppa-purge"  :-)

```
sudo apt-get install ppa-purge
```

..then run again 

```
sudo ppa-purge xorg-edgers
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by joe1363 on 2011-02-07
I entered "sudo apt-get install ppa-purge" and got the package. I then entered "sudo ppa-purge xorg-edgers" and got this:

PPA to be removed: xorg-edgers ppa
Warning:  Could not find package list for PPA: xorg-edgers ppa

Does this mean that it's already removed and I can go ahead and reinstall? Please forgive my linux noobness yet again.

---

### Post by realzippy on 2011-02-07
Yes.
You can also open eg System/Administration/Synaptic
and sort the software sources by "origin" to check...installed PPAs on the top.

---

### Post by joe1363 on 2011-02-07
I'm not sure if it worked. This is what happened:

joe@ubuntu:~$ sudo add-apt-repository ppa: xorg-edgers/ppa
[sudo] password for joe: 
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv 165D673674A995B3E64BF0CF4F191A5A8844C542
gpg: requesting key 8844C542 from hkp server keyserver.ubuntu.com
gpg: key 8844C542: public key "Launchpad PPA for xorg crack pushers" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)

What else do I need to do?

---

### Post by realzippy on 2011-02-07
*sudo add-apt-repository ppa: xorg-edgers/ppa*

*installs* the ppa.Thought you wanted to *purge* it?

---

### Post by joe1363 on 2011-02-07
Well, I want to reinstall it since several of the packages for it failed to build. I read that trying to install without purging first could lead to some serious problems. After running that though, nothing comes up in the additional drivers list, so I figure I probably missed something. I'm quite the ubuntu noob, so don't spare any details that might help.

I was rereading this some earlier replies and realized that I'm completely sure what xorg-edgers is (and possibly xorg itself for that matter). Do I need to install the base xorg and then xorg-edgers after it? I need to know the whole process for doing so.

---

### Post by realzippy on 2011-02-07
There will be no additional driver available.
In vanilla Ubuntu the kernel recognises your ATI card and
the free driver is loaded automatically.If you now add xorgedgersPPA,
only certain files are mofified (eg xserver-xorg-video-ati).
Nothing to install,just run
sudo apt-get update 
and
sudo apt-get upgrade
after you added or purged a PPA.

In this case it is graphics driver related (Xserver has to be restarted)
so after a reboot your xorgedgers modified ATI driver is working.
Btw,do not think there is a huge difference to vanilla ATI as somebody mentioned in this thread,but you will find out.
After you rebooted,run:

```
lshw -C Display
```

what does the "configuration" line say?ATI?

---

### Post by joe1363 on 2011-02-07
I put "lshw -C display" into the terminal and yes, it shows my ati card. Maybe I was asking the wrong question.

My problem seem to be when displaying 3D graphics. When playing some games that have 3D (e.g. Minecraft, some psx games) it runs, but it's slow and choppy. I figured that I could find a solution to that by checking the driver in the additional drivers, but since my list blank that may not be the way to do it. Is there anything I can do in this situation?

---

### Post by realzippy on 2011-02-07
..it should also show your driver:

```
configuration: driver=ati latency=0
```

or similar.

If this is the case,then there is nothing you can do..
You could install an old and **unsupported** version of ubuntu (8.04) where an old fglrx proprietary ATI driver is still working...but as far as I can remember,this driver was also buggy and not so easy to set up.

---

### Post by joe1363 on 2011-02-07
Well, if there's no way to configure it, I guess I'm stuck. I wanted to attempt a full move to ubuntu but I guess that's not happening with my current computer. Thanks anyway.

---

### Post by realzippy on 2011-02-07
Mark this thread as solved please,sorry nobody can help.
Note that it is ATI's decision not to support old cards in linux...
So,if you like Ubuntu for any reason,you can set up a dualboot for casual gaming.

---

