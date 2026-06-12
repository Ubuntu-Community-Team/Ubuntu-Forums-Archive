---
title: "Problems upgrading to 10.04"
date: 2010-08-05
forum: New to Ubuntu
---

### Post by whitemagicwoman on 2010-08-05
I am new to the forum and Ubuntu, though I have a small amount of Unix background from my college days.  I installed Ubuntu 7.04 via WUBI on my old Dell Latitude C600 a few days ago.  (Long story short, the CDROM drive does not work and I can't boot via USB.)  All went well with help from the support forums, and since that point I have been working on upgrading things.  All went well until I tried to make the transition from 8.04 to 10.04.

As near as I can tell, what happened is this: I was prompted to upgrade by the Upgrade Manager.  I clicked "Install Upgrade."  Then, I got a message saying, "Once this is started it may take several hours and can't be stopped, are you sure?"  I clicked "No" because I was about to go out.

When I attempted to restart the process the next day, I started getting error messages.  One said that the upgrade was aborting and that my system may no longer be usable.  (I am backed up.)  I also was prompted to send a bug report, and started a LaunchPad account for that purpose.  I had not yet read the post about filing bug reports in this forum, so I hadn't enabled aptitude, so the bug report didn't go through.  This works out since apparently it's more appropriate to post here first.

Anyway, this is what I got:
```

$ubuntu-bug update-manager
hook /usr/share/apport/general-hooks/automatix.py crashed:
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/apport/report.py", line 598, in add_hooks_info
    symb['add_info'](self)
  File "/usr/share/apport/general-hooks/automatix.py", line 17, in add_info
    if apport.packaging.get_version('automatix') or \
  File "/usr/lib/python2.6/dist-packages/apport/packaging_impl.py", line 71, in get_version
    pkg = self._apt_pkg(package)
  File "/usr/lib/python2.6/dist-packages/apport/packaging_impl.py", line 66, in _apt_pkg
    raise ValueError, 'package does not exist'
ValueError: package does not exist
Traceback (most recent call last):
  File "/usr/share/apport/apport-gtk", line 254, in <module>
    app.run_argv()
  File "/usr/lib/python2.6/dist-packages/apport/ui.py", line 553, in run_argv
    return self.run_report_bug()
  File "/usr/lib/python2.6/dist-packages/apport/ui.py", line 407, in run_report_bug
    response = self.ui_present_report_details(False)
TypeError: ui_present_report_details() takes exactly 1 argument (2 given)
```I tried fixing the broken packages using the terminal first:

```
$sudo apt-get -f install
[sudo] password for betty: 
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
```And, when I tried to fix the broken packages using Synaptic Fix Broken Packages, I get the following error message:

```

W: Duplicate sources.list entry http://security.ubuntu.com/ubuntu/ lucid-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_lucid-security_main_binary-i386_Packages)
W: Duplicate sources.list entry http://security.ubuntu.com/ubuntu/ lucid-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_lucid-security_restricted_binary-i386_Packages)
W: Duplicate sources.list entry http://security.ubuntu.com/ubuntu/ lucid-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_lucid-security_universe_binary-i386_Packages)
W: Duplicate sources.list entry http://security.ubuntu.com/ubuntu/ lucid-security/multiverse Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_lucid-security_multiverse_binary-i386_Packages)
```At the same time, 

```

$cat /etc/issue
Ubuntu 10.04.1 LTS \n \l
```so I guess it worked to some extent.

I am not sure what to try next, and I am concerned that if I try to reboot I won't be able to access Linux at all.  While I am now fairly confident about my ability to reinstall from 7.04 via WUBI and upgrade it again, I'd much prefer to fix the current install.  I would greatly appreciate any help you wise folks can give me.

I imagine there are log files you might like to see beyond what I've posted above.  I'll be more than happy to provide them - sadly, first you will have to tell me how.

Many thanks.  

WMW

---

### Post by Paddy Landau on 2010-08-05
I'm sorry to say that Wubi is not the best system to use long-term. I have seen many posts from people who have had major problems upgrading Wubi.

Wubi's idea is great, but it's simply not suitable for long-term. It's really suitable only for testing to find out whether Ubuntu is for you.

You said that you can't boot from USB or CD, so that narrows your choice greatly; you probably have no choice but to stick with Wubi.

As you have backups =D> I would suggest that you uninstall Wubi completely; [defrag]("http://www.auslogics.com/en/software/disk-defrag/") your Windows drive; then reinstall Wubi 10.04 and restore your backups. In future, I would repeat that exercise whenever you wish to upgrade to a new version (so, you may want to stick with LTS, i.e. long-term systems, which are upgraded only every two years or so).

* EDIT * And keep your backups up-to-date. Wubi sometimes fails unexpectedly.

---

### Post by whitemagicwoman on 2010-08-05
Thanks, Paddy.  The trouble is that I was unable to install WUBI 10.04.  I got an "invalid login" message during boot (without being prompted to log in) and the only fix I could find for it applied only to the 7.04 release.  That was why I used a previous version in the first place.  So, installing WUBI 10.04 is not going to work for me unless you know something I don't (which would be lovely, I hope you do).  Though I suppose if that seems like the only option I could start a new thread on the original issue.

The other thing that my partner suggested might be a possibility is doing a NIC installation while running Ubuntu Server on another computer.  I've enjoyed Ubuntu enough to commit to it permanently at least on one machine, so I'd be willing to try that - I just worry that it would be even more "pulling myself up by my bootstraps without really knowing what the heck I'm doing" than what I've done in the past week.

---

### Post by Paddy Landau on 2010-08-06
> **whitemagicwoman said:**
> The trouble is that I was unable to install WUBI 10.04.  I got an "invalid login" message during boot...
If you uninstall Wubi, reboot, install Wubi 10.04, and you still get that error, then start a new thread. Some knowledgeable Wubi types probably will have the answer for you.

By the way, when you download Wubi, do be sure to check the MD5 sum to ensure that the download was not corrupt.

> **whitemagicwoman said:**
> ... might be a possibility is doing a NIC installation
I guess that means an installation over a network. If that works for you, go for it. A native Ubuntu installation will be more stable.

---

### Post by whitemagicwoman on 2010-08-09
All right.  I uninstalled WUBI, tried reinstalling 10.04.  Still no go.  But I was able to successfully reinstall Ubuntu 8.04 using the WUBI.  Given your comments on the bugginess of upgrading it, I will not try to upgrade it for now.

I have now read about LVPM and that seems like it could be a good way to get out of my WUBI woes.  I will start a new thread on that.

Thanks again for your help Paddy!

---

### Post by Paddy Landau on 2010-08-09
> **whitemagicwoman said:**
> I have now read about LVPM and that seems like it could be a good way to get out of my WUBI woes.
LVPM is new to me. I see that "[LVPM currently does not work with installs generated by Wubi 10.04]("http://lubi.sourceforge.net/lvpm.html")".

Please post the URL of your new thread here so that I can learn from it.

---

### Post by Jazzy_Jeff on 2010-08-09
If you really want to use Ubuntu I would recommend buying a new CD or DVD burner. You can get a DVD burner on newegg.com for less than 25 dollars. This would save you a lot of hassels. That is my advice.

---

### Post by whitemagicwoman on 2010-08-09
All right kids.  To make a long story short, the 8.04 WUBI was working fine, and then, much to my surprise, my CD drive came back from the grave, for one last hurrah I guess!

I didn't wait for it to change its mind but immediately burned a new live CD of 10.04.  It took three tries but I persevered, and now I actually have Ubuntu 10.04 installed dual boot and backed up.  Yippee!  I am very pleased.

Thanks to everyone who commented for your help, though really it seems to be divine intervention that pulled this one off.

---

### Post by Jazzy_Jeff on 2010-08-09
Glad to hear it. Let us know if you have any problems. We are more than happy to help.

---

### Post by Paddy Landau on 2010-08-10
> **whitemagicwoman said:**
> ... I actually have Ubuntu 10.04 installed dual boot and backed up.
Brilliant! ;)

Please would you mark the thread as Solved.

---

### Post by whitemagicwoman on 2010-08-11
Thanks, Paddy and Jeff!  I so much appreciate your help and am enjoying getting back into the Unix world.

---

