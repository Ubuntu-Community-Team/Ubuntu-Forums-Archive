---
title: "Uninstall oops"
date: 2009-08-19
forum: New to Ubuntu
---

### Post by jrlii on 2009-08-19
As a preamble, let me say I've been using AVG to make sure I don't pass on virus infected e-mails to my friends still living in the dark ages of Windows.

I was trying to upgrade my version of AVG the other day and, rather than uninstalling the old version and then installing the mew, I tried upgrading it.

The upgrade ran 'till it came to a file which was "in use" So I foolishly deleted it, assuming that would solve the problem.

I tried again, and the same problem.

I deleted all of the old installation I could find, and it still didn't go, and now I can't run a normal uninstall, 'cause most of it is gone.

So, how do you manually uninstall something like this?

As I said, I looked at the install script and deleted the files and the directories which weren't shared.

However I still can't get the new version to install - it fails at the same place as initially, and I don't know how to get the icon out of the accessories menu. If I could just kill off the menu entry, I'd probably just try something else. . .

Thanks in advance.

---

### Post by alexlafreniere on 2009-08-19
Have you tried looking in Synaptic or Add/Remove? Did you compile it from source? If you installed it from a .deb try this:

```
sudo apt-get remove <your-program>
```

---

### Post by credobyte on 2009-08-19
Try ( one of them ):
```
sudo dpkg -r <package>
sudo apt-get remove <package>

```

---

### Post by jrlii on 2009-08-19
I've tried both synaptic and apt-get, but they fail 'cause they try to remove files &c. I've manually removed already.

Since AVG isn't in the repositories, I installed it with dpkg initially but I haven't tried to remove it with dpkg.

Hmm. . . The developers could make the remove function of synaptic and apt-get more robust by providing for error warning continue/abort functionality instead of just error abort.

---

### Post by LewRockwell on 2009-08-19
there is a reason for Synaptic...

and why there are thousands of applications one may install utilizing it...

.

---

### Post by LewRockwell on 2009-08-19
> **jrlii said:**
> I've tried both synaptic and apt-get, but they fail 'cause they try to remove files &c. I've manually removed already.

Since AVG isn't in the repositories, I installed it with dpkg initially but I haven't tried to remove it with dpkg.

Hmm. . . The developers could make the remove function of synaptic and apt-get more robust by providing for error warning continue/abort functionality instead of just error abort.

your reference and commentary regarding Synaptic and apt-get is quite misleading and unappropriate since you neglected to utilize them for your selection of program and application

.

---

### Post by jrlii on 2009-08-19
Lew, Both apt-get and synaptic TRIED to remove the package and errored out.

If they hadn't tried, if they had flat refused with something like "I didn't install this, I don't know how to remove it, I wouldn't have complained. . . That would have been like the old Quarterdeck CleanSweep program, which could get rid of most anything from Windows without a trace (a big challenge) so long as it monitored the install.

---

