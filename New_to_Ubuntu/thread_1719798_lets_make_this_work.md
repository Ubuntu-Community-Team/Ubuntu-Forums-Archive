---
title: "lets make this work"
date: 2011-04-02
forum: New to Ubuntu
---

### Post by fattyz on 2011-04-02
Hi guys I decided, now that I got everything working in windows, to get everything working in ubuntu 10.04

Here is my setup.  1 hp desktop windows 7 64 bit, 1 acer laptop windows 7 64 bit, 1 dell laptop windows vista 32 bit, everything networked, printing, sharing files, and mounting iphones.
so far so good.

Now I have a clean 10.04 install on everything and am trying to get the dell laptop and desktop working correctly under 10.04, I'll deal with the acer lappy later.

Here is what I have under ubuntu.

Network shares and printing

Can not find samba shares.  Following instructions, I tried to share public folders using samba shares. Can not mount location error. Although I can see all the computers on the network under network, I can not share files. (oddly enough, the windows share works and files can be copied between machines running ubuntu and the laptop running windows 7)

Can not print from either machine.  Though the desktop tries to go to the correct printer, nothing happens.  The laptop can not see it at all and i am not sure how to share it.

Iphone 

following the instructions here,  [http://ubuntuforums.org/archive/index.php/t-1628529.html](http://ubuntuforums.org/archive/index.php/t-1628529.html) I got the iphone 3gs 4.2.1 to mount on the laptop but the desktop stubbornly refuses to see it.  I can see it under network as my iphone, looks like a computer but can not access it.  Can not mount location error.

Should I upgrade to 10.04.2?  I tried to do that and made a boot usb stick originally but, after the install I had no networking so I went back and made a 10.04 stick and got everything installed from that.

Any advice appreciated, I'm going to get it all working this time!

FattyZ

---

### Post by wolfen69 on 2011-04-02
Just as an fyi, you should ask questions one at a time. It can seem overwhelming to us volunteers (no one gets paid here) trying to help.

Btw, if you have 10.04 fully updated, then you are using 10.04.2 The .2 just means it has all updates since the beginning.

---

### Post by fattyz on 2011-04-04
I thought of that but, doing it on the fly I made a list.  So on th e topic of updates, if you just keep hitting update manager it'll bump you up to 10.04.2 is what I hear you saying.  I thought you had to do a version update.

ALMOST THERE

Update:  I guess the upstairs machine (desktop) had to digest all the updates because today the iphone appeared so, now it is working on both ubuntu boxes.

Last 2 things are networking and printing, I'm sure the printing will be ok once the 2 machines start talking (I had it working last year but I moved and was taking some medication that was REALLY not good for me.  : ))

Anyway, I will fool around with it some more but right now the network will not allow me to copy files, though I can see everything.  This time I tried it and I got an error that said I did not have permission to copy files from one computer to the other.  I set up samba shares for the public folders on both computers.

I have very little experience in ubuntu though I can use the GUI pretty well now and managed to sudo apt-get upgrade update everything.  My terminal knowledge consists of cutting and pasting commands from the internet!

FattyZ

---

### Post by fattyz on 2011-04-04
Got it, followed this [http://ubuntuforums.org/showthread.php?t=1468498](http://ubuntuforums.org/showthread.php?t=1468498)

Made samba work, I wish it were easier to find but, I think the answer is, search here in this forum as opposed to searching the web in general,

Thx,

FattyZ

---

### Post by wolfen69 on 2011-04-04
> **fattyz said:**
> Got it, followed this [http://ubuntuforums.org/showthread.php?t=1468498](http://ubuntuforums.org/showthread.php?t=1468498)

Made samba work, I wish it were easier to find but, I think the answer is, search here in this forum as opposed to searching the web in general,

Thx,

FattyZ

Don't limit yourself to just the forums. [www.googlubuntu.com](www.googlubuntu.com) is really good too, as you will only find answers related to ubuntu. But I find regular old Google to be good too.

---

### Post by Mark Phelps on 2011-04-05
To avoid future problems, I would strongly advise that you do NOT copy files from your Linux PC to any of the Windows PCs running Vista or Win7 -- especially if you are copying to the OS partitions on those PCs.

Vista and Win7 are especially touchy to changes made to their OS partitions from Linux.  Real easy to accidentally corrupt their OS partitions, rendering them unbootable.

OK to read from them, though.

---

### Post by fattyz on 2011-04-07
OK thanks!  I just got the last thing working.  I was able to print across the wireless network but not from the server.  Since the server is actually connected to the printer via wireless, I just re-did the settings to make it not a server and viola!  all is well.

That, as they say is that, until I run into something I can't do and so end up here for another dose of your excellent advice, (like when I upgrade to 11.04 hahaha)  For now since everything is working I think I'll stay where I am.  I'll probably keep this thread going as things pop up as it is a great learning tool.  Thankfully, I recall most of what I did last time I was using Ubuntu and it all came back to me quickly.  

Compiz is a particular favorite and I currently :guitar:have it humming along with a nice skydome and emerald theme.  In addition, I really love the native Iphone support which makes life so much happier.  I have never used Itunes and never will, and it's great not to have to hunt down all kinds of third party software to make the stupid phone do what it should have done anyway.

I'll be talking to you guys and thanks as always!

FattyZ

---

### Post by fattyz on 2011-04-20
Hi all,

Just out of curiosity, where'd the network go?  As I explained earlier, I got everything working in the network department.  Shared the public folder using samba.  Everything showed up and worked fine.  I went to transfer a file earlier  today after not looking at the network for about a week, and without doing anything to anything during that time, as far as I know, the network shares were gone!  I have run update manager when the system requests I do so, but aside from that, I have not made any major changes I'm aware of.  The windows network Icons still showed up. Unfortunately under the wrong workgroup and they don't work. The windows shares want a password, which dosen't work even if you provide the correct one. The samba shares are just plain gone.

I wonder what could have happened to them?

Naturally, I'll get around to going in and setting everything back up when I get a chance but, I am surprised.  Any Ideas?

Thanks as always,

FattyZ

---

### Post by fattyz on 2011-04-23
Well, I don't know what happened except to say the network burped or had an off day.  I went into samba on both Ubuntu machines to check the settings and found that the "writeable" check box had somehow mysteriously come unchecked. Ubuntu machines.  One of my kids insists on running windows so, I'll look into that later.

Other than that, everything is running great, super fast, no spyware, malware or viruses to scan for!

FattyZ

---

### Post by fattyz on 2011-04-26
Hi I forget how to fix this, I looked in sources.list and I do not see the reference to these repos.  I vaguely remember this problem from the last time I used Ubuntu, but not enough to fix it.

I added software sources to system>administration and it updated but, I got more or less the same errors.

W: Failed to fetch [http://ppa.launchpad.net/ferramroberto/lucidtest/ubuntu/dists/maverick/main/source/Sources.gz](http://ppa.launchpad.net/ferramroberto/lucidtest/ubuntu/dists/maverick/main/source/Sources.gz)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/ferramroberto/lucidtest/ubuntu/dists/maverick/main/binary-i386/Packages.gz](http://ppa.launchpad.net/ferramroberto/lucidtest/ubuntu/dists/maverick/main/binary-i386/Packages.gz)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/pmercenary/ppa/ubuntu/dists/maverick/main/source/Sources.gz](http://ppa.launchpad.net/pmercenary/ppa/ubuntu/dists/maverick/main/source/Sources.gz)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/pmercenary/ppa/ubuntu/dists/maverick/main/binary-i386/Packages.gz](http://ppa.launchpad.net/pmercenary/ppa/ubuntu/dists/maverick/main/binary-i386/Packages.gz)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/pmercenery/ppa/ubuntu/dists/maverick/main/source/Sources.gz](http://ppa.launchpad.net/pmercenery/ppa/ubuntu/dists/maverick/main/source/Sources.gz)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/pmercenery/ppa/ubuntu/dists/maverick/main/binary-i386/Packages.gz](http://ppa.launchpad.net/pmercenery/ppa/ubuntu/dists/maverick/main/binary-i386/Packages.gz)  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.


Appreciate your answers in advance,

Thanks,

FattyZ

---

### Post by fattyz on 2011-04-27
oops! I just found something called sources.list.d which might be the culprit...



/etc/apt/sources.list.d/canonical-partner-maverick.list
/etc/apt/sources.list.d/canonical-partner-maverick.list.save
/etc/apt/sources.list.d/deluge-team-ppa-maverick.list
/etc/apt/sources.list.d/deluge-team-ppa-maverick.list.save
/etc/apt/sources.list.d/ferramroberto-lucidtest-maverick.list
/etc/apt/sources.list.d/ferramroberto-lucidtest-maverick.list.save
/etc/apt/sources.list.d/kernel-ppa-ppa-maverick.list
/etc/apt/sources.list.d/kernel-ppa-ppa-maverick.list.save
/etc/apt/sources.list.d/medibuntu.list
/etc/apt/sources.list.d/medibuntu.list.save
/etc/apt/sources.list.d/pmcenery-ppa-maverick.list
/etc/apt/sources.list.d/pmcenery-ppa-maverick.list.save
/etc/apt/sources.list.d/pmercenary-ppa-maverick.list
/etc/apt/sources.list.d/pmercenary-ppa-maverick.list.save
/etc/apt/sources.list.d/pmercenery-ppa-maverick.list
/etc/apt/sources.list.d/pmercenery-ppa-maverick.list.save
/etc/apt/sources.list.d/tualatrix-ppa-maverick.list
/etc/apt/sources.list.d/tualatrix-ppa-maverick.list.save

These all appear as individual icons in sources.list.d and it seems this is what is being used when I try to sudo apt-get update && sudo apt-get upgrade, should I just delete the offending entries?

Thanks

FattyZ

---

### Post by alphacrucis2 on 2011-04-27
> **fattyz said:**
> oops! I just found something called sources.list.d which might be the culprit...



/etc/apt/sources.list.d/canonical-partner-maverick.list
/etc/apt/sources.list.d/canonical-partner-maverick.list.save
/etc/apt/sources.list.d/deluge-team-ppa-maverick.list
/etc/apt/sources.list.d/deluge-team-ppa-maverick.list.save
/etc/apt/sources.list.d/ferramroberto-lucidtest-maverick.list
/etc/apt/sources.list.d/ferramroberto-lucidtest-maverick.list.save
/etc/apt/sources.list.d/kernel-ppa-ppa-maverick.list
/etc/apt/sources.list.d/kernel-ppa-ppa-maverick.list.save
/etc/apt/sources.list.d/medibuntu.list
/etc/apt/sources.list.d/medibuntu.list.save
/etc/apt/sources.list.d/pmcenery-ppa-maverick.list
/etc/apt/sources.list.d/pmcenery-ppa-maverick.list.save
/etc/apt/sources.list.d/pmercenary-ppa-maverick.list
/etc/apt/sources.list.d/pmercenary-ppa-maverick.list.save
/etc/apt/sources.list.d/pmercenery-ppa-maverick.list
/etc/apt/sources.list.d/pmercenery-ppa-maverick.list.save
/etc/apt/sources.list.d/tualatrix-ppa-maverick.list
/etc/apt/sources.list.d/tualatrix-ppa-maverick.list.save

These all appear as individual icons in sources.list.d and it seems this is what is being used when I try to sudo apt-get update && sudo apt-get upgrade, should I just delete the offending entries?

Thanks

FattyZ

Don't delete them just uncheck the ones reporting not found errors via software sources. Access software sources via System Administration - Synaptic Package Manager. Then select the Settings - Repositories. (Other Software) The above PPA's (which are unofficial repos you must have manually added) will be listed. You can just uncheck them to temporarily disable them. PPA's are used for installing either software that is not available in the normal repos or to get newer versions. They are on a use at your own risk basis. If you are playing around with PPA's it's a good idea to install ppapurge and that allows you to back out any specific ppa back to the standard repo version in case something goes bad.

---

### Post by fattyz on 2011-05-01
I tried to upgrade to 11xx today since the system offered me the opportunity but the update failed.  Couldn't get software, check your internet connection.  Well, there is nothing wrong with the connection, I think it just couldn't source what it needed.  

I'll try it again and if it fails, I'll probably make a bootable usb stick and put it on that way.  Or I'll stick with this until I make the update manager run with no errors.

Thanks,

FattyZ

---

### Post by fattyz on 2011-05-01
Sigh.  Nothing will update or upgrade completely, not even a version upgrade.  To get around this and hopefully correct the software update errors I created somehow, I may run the version upgrade from the USB stick.

Should I do this or will I have the same problem?  Or am I just creating work for myself for nothing?

Thanks 

FattyZ

---

### Post by fattyz on 2011-05-02
Before I do a version upgrade, I'd like to figure out what went wrong with my upgrade/update.  Why am I not able to get the updates?  Why can't I do the version upgrade?  Did I do something to the file that is keeping it from working?  

Anyone?

Thanks,

FattyZ

---

### Post by fattyz on 2011-05-02
Here are the files

sources.list.distupgrade

# deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/ maverick main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://76.73.4.58/ubuntu/](http://76.73.4.58/ubuntu/) maverick restricted main universe
deb-src [http://76.73.4.58/ubuntu/](http://76.73.4.58/ubuntu/) maverick restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://76.73.4.58/ubuntu/](http://76.73.4.58/ubuntu/) maverick-updates restricted main universe
deb-src [http://76.73.4.58/ubuntu/](http://76.73.4.58/ubuntu/) maverick-updates restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://76.73.4.58/ubuntu/](http://76.73.4.58/ubuntu/) maverick multiverse
deb-src [http://76.73.4.58/ubuntu/](http://76.73.4.58/ubuntu/) maverick multiverse
deb [http://76.73.4.58/ubuntu/](http://76.73.4.58/ubuntu/) maverick-updates multiverse
deb-src [http://76.73.4.58/ubuntu/](http://76.73.4.58/ubuntu/) maverick-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) maverick-backports main restricted multiverse universe
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) maverick-backports main restricted multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) maverick main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) maverick main

deb [http://76.73.4.58/ubuntu/](http://76.73.4.58/ubuntu/) maverick-security restricted main universe
deb-src [http://76.73.4.58/ubuntu/](http://76.73.4.58/ubuntu/) maverick-security restricted
deb [http://76.73.4.58/ubuntu/](http://76.73.4.58/ubuntu/) maverick-security multiverse
deb-src [http://76.73.4.58/ubuntu/](http://76.73.4.58/ubuntu/) maverick-security multiverse

sources.list.d

/etc/apt/sources.list.d/canonical-partner-maverick.list
/etc/apt/sources.list.d/canonical-partner-maverick.list.distUpgrade
/etc/apt/sources.list.d/canonical-partner-maverick.list.save
/etc/apt/sources.list.d/deluge-team-ppa-maverick.list
/etc/apt/sources.list.d/deluge-team-ppa-maverick.list.distUpgrade
/etc/apt/sources.list.d/deluge-team-ppa-maverick.list.save
/etc/apt/sources.list.d/ferramroberto-lucidtest-maverick.list
/etc/apt/sources.list.d/ferramroberto-lucidtest-maverick.list.distUpgrade
/etc/apt/sources.list.d/ferramroberto-lucidtest-maverick.list.save
/etc/apt/sources.list.d/kernel-ppa-ppa-maverick.list
/etc/apt/sources.list.d/kernel-ppa-ppa-maverick.list.distUpgrade
/etc/apt/sources.list.d/kernel-ppa-ppa-maverick.list.save
/etc/apt/sources.list.d/medibuntu.list
/etc/apt/sources.list.d/medibuntu.list.distUpgrade
/etc/apt/sources.list.d/medibuntu.list.save
/etc/apt/sources.list.d/pmcenery-ppa-maverick.list
/etc/apt/sources.list.d/pmcenery-ppa-maverick.list.distUpgrade
/etc/apt/sources.list.d/pmcenery-ppa-maverick.list.save
/etc/apt/sources.list.d/pmercenary-ppa-maverick.list
/etc/apt/sources.list.d/pmercenary-ppa-maverick.list.distUpgrade
/etc/apt/sources.list.d/pmercenary-ppa-maverick.list.save
/etc/apt/sources.list.d/pmercenery-ppa-maverick.list
/etc/apt/sources.list.d/pmercenery-ppa-maverick.list.distUpgrade
/etc/apt/sources.list.d/pmercenery-ppa-maverick.list.save
/etc/apt/sources.list.d/tualatrix-ppa-maverick.list
/etc/apt/sources.list.d/tualatrix-ppa-maverick.list.distUpgrade
/etc/apt/sources.list.d/tualatrix-ppa-maverick.list.save

Thanks again,

FattyZ

---

### Post by fattyz on 2011-05-04
Anyone know how to make this work?

Anyone?

FattyZ

---

### Post by Nickjpost on 2011-05-04
> **fattyz said:**
> Anyone know how to make this work?

Anyone?

FattyZ

I had a similar issue and the only way I was able to upgrade was to create a live USB. I upgraded successfully and haven't had any other issues......yet.

---

### Post by fattyz on 2011-05-06
Sounds good thanks, I'll do that.

yours,

Fattyz

---

### Post by fattyz on 2011-05-09
After several attempts I got upgraded via bootable usb stick to 11.04.  It seems cool and will take some getting used to but the update upgrade works so far and it seems like it has lots of great new stuff in it so I'll be talking with you when I break it.

Thanks

FattyZ

---

### Post by fattyz on 2011-05-12
Just would like to see the compiz fusion icon appear in it's usual location, allowing me to pick metacity or whatever.  Anyone else having this problem?  I've tried everything I can think of.

Also, the compiz simple settings manager will not install, says there is some sort of conflict.

Thanks 

Fattyz

---

### Post by fattyz on 2011-05-15
dconf-editor.  good luk!

---

### Post by fattyz on 2011-05-20
Seemingly without help why is this?  "Can't download certain pkgs would you like to continue to ignore this?"

No, I don't want to continue to ignore it I want to know what corrupts that file and I'd like to be able to fix it without having to upgrade to 11.04.

This I know from the last time I posted the question does not just happen to me.

Anyone know how or why this happens and how to fix it.  Edit the sources file or "try another server" something I never had much luck with?

Thanks,

FattyZ

---

### Post by fattyz on 2011-05-23
sudo add-apt-repository ppa:team-xbmc-svn/ppa && sudo apt-get update

failed to fetch.

whats going on?  Anyone know how to get xbmc?  Every time I try something out of the ordinary I start getting update failures and 404 not found errors??

FattyZ

---

### Post by fattyz on 2011-06-19
A little disappointed that I have to go back to windows to move music back and forth to my iphone (ares to media monkey) easily make a quick video (windows movie maker).  I just don't find anything in Ubuntu that measures up for ease of use.

I tried a bunch of stuff under Ubuntu to do these simple tasks and was consistently frustrated.

FattyZ

---

### Post by wildmanne39 on 2011-06-20
> **fattyz said:**
> A little disappointed that I have to go back to windows to move music back and forth to my iphone (ares to media monkey) easily make a quick video (windows movie maker).  I just don't find anything in Ubuntu that measures up for ease of use.

I tried a bunch of stuff under Ubuntu to do these simple tasks and was consistently frustrated.

FattyZHi, you could always install windows inside virtualbox on ubuntu that way you can run them at the same time when needed.
[http://www.virtualbox.org/](http://www.virtualbox.org/)

---

### Post by fattyz on 2011-06-21
Virtual box should be a good project, I'll try it.

Thx 

FattyZ

---

### Post by fattyz on 2011-06-23
I don't understand after all the upgrades and stuff of I can stick a dvd in the drive and it won't play giving me a message it's encrypted.

When I tried to update the codecs I get 404 errors and some stuff found or old stuff used instead.

The network vanishes.  I'm back to sneaker net.

I know it's bad form to make fun here of oo bun too but come on?  Is this backwards mobility or what?  Its not like I'm screwing around with the thing im just trying to use it!

Can anyone tell me what I'm doing wrong?  Does update manager knock out things you've already struggled to accomplish?

FattyZ

---

### Post by fattyz on 2011-06-24
W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) natty InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: Failed to fetch [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/dists/natty/main/source/Sources](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/dists/natty/main/source/Sources)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/dists/natty/main/binary-i386/Packages](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/dists/natty/main/binary-i386/Packages)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.

FattyZ

---

### Post by fattyz on 2011-06-24
network next, i still do not understand those 404 errors.  Why won't it update itself correctly?

FattyZ

---

