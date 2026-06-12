---
title: "Some programs not showing in &quot;Add/Remove&quot; nor in &quot;Synaptic&quot; but repositories are ok"
date: 2009-06-09
forum: New to Ubuntu
---

### Post by AvatarGG on 2009-06-09
Hello:

I installed Ubuntu 9.04 final version (fresh install) when it was available. Since the first day there were some programs missing in "Add/Remove programs" and "Synaptic": Skype, Opera, aMule, BOINC client, etc... (that was not the case in previous versions). I thought that maybe the repositories were not updated but today the situation it's the same.

I checked "Software origins" and all the options are activated, I also activated the "third party" option but there is not change. All the security updates are installed. Any help would be appreciated.

Thanks in advance.

---

### Post by wpshooter on 2009-06-09
Are you sure that you have MAIN, UNIVERSE, and MULTIVERSE checked ?

When you say **fresh install**, do you mean from scratch or as an upgrade ?

---

### Post by SoftwareExplorer on 2009-06-09
First make sure that the Add/remove programs has show: set to 'All Availible Applications'

I think that skype is not free software, so you have to download it from medibuntu.org.

As far as BOINC client, Does BOINC Manager come up when you enter BOINC into the add/remove software search?

---

### Post by AvatarGG on 2009-06-09
Yes. Main, Multiverse and Universe are checked.

I mean from scratch.

Yes, "All available applications" is selected.

"BOINC Manager" shows up, but not "BOINC Client".

---

### Post by lisati on 2009-06-09
An Ubuntu-friendly version of Skype can be downloaded here: [http://www.skype.com/intl/en/download/skype/linux/choose/](http://www.skype.com/intl/en/download/skype/linux/choose/)

---

### Post by zvacet on 2009-06-10
For Skype add [Medibuntu repo]("https://help.ubuntu.com/community/Medibuntu") and you can download Opera from [here]("http://www.opera.com/download/index.dml?platform=linux") or you can add 

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner

to your source list.

---

### Post by AvatarGG on 2009-06-10
Thank you for the help but why aren't those programs on the list? I am completely sure that at least Opera and aMule where on the list the last time I installed Ubuntu about a year ago. I think there must be more people with the same problem because I started a live session of Ubuntu 9.04 on another computer using the LiveCD and those programs are not on the list. Can anyone with an installation from scratch of Ubuntu 9.04 check if that is the case? Thank you.

Also, if I install a program from its official website there will be an icon created for it in the menu? And will it be updated automatically like the "normal ones"? And if I add the repo instead of downloading it from the web?

Thank you very much.

---

### Post by LowSky on 2009-06-10
> **AvatarGG said:**
> Also, if I install a program from its official website there will be an icon created for it in the menu? And will it be updated automatically like the "normal ones"? And if I add the repo instead of downloading it from the web?


depending on the source most will install an icon. it wont auto update unless it has a repo, using an extra repo will update but they are not supported by canonical and if there is a conflict it can casue issues. Dont worry about repos form respected programs like opera, or medibuntu, but small projects like many found on sourceforge or similar can be problematic. and dont assume that a debian repo will work correctly in ubuntu

---

### Post by zvacet on 2009-06-10
@ **AvatarGG**

> Also, if I install a program from its official website there will be an icon created for it in the menu? And will it be updated automatically like the "normal ones"? And if I add the repo instead of downloading it from the web?


It will create icon if you install from web site and you can check for updates.if you install from repos you have to wait until updated version is put in repos.It doesn't take much time.I prefer install from web site,but that is just me.

---

### Post by egalvan on 2009-06-10
> I am completely sure that at least Opera and aMule where on the list the last time I installed Ubuntu about a year ago.
 Can anyone with an installation from scratch of Ubuntu 9.04 check if that is the case? Thank you.


Clean install of 9.04, all repositories enabled, medibuntu installed, all updates taken.

In Synaptic,

Skype shown
Opera not shown
aMule not shown

---

### Post by Rokashevich on 2009-06-10
$ sudo rm -fr /var/lib/apt-xapian-index
$ sudo update-apt-xapian-index

---

### Post by AvatarGG on 2009-06-10
So, for some reason, programs like Opera, aMule, BOINC... were deleted from the default repositories. Does anyone know why? Did those programs become "unsupported" or something?

> **Rokashevich said:**
> $ sudo rm -fr /var/lib/apt-xapian-index
$ sudo update-apt-xapian-index Can you explain what are those commands for, please? I'm afraid of typing them without knowing what they do.

---

### Post by ttoolin on 2009-07-15
I have a fresh question to ask, and it seems to fit here.

I few weeks ago, the BOINC software advised that there is a new update available, and there was on the BOINC website.  The synaptic package manager has the same version that I have installed.

I downloaded the copy from the BOINC website, and after a little research, managed to figure out how to do something with it from a terminal screen.  It put the program into a new folder on my desktop.  It seemed to run okay, but since the installation was obviously not what I wanted to happen, I moved the new folder into the trash and rebooted, and when I verified all was okay, emptied my trash.  I could probably (likely, quite easily) work on getting the software loaded into the BOINC native folder, but it really isn't that important to me, and I'm more than happy to wait for the synaptic package manager to come up with the newer version, which is likely on a developer's things to do list.

My question, which really isn't a BOINC question, is . . . Is it wiser to wait for the ubuntu community to provide an update, or to try to use a third-party vendor's update release.  In this case, and I've seen others, the vendor states that it is compatible with my ubuntu version (which is 9.04, but that changes from time-to-time).

Thanks in advance.

terry

---

### Post by cariboo on 2009-07-15
Whatever packages are in the repositories when a version is released. are the version we are stuck with, the only updates will be bug fixes and security updates. 

If you want a newer version of a package, you have to install it from other sources, unless you feel like walking on the edge and trying the next version while it is still in alpha.

---

### Post by ttoolin on 2009-07-15
thanks!

terry

---

