---
title: "BIG PROBLEM!!! no more wireless connection"
date: 2008-03-29
forum: Networking &amp; Wireless
---

### Post by gangsterhead3 on 2008-03-29
i have recently installed ubuntu and i couldnt go wireless so i installed the boardcom bcm4.3xx thing because i have a bcm4312 wireless card.

when i installed that, i went on wireless internet and installed compiz. it asked me to restart my computer so i did it.

now, theres no more wireless connection in the options in the place where we set up the connection.

i tried restarting 7 times but it still doesnt come back.

ill send u a screenshot

---

### Post by waspbr on 2008-03-29
what did you use to isntall it? what method did you follow? ndiswrapper?

---

### Post by gangsterhead3 on 2008-03-29
i use this
[http://ubuntuforums.org/showthread.php?t=405990](http://ubuntuforums.org/showthread.php?t=405990)

---

### Post by waspbr on 2008-03-29
hmmm

if it already worked then perhaps the ndiswrapper module is already in place, 

go to console and type:

```
sudo modprobe ndiswrapper
```

see if that works

then if yes, reboot, odds are that it won't work anymore, but I know what to do then

if that doesn't work

go to console again and type

```
sudo ndiswrapper -l
```

post the output of that

---

### Post by gangsterhead3 on 2008-03-29
i think it doesnt work because when i typed sudo apt-get install ubuntu-restricted-extras, it told me that it is corrupted and should be removed.

ill post you the thing later cuz im not on my laptop right now

---

### Post by gangsterhead3 on 2008-03-29
sudo ndiswrapper -l
sudo: ndiswrapper: command not found


should i reinstall ndiswrapper?

---

### Post by waspbr on 2008-03-29
hmm, I jjust checked out that installer thing in the link you gave me, apparentlythe installer let&#347; you select from a few instaltion methods, if that command I gave didn't do anything than this means you don't have ndiswrapper at all.

I doubt compiz/ the restricted extras have anything to do with your problem, the thing is that the installer you used did not stick, the changes were gone after reboot. A piece of good news is that your card is already supported in hardy (the newest ubuntu release) which is in beta, but it is pretty stable, I am writing from it.

according to the thread, that method is no longer supported so, yeah, it might backfire...

while you should consider moving to hardy as an option  I am gonna look up a method for installing your card, so hang in there... have a beer in the mean time

---

### Post by waspbr on 2008-03-29
k, I went back and took a look at the method the dude used, in principle it is not bad, you could try running it again and see if that sticks.

alternatively you could use ndiswrapper which should work,  this link points out how to do this.

[http://ubuntuforums.org/showpost.php?p=3491929&postcount=257]("http://ubuntuforums.org/showpost.php?p=3491929&postcount=257")

actually the method should also sort out the whole thing all together, it takes some work but at the end you should be sorted.the drivers should be under tx1000z.

---

### Post by gangsterhead3 on 2008-03-29
ive had ubuntu before on my laptop 7.10

yesterday, i reinstalled because sabayon linux messed up my grun real bad

it worked almost perfect when i had it before


where can i dl hardy?

---

### Post by waspbr on 2008-03-29
kewl, though you should know the drill, if this is a beta version, so in case of the worst case scenario, (which is unlikely) you should have your data safely back up, if this is your main pc you might wanna consider waiting untul the stable version.

now that the dsclaimer has been given , here's the link:
[http://www.ubuntu.com/testing/hardy/beta]("http://www.ubuntu.com/testing/hardy/beta")

Do you have a wired connection maybe? I checked and saw that the package that makes your card work does not come in the cd itself, it is in the ubuntu repository, so you would have to download it from synaptic to make it work.


the package is called  b43-fwcutter, you just need to select it in synaptic , say yes to whatever comes up and it should be done.

---

### Post by gangsterhead3 on 2008-03-29
is there a way to upragde?
like with no cd and stuff just to go from 7.10 to 8.04?

---

### Post by waspbr on 2008-03-29
yep you can upgrade, although a fresh install is , well, fresh.

[https://help.ubuntu.com/community/HardyUpgrades]("https://help.ubuntu.com/community/HardyUpgrades")

---

### Post by gangsterhead3 on 2008-03-29
thanks for helpin me out

---

### Post by gangsterhead3 on 2008-03-29
one last question

when the real hardy will come out, am i going to have to re-download it or its just going to update?

---

### Post by waspbr on 2008-03-29
updating hardy should be enough

---

### Post by gangsterhead3 on 2008-03-29
it still doesnt work


theres only 3 wired connections and 1 point to point

NO WIRELESS!!!!!


ill make a new thread and ill put a screenshot on it

---

