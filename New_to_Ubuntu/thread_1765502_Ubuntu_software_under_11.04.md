---
title: "Ubuntu software under 11.04"
date: 2011-05-23
forum: New to Ubuntu
---

### Post by captainiom on 2011-05-23
I have upgraded to 11.04 in the last few days but can no longer access Ubuntu software. The 11.04 upgrade went perfectly with no errors and everything else so far seems to be OK. However, when software is selected the window opens with the categories showing but as soon as you either select a main category, eg system, or enter a search criterion a rotating icon of a spoked wheel appears signifying processing of the request but it just keeps on rotating and nothing happens. I have restarted the application, rebooted the machine etc but to no avail. The bottom of the window shows 35888 items available - and has done for the last 25 minutes!
Any suggestions please?

---

### Post by powerpleb on 2011-05-23
Try this in the terminal:
```
sudo apt-get purge software-center
```
Then...
```
sudo apt-get install software-center ubuntu-desktop
```

---

### Post by philinux on 2011-05-23
Post back any errors from this.

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by captainiom on 2011-05-23
> **philinux said:**
> Post back any errors from this.

```
sudo apt-get update && sudo apt-get upgrade
```


Tried both suggestions with errors as follows (first command OK I think)
.....
.....
Ign [http://im.archive.ubuntu.com](http://im.archive.ubuntu.com) natty-updates/universe Translation-en_US
Ign [http://im.archive.ubuntu.com](http://im.archive.ubuntu.com) natty-updates/universe Translation-en
Fetched 327 kB in 2s (135 kB/s)
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/im.archive.ubuntu.com_ubuntu_dists_natty_main_i18n_Translation-en
E: The package lists or status file could not be parsed or opened.


Confirm restart of application still same with rotating icon.
jsm

---

### Post by captainiom on 2011-05-23
Tried to start update manager now to see if I had missed any mandatory updates - a lot worse ):

It crashed saying to report problem as a bug

jsm

---

### Post by captainiom on 2011-05-23
I suspect that the next suggestion will be to reconfigure dpkg and clean apt-get so I have done the following:

sudo dpkg --configure -a
sudo apt-get clean

(Both fine no errors)

sudo apt-get update
crashed as follows:
Ign [http://im.archive.ubuntu.com](http://im.archive.ubuntu.com) natty-updates/universe Translation-en_US
Ign [http://im.archive.ubuntu.com](http://im.archive.ubuntu.com) natty-updates/universe Translation-en
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/im.archive.ubuntu.com_ubuntu_dists_natty_main_i18n_Translation-en
E: The package lists or status file could not be parsed or opened.

So cleaning doesnt seem to work.
jsm

---

### Post by captainiom on 2011-05-24
Is this repairable please?
jsm

---

### Post by wildmanne39 on 2011-05-24
> **captainiom said:**
> Is this repairable please?
jsm

That file that is showing errors a lot of people have had the same type errors and they deleted that file and then it worked.

---

### Post by captainiom on 2011-05-24
> **wildmanne39 said:**
> That file that is showing errors a lot of people have had the same type errors and they deleted that file and then it worked.
 
 
Tried that - and repeated it for half a dozen similar files but gave up as each time apt-get update failed with yet another file that could not be parsed.
 
Does this mean a reinstall of 11.04 and if so how do I go about it??
 
jsm

---

### Post by jre6 on 2011-05-24
Try this and please report the results (**[COLOR="Red"]this may have dangerous consequences, do at your own risk, and even if you do run these commands, do not blame me -- I have warned you![/COLOR]. **Since the situation looks a little hopeless, I have suggested it.):

[COLOR="Black"]```
sudo rm -r /var/lib/apt/lists
sudo apt-get update
```[/COLOR]

---

### Post by captainiom on 2011-05-24
> **jre6 said:**
> Try this and please report the results (**[COLOR=Red]this may have dangerous consequences, do at your own risk, and even if you do run these commands, do not blame me -- I have warned you![/COLOR]. **Since the situation looks a little hopeless, I have suggested it.):

[COLOR=Black]```
sudo rm -r /var/lib/apt/lists
sudo apt-get update
```[/COLOR]


Held my breath and proceeded.  Its not a problem I am only running Ubuntu to familiaries myself with this opsys (I am running six other computers with all current Windows and some Unix systems).

Success.  Killing off all the lists allowed both an update and apt-get upgrade.

Most of all when I started software the various items loaded immediately.

Thanks to all who scratched their heads - until the next time I bollix it up  (:

jsm

---

### Post by captainiom on 2011-05-24
> **jre6 said:**
> Try this and please report the results (**[COLOR=red]this may have dangerous consequences, do at your own risk, and even if you do run these commands, do not blame me -- I have warned you![/COLOR]. **Since the situation looks a little hopeless, I have suggested it.):
 
[COLOR=black]```
sudo rm -r /var/lib/apt/lists
```[/COLOR]```

[COLOR=black]sudo apt-get update[/COLOR]
```
 
 
[Reply got lost due Firefox being upgraded so posting again]
 
 
Held my breath and proceeded. Not a problem as this is just one of many computers I am running (all current Windows and some Unix variants) to keep familiarity.
 
Killing off the list was succesful in allowing the update which I followed with apt-get upgrade - no errors.
 
Best of all when I now started Ubuntu software it loaded up the items immediately.
 
Thanks to all who scratched their heads and helped - until the next time I manage to bollix something (:
 
jsm

---

