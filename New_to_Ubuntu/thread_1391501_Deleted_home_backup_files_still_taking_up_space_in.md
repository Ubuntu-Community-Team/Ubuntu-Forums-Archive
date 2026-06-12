---
title: "Deleted home_backup files still taking up space in /home"
date: 2010-01-26
forum: New to Ubuntu
---

### Post by kudzu on 2010-01-26
Hey everyone,

I recently created a new /home partition using the psychocats guide.  After some struggles things seem to be sorted out, thanks to the help of someone on this forum.  So, I went ahead and deleted my home_backup that I had created on my new /home partition so that I could free up some space.  That's where things got weird again:

I typed "sudo rm -rf /home_backup" into the terminal, but all I got was a weird sound.  The files where still there.  So, I used "gksudo palimpsest" to delete the files.  That worked, but I gained no space from deleting the 11GB worth of files in the folder.  I looked into /root trash and they weren't there, so I have no idea what's going on.  My /home partition is 42GB, according to disk utility, and when I right-click and select "properties" in the /home folder it shows that I only have 24.5GB currently in use, yet it only shows 5.4GB as being free.

Any idea what the problem is?

---

### Post by lyall on 2010-01-26
did you check your Trash can to see what is in it?
it would be a place to look why you did not get free space back

good luck and have fun learning

---

### Post by kudzu on 2010-01-26
Yeah, I checked my user trash can and used gksudo nautilus to check my root trash can.  Are there other trash cans?

---

### Post by Seq on 2010-01-26
So /home is it's own partition now. Just out of curiosity, can you run the following?
```
ls -al /home
```

---

### Post by kudzu on 2010-01-26
> **Seq said:**
> So /home is it's own partition now. Just out of curiosity, can you run the following?
```
ls -al /home
```

It's supposed to be.  Here's what I get when I enter that command (my username is "jake"):


total 32
drwxr-xr-x  5 root root  4096 2010-01-27 01:24 .
drwxr-xr-x 22 root root  4096 2010-01-27 00:05 ..
drwx------ 56 jake jake  4096 2010-01-27 13:05 jake
drwx------  2 root root 16384 2010-01-23 18:14 lost+found
drwx------  4 root root  4096 2010-01-27 01:24 .Trash-0

---

### Post by Seq on 2010-01-26
> **kudzu said:**
> It's supposed to be.  Here's what I get when I enter that command (my username is "jake"):


total 32
drwxr-xr-x  5 root root  4096 2010-01-27 01:24 .
drwxr-xr-x 22 root root  4096 2010-01-27 00:05 ..
drwx------ 56 jake jake  4096 2010-01-27 13:05 jake
drwx------  2 root root 16384 2010-01-23 18:14 lost+found
drwx------  4 root root  4096 2010-01-27 01:24 .Trash-0

There you are. Were you running nautilus as root? It looks like you got a .Trash-0 (0 is root's uid) on the root of that new file system.

It doesn't make sense to copy a file across file systems just to stick it in the trash, so typically a .Trash-XXX is created, where XXX is your uid, and then deletions are simply a mv operation that can happen relatively quickly (and not eat up disk space on some other partition by accident). Root's home directory is /root, so it is on a different partition and thus the files were not copied there. Since root can write to /home directly (and you can't, which is good. see the permissions on "." in your output above), it created a trash there.

This should show you your missing space:

```
du -chs /home/.Trash-0
```

You probably don't want to keep it around. Make sure you double-check this command as running rm as root is always dangerous.

```
sudo rm -r /home/.Trash-0
```

---

### Post by kudzu on 2010-01-26
> **Seq said:**
> There you are. Were you running nautilus as root? It looks like you got a .Trash-0 (0 is root's uid) on the root of that new file system.

It doesn't make sense to copy a file across file systems just to stick it in the trash, so typically a .Trash-XXX is created, where XXX is your uid, and then deletions are simply a mv operation that can happen relatively quickly (and not eat up disk space on some other partition by accident). Root's home directory is /root, so it is on a different partition and thus the files were not copied there. Since root can write to /home directly (and you can't, which is good. see the permissions on "." in your output above), it created a trash there.

This should show you your missing space:

```
du -chs /home/.Trash-0
```You probably don't want to keep it around. Make sure you double-check this command as running rm as root is always dangerous.

```
sudo rm -r /home/.Trash-0
```

Worked like a charm.  Thanks for the knowledge, man.:popcorn:

---

### Post by Seq on 2010-01-26
Yeah, or I could think it over and realize you probably had home_backup on /, which is pretty much what you said in the first message. Although I think, after looking at palimsest, that this is still what happened, just not on /home.

Do what I suggested above, but on / instead of /home. You should have a .Trash-0 there as well. Doing a df on that should show you your space. You should be able to adjust your commands appropriately.

```
ls -la /
```

It looks like palimpsest launches nautilus when you click on a mount point. Since palimpsest runs as root, so does nautilus.

Also, "sudo rm -rf /home_backup" would indeed error as

---

### Post by kudzu on 2010-01-26
What you suggested first seems to have worked.  I went ahead and tried your latest suggestions anyway.  I typed "du -chs /.Trash-0" into terminal (you said to do the same thing with "/" instead of "/home," right?) and got:

du: cannot access `/.Trash-0': No such file or directory
0    total

Here's what I get when I enter "ls -la /:"

total 104
drwxr-xr-x  22 root root  4096 2010-01-27 00:05 .
drwxr-xr-x  22 root root  4096 2010-01-27 00:05 ..
drwxr-xr-x   2 root root  4096 2010-01-21 13:18 bin
drwxr-xr-x   3 root root  4096 2010-01-24 02:59 boot
lrwxrwxrwx   1 root root    11 2008-07-09 04:10 cdrom -> media/cdrom
drwxr-xr-x  15 root root  3840 2010-01-27 12:44 dev
drwxr-xr-x 152 root root 12288 2010-01-27 12:44 etc
drwxr-xr-x   4 root root  4096 2010-01-27 13:24 home
drwxr-xr-x   2 root root  4096 2008-07-02 19:16 initrd
lrwxrwxrwx   1 root root    33 2010-01-09 18:04 initrd.img -> boot/initrd.img-2.6.31-17-generic
drwxr-xr-x  19 root root 12288 2010-01-21 13:18 lib
drwx------   2 root root 16384 2008-07-09 04:10 lost+found
drwxr-xr-x   3 root root  4096 2010-01-27 12:44 media
drwxr-xr-x   2 root root  4096 2008-04-15 14:53 mnt
drwxr-xr-x   6 root root  4096 2010-01-27 00:50 opt
dr-xr-xr-x 181 root root     0 2010-01-27 21:43 proc
drwxr-xr-x  24 root root  4096 2010-01-27 01:57 root
drwxr-xr-x   2 root root  4096 2010-01-14 13:28 sbin
drwxr-xr-x   2 root root  4096 2009-03-07 01:21 selinux
drwxr-xr-x   3 root root  4096 2010-01-09 18:05 srv
drwxr-xr-x  12 root root     0 2010-01-27 21:43 sys
drwxrwxrwt  15 root root  4096 2010-01-27 13:37 tmp
drwxr-xr-x  12 root root  4096 2010-01-11 16:17 usr
drwxr-xr-x  15 root root  4096 2008-07-02 19:34 var
lrwxrwxrwx   1 root root    30 2010-01-09 18:04 vmlinuz -> boot/vmlinuz-2.6.31-17-generic

---

### Post by Seq on 2010-01-26
> **kudzu said:**
> What you suggested first seems to have worked.  I went ahead and tried your latest suggestions anyway.  I typed "du -chs /.Trash-0" into terminal (you said to do the same thing with "/" instead of "/home," right?) and got:

du: cannot access `/.Trash-0': No such file or directory
0    total

Hmm, I guess I'm just thinking too hard then ;)

As long as you got your disk space back all is good. :)

---

### Post by kudzu on 2010-01-26
> **Seq said:**
> Hmm, I guess I'm just thinking too hard then ;)

As long as you got your disk space back all is good. :)

I'll mentally log your other would-be solution for the inevitable next mystery.

---

### Post by kudzu on 2010-01-27
> **Seq said:**
> Hmm, I guess I'm just thinking too hard then ;)

As long as you got your disk space back all is good. :)

Actually, now that you mention it and after having done the math, 3GB worth of unused space on my /home partition is unaccounted for: Right-clicking and selecting "Properties" in my home folder turns up 24.5GB as in use and 14.6GB free.  Is this normal?

---

### Post by Seq on 2010-01-27
> **kudzu said:**
> Actually, now that you mention it and after having done the math, 3GB worth of unused space on my /home partition is unaccounted for: Right-clicking and selecting "Properties" in my home folder turns up 24.5GB as in use and 14.6GB free.  Is this normal?

It depends. Due to the way the filesystem works, files can take up more space than they actually need. Compare my output below between file system (df) and useage (du).

```
$ df /home -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/mapper/vg_macbook-lv_home
                      173G  124G   41G  76% /home
$ du -chsx /home
123G	/home
```

For me, there is not much of a difference, but it depends on several variables. You can also try using the Disk Usage Analyzer (baobab).

---

### Post by Seq on 2010-01-27
On second thought, three gigs is quite a bit of space. I'd keep looking...

---

### Post by kudzu on 2010-01-27
What should I be looking for with the Disk Usage Analyzer?

---

### Post by kudzu on 2010-01-27
Here's my filesystem and usage information, too:

$ df /home -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda2              39G   23G   15G  61% /home

and 

$ du -chsx /home
du: cannot read directory `/home/lost+found': Permission denied
22G    /home
22G    total

That looks more like yours, but when I do the right-click "Properties" thing in my /home folder I still get 24.5G used and 14.6G available on a filesystem that is 42G, according to Disk Utility.  Weird.

---

### Post by Seq on 2010-01-27
> **kudzu said:**
> Here's my filesystem and usage information, too:

$ df /home -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda2              39G   23G   15G  61% /home

and 

$ du -chsx /home
du: cannot read directory `/home/lost+found': Permission denied
22G    /home
22G    total

That looks more like yours, but when I do the right-click "Properties" thing in my /home folder I still get 24.5G used and 14.6G available on a filesystem that is 42G, according to Disk Utility.  Weird.

Actually, that just looks like a representation issue. Nautilus is probably using powers of 1000 to represent units. The -h argument for both df and du uses binary-aligned units (1MB=1024KB, etc). You can use --si instead to use powers of 10 instead (1MB=1000KB).

The SI units are what disk manufacturers actually use currently, so it makes sense to use them for disk size as well. Otherwise when you stick in your 8GB usb key, it says "7.4GB disk", which irks some folks. In the end, it doesn't really matter which representation you use.

Here is output from a machine I have access to right now:

```
$ df -h /home
Filesystem            Size  Used Avail Use% Mounted on
/dev/mapper/vg_jupitertwo-lv_home
                      230G  152G   67G  70% /home

$ df --si /home
Filesystem             Size   Used  Avail Use% Mounted on
/dev/mapper/vg_jupitertwo-lv_home
                       247G   163G    72G  70% /home
```

---

### Post by kudzu on 2010-01-28
Ah, I figured it was a representation issue after I put in the terminal commands you showed me.  Here's my si output:

```
$ df --si /home
Filesystem             Size   Used  Avail Use% Mounted on
/dev/sda2               42G    24G    16G  61% /home
```

That still shows 2G as being unaccounted for, though.  Is that within the normal range of unaccounted for space?

---

### Post by Seq on 2010-01-28
> **kudzu said:**
> Ah, I figured it was a representation issue after I put in the terminal commands you showed me.  Here's my si output:

```
$ df --si /home
Filesystem             Size   Used  Avail Use% Mounted on
/dev/sda2               42G    24G    16G  61% /home
```

That still shows 2G as being unaccounted for, though.  Is that within the normal range of unaccounted for space?

Hmm, correct. I see the same as well, actually. I've never really looked before.

```
$ df /home
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/mapper/vg_jupitertwo-lv_home
                     240306696 158724808  69374992  70% /home

# Add Used + Available
$ echo "158724808 + 69374992" | bc
228099800

# Size - (Used + Available), convert to MB
$ echo "(240306696 - 228099800) / (1024)" | bc
11920

```

I am now somewhat curious too as the above shows almost 12GB mismatch. Now bc doesn't seem to do decimal, so I did some fuzzy math. It seems 11920 is roughly 5% of my disk, while 2 GB is roughly 5% of 42GB.

It could be that the "Used" column doesn't include filesystem overhead, causing the mismatch. Or it could be that df does not include reserved blocks as "Available". 5% is the default for reserved blocks, if I remember.

```
$ sd tune2fs -l /dev/vg_jupitertwo/lv_home | grep -e "Reserved block count" -e "Block size"
Reserved block count:     3051724
Block size:               4096

# Convert from blocks reserved to bytes, convert to MB
$ echo "(3051724 * 4096) / (1024 * 1024)" | bc
11920

```

So it looks like it may be the latter, reserved space is not included as either Used or Available. So I did a search, and while there is no mention in `man df` of "reserved", there is on the [wikipedia page for df]("http://en.wikipedia.org/wiki/Df_%28Unix%29").
> <total space>
    The total size of the file system in 512-byte units. The exact meaning of this figure is implementation-defined, but should include <space used>, <space free>, **plus any space reserved by the system not normally available to a user**.

So hopefully that answers that. Now, the merits of reserved space on /home may be dubious, it does make sense as a default (for / and other filesystems). I may try to bring my reserved space down to 1%, or maybe eliminate it completely from /home. I'll have to read up on it a bit more before I start changing my filesystem.

---

