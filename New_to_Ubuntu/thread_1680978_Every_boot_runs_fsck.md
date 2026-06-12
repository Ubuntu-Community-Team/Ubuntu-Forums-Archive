---
title: "Every boot runs fsck?"
date: 2011-02-03
forum: New to Ubuntu
---

### Post by myanon0001 on 2011-02-03
Greetings from an "ubuntu newbie" ... 

Questions: 
Is fsck being run every time I boot ubuntu? If so, isn't this overkill, and what should I do about it? 

Mine is a dual-boot system (win7, ubuntu 10.10 64-bit), and during every boot of ubuntu the following two-line message shows  briefly on the screen (and in /var/log/boot.log):

[B]fsck from util-linux-ng 2.17.2
/dev/sda5: clean, 159106/5513216 files, 1743352/22023936 blocks[/B]

(These two lines are usually followed by others that seem okay and unrelated to my questions; e.g., stuff about  "Starting AppArmor profiles" and "Setting sensors limits".)

However, after booting, the command 
```

sudo tune2fs -l /dev/sda5

```
now displays the following info:

...
Mount count:              <less than 31, increasing by 1 after each boot>
Maximum mount count:      31
**Last checked:             Wed Feb  2 10:38:56 2011**    [COLOR="Blue"]<---- this remains the same before/after booting[/COLOR]
Check interval:           15552000 (6 months)
Next check after:         Mon Aug  1 11:38:56 2011
...

(The "Last checked" time is yesterday when the Mount count reached the Maximum count, presumably causing fsck to be run, and the count was reset to 1.)

So, is fsck *not* being run now at every boot, in spite of the two-line boot-time message that seems to say otherwise?

btw, DO NOT attempt to run fsck for a mounted partition (e.g. "fsck /dev/sda5" in my case), as doing so results in the following ...  
[COLOR="Red"]WARNING!!!  The filesystem is mounted.   If you continue you ***WILL*** cause ***SEVERE*** filesystem damage.[/COLOR]

---

### Post by CharlesA on 2011-02-03
It's just an information message letting you know that the volume is "clean"

---

### Post by vanadium on 2011-02-03
fsck *is* run on every boot. However, it only concerns a very quick check to see whether the journal is clean. Only once in a while, a full check is performed. This used to take quite some time, but nowadays, with ext4, these full checks are also quite fast.

You really want your partitions checked on every boot

As a tip, consider checking removable USB disks manually every now and then. These drives otherwise *NEVER* get checked.

Whether a partition is checked or not during startup is controlled by a setting in /etc/fstab.

---

### Post by Rubi1200 on 2011-02-03
Unless you change the settings, a full fsck is run every 30 boots (or perhaps every 30 days whichever comes first I think).

As pointed out, you should leave things as they are in order to keep things stable.

---

### Post by blind2314 on 2011-02-03
I'm curious as to the reasoning of why fsck should be left to run on every boot and "keep everything stable". Unless someone is consistently unplugging their computer during the middle of intensive writes/reads, I see no reason why a hard drive would have that many file system errors on it, especially not one with an advanced journaling file system.

---

### Post by CharlesA on 2011-02-03
> **blind2314 said:**
> I'm curious as to the reasoning of why fsck should be left to run on every boot and "keep everything stable". Unless someone is consistently unplugging their computer during the middle of intensive writes/reads, I see no reason why a hard drive would have that many file system errors on it, especially not one with an advanced journaling file system.

It runs every boot by default, but it doesn't actually run a file system check unless you are at the mount/time limit or unless you tell it to run a check with:

```
sudo touch /forcefsck
```

---

### Post by myanon0001 on 2011-02-03
Thanks for the explanations, everyone.  To further explore the matter, I ran fsck with and without the "full" option from a Live USB-stick with /dev/sda5 not mounted.  

Indeed, the command
```

sudo fsck /dev/sda5

```
took only an instant to execute, and gave exactly the same "clean" report as mentioned above -- consistent with "checking" only by referring to info journaled since the last "full" check. 

On the other hand, the "full" version of the command 
```

sudo fsck -f /dev/sda5

```
resulted in ...

fsck from util-linux-ng 2.17.2
e2fsck 1.41.12 (17-May-2010)

Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information

/dev/sda5: ***** FILE SYSTEM WAS MODIFIED *****
/dev/sda5: 159136/5513216 files (0.3% non-contiguous), 1743062/22023936 blocks
ubuntu@ubuntu:~$

... and now the above tune2fs command shows a correspondingly updated "Last checked" time.

(I've marked this thread as SOLVED.  Thanks again.)

---

### Post by CharlesA on 2011-02-03
The "file system was modified" message usually means that something was changed, either an error was fixed, or something.

Does it do the same thing it you use fsck -f again ?

---

### Post by myanon0001 on 2011-02-03
> **CharlesA said:**
> The "file system was modified" message usually means that something was changed, either an error was fixed, or something.

Does it do the same thing it you use fsck -f again ?

No, it now goes through all those passes with no report of any modifications.

I figure the modifications the first time were probably benign, maybe something like ms-windows "defrag"?

---

### Post by CharlesA on 2011-02-03
That's good then. Normally fsck will only make modifications after prompting you.

---

### Post by myanon0001 on 2011-02-03
> **CharlesA said:**
> That's good then. Normally fsck will only make modifications after prompting you.

Hmmm, wait a sec ...  The first time I ran fsck with the -f option, the output included the following line ...[INDENT]Superblock last mount time is in the future.
    (by less than a day, probably due to the hardware clock being incorrectly set)  Fix<y>? yes
[/INDENT]... which I had omitted, thinkiing it wasn't relevant.  Sorry for the omission -- that may actually be the only modification it's referring to?  (Presumably because I'd booted from a Live USB-stick, the system time was being misreported by some hours, according to the desktop clock.)

---

### Post by CharlesA on 2011-02-03
> **myanon0001 said:**
> Hmmm, wait a sec ...  The first time I ran fsck with the -f option, the output included the following line ...[INDENT]Superblock last mount time is in the future.
    (by less than a day, probably due to the hardware clock being incorrectly set)  Fix<y>? yes
[/INDENT]... which I had omitted, thinkiing it wasn't relevant.  Sorry for the omission -- that may actually be the only modification it's referring to?  (Presumably because I'd booted from a Live USB-stick, the system time was being misreported by some hours, according to the desktop clock.)
That's why it said it was modified then.

You are good to go.

---

