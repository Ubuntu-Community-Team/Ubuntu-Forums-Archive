---
title: "Manually installed programs"
date: 2010-05-16
forum: New to Ubuntu
---

### Post by ratanv on 2010-05-16
Hi,
i've just downloaded and installed netbeans from netbeans' site. the installer ran well and everything seemed to work fine but on rebooting my system, the program doesn't appear in the program list, though the installed files are still on my system. can anybody please help me regarding this?

---

### Post by ell02 on 2010-05-16
My first instinct would be to type netbeans or beans or something like that in the terminal, see if it starts up.Then i would look for its launcher in the file system. Perhaps usr/share/bin.Anyway once you find how to start it from the file system you can make a launcher with the main  menu option in  preferences.
Try and get a deb package next time as it will be a whole lot easier(google getdeb).
This is what i would do i'm sure there are many other ways. peace

---

### Post by 3rdalbum on 2010-05-16
Netbeans is in the Ubuntu repositories.

The command 'netbeans' will start it - so you can create a launcher or a menu item with that command.

---

### Post by slibuntu on 2010-05-16
The mistake you made here was installing from the website. The first thing you should always do is check is the program in the repositories. Netbeans is. Some programs aren't in the repositories, but there may be a repository out there that has it, or a PPA, so look for one of those if the program isn't in the normal repositories.

Why? Programs installed through repositories automatically update along with the rest of Ubuntu, so you always have the latest patches. Also, packages installed in this way are much easier to uninstall, and integrate better with Ubuntu (menu items etc)

A final tip, the Ubuntu repositorys are usually slow to update to the latest version (eg, Firefox major releases don't get into the main repository till the next version of Ubuntu)

To overcome this, you can use a PPA that updates more regularly, meaning you'll get the latest and greatest as soon as it releases. Ubuntu Tweak can make this process pretty easy. It's not in the repos, but there is a PPA for it here - [https://launchpad.net/~tualatrix/+archive/ppa](https://launchpad.net/~tualatrix/+archive/ppa)

To add this PPA to your system, run the following command - 

```
 
sudo add-apt-repository ppa:tualatrix/ppa

```

Then to install it, you can simply run ```
sudo apt-get install ubuntu-tweak
```

---

