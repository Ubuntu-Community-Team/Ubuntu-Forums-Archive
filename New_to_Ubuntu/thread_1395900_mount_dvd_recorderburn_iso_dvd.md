---
title: "mount dvd recorder/burn iso dvd"
date: 2010-02-01
forum: New to Ubuntu
---

### Post by pottzie on 2010-02-01
I've downloaded an iso image that I want to burn to a DVD. When I go to K3B it says to put in a recordable  media, even though I have a blank DVD in already. How do I get the system to recognize the DVD recorder (I swapped it out a while back), and what's the best way to burn this iso that I spent half a lifetime downloading...like 10 hours on DSL....to find out what OpenSUSE has that's different..
 Thanks

---

### Post by sandyd on 2010-02-01
whats does
```

ls /dev

```
output?

---

### Post by pottzie on 2010-02-01
pottzie@pottzie-desktop:~$ ls /dev
adsp             log                 ram1    sequencer   tty2   tty45  urandom
agpgart          loop0               ram10   sequencer2  tty20  tty46  usbmon0
audio            loop1               ram11   sg0         tty21  tty47  usbmon1
audio1           loop2               ram12   sg1         tty22  tty48  usbmon2
binder           loop3               ram13   sg2         tty23  tty49  usbmon3
block            loop4               ram14   sg3         tty24  tty5   usbmon4
bus              loop5               ram15   shm         tty25  tty50  v4l
cdrom            loop6               ram2    snapshot    tty26  tty51  vcs
cdrom1           loop7               ram3    snd         tty27  tty52  vcs1
cdrw             lp0                 ram4    sndstat     tty28  tty53  vcs2
char             mapper              ram5    sr0         tty29  tty54  vcs3
console          mcelog              ram6    sr1         tty3   tty55  vcs4
core             mem                 ram7    stderr      tty30  tty56  vcs5
cpu_dma_latency  mixer               ram8    stdin       tty31  tty57  vcs6
disk             mixer1              ram9    stdout      tty32  tty58  vcs7
dri              net                 random  tty         tty33  tty59  vcs8
dsp              network_latency     rfkill  tty0        tty34  tty6   vcsa
dsp1             network_throughput  rtc     tty1        tty35  tty60  vcsa1
dvd1             null                rtc0    tty10       tty36  tty61  vcsa2
ecryptfs         oldmem              scd0    tty11       tty37  tty62  vcsa3
fd               parport0            scd1    tty12       tty38  tty63  vcsa4
fd0              pktcdvd             sda     tty13       tty39  tty7   vcsa5
full             port                sda1    tty14       tty4   tty8   vcsa6
fuse             ppp                 sda2    tty15       tty40  tty9   vcsa7
hidraw0          psaux               sda3    tty16       tty41  ttyS0  vcsa8
hpet             ptmx                sda4    tty17       tty42  ttyS1  video0
input            pts                 sdb     tty18       tty43  ttyS2  zero
kmsg             ram0                sdb1    tty19       tty44  ttyS3
pottzie@pottzie-desktop:~$

---

### Post by samantha_ on 2010-02-01
> **pottzie said:**
> pottzie@pottzie-desktop:~$ ls /dev
adsp             log                 ram1    sequencer   tty2   tty45  urandom
agpgart          loop0               ram10   sequencer2  tty20  tty46  usbmon0
audio            loop1               ram11   sg0         tty21  tty47  usbmon1
audio1           loop2               ram12   sg1         tty22  tty48  usbmon2
binder           loop3               ram13   sg2         tty23  tty49  usbmon3
block            loop4               ram14   sg3         tty24  tty5   usbmon4
bus              loop5               ram15   shm         tty25  tty50  v4l
cdrom            loop6               ram2    snapshot    tty26  tty51  vcs
cdrom1           loop7               ram3    snd         tty27  tty52  vcs1
cdrw             lp0                 ram4    sndstat     tty28  tty53  vcs2
char             mapper              ram5    sr0         tty29  tty54  vcs3
console          mcelog              ram6    sr1         tty3   tty55  vcs4
core             mem                 ram7    stderr      tty30  tty56  vcs5
cpu_dma_latency  mixer               ram8    stdin       tty31  tty57  vcs6
disk             mixer1              ram9    stdout      tty32  tty58  vcs7
dri              net                 random  tty         tty33  tty59  vcs8
dsp              network_latency     rfkill  tty0        tty34  tty6   vcsa
dsp1             network_throughput  rtc     tty1        tty35  tty60  vcsa1
dvd1             null                rtc0    tty10       tty36  tty61  vcsa2
ecryptfs         oldmem              scd0    tty11       tty37  tty62  vcsa3
fd               parport0            scd1    tty12       tty38  tty63  vcsa4
**fd0  **            pktcdvd             sda     tty13       tty39  tty7   vcsa5
full             port                sda1    tty14       tty4   tty8   vcsa6
fuse             ppp                 sda2    tty15       tty40  tty9   vcsa7
hidraw0          psaux               sda3    tty16       tty41  ttyS0  vcsa8
hpet             ptmx                sda4    tty17       tty42  ttyS1  video0
input            pts                 sdb     tty18       tty43  ttyS2  zero
kmsg             ram0                sdb1    tty19       tty44  ttyS3
pottzie@pottzie-desktop:~$

The DVD recorders regonized, i bolded it.
What model is the DVD recorder, it may be a device specific problem.

---

### Post by pottzie on 2010-02-01
HP dvd 740

---

### Post by pottzie on 2010-02-01
Found an external DVD burner, plugged it in and everything worked, so I guess I'll mark this solved.

---

### Post by samantha_ on 2010-02-01
> **pottzie said:**
> HP dvd 740

your out of luck, really. a lot of people such as [http://ubuntuforums.org/showthread.php?t=633704](http://ubuntuforums.org/showthread.php?t=633704)

have the problem, but there never really was a solution.
Filing a bug report would be a nice idea for future users.

---

