---
title: "Memory Leak?"
date: 2009-05-09
forum: New to Ubuntu
---

### Post by cwmoser on 2009-05-09
Installed Ubuntu 9.04.  Closed all windows and did a free:

```
$ free
             total       used       free     shared    buffers     cached
Mem:       6034804    5177148     857656          0     355652    3980528
-/+ buffers/cache:     840968    5193836
Swap:      4096564          0    4096564
```


I have 6GB RAM, running Jaunty 64-bit.  Why does the "used" show 5GB and I only have 857K free?

Carl

---

### Post by Bölvaður on 2009-05-09
please re do this with ```
free -m
``` as it is easier to read

---

### Post by Didius Falco on 2009-05-09
Run ```
top
``` and it'll show you.

Here is a snapshot of the output from mine:

t```
op - 21:48:24 up 13:38,  2 users,  load average: 0.01, 0.05, 0.08
Tasks: 135 total,   1 running, 134 sleeping,   0 stopped,   0 zombie
Cpu(s):  0.5%us,  0.3%sy,  0.0%ni, 99.2%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   3354744k total,  2756232k used,   598512k free,   272968k buffers
Swap:  1890868k total,        0k used,  1890868k free,   877128k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 3267 paul      20   0  400m 268m  31m S    1  8.2  40:06.66 firefox            
 2689 root      20   0  545m 225m  24m S    0  6.9  18:01.79 Xorg               
17140 paul      20   0  2448 1192  912 R    0  0.0   0:00.14 top                
    1 root      20   0  3084 1884  564 S    0  0.1   0:01.02 init               
    2 root      15  -5     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/0        
    4 root      15  -5     0    0    0 S    0  0.0   0:00.18 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0         
    6 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/1        
    7 root      15  -5     0    0    0 S    0  0.0   0:00.49 ksoftirqd/1        
    8 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/1         
    9 root      15  -5     0    0    0 S    0  0.0   0:00.00 events/0           
   10 root      15  -5     0    0    0 S    0  0.0   0:00.21 events/1           
   11 root      15  -5     0    0    0 S    0  0.0   0:00.00 khelper            
   12 root      RT  -5     0    0    0 S    0  0.0   0:00.00 kstop/0            

```

Regards,

Didius

---

### Post by cwmoser on 2009-05-09
After rebooting, I get this:

```
$ free
             total       used       free     shared    buffers     cached
Mem:       6034804     943184    5091620          0      17680     643024
-/+ buffers/cache:     282480    5752324
Swap:      4096564          0    4096564

```

Now I have 5GB free.

Any ideas?

Carl

---

### Post by Panzor on 2009-05-09
You could try this, though they warn against losing data if you do. I do it after I've used Azureus for more than a few hours as it's written in java and leaks a CRAPTON. A ton.

As a superuser:
```
sync
```
```
echo 3 > /proc/sys/vm/drop_caches
```
[source]("http://www.unix.com/linux/91399-free-linux-memory-dropping-caches.html")

---

### Post by Bölvaður on 2009-05-09
umm.... I wasn't going to say this earlier, but I belief this might not be a memory leak.

Please... do not respect my beliefs.. no one should have to respect some one's stupid beliefs. so please... correct me if Im wrong. People like me that belief in stupid things should be flamed.

---

### Post by hw-tph on 2009-05-09
> **cwmoser said:**
> I have 6GB RAM, running Jaunty 64-bit.  Why does the "used" show 5GB and I only have 857K free?

First of all, you have 857MB free so it adds up pretty good.

Second, your system is working as intended. It is actually using most of the memory available to it. Unused memory is basically wasted memory... If the memory isn't even used for buffering or caching stuff that you might need again (if you reopen an application for example), then what's the use of having a lot of RAM in the first place? If you start a new application memory will be allocated to that instead so don't worry about it.

This is a common misconception for people that come from Windows land. The "-/+ buffers/cache" line will give you a more Windowsish figure of the allocated memory.

---

### Post by cwmoser on 2009-05-09
The top command reveals that the biggest percentage memory hogs are vmware-vmx, firefox, Xorg, and compiz.real

Do any of these have problems?

Carl

---

### Post by hw-tph on 2009-05-09
You have 840MB of RAM in real use in your first post. That's not too bad when running VMWare and Firefox and a flashy desktop like Compiz.

---

### Post by Didius Falco on 2009-05-09
> **Bölvaður said:**
> umm.... I wasn't going to say this earlier, but I belief this might not be a memory leak.

Please... do not respect my beliefs.. no one should have to respect some one's stupid beliefs. so please... correct me if I'm wrong. People like me that belief in stupid things should be flamed.

It's against my beliefs to flame you when you are right. I guess we are forced to live in peace and brotherhood. Bummer! :tongue:

The reason my numbers are that way is because this machine has been up for over 14 hours, with various apps opened and closed numerous times - but it's still just as snappy as when I booted it this morning.

In fact, it's a lot snappier than I am, at this stage. <G>

Like hw-tph, I believe that unused RAM is wasted RAM, and I won't abide any lazy RAM laying about doing nothing. It's bad enough that I have a 500 Meg swap file that's never done a thing but take up space!!

In short: Don't Worry, Be Happy!!


Regards,

Didius

---

### Post by Bölvaður on 2009-05-09
install preload, it will take up some ram and give you snappier system. It doesnt that the name suggest, but in a smarter way than you would first think.

---

### Post by Fujiyama11 on 2009-05-09
i had the same problem with the compiz.real process, but not any more, i fixed the problem and this is how i proceed

NB: this solution solvs the problem for my integrated graphic card (laptop).

first look for the xorg.conf file, open it as root and in the "Device" section modify yours to:


Section "Device"
          Identifier "Configured Video Device"
          Driver "intel"
          Option "AccelMethod" "EXA"
          Option "MigrationHeuristic" "greedy"
  EndSection

save and that's it, problem solved, cpu usage return normal :P.

---

### Post by NightwishFan on 2009-05-09
Trust me you are fine. People coming from Windows Xp do not understand that you need to use as much RAM as possible to gain performance. Xp tends to use disk over RAM, which results in noise and slowdowns, well unless you have a disk dedicated to a page file...

Buffers and cache are ways that Linux uses ram to speed up your system. Like the previous poster, I advise you install preload, it actually makes a noticeable difference. Optionally you can install prelink as well. Both try to make programs come up faster. It is similar to Windows Vista Superfetch only it is unbiased and does not over do it.

---

### Post by cwmoser on 2009-05-09
I'm already running preload

Carl

---

### Post by ukblacknight on 2009-05-10
Whilst were on this topic and it' still new...

I was always under the impression that Swap was to be utilised when free RAM was low, and thus had to 'swap' between the HDD and RAM.  Of course, using the HDD as a memory area is slow.

I've been running conky for a few weeks now, and I can't help but notice that after a day or two, my swap % goes up slightly.  I've got 3GB of Ram, using Jaunty 64bit, but the swap goes up even if my RAM is at say 25%.  I would of expected swap to start being utilised when the RAM usage is at say 95%.

```

tom@blacknight:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          2984       2966         18          0        666        910
-/+ buffers/cache:       1389       1594
Swap:          972         24        948

```

I've no idea why it says Mem (free) is 18mb, or used is 2966mb.

---

### Post by mcduck on 2009-05-10
> **ukblacknight said:**
> Whilst were on this topic and it' still new...

I was always under the impression that Swap was to be utilised when free RAM was low, and thus had to 'swap' between the HDD and RAM.  Of course, using the HDD as a memory area is slow.

I've been running conky for a few weeks now, and I can't help but notice that after a day or two, my swap % goes up slightly.  I've got 3GB of Ram, using Jaunty 64bit, but the swap goes up even if my RAM is at say 25%.  I would of expected swap to start being utilised when the RAM usage is at say 95%.

```

tom@blacknight:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          2984       2966         18          0        666        910
-/+ buffers/cache:       1389       1594
Swap:          972         24        948

```

I've no idea why it says Mem (free) is 18mb, or used is 2966mb.
Little swapping is just a part of normal memory management, and while the system's tendency to swap can be adjusted your memory/swap use seems perfectly normal and I wouldn't worry about.

What comes to your actual memory usage, and the numbers "free -m" gives to you, here's the explanation:

You have total 2984MB of available RAM. (bit less than your total installed RAM, because the kernel is loaded into memory at boot, and always stays there. That part of RAM doesn't count as being available).

Total of 2966MB of RAM is currently used. This is a total sum of memory used by running programs (1389MB), buffered data (666MB) and disk cache (910MB).

As cache simply uses the "extra" RAM you have, the part that's not used for anything else at the moment, that part of memory is still available for programs to use if they need it. Because of this you should read the "+/- buffers/cache"-line if you want to see how much memory your programs are using, and how much is still available for them.

When you read that line, you'll find that your programs are now using 1389MB of RAM, and 1594MB is still available for them if they need it. :)

Like already mentioned in this thread, if the RAM is simply not used for anything it's not making your computer any faster or really helping anything at all. Because of this Linux uses the extra RAM as temporaty storage to keep recently accessed data quickly available and to avoid having to read it from the disk (which would be much slower). In other words, the part of RAM that wouldn't otherwise be used for anything is now being used to make to make your system more responsive and your programs and data to load quicker.

---

### Post by ukblacknight on 2009-05-10
Cheers mcduck, that cleared things up!  What happened to the "thanks" button on the forums?!

---

### Post by mcduck on 2009-05-11
> **ukblacknight said:**
> Cheers mcduck, that cleared things up!  What happened to the "thanks" button on the forums?!

No problem. :)

I've understood that there was some problems with the forum database and the thanks-button (and the solved-button or threads) was removed to get the forum working correctly. I suppose it will appear again if the forum guys get it working..

---

### Post by NightwishFan on 2009-05-11
666mb of buffered RAM?? Geez I have like 22mb... I need to stay with the times and get more than 800mb of ram.

---

### Post by ukblacknight on 2009-05-11
> **NightwishFan said:**
> 666mb of buffered RAM?? Geez I have like 22mb... I need to stay with the times and get more than 800mb of ram.

Think I'd go nuts on 800mb of RAM!  I've seen Firefox hitting 500mb, Banshee 120mb and Gnome-Do at 50mb!

Still, I've been thinking of an upgrade soon, need a new CPU as my AMD4000 single core is creaking along a bit with games :(

---

### Post by emeraldgirl08 on 2009-05-11
> **NightwishFan said:**
> 666mb of buffered RAM?? Geez I have like 22mb... I need to stay with the times and get more than 800mb of ram.

I have 20mb. I think I may need to get me a 1gb stick of DDR. Yeah and a newer comp when I can afford it!

You guys hear about the guy that saved spare coins in a pickle jar and bought a laptop with it??? He's an inspiration at this point for me :P

---

### Post by NightwishFan on 2009-05-13
Ubuntu is quite usable on 800mb of RAM. Well actually I use OpenSUSE currently. The only thing I cannot do with 800mb is run aptoncd with over 1gb of packages and open 'massive' images with GIMP.

---

### Post by practic on 2009-05-16
I'd like to revisit the original question. 

I've noticed some behaviour in Jaunty which I thought was strange, and is being discussed as a possible bug elsewhere (on [Launchpad]("https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/343714").

It is simply this: add the System Monitor applet to your panel and make sure the Memory item is checked on. Now watch it. What happens is that the memory used by programs goes up and down as expected (when you open and close programs), but the memory used as "cache" goes higher and higher until all the memory is filled.  Some have claimed that at this point, if they continue to use the system, it slows down quite a bit.

I'm currently keeping a terminal window open with "sudo su" and issuing this command every half hour or so to clear the cache memory:

echo 1 > /proc/sys/vm/drop_caches

Is this the normal behaviour, that the cache memory should climb until it fills all available RAM?  I don't think I noticed it that way on Ubuntu 8.10.

It seems to me like something in the system is not doing proper house-cleaning.

In the bug report on Launchpad, it particularly dealt with Kubuntu, and although I am running Ubuntu, I use Kontact and some other KDE apps quite frequently. But I don't know if it is related to KDE or not.

Now, does everyone see this behaviour also? Or perhaps it depends on certain programs being installed and running? I'd like to get some feedback from others as to what they see happening on their systems.

---

### Post by cwmoser on 2009-05-16
When I try that I get Permission denied:

```
sudo echo 1 > /proc/sys/vm/drop_caches
bash: /proc/sys/vm/drop_caches: Permission denied

```

Carl

---

### Post by NightwishFan on 2009-05-18
Kubuntu and other KDE 4.2 distros seem to use a lot of memory. Ubuntu even on 64-bit is fairly slim, though I believe it would not make much difference. However I do believe cache should always be full. Though it is technically 'used' it is really free should you need to use it.

---

