---
title: "Ubuntu 9.10 refusing to work"
date: 2011-04-01
forum: New to Ubuntu
---

### Post by El-Linux on 2011-04-01
Hi guys,

I'm hoping someone can help me with an issue I've had. I am currently running Ubuntu 9.10 (yeah, I know it's outdated now), literally just surfing the internet. Every program running starts to lag and crash one by one. I finally manage to get everything shut and decide to reboot the machine.

Upon reloading, I am confronted with the following;



```
error: could not read file
failed to book default entries
press any key to continue
```I'll press a button and it just re-displays the above. After rebooting the machine a couple of times, I got lucky and it took me to GRUB but would not load in either normal or recovery mode. It simply failed to load and took me back to GRUB. This however is now gone and I'm stuck with the above once more.

I haven't installed any updates tonight which could affect things and it doesn't bring me anywhere close to the initial log-in screen, etc. Despite using Ubuntu for a year or so now, I haven't delved into the more complicated aspects of it so I turn to you guys for help!

Cheers!

---

### Post by AnnAni1234 on 2011-04-01
there is one thing that you can try 

If you have a CD of ubutnu yout could boot with that and try the repair option and see if that helps

and this goes without saying but the updates are important and you have to keep up with them 


hope this helps

annani1234

---

### Post by El-Linux on 2011-04-01
I'm trying to dig out the disk I installed this old edition from but cannot find it at the moment, I shall endevour to continue though! A repair shouldn't wipe my data though, right?

Yes, updates are important, I just hadn't done any tonight that may have affected the system causing this to happen :)

---

### Post by El-Linux on 2011-04-01
On a side note, I have some progress since first post.

I have reached the GRUB screen and booted it up in Recovery mode. Rather than just failing, it now gives me a massive long list of checks, etc that is does and finishes with the following:

```
/dev/sda1: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY
(i.e. without -a or -p options)
mountall: fsck/[407] terminated with status 4
mountall: filesystem has errors: /


init: mountall main process (399) terminated with status 3
mount of filesystem failed
A maintenance shell will now be started
CONTROL-D will terminate this shell and re-try
root@mlaptop:~# 
```You can type in that last line, much like (probably exactly the same) as in the terminal. It won't do anything until I enter a command. The only command I know is the reboot one so this is a dead end for my own personal knowledge!

Basically, from my non-expert point of view, it seems the filesystem has somehow messed up, won't load/mount and needs fixing somehow. Is this something the repair function on the disk can sort? Will I lose the data on the HDD if I do so?

Thanks again!

Edit: I also took advantage of the GRUB screen and did a memory test, for what it's worth. No errors found.

---

### Post by AnnAni1234 on 2011-04-01
the repair function serves as a backup to restore files and correct errors that occur within the operating system the repair function isn't like the repair function of windows it doesn't touch your data and if all else fails you could use the live cd and backup your data and do a fresh install.

---

### Post by Hedgehog1 on 2011-04-02
You have another repair option (in case you cannot locate the old CD, or the old CD no longer reads properly):

You can use a current Ubuntu LiveCD/LiveUSB (10.04 or 10.10), select 'TRY', and then run the repair commands from there.

Please do not update grub from a LiveCD that is not the same version as your install - however any other repair from the current LiveCD should be fine.

***The Hedge***

:KS

---

### Post by El-Linux on 2011-04-03
Alright, I found the original 9.10 CD and I thought I knew but apparently I don't.. how do you repair?

All checks I've run from GRUB and the LiveCD boot menu say there's no errors on the computer, despite it still not loading.

Thanks to you both for your help.

---

