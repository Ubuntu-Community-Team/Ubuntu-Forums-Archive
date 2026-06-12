---
title: "dd to wipe out external HD"
date: 2009-01-25
forum: New to Ubuntu
---

### Post by minsf on 2009-01-25
i am running
```
sudo dd if=/dev/zero of=/dev/sdb bs=8M
```
with the goal of wiping out an external HD (so that i can sell it)
how can i monitor the pace of dd? 
that is, how can i tell how many 0 bytes has already been written?
is it ever going to finish, or will i eventually need to break it?

---

### Post by NewJack on 2009-01-25
I have not used dd to wipe a drive before, but I can recommend Dariks Boot and Nuke [http://www.dban.org](http://www.dban.org).  I have used it quite a few times and never had issues with it.  I will give you a progress bar while it works.  I've never had to break it's usage and the timer is very acurate.

Hope that helped.

---

### Post by handydan918 on 2009-01-25
DBAN is actually better than a simple dd...

---

### Post by minsf on 2009-01-26
thanks guys i will check out this tool as soon as the dd is done.
though i would really love to be able to monitor the dd somehow.
it has been running on my 500GB HD (through usb) for the last 9 hours, so i want to know if it is near completion or if it got stuck on something...

---

### Post by minsf on 2009-01-26
SOLVED!
```
sudo kill -USR1 <pid>
```
will make dd spit out statistics, and then resume its job.
in the above, <pid> is the process number- you can get it from
```
ps -e| grep dd
```
i found the solution at the end of the manpage. i missed it the first time i read it...
i will check out dban tomorrow. how long does it take dban to run on 500GB?

---

### Post by mcduck on 2009-01-26
> **minsf said:**
> i am running
```
sudo dd if=/dev/zero of=/dev/sdb bs=8M
```
with the goal of wiping out an external HD (so that i can sell it)
how can i monitor the pace of dd? 
that is, how can i tell how many 0 bytes has already been written?
is it ever going to finish, or will i eventually need to break it?

Better use /dev/urandom to overwrite the disk with random data instead of just zeroing it. You can just leave dd running, it will stop when the drive is full.

..or the true paranoid option, overwrite 7 times with random data:
```
for n in `seq 7`; do dd if=/dev/urandom of=/dev/sdb bs=8b conv=notrunc; done
```

---

### Post by caljohnsmith on 2009-01-26
Instead of using dd, you could use "dcfldd", which is dd with more features, including a "statusinterval" so you can see the progress:
```
sudo dcfldd if=/dev/zero of=/dev/sdb [COLOR="Blue"]statusinterval=10 bs=10M[/COLOR] conv=notrunc
```
So dcfldd will update its progress every 10 X 10 MB = 100 MB in the above example.

---

### Post by minsf on 2009-01-26
thanks guys.
i will check out dcfldd
what is the meanning of not truncating the output file (conv=notrunc)?
anyways, my biggest problem is the speed.
i posted a thread here:
[http://ubuntuforums.org/showthread.php?t=1051080](http://ubuntuforums.org/showthread.php?t=1051080)
it is written about "cp", but i have the same slow rate when running the above dd command. 
hope you can help
thanks a lot :)

---

### Post by caljohnsmith on 2009-01-26
> **minsf said:**
> thanks guys.
i will check out dcfldd
what is the meanning of not truncating the output file (conv=notrunc)?
anyways, my biggest problem is the speed.

Unless your HDD is an exact multiple of the blocksize that you use (in your case you used 8 MB), then dd will not write to the remaining bytes. For instance, if your HDD were say 100 MB and you use an 8 MB blocksize, that means dd will write the first 96 MB (12 X 8 = 96), but it will skip the last 4 MB unless you use "conv=notrunc".

---

### Post by minsf on 2009-01-26
> **caljohnsmith said:**
> Unless your HDD is an exact multiple of the blocksize that you use (in your case you used 8 MB), then dd will not write to the remaining bytes. For instance, if your HDD were say 100 MB and you use an 8 MB blocksize, that means dd will write the first 96 MB (12 X 8 = 96), but it will skip the last 4 MB unless you use "conv=notrunc".
thanks a lot! this was very helpful

---

