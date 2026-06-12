---
title: "Ubuntu or Xbuntu for a slightly older computer?"
date: 2010-08-19
forum: New to Ubuntu
---

### Post by LinuxFox on 2010-08-19
I have a question about installing Ubuntu.  My mother is running Ubuntu 8.04 on her computer and I've been able to help her for most of the part.  Now she claims it's running slowly, so I was going to try and reinstall Ubuntu for her, and upgrade it to Lucid.

Problem is her computer is slightly older.  It's using a 2.0 GHz processor with 512 MB of RAM.  Since I don't know the requirements, I want to know if installing Ubuntu 10.04 is ok, or should I give Xubuntu a try.

She's use to Ubuntu so I don't know how she'll adjust to Xubuntu.  Any advice please.

---

### Post by ranch hand on 2010-08-19
Xubuntu will not run noticibly better on that box.

I would boot to the live CD for 10.04 and see if it works well on there.  It will be slow as it is working from ram.

The first thing I would do is see why 8.04 is running slow.  Is the drive getting full?

I would try running;
```

sudo apt-get auto remove

```
and;
```

sudo apt-get clean

```
and see if that does not speed it up.

I would also check the specs for that box and see if you could install more ram.  You have enough to run anything really but if you could get 1Gb of ram it would be quite a bit better.

You might also want to check for deals on a larger drive if that one is filling up.  Drive prices are quite reasonable on the 320Gb and under sizes.

All that said I really think that 10.04 would be fine on there.  A clean install would be best as there are a lot of changes under the hood in 10.04 and that way you would get them all.

The biggest one is that 10.04 is built to run on ext4 and does much better on it than on ext3.  I have several drives and tested the 8.04>10.04 upgrade (you can upgrade from one LTS to the next LTS).  The installs that were upgraded did not run as fast as the clean installs with the old files put in from backup.

---

### Post by LinuxFox on 2010-08-19
Thanks, I'll try those apt-gets and see what happens.  If not, then I'll try installing 10.04.  Seeing how there's no difference than Xubunu, then it shouldn't be a problem.

---

### Post by ranch hand on 2010-08-19
I have installed Xubuntu and never found it to be much smaller or faster than Ubuntu.  I am running 8.10 on a box much older than your mothers.  Do not have it up right now but the cpu is less than a gig and has the same ram as hers (I doubled it up to that point which is the max for that MB), not real fast but it runs all right.  Am going to try 10.04 on it.  If that doesn't work well I will use Lubuntu.

The Lubuntu (not an official member of the Ubuntu family yet) version is very good and VERY light.  It is a bit different than the Gnome desktop but not real hard to use.

I do not know how old your mother is but I think she could handle it if she wants more speed.

---

### Post by Nick_Jinn on 2010-08-19
Lubuntu might be faster than either of them. Lubuntu uses less ram, but then Xubuntu RE-loads web pages faster supposedly but uses more ram initially.

---

### Post by -kg- on 2010-08-19
Something that you might want to try, and that will make a "disk clean-up" easier and more automated:

Some time back I came across a little script that will automatically do the disk cleanup with a click or two.  It is called "disk-cleanup-script."  Open your favorite text editor and copy and paste the below into it:

```
#!/bin/bash

sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade
sudo apt-get autoremove

sudo -k
```

Save it to your desktop (or where ever you want to store it) as "Disk-Cleanup-Script.sh".  This Bash Script will automate the process of cleaning up unneeded files, etc.  I have used this successfully quite a few times.  All you have to do is click on it and select "Run" from the Dialog box.

One caveat...

Never take someone's word for code in this or any other forum.  Check out the commands yourself and ***_make_ _sure_*** that the code is safe and correct.  I give you my word that this code is correct and good and I've used it many times ***and*** I copied directly from the text file that I've used, but you don't know me and my word is as good as the words I type.

Always check and make sure yourself!

---

### Post by mike555 on 2010-08-19
You can also uninstall things that aren't used , I got mine done to 88mb at startup.......... let me know if your interested in the list of things I uninstalled.......

---

### Post by ranch hand on 2010-08-19
> **-kg- said:**
> Something that you might want to try, and that will make a "disk clean-up" easier and more automated:

Some time back I came across a little script that will automatically do the disk cleanup with a click or two.  It is called "disk-cleanup-script."  Open your favorite text editor and copy and paste the below into it:

```
#!/bin/bash

sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade
sudo apt-get autoremove

sudo -k
```Save it to your desktop (or where ever you want to store it) as "Disk-Cleanup-Script.sh".  This Bash Script will automate the process of cleaning up unneeded files, etc.  I have used this successfully quite a few times.  All you have to do is click on it and select "Run" from the Dialog box.

One caveat...

Never take someone's word for code in this or any other forum.  Check out the commands yourself and ***_make_ _sure_*** that the code is safe and correct.  I give you my word that this code is correct and good and I've used it many times ***and*** I copied directly from the text file that I've used, but you don't know me and my word is as good as the words I type.

Always check and make sure yourself!
+1 for the warning on code.

Thanks for the script, never even thought about it.

I have several installs, mainly what ever the next version is (right now 10.10 testing) and use a chroot script so that I can update/upgrade from one of them (usually this one that I am on now) as I try to use it as a "production" OS and need other installs to, mainly, test upgrades for lethal content.  Also for other features that may be interesting (Lubuntu and the new Unity UNE desktop right now).

Your script looks real handy and I may incorporate it into my chroot, with some commented out (don't need the cleaning agents all the time).  Could well speed things up a bunch.

Thanks again.

---

### Post by LinuxFox on 2010-08-22
Update, I decided to upgrade my mom's computer by installing Ubuntu 10.04.  I did a fresh install, and she told me it's running a bit better.  If anything, it's running just like 8.04 did.  Thanks for the help.

-kg-, I just tried that script out on my computer, that's really handy.  Thanks for the heads up about commands.

Sorry I replied so late.

---

### Post by dummy910 on 2010-08-22
yes, i'll add to the **Lubuntu** motion here... good stuff, especially on elder, lighter rammed hardware setups.

**[http://lubuntu.net/](http://lubuntu.net/) **

---

### Post by fooman on 2010-08-22
> **dummy910 said:**
> yes, i'll add to the **Lubuntu** motion here... good stuff, especially on elder, lighter rammed hardware setups.

**[http://lubuntu.net/](http://lubuntu.net/) **

+1....i just bought an asus eeepc with a 900mhz celeron, 512mb ram and 4gb solid state drive last week for $40 and installed lubuntu on it.

works fantastic!

---

