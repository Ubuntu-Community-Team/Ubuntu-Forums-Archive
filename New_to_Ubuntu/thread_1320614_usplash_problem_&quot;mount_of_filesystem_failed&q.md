---
title: "usplash problem &quot;mount of filesystem failed&quot;"
date: 2009-11-09
forum: New to Ubuntu
---

### Post by manilaph on 2009-11-09
Hi to all!

I just got this recently when I booted my Ubuntu 9.10....


[B]usplash: setting mode 1152x864 failed
usplash: using mode 1024x768
mount of filesystem failed
A maintenance shell will now be started
CONTROL-D will terminate this shell & retry[/B]

how to i fix this problem. i was using Ubuntu for a week without any problems. i did a recent update and this happened.

Thank you!

---

### Post by skakid177 on 2009-11-09
i just now have a similar problem except it doesnt sya anything about usplash, it just doesnt boot.
 
mount of filesystem failed
a maintenance shell will now be started.
Control-D will terminate this shell and re-try
[EMAIL="root@kubuntu"]root@kubuntu[/EMAIL]:~#
 
its ridiculous, this just happened randomly

---

### Post by rscottj on 2009-11-09
For the record I am new to Ubuntu. Performed a full 9.10 install over XP. Easy install. All worked well for about three days and then I too got the "mount of filesystem failed" message. Tried all options to recover but to no avail. 

I wrote it off to bad luck. Since I didn't have much time/effort invested at that time I opted to just reinstall. All went well again. We'll see if it holds this time.

---

### Post by cslav on 2009-11-09
apt-get remove usplash
this should have no ill effects

---

### Post by manilaph on 2009-11-10
this exact same problem happened to my Kubuntu 9.10 installation.

another "mount of filesystem failed"

is this a bug?

do we need an Ubuntu 9.10.1 version?

i do not mind a quick fix if the problem is acknowledged.

had no problems with earlier Ubuntu, Kubuntu, Xubuntu versions in the past. only the 9.10 version. Is it the Kernel?

---

### Post by scifiville on 2009-11-10
This has happened to me as well. First happened yesterday so I reinstalled 9.10. Now it's happened again and I can't get it to boot at all.

I'm running Ubuntu 9.10 power PC version on a G4 iBook.

---

### Post by manilaph on 2009-11-11
sorry to say that this time around... the previous version of Ubuntu... is much better than the current version..

this is definitely a bug
[http://ubuntuforums.org/archive/index.php/t-1305536.html](http://ubuntuforums.org/archive/index.php/t-1305536.html)

it appears in Kubuntu 9.10 as well.

i've never had so much difficulty with Ubuntu/Kubuntu... only now. Karmic is virtually impossible to use. very unstable. not recommended for newbies at all. it will turn-off linux newbies.

---

### Post by rscottj on 2009-11-13
I'm back. Crashed again...Quick vote. If I go back for an older version which is most stable.

---

### Post by manilaph on 2009-11-16
nobody seems to be helping out with a solution to this problem.

will removing usplash solve the problem?

```
sudo apt-get remove usplash
```

i hope Linuxmint 8 does not inherit this problem

---

### Post by philinux on 2009-11-16
> **manilaph said:**
> Hi to all!

I just got this recently when I booted my Ubuntu 9.10....


[B]usplash: setting mode 1152x864 failed
usplash: using mode 1024x768
mount of filesystem failed
A maintenance shell will now be started
CONTROL-D will terminate this shell & retry[/B]

how to i fix this problem. i was using Ubuntu for a week without any problems. i did a recent update and this happened.

Thank you!

At the command prompt use this.

fsck -v dev/sd??

where ?? is your root file system. Mine is sda1 on drive 1 and sdb1 on my second internal drive.

---

### Post by manilaph on 2009-11-16
so far, my re-installation of Ubuntu 9.10 seems fine. before anything (like updates etc), I removed usplash and re-started my computer. it actually booted-up faster without usplash.

before removing usplash (the first boot-up)... the "restricted drivers available" were being announced but when the usplash was removed, i do not receive the announcements anymore.

as per other threads... some say the problem is usplash and some say it is the nvidia drivers. and so, i removed usplash and will not install any nvidia drivers.

i think the problem may be the usplash-nvidia tandem but i am not an expert.

i will update everyone if my installation lasts a week without errors.

it also seems that i do not receive automatic update notifications. i did a manual update using Update Manager. not sure if the automatic update notification is triggered by usplash.

again, my boot-up is faster and error-free without usplash.

---

### Post by rscottj on 2009-11-19
> **rscottj said:**
> I'm back. Crashed again...Quick vote. If I go back for an older version which is most stable.
I jumped to Linux Mint (Gloria) and so far life is good.

---

### Post by vvh1teb01 on 2009-11-29
Before i post this i should mention i am a complete newb. 

I was having the same problems and ran this command

"fsck -f" then hit "Y" for all the errors it prompted me with.

Now i dont know what i REALLY did here, all i know is that it fix the problem, as of right now.

Use caution because i cant guarantee that this will fix the issue.

---

