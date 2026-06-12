---
title: "Cant Install Ubuntu Whatsoever, Any Advice?"
date: 2009-01-25
forum: New to Ubuntu
---

### Post by wildfire95 on 2009-01-25
Ill sum up whats happened to me in a few bullet-points:```


Cant use "Shrink" volume in vista, i get teh "not enough memory" error, i have 1GB ram.

The GPARTED program on the LiveCD, it says i need to run chkdsk /f ?? And it wont create parititions.

I tried creating partitions in 2 3rdParty software... both gave me blue screen errors.

Its not a Defrag problem, my PC is cleaned every week.
```

Im wondering whether theres a way to delete all the custom files in vista APART from my Accounts etc. It would probably work then, since it would be a basically factory restored OS. TuneUpUtilites and Vista said my RAM and HDD had no errors. 

HELP! :(

---

### Post by xikarrousx on 2009-01-25
three things... have you tried using your windows recovery cd? if you didnt, give that a shot. however, do it before you have ubuntu on your hard drive... i made the mistake of inserting the recovery disk on my ubuntu machine and it automatically reformatted!

is your ubuntu cd from a downloaded .iso file, or is it an official disk? well, either way, get another cd and rip the .iso slower (like x2) and give it a shot. i have even had problems with official ubuntu disks, so make sure you try a new disk.

try downloading the gparted live cd. it is totally separate from ubuntu, and it is a convenient disk to keep lying around. 

[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

if none of those options work, then bring the issue back to the table :D

---

### Post by diablo75 on 2009-01-25
This may sound kind of hocus-pocus but:

Open up Vista, right click on your C: drive in My Computer>Properties.  Click on the Tools tab>Check for errors.  Tell it to look for and automatically fix errors.  When you click okay, it'll say it can't do a scan just yet because the drive is in use, so it wants to set up a scan to take place upon next reboot.  Do that.

Reboot, let it scan, login in, RESTART, login one more time, then restart with the Ubuntu live CD and try again.  It should work.  Those NTFS volumes can be a little picky if there are errors.

---

### Post by wildfire95 on 2009-01-25
> **diablo75 said:**
> This may sound kind of hocus-pocus but:

Open up Vista, right click on your C: drive in My Computer>Properties.  Click on the Tools tab>Check for errors.  Tell it to look for and automatically fix errors.  When you click okay, it'll say it can't do a scan just yet because the drive is in use, so it wants to set up a scan to take place upon next reboot.  Do that.

Reboot, let it scan, login in, RESTART, login one more time, then restart with the Ubuntu live CD and try again.  It should work.  Those NTFS volumes can be a little picky if there are errors.

I tried that, and i got no errors, but the same Ubuntu response :S

---

### Post by Tomatz on 2009-01-25
Try wubi ;)

[http://wubi-installer.org/](http://wubi-installer.org/)

---

### Post by wildfire95 on 2009-01-25
Wubi cant create the partitions can it? ;P

Because i checked it out before, and i would have to install it to my Vista drive =S if it cant create the partitions ... what it will overwrite vista correcT? ^.^

---

### Post by DeadRobot on 2009-01-25
I think Wubi allows you to install without partitions. ;)

And Wubi wont overwrite Vista.

---

### Post by boof1988 on 2009-01-25
[EDIT:]
+1 on Wubi... I haven't used it (no Windoze here), but others seem to be happy with it.
[/EDIT]

If you are not too concerned about the data on the Windows partition, then another option is the following:
[LIST=1]
[*]Download and burn a GPartEd LiveCD
[*]Use the GParted LiveCD to resize your Windows partition
[*]Boot up the Ubuntu LiveCD and proceed (hopefully) as planned
[/LIST]

I have noticed that the GPartEd LiveCD can resize partitions when other methods fail... But... I have also gotten frustrated enough to relabel the disk and start from scratch on a whim (I'm sometimes reckless).  So a GPartEd LiveCD may do the trick but it has great power.

---

### Post by wildfire95 on 2009-01-25
> **DeadRobot said:**
> I think Wubi allows you to install without partitions. ;)

And Wubi wont overwrite Vista.

Ah brilliant!
*Starts Install*

Ill tell you how it goes yea? ;P

---

### Post by desilva on 2009-01-25
Hi, Wubi creates a virtual partition as far as I know, it also allows you to dual boot! :) hope this helps

---

### Post by wildfire95 on 2009-01-25
Woo! 
It worked, im now running a Dual-Boot.. my only issue now is:
How do i compile program source code? 
:S

---

### Post by Tomatz on 2009-01-25
> **wildfire95 said:**
> Woo! 
It worked, I'm now running a Dual-Boot.. my only issue now is:
How do i compile program source code? 
:S

Usually:

```
cd /to/source/directory
```

```
./configure
```

```
make
```

```
sudo make install
```

**BUT**

Everything you will probably need will be in the repos. Either go to ***applications, add/remove*** or for more advanced package management go to ***system, administration, synaptic package manager***

1000's of apps are ready to install in a few clicks ;)

---

### Post by wildfire95 on 2009-01-25
> **Tomatz said:**
> Usually:

```
cd /to/source/directory
```

```
./configure
```

```
make
```

```
sudo make install
```

**BUT**

Everything you will probably need will be in the repos. Either go to ***applications, add/remove*** or for more advanced package management go to ***system, administration, synaptic package manager***

1000's of apps are ready to install in a few clicks ;)

Thanks, im starting to get to grips with this amazing OS finally :)

Any reccomended applications which ill need must likely?

---

### Post by diablo75 on 2009-01-25
> **wildfire95 said:**
> Any reccomended applications which ill need must likely?

See my signature.

---

### Post by oldos2er on 2009-01-25
"How do i compile program source code?"

 You first need to install the package build-essential. Open up a terminal and enter

```
sudo apt-get update && sudo apt-get install build-essential
```

 More info here: [https://help.ubuntu.com/community/CompilingSoftware](https://help.ubuntu.com/community/CompilingSoftware) and [https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

 There are ~20,000 packages available from the repositories; check there first.

---

