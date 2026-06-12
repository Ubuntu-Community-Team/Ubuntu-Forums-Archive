---
title: "Clearing out leftover config files and such"
date: 2010-07-19
forum: New to Ubuntu
---

### Post by new__buntu on 2010-07-19
Let's say that I just downloaded and installed chrome for my computer, and that I've decided that I don't really want to keep it around. So I go ahead and type "sudo apt-get purge google-chrome-stable" into the terminal. But then I run a quick search through nautilus for files with chrome in the name only to find that they're still quite numerous. Is there some way for me to remove a package PLUS all the junk that it spawns after being installed on a computer?

Thanks in advance.

---

### Post by techunit on 2010-07-19
Well go to your home folder hit CTRL H and search for .googlechrome or something of that sort... Delete it.

---

### Post by new__buntu on 2010-07-19
Chrome's puked files all over my system (a search turns up 10 directories labeled chrome, all scattered throughout my system, in addition to many more files with chrome in the name), and that's after I cleared out the chrome config folder :(. Do you know of a method to clean up that mess?

---

### Post by techunit on 2010-07-19
Well there is a chrome folder that is used by firefox thunderbird and many other applications...

---

### Post by friv_livs on 2010-07-19
For cleanup:

In terminal, sudo rm or sudo rm -rf the files/directorties that show in nautilus search.

---

### Post by new__buntu on 2010-07-19
oh... >.>

---

### Post by new__buntu on 2010-07-19
> **friv_livs said:**
> For cleanup:

In terminal, sudo rm or sudo rm -rf the files/directorties that show in nautilus search.


I'm a little bit nervous about the idea of running around "rm -rf"-ing things, and even more about "sudo rm -rf"-ing things, especially since the file system still looks like gibberish to me, and I have no way of determining which files, if any, are clutter, and which just look like clutter to my very untrained eye.

---

### Post by cbowman57 on 2010-07-19
> **new__buntu said:**
> Let's say that I just downloaded and installed chrome for my computer, and that I've decided that I don't really want to keep it around. So I go ahead and type "sudo apt-get purge google-chrome-stable" into the terminal. But then I run a quick search through nautilus for files with chrome in the name only to find that they're still quite numerous. Is there some way for me to remove a package PLUS all the junk that it spawns after being installed on a computer?

Thanks in advance.

Have you tried ubuntu tweak?  I find that it and bleachbit are indispensable.

---

### Post by oldsoundguy on 2010-07-19
> **cbowman57 said:**
> Have you tried ubuntu tweak?  I find that it and bleachbit are indispensable.

+1 for Ubuntu Tweak .. also nice manager for your sources list for synaptic!

---

### Post by new__buntu on 2010-07-19
> **cbowman57 said:**
> Have you tried ubuntu tweak?  I find that it and bleachbit are indispensable.

Just downloaded tweak, and it's awesome.

---

### Post by lovinglinux on 2010-07-19
> **new__buntu said:**
> I'm a little bit nervous about the idea of running around "rm -rf"-ing things, and even more about "sudo rm -rf"-ing things, especially since the file system still looks like gibberish to me, and I have no way of determining which files, if any, are clutter, and which just look like clutter to my very untrained eye.

Don't do that. Chrome also refers to graphical interface elements, particularly on those browsers and other applications that use XUL. Firefox and Thunderbird for example has a chrome directory, but also every extension for those applications installed in your system will have a chrome directory. So if you delete all chrome directories and files, you will probably end up messing with things you don't want.

Don't use **sudo rm** and specially **sudo rm -rf** if you don't absolutely know what you are doing. You can really screw your system if you do something wrong. Linux is not like Windows. Most of the files installed by applications are removed using the package manager.

The only configuration folder that Google Chrome could left behind is ~/.config/google-chrome. 

The browser itself is installed under /opt/google/chrome, but that should be removed with the command you used to uninstall it.

What command or tool did you use to get the list of files?

Can you post a list of them?

---

### Post by new__buntu on 2010-07-19
> **lovinglinux said:**
> Don't do that. Chrome also refers to graphical interface elements, particularly on those browsers and other applications that use XUL. Firefox and Thunderbird for example has a chrome directory, but also every extension for those applications installed in your system will have a chrome directory. So if you delete all chrome directories and files, you will probably end up messing with things you don't want.

Don't use **sudo rm** and specially **sudo rm -rf** if you don't absolutely know what you are doing. You can really screw your system if you do something wrong. Linux is not like Windows. Most of the files installed by applications are removed using the package manager.

The only configuration folder that Google Chrome could left behind is ~/.config/google-chrome. 

The browser itself is installed under /opt/google/chrome, but that should be removed with the command you used to uninstall it.

What command or tool did you use to get the list of files?

Can you post a list of them?

I used the nautilus search function to find the files. Attached iss a screenshot of the search. Given the information you provided me most of these probably have nothing to do with google-chrome (I assumed that chrome was a unique name, clearly I was wrong). At least one or two actually appears to be related to google though.

---

### Post by lovinglinux on 2010-07-19
> **new__buntu said:**
> I used the nautilus search function to find the files. Attached iss a screenshot of the search. Given the information you provided me most of these probably have nothing to do with google-chrome (I assumed that chrome was a unique name, clearly I was wrong). At least one or two actually appears to be related to google though.

Yes, lots of files there not related to google-chrome. Don't mess with them. You probably won't gain anything by deleting those google-chrome related files. Just leave them there. They won't hurt your system or slow it down.

---

### Post by k3lt01 on 2010-07-19
LovingLinux is spot on, Unless you know what you are doing you are better of just leaving it well enough alone. I would bet that there would be, at the most, 1 folder/file that would have anything to do with Google Chrome and that would be the file you initially downloaded.

EDIT: I also wouldn't go playing with UbuntuTweak or anything like it unless you are confident in your ability and the tool you are using. It is quite easy to destroy a system and difficult to repair if you stuff it up. IMHO you are much better off learning to use the native tools that are already provided with Ubuntu than to add more that can just add to any confusion you may, or may not, already have.

---

### Post by new__buntu on 2010-07-19
> **k3lt01 said:**
> LovingLinux is spot on, Unless you know what you are doing you are better of just leaving it well enough alone. I would bet that there would be, at the most, 1 folder/file that would have anything to do with Google Chrome and that would be the file you initially downloaded.

EDIT: I also wouldn't go playing with UbuntuTweak or anything like it unless you are confident in your ability and the tool you are using. It is quite easy to destroy a system and difficult to repair if you stuff it up. IMHO you are much better off learning to use the native tools that are already provided with Ubuntu than to add more that can just add to any confusion you may, or may not, already have.

Your concern is noted, and understandable, but if I'm going to destroy my system now's the time - before I go back to school. My primary concern right now is learning how to control my linux system effectively, not seeing this linux system survive the night :)

---

### Post by k3lt01 on 2010-07-19
> **new__buntu said:**
> Your concern is noted, and understandable, but if I'm going to destroy my system now's the time - before I go back to school. My primary concern right now is learning how to control my linux system effectively, not seeing this linux system survive the night :)Then my advice is to learn the tools already there and not use tools that are not supported by the parent company.

---

### Post by new__buntu on 2010-07-19
> **k3lt01 said:**
> Then my advice is to learn the tools already there and not use tools that are not supported by the parent company.

I suppose that so long as I'm bothering to not run everything as root I might as well go all the way and behave semi-responsibly on my computer. Bad habits and all that.

---

### Post by lovinglinux on 2010-07-19
> **new__buntu said:**
> Your concern is noted, and understandable, but if I'm going to destroy my system now's the time - before I go back to school. My primary concern right now is learning how to control my linux system effectively, not seeing this linux system survive the night :)

If you want to do that, install Virtual Box, then install another Ubuntu as guest and mess with it. With a virtual machine you can create snapshots and revert any change you make, even if they destroy the system. Why would you do that on your system when you can do on a VM?

---

### Post by tahitiwibble on 2010-07-19
Do you do [this]("http://ubuntuforums.org/showpost.php?p=2573173&postcount=6")?

And do you have gtkorphan?

:)

---

### Post by CharlesA on 2010-07-20
> **lovinglinux said:**
> If you want to do that, install Virtual Box, then install another Ubuntu as guest and mess with it. With a virtual machine you can create snapshots and revert any change you make, even if they destroy the system. Why would you do that on your system when you can do on a VM?

+1 to running a VM of Ubuntu to mess around with. Snapshots just rock.

> **tahitiwibble said:**
> Do you do [this]("http://ubuntuforums.org/showpost.php?p=2573173&postcount=6")?

And do you have gtkorphan?

:)

apt-get purge will remove most config files, but autoclean and autoremove only remove packages that are no longer needed, not config files.

---

### Post by tahitiwibble on 2010-07-20
> **CharlesA said:**
>  apt-get purge will remove most config files, but autoclean and autoremove only remove packages that are no longer needed, not config files.

Thanks for the precision. Another one to tuck away :)

---

