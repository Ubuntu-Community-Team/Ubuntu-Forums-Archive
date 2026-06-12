---
title: "How does Ubuntu run with Wubi?"
date: 2010-06-02
forum: New to Ubuntu
---

### Post by Effect on 2010-06-02
I picked up a new hard drive last night and after cloning my Vista install to the new drive I thought about reinstalling Ubuntu (10.04 version) so I could dual boot into it. However I've held off until today (had the clone run while I slept) so I could print out some instructions as its been a while since I installed Linux. Don't remember everything. However in the process of looking for instructions I came across that you could install things from within Windows as you would any other application. Great news. Should save me a LOT of hassle if I want to remove it. However performance is what I'm wondering about.

If you install Ubuntu this way what kind of performance can I expect? (My current system is running Vista Home Premimum with 3 gigs of ram, SAPPHIRE ATI Radeon X1950GT 256MB PCI Express x16 and AMD Athlon 64 X2 4200+.) Noticeable differences compared to installing it the original way? How about running games in Ubuntu with this method? Accessing NTFS drives? Etc?

Thanks.

---

### Post by stormchaser2063 on 2010-06-02
well I recentally installed ubuntu on my compaq desktop its a 3 ghz processor with 512 of ram. I hate windows so much my laptop is a macbook pro but didnt really want to replace a good working desktop with a new mac desktop yet so my buddy suggested ubuntu. my only issue with installing it as a stand alone install was the fact i use cricket wireless for internet, no wired internet here so my buddy suggested using wubi... so i did and so far i really like it. it seems to be much faster than windows and if your using vista you should really enjoy ubuntu and the ease of installing it with wubi.

---

### Post by Effect on 2010-06-02
Another question. If installing this way would a swap partition be needed still?

Thanks.

---

### Post by philinux on 2010-06-02
> **Effect said:**
> Another question. If installing this way would a swap partition be needed still?

Thanks.

The wubi site says performance is as good as a full install. Caveat. Defrag windows first and performace can degrade over time I'm told. Ignore the swap question wubi sorts itself out.

The problems I've seen on here are borked windows install because of an unclean wubi shutdown. It seems sensitive to this.

If I were you I'd go for a full dual boot.
Good resource to read up.
[http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)

---

### Post by lukeiamyourfather on 2010-06-02
Dual booting is the best option if you plan to use both on a regular basis. Performance wise installing with Wubi is identical except for the disk I/O. Disk performance will be diminished since the Linux "partition" is really a file on the Windows drive. Cheers!

---

