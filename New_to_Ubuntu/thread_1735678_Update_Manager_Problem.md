---
title: "Update Manager Problem"
date: 2011-04-21
forum: New to Ubuntu
---

### Post by ProntoAnthony on 2011-04-21
When running Update Manager I get an initial response that says,

Not all updates can be installed

Run a partial upgrade, to install as many updates as possible.

This can be caused by:
* A previous upgrade which didn't complete
* Problems with some of the installed software
* Unofficial software packages not provided by Ubuntu
* Normal changes of a pre-release version of Ubuntu

I'm presented with 2 buttons:
Partial Upgrade and Close.

Something is amiss. I have encountered this response in Update Manager for 2 months.When I press the Partial Upgrade button the updates are not  installed. 

I click Partial Upgrade and a new window pops up:

Running partial upgrade

> Preparing to upgrade

Getting new packages
Installing upgrades
Cleaning up

The real problem is that it spends a lot of time accessing the hard drive, making noise, acting like it is chewing up the disk.All the while the window has 'Preparing to upgrade" highlighted. I was curious about how long it is taking, so I downloaded the stopwatch application and ran it while the disk was being accessed. It hit on the disk for over 20 minutes. 20 minutes!!!


So I start Update Manager again and the same 9 packages still have not been installed. Just to be certain I'm writing this as Update Manager is running a second time. Hopefully it won't take another 20 minutes.

Unfortunately it did take another 20 minutes.

What is interesting to me is that I have a desktop and a laptop. The problem exists only on my desktop system. Both computers are running  Ubuntu 10.10 - the Maverick Meerkat. 

Any clues as to how I can fix my desktop?

Thanks,

-Anthony

---

### Post by vuetrip on 2011-04-21
click Applications -> Accecories -> Terminal

Type sudo apt-get update -f

once it's done it's thing type:

sudo apt-get upgrade -f

run the upgrade again and you should see it's sorted :D

---

### Post by ProntoAnthony on 2011-04-21
No, that wasn't it.  I ran the command:

sudo apt-get update -f

Twice.

Then I once again clicked on Update Manager and it is running, probably for another 20 minutes, without any way to stop it.

-Anthony

---

### Post by plucky on 2011-04-22
> **ProntoAnthony said:**
> No, that wasn't it.  I ran the command:

sudo apt-get update -f

Twice.

Then I once again clicked on Update Manager and it is running, probably for another 20 minutes, without any way to stop it.

-Anthony

Try ```

sudo apt-get dist-upgrade
```

Good Luck

---

### Post by Raan03 on 2011-04-22
most likely the "sudo apt-get dist-upgrade" will work then. If not, would you be so kind to supply us the output files

```

sudo apt-get update >> update.txt
sudo apt-get upgrade >> upgrade.txt

```
update.txt & upgrade.txt are in the directory where your CLI was working in (default it's in your home directory).

** EDIT **
By the way, notice that you don't have to type "sudo apt-get update -f" twice, but you type "sudo apt-get up**date** -f" and afterwards "sudo apt-get up**grade** -f"

---

### Post by ProntoAnthony on 2011-04-22
Success!

The command 'sudo apt-get dist-upgrade' fixed my problem.

Thank you so much!!!

-Anthony

---

