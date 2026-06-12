---
title: "Remote rsync"
date: 2017-10-07
forum: Networking &amp; Wireless
---

### Post by Geoff_Lane on 2017-10-07
Folks,

I look after my girlfriend's 16:04 machine remotely, I am trying to transfer a 3GB file from her machine to my 16:04 system using scp

Setting up the system on tmux it starts well but two attempts seem to have stalled around 700MB

scp can't resume like wget so am looking in to rscnc but am struggling because I usually connect to her computer using ssh and a different port 2288

Here is my scp command;

```
scp -P 2288 carole@remoteIP:~/Desktop/videos/Movies/FILE.mpg FILE.mpg
```

This transfers her file into my current directory on my machine but as mentioned two attempts have failed at around 700MB

I have tried this using rsync;

```
rsync -v -e 'ssh -p 2288' carole@remoteIP:~/Desktop/videos/Movies/File.mpg
receiving file list ... done
-rw-r--r--  3565088768 2015/06/14 15:02:26 File.mpg

sent 19 bytes  received 43 bytes  13.78 bytes/sec
total size is 3565088768  speedup is 57501431.74


```

The last entry seems to report the file correctly (Size, name etc) but nothing gets transferred.

Any suggestions as to what I might be doing wrong appreciated.

Geffers

---

### Post by sudodus on 2017-10-07
From the manual ```
man rsync
```

> As  a  special  case,  if a single source arg is specified without a destination, the files are listed in an output format similar to "ls -l".

I guess this means that it works as **ls -l** and not as **cp**

So please add the destination (file or directory). Dot might do, if you want it into the current directory with the same file name.

---

### Post by Geoff_Lane on 2017-10-07
> **sudodus said:**
> From the manual ```
man rsync
```



I guess this means that it works as **ls -l** and not as **cp**

So please add the destination (file or directory). Dot might do, if you want it into the current directory.

I am currently experimenting - I've issued the same command with a full file path as a destination rather than just the file name.

Not sure what is happening, ntop shows about 2mbps connection between both machines, so far 500MB transferred but my file is still the same size.

Something is going on but presently I have no idea what, shall leave it a while and see what happens. I would have thought the partial file I am attempting to copy would have grown in size but not so as yet.

8-[

Geffers

---

### Post by SeijiSensei on 2017-10-07
While rsync is transferring files, it writes them to the destination directory as a hidden file with a dot added to the front of the name.  When the file is completely transferred, rsync will rename the hidden file to its original name.  At the terminal, try using "ls -a" to see the hidden files.

---

### Post by Geoff_Lane on 2017-10-07
> **SeijiSensei said:**
> While rsync is transferring files, it writes them to the destination directory as a hidden file with a dot added to the front of the name.  When the file is completely transferred, rsync will rename the hidden file to its original name.  At the terminal, try using "ls -a" to see the hidden files.

Thanks, just looked and found that.

If the transfer is interrupted whilst rsync is running what happens then? I thought all was going well, ntop was showing well in excess of 1GB transferred. Somehow transfer interrupted and when I issued rsync command again the GB originally shown as transferred has gone somewhere.

It has started again from the beginning.

Geoff Lane

---

### Post by sudodus on 2017-10-07
Maybe it helps if you use the option --partial

```
       --partial
              By  default,  rsync will delete any partially transferred file if the transfer is inter&#8208;
              rupted. In some circumstances it is more desirable to keep partially transferred  files.
              Using the --partial option tells rsync to keep the partial file which should make a sub&#8208;
              sequent transfer of the rest of the file much faster.

```

---

### Post by Geoff_Lane on 2017-10-07
> **sudodus said:**
> Maybe it helps if you use the option --partial

```
       --partial
              By  default,  rsync will delete any partially transferred file if the transfer is inter&#8208;
              rupted. In some circumstances it is more desirable to keep partially transferred  files.
              Using the --partial option tells rsync to keep the partial file which should make a sub&#8208;
              sequent transfer of the rest of the file much faster.

```

OK, thanks for that suggestion. Shall give that a try now.

Geffers

---

