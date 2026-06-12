---
title: "apt-get vs. Update Manager"
date: 2009-09-03
forum: New to Ubuntu
---

### Post by mejohnsn on 2009-09-03
What **is** the difference between these two? I thought apt-get was the command line version of Update Manager, so I opened a terminal window and executed "sudo apt-get update" followed by "sudo apt-get upgrade" just like the man page said to do.

But after successfully completing that, then restarting the system like the final message from apt-get said to do, I see the update notification offering 16 more updates.

What gives? Why are there still updates to do even after successful completeion of "apt-get upgrade"? Or are security updates not covered by apt-get?

---

### Post by nhasian on 2009-09-03
apt-get update does update exactly like update-manager.  the only difference is you have distribution updates, then you would need to run:

```
sudo apt-get dist-upgrade
```

---

### Post by dearingj on 2009-09-03
Apt-get does use the same backend as Update Manager, so they both should install the same updates. The difference is that apt-get can also be used to install or remove packages.

There are two explanations that I can think of for this discrepancy:
1) Not all updates were installed successfully when you used apt-get, in which case they would not be successfully installed through Update Manager either (are they still listed? Have you tried to install them again?)
2) Some updates were released while your computer rebooted

---

### Post by jimingkui on 2009-09-03
nhasian,I'm really confused with them before your post,thanks!

---

### Post by j7%&lt;RmUg on 2009-09-03
In update manager, do the updates that appeared after reboot have a tick in the box next to them, if not they are PROPOSED updates and you should be able to tick them when they become available, just go to System > Administration > Software Sources and check to see if "install proposed updates is ticked, if it is untick it and it should fix your problem.

---

### Post by mejohnsn on 2009-09-03
> **nhasian said:**
> apt-get update does update exactly like update-manager.  the only difference is you have distribution updates, then you would need to run:

```
sudo apt-get dist-upgrade
```

I assume you mean, "the only difference is if you have...".

So I looked again at the updates offered by Update Manager. One of the 16 is a "security update" to "dnsutils", version 1:9.4.2.dfsg.P2-2ubuntu0.2.

Does this sound like a distribution update to you? I really can't tell from the name alone: this is an "Absolute Beginner Talk" forum, you know;)

BTW: even as a beginner, I have already spotted one thing Update Manager does quite differently from apt-get: it lists the proposed updates/upgrades before actually applying them. I see no way to do this with 'apt-get', "sudo apt-get upgrade" lists them one by one as it applies them.

So I do have to ask what you really mean when you say, "apt-get update does update exactly like update-manager".

Finally, the reason I did not go ahead and let Update Manager apply all the security updates is that not so long ago, I found my system stuck in this loop of 1) apt-get insists on upgrading/updating, then 2) Update Manager insists I need an update but then 1') apt-get insists I need an upgrade/update again, then 2') Update Manager insists I need an update...

But I have to admit that when I saw all this, I may have confused "apt-get update" with "apt-get upgrade". I started all this with Ubuntu 8.04.1, and now Grub says I have 8.04.3.

---

### Post by mejohnsn on 2009-09-03
> **nisshh said:**
> In update manager, do the updates that appeared after reboot have a tick in the box next to them, if not they are PROPOSED updates and you should be able to tick them when they become available, just go to System > Administration > Software Sources and check to see if "install proposed updates is ticked, if it is untick it and it should fix your problem.

They all have a tick in the box. They are all described as "important security updates", to things like 'dnsutils' and 'linux-generic'.

My main question is why these "security updates" weren't picked up and applied by "sudo apt-get update" followed by "sudo apt-get upgrade". The man page for apt-get says the latter should install the latest version of ALL packages on my system. So why wasn't the latest security update for dnsutils included?

---

### Post by dannyboy79 on 2009-09-03
> **mejohnsn said:**
> 

BTW: even as a beginner, I have already spotted one thing Update Manager does quite differently from apt-get: it lists the proposed updates/upgrades before actually applying them. I see no way to do this with 'apt-get', "sudo apt-get upgrade" lists them one by one as it applies them.

So I do have to ask what you really mean when you say, "apt-get update does update exactly like update-manager".



apt-get along with the -s option allows you to see the proposed upgrades. it stand for simulation mode. so if you run from the terminal sudo apt-get -s upgrade. (note, you always want to run sudo apt-get update always first) it will list all the proposed upgrades but not actually upgrade anything. update merely downloads all the packages into cache and ensures that your package list is up to date to with the server where as upgrade will actually apply any changes to packages when a new version is available. not to confuse you even more but there is also aptitude besides apt-get. i believe update-manager merely uses apt-get or aptitude in a gui just like synaptic (i think)

---

### Post by slakkie on 2009-09-03
Don't use apt-get, use aptitude instead.

You can find out which packages will be upgraded by running:

aptitude -s safe-upgrade

the -s is simulate, if you are happy with the proposed changes, you can remove the -s or replace it -y. man aptitude for more information about all the different switches.

---

### Post by mcduck on 2009-09-03
The Update Manager is just a front end to apt-get, so apart from the obvious differences in the user interface they are, in the end, one and the same program. Everything Update Manager does, it does by calling apt-get to do the actual job.

**apt-get update** updates information about available and installed package versions. This is the same as using the "check" button in Update Manager or in Synaptic Package Manager

**apt-get upgrade** upgrades installed packages to new versions from repositories, and can also add new packages if required to solve the dependencies. This is also how the *Update Manager* works.

**apt-get dist-upgrade** is the same as above, but is in addition also able to remove installed packages, if required to solve the dependencies for the upgrade. Upgrading your packages through *Synaptic Package Manager* behaves this way.

apt-get will only list the proposed updates before applying them if t needs to add additional packages or remove something. If the upgrade simply replaces each package with a new version it won't show the changes, since you ran the command to upgrade it can safely assume that upgrading your packages is what you want to do.. ;)

What comes to original problem, it's hard to say with this little information, but perhaps the new updates were loaded into repositories while you were rebooting the system? Or perhaps you didn't update package information first, so the rest of the upgrades were available all the time, it's just that your computer didn't know about them until you rebooted and the Update Manager reloaded the package information automatically?

Also remember that in Jaunty the Update Manager will, by default, only prompt you for non-security updates max once per every week. It it's been less than a week from last update it will not show such updates to you even if it already knows about them. However using the apt-get from command line will of course handle everything immediately.

---

### Post by mejohnsn on 2009-09-03
> **dearingj said:**
> Apt-get does use the same backend as Update Manager, so they both should install the same updates. The difference is that apt-get can also be used to install or remove packages.

There are two explanations that I can think of for this discrepancy:
1) Not all updates were installed successfully when you used apt-get, in which case they would not be successfully installed through Update Manager either (are they still listed? Have you tried to install them again?)

2) Some updates were released while your computer rebooted

#2 seems really unlikely, so I will focus on #1. I wasn't keeping a list, since so many scrolled by while running apt-get upgrade. But I can say I saw no error messages during the upgrade. It looked like it all completed successfully.

Ooh! I just made an interesting discovery, one which may help explain what is going on: when I run "sudo apt-get -s -u upgrade", I get the surprising list

```


The following packages have been kept back:
  bind9-host dnsutils libbind9-30 libisccc30 libisccfg30 linux-generic
  linux-headers-generic linux-image-generic linux-restricted-modules-generic

```

Now I recognize 'dnsutils' and 'linux-generic' as being on the same list of 16 "security updates" offered by the Update Manager. But the list is still not exactly the same: UM also offers libdns35 and libisc35, not in the above list.

Yet they also show up in " sudo apt-get -u -s dist-upgrade", so that is what I am going to try now (removing the '-s').

---

### Post by mejohnsn on 2009-09-03
> **mejohnsn said:**
> Yet they also show up in " sudo apt-get -u -s dist-upgrade", so that is what I am going to try now (removing the '-s').

Sure enough, that has solved the problem. After running "sudo apt-get -u dist-upgrade" (and rebooting), Nautilus no longer displays a notification saying I need updates.

---

### Post by mejohnsn on 2009-09-03
> **mejohnsn said:**
> 
But I have to admit that when I saw all this, I may have confused "apt-get update" with "apt-get upgrade". I started all this with Ubuntu 8.04.1, and now Grub says I have 8.04.3.

Just in case someone is relying on the accuracy of what I wrote, I have to correct myself: it wasn't Grub that says this. I forget where I saw it in the process of starting up Ubuntu, but I did see it.

And I think I was confusing 'update' with 'upgrade' earlier. Strange that the history file does not show it.

So the moral of the story is: don't confuse "apt-get update" with "apt-get upgrade"! Rely on the man page description of these options, NOT on the names 'update' and 'upgrade' themselves. The names are misleading, since 'update' only updates the list of "package index files".

---

### Post by mejohnsn on 2009-09-03
As you can see from the timestamp on post #10, I had already figured much of this out, but I still have to say: yours is by far the best reply. Thank you.

---

### Post by dannyboy79 on 2009-09-03
> **mejohnsn said:**
> 

BTW: even as a beginner, I have already spotted one thing Update Manager does quite differently from apt-get: it lists the proposed updates/upgrades before actually applying them. I see no way to do this with 'apt-get', "sudo apt-get upgrade" lists them one by one as it applies them.

So I do have to ask what you really mean when you say, "apt-get update does update exactly like update-manager".



apt-get along with the -s option allows you to see the proposed upgrades. it stand for simulation mode. so if you run from the terminal sudo apt-get -s upgrade. (note, you always want to run sudo apt-get update always first) it will list all the proposed upgrades but not actually upgrade anything. update merely downloads all the packages into cache and ensures that your package list is up to date to with the server where as upgrade will actually apply any changes to packages when a new version is available. not to confuse you even more but there is also aptitude besides apt-get. i believe update-manager merely uses apt-get or aptitude in a gui just like synaptic (i think)

---

### Post by dannyboy79 on 2009-09-03
oops, double post.

---

