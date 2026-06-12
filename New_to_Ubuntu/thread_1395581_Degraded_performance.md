---
title: "Degraded performance"
date: 2010-02-01
forum: New to Ubuntu
---

### Post by mvalviar on 2010-02-01
I recently moved from a 32 bit to a 64 bit ubuntu. I thought the 64 bit would perform better but something is terribly wrong. The performance of my box is significantly sloppy. I think it has something to do with ram. I have only 1gig of it. It's almost always 100% used with my swap at 50%. I never experienced this much memory use with 32bit. ```

mvalviar@mumee:~$ cat /proc/meminfo                                         
MemTotal:        1023256 kB                                                 
MemFree:           60204 kB                                                 
Buffers:            7848 kB                                                 
Cached:            58736 kB                                                 
SwapCached:        83844 kB                                                 
Active:           264020 kB                                                 
Inactive:         322048 kB                                                 
Active(anon):     232596 kB                                                 
Inactive(anon):   290764 kB                                                 
Active(file):      31424 kB                                                 
Inactive(file):    31284 kB                                                 
Unevictable:          16 kB                                                 
Mlocked:              16 kB                                                 
SwapTotal:       1097756 kB                                                 
SwapFree:         514080 kB
Dirty:                32 kB
Writeback:             0 kB
AnonPages:        435928 kB
Mapped:            36964 kB
Slab:              40916 kB
SReclaimable:      12832 kB
SUnreclaim:        28084 kB
PageTables:        34204 kB
NFS_Unstable:          0 kB
Bounce:                0 kB
WritebackTmp:          0 kB
CommitLimit:     1609384 kB
Committed_AS:    2687448 kB
VmallocTotal:   34359738367 kB
VmallocUsed:      106448 kB
VmallocChunk:   34359630331 kB
HugePages_Total:       0
HugePages_Free:        0
HugePages_Rsvd:        0
HugePages_Surp:        0
Hugepagesize:       2048 kB
DirectMap4k:       13888 kB
DirectMap2M:     1034240 kB

```

```

top - 14:46:58 up  7:05,  1 user,  load average: 0.09, 0.45, 1.24
Tasks: 173 total,   4 running, 169 sleeping,   0 stopped,   0 zombie
Cpu(s):  6.8%us,  1.5%sy,  0.0%ni, 91.5%id,  0.0%wa,  0.2%hi,  0.1%si,  0.0%st
Mem:   1023256k total,   958896k used,    64360k free,     4344k buffers
Swap:  1097756k total,   588588k used,   509168k free,    65384k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 2408 mvalviar  20   0  959m 289m  15m S    0 28.9  26:47.41 firefox
 1147 root      20   0  232m  37m 5540 R    6  3.7  14:39.49 Xorg
 6866 mvalviar  20   0  246m  22m  16m S    7  2.3   0:22.68 gnome-system-mo
 2253 mvalviar  20   0  374m  21m 6464 S    0  2.1   0:52.39 gnome-panel
 2415 mvalviar  20   0  716m  16m 8276 S    0  1.6   0:09.35 evolution
 2412 mvalviar  20   0  581m  15m 7388 S    0  1.5   0:09.72 pidgin
 2256 mvalviar  20   0  609m  14m 5292 S    0  1.5   0:33.52 nautilus
 2871 mvalviar  20   0  405m  13m 4120 S    0  1.3   1:08.44 evince
 4211 mvalviar  20   0  553m  12m 4272 S    0  1.3   1:13.63 gimp-2.6
 2300 mvalviar  20   0  460m  12m 7980 S    0  1.2   0:07.64 yakuake
 3493 mvalviar  20   0 1256m  11m 4432 R    2  1.2  10:09.72 audacious2
 3670 mvalviar  20   0  461m  11m 5076 S    0  1.2   0:23.72 transmission
 2248 mvalviar  20   0  352m 9640 5032 S    0  0.9   1:57.52 metacity
 2232 mvalviar  20   0  206m 6860 4144 S    0  0.7   0:06.84 notify-osd
 6661 mvalviar  20   0 71952 5688 1644 S    1  0.6   0:14.25 npviewer.bin
 5257 mvalviar  20   0  278m 5040 4004 S    0  0.5   0:00.68 knotify4
 2276 mvalviar  20   0  192m 4820 3236 S    0  0.5   0:00.43 gnome-power-man
 2274 mvalviar  20   0  282m 4800 3544 S    0  0.5   0:00.88 gnome-volume-co

```

Is it normal for firefox to use that much ram? Is there anything I can do about this?

---

### Post by nhasian on 2010-02-01
> **mvalviar said:**
> Is it normal for firefox to use that much ram? Is there anything I can do about this?

yep i have 6 tabs open in firefox now and have a similar memory footprint for firefox.

```
  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND              
 7634 nhasian    20   0 1359m 314m  37m S    3 15.6 100:28.22 firefox 
```

any chance you could drop another couple gigs of ram into your system?  :)

---

### Post by lotharmat on 2010-02-01
I was always told that unless you have 4 GB of RAM or more; there is no real point having a 64 bit OS.

---

### Post by mvalviar on 2010-02-01
What is the IO Wait? It spikes everytime I do something. Often times taking 100% of the cpu for ages.

---

### Post by jd65pl on 2010-02-01
> **mvalviar said:**
> What is the IO Wait? It spikes everytime I do something. Often times taking 100% of the cpu for ages.

The CPU is waiting for IO operations complete, its is more than likely a symptom of you running out of free ram, it could also be caused by not having enough free space on a disk.

Use the command below to see if a lot of memory is used as cache, this isn't a problem if it is, unused memory is wasted memory. It is just as quick to over write cached memory as it is to write to free blocks.

```
free -m
```

---

### Post by PCA on 2010-02-01
@Iotharmat, Not really. I also believed in that for sometime. I was using Jaunty till a few days back. but now I have upgraded to Karmic 64bit version. I only have 512MB ram and just as much swap and THERE IS some improvement in the speed. The system seems more responsive. Computing intensive tasks like compressing a large file etc. seems to be a bit faster.

The transition wasn't trouble free. I had to reinstall it a couple of times. There was a sound problem which I now have zeroed down onto the softmodem driver sl-modem-daemon. Now everything is fine :p

---

### Post by howefield on 2010-02-01
64 bit will take more memory to run that 32 bit, so it isn't a surprise to see more pressure on your RAM, having said that, I'd expect one gig to cope reasonably well. 

Think I'd put more RAM in, or switch back to 32 bit.

---

### Post by warfacegod on 2010-02-01
> I recently moved from a 32 bit to a 64 bit ubuntu.

How long is "recently"? I've seen a few threads were 64 was sluggish at first and then sort of "came out of it" after a few fays, like a car needing a breaking in period.

---

### Post by jd65pl on 2010-02-01
> **warfacegod said:**
> How long is "recently"? I've seen a few threads were 64 was sluggish at first and then sort of "came out of it" after a few fays, like a car needing a breaking in period.

Something must have changed for users to experience this change, this won't just fix itself of its own accord, is there any trend in what you have seen which could explain this? Can you give examples?

---

### Post by warfacegod on 2010-02-01
The only thing we did was resize some partitions and reduce the swap space. Making swap smaller can't have that much effect on performance.

[http://ubuntuforums.org/showthread.php?t=1385569&highlight=64bit+running+slow&page=5]("http://ubuntuforums.org/showthread.php?t=1385569&highlight=64bit+running+slow&page=5")

---

### Post by PCA on 2010-02-01
I like to add a related thing here. Whenever I install/un-install something significant like drivers or update my system etc. and restart the system,it's extremely sluggish, lotsa disk activity.... but this clears after another restart. After the second restart, Karmic Koala is back to its usual quick self.

I don't consider this a problem, although I would like to know why this is so. I never experienced anything like this with the 32-bit Jaunty.

---

### Post by lisati on 2010-02-01
> **PCA said:**
> I like to add a related thing here. Whenever I install/un-install something significant like drivers or update my system etc. and restart the system,it's extremely sluggish, lotsa disk activity.... but this clears after another restart. After the second restart, Karmic Koala is back to its usual quick self.

I don't consider this a problem, although I would like to know why this is so. I never experienced anything like this with the 32-bit Jaunty.

I haven't used Karmic regularly (some niggles when I tried it, too lazy to investigate and put right, I wend back to 9.04)

Its possible that your partitions are filling up, slowing things down when you've updated;  and that when you restarted, the restart process cleaned up enough of the temporary files used by the updates for you to notice an improvement.

---

### Post by mvalviar on 2010-02-01
```
mvalviar@mumee:~$ free -m
             total       used       free     shared    buffers     cached
Mem:           999        573        426          0         18        155
-/+ buffers/cache:        399        599
Swap:         1072          0       1071

```

I installed it a couple of days ago. I usually use GIMP, Firefox, GVim, audacious, transmission together. I never had a problem using those applications together in 32 bit. I even have compiz on. In 64 bit the music chops as I move from window to window. As I mentioned before doing stuff makes a huge dark blue spike (on the system monitor).

---

### Post by k3lt01 on 2010-02-01
> **PCA said:**
> I like to add a related thing here. Whenever I install/un-install something significant like drivers or update my system etc. and restart the system,it's extremely sluggish, lotsa disk activity.... but this clears after another restart. After the second restart, Karmic Koala is back to its usual quick self.

I don't consider this a problem, although I would like to know why this is so. I never experienced anything like this with the 32-bit Jaunty.That is caused by ureadahead. Whenever you update your system and there are init files in the update ureadahead has to go through the whole process again. I had difficulty with it for a while and then removed it from my system and since then I have never had a problem.

---

### Post by k3lt01 on 2010-02-01
@ mvalviar, if you have the disk space I would advise even on a 64 bit system to make 2gb of SWAP. It helps to take up the slack on the RAM. 

Regarding the cpu usage, I don't know why you would be getting 100% cpu usage unless there are processes running in the background you are not aware of.

---

### Post by NightwishFan on 2010-02-01
Using 64-bit on a machine with less than 4gb of RAM will have improvements in intensive operations such as audio/video conversion. It also is able to map larger files to memory. 64-bit does cause processes to use more RAM.

My machine has only 870mb of usable RAM. My usage is as follows:
```
             total       used       free     shared    buffers     cached
Mem:           870        662        208          0         44        247
-/+ buffers/cache:        369        501
Swap:         2384          0       2384

```

I use vm.swappiness=100 to swap unused pages out to disk. It seems to work well though since I now use Metacity compositing I never seem to need SWAP.

---

### Post by mvalviar on 2010-02-01
@NightwishFan - how do I go about increasing my swap? I have the disk space however I don't know how to repartition without putting my files in jeopardy.

---

### Post by NightwishFan on 2010-02-01
How much swap do you have? If you have about as much swap as you have RAM or more, then I do not advise you to add more.

You will probably need from 1x to 2x your RAM in SWAP if you want to hibernate. There is an article about using SWAP in Ubuntu.
[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

The tweak I mentioned with vm.swappiness=100 is explained in the article above, and I got the idea from Andrew Morton on this page. I honestly do not see much difference but the logic makes sense to me.
[http://kerneltrap.org/node/3000](http://kerneltrap.org/node/3000)

---

### Post by k3lt01 on 2010-02-01
> **mvalviar said:**
> @NightwishFan - how do I go about increasing my swap? I have the disk space however I don't know how to repartition without putting my files in jeopardy.Check [this thread]("http://ubuntuforums.org/showthread.php?t=1385729") out.

---

### Post by mvalviar on 2010-02-01
I have 1Gig of swap. 

I just noticed that on a fresh boot. I use 50% of my ram already. With firefox running I'm at 38% for programs and 38% for cache. 

I had to kill a previous session earlier when I was working with GIMP firefox, gvim and audacious.

If this persists I'm afraid I'd have to move back to 32bit.

---

### Post by k3lt01 on 2010-02-01
> **mvalviar said:**
> If this persists I'm afraid I'd have to move back to 32bit.Try the 2gb of swap idea first, you shouldn't be having much more difficulty, if any, with 64 bit compared to 32 bit.

---

### Post by mvalviar on 2010-02-02
I'm back to 32 bit. I'm afraid expanding my swap wont make any difference since it will still need HD I/O.

On 32 bit the memory foot print of a fresh boot is 50% lower than 64 bit. 

I guess I'd just use 64 bit on better hardware.

---

