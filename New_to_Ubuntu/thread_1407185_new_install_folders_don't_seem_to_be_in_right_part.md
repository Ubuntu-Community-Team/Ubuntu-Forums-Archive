---
title: "new install folders don't seem to be in right partitions"
date: 2010-02-15
forum: New to Ubuntu
---

### Post by hortstu on 2010-02-15
just installed hardy.  Did a manual partition.  This is the way I set it up.

partition    size      partition type    label         filesystem    mount pt
/dev/sda1    120 GB    extended          --            --            --
/dev/sda2    15 GB     logical           hardy_root    ext3         /
/dev/sda3    3 GB      logical           hardy_home    ext3         /home
/dev/sda4    15 GB     logical           lucid_root    ext3         /mnt/lucid_root
/dev/sda5    3 GB      logical           lucid_home    ext3         /mnt/lucid_home
/dev/sda6    80 GB    logical           data          ext3         /mnt/data
/dev/sda7    4 GB      logical           --            swap         --

The sda# probably is not right there.  I'm installing gparted now so I can verify them.

Desktop and documents seem to be in one of the 3gb partitions.  Shouldn't it be in the data?

---

### Post by jken146 on 2010-02-15
No, the desktop is /home/yourUsername/Desktop and all your user's settings will be in /home/yourUsername too (these files begin with a . and are hidden in the file browser; press Ctrl+h yo see them).

I'd assumed from your partitioning plan that you wanted to keep your work/music/whatever files separate from the config files of your users, i.e. put all your stuff on /mnt/data

---

### Post by hortstu on 2010-02-15
> No, the desktop is /home/yourUsername/Desktop and all your user's settings will be in /home/yourUsername too (these files begin with a . and are hidden in the file browser; press Ctrl+h yo see them).

I'd assumed from your partitioning plan that you wanted to keep your work/music/whatever files separate from the config files of your users, i.e. put all your stuff on /mnt/data

Thanks Jken... but i'm just pushing forward and figuring t out by screwing it up.  I'm getting much better at using and installing the live cd than i was 1 year ago :)

I want to move something from another drive to the data file.  It's about 25gb.  some of it is pics, a language program, just general stuff I can't replace.  I want to put it somewhere where I can get at it easily and graphically sort it out... since that will go much faster for me than using the terminal.

Still don't have those partition labels... doing an update now.

---

### Post by jken146 on 2010-02-15
If you're asking what I think, just point your file browser at /mnt/data

---

### Post by hortstu on 2010-02-15
yep did that a second ago... it's telling me I don't have permissions... is that going to be a problem?

I figure I can get it in there via

```
sudo cp -a file1 file2
```

but is this lack of permission to use the data file going to cause me problems?

---

### Post by jken146 on 2010-02-15
Is there just one user on this machine?

---

### Post by hortstu on 2010-02-15
yes

---

### Post by hortstu on 2010-02-15
i think i have another problem... I labeled the file D&S... I think that & is screwing up the cp command

---

### Post by jken146 on 2010-02-15
If your username is hortstu,
```
sudo chown -R hortstu:hortstu /mnt/data
```

---

### Post by hortstu on 2010-02-15
should I do that with all the different partitions I made or just the data one?

---

### Post by jken146 on 2010-02-15
> **hortstu said:**
> i think i have another problem... I labeled the file D&S... I think that & is screwing up the cp command

You have to escape special characters with a backslash. So you'd type ```
cp D\&S /path/to/destination
```

---

### Post by jken146 on 2010-02-15
> **hortstu said:**
> should I do that with all the different partitions I made or just the data one?

Just the one. Then all the files there will be owned by you.

---

### Post by hortstu on 2010-02-15
> sudo chown -R hortstu:hortstu /mnt/data

So 'chown' is change owner?

just out of curiosity what if multiple users were using the system?

---

### Post by hortstu on 2010-02-15
> **jken146 said:**
> You have to escape special characters with a backslash. So you'd type ```
cp D\&S /path/to/destination
```

Man it's cool that you know all this.  Thanks

---

### Post by hortstu on 2010-02-15
So after changing permission I tryed doing it graphically and messages were popping up about not having permission to red certain files so it wont copy them... will I get around this with the terminal command or is there something else I have to do?

---

### Post by jken146 on 2010-02-15
> **hortstu said:**
> So 'chown' is change owner?

just out of curiosity what if multiple users were using the system?

Yes. Read ```
man chown
``` for all the details.

If there were multiple users? One solution would be to make directories in /mnt/data for each user,
```

cd /mnt/data
sudo mkdir bob
sudo chown bob:bob bob
sudo mkdir jane
sudo chown jane:jane jane
...

```

---

### Post by jken146 on 2010-02-15
> **hortstu said:**
> So after changing permission I tryed doing it graphically and messages were popping up about not having permission to red certain files so it wont copy them... will I get around this with the terminal command or is there something else I have to do?

To *read* certain files? Where are these files?

---

### Post by hortstu on 2010-02-15
> To read certain files? Where are these files?

Not sure... I'll try it again and let you know probably part of the language pack.

I imagine part of the problem is that I'm moving everything from an external that was my old os that won't boot anymore.  So since I'm not logged in maybe?

---

### Post by jken146 on 2010-02-15
So you're trying to copy your personal stuff, which is backed up on an external drive, onto the PC?  If that's right, copy whatever are your personal files into /mnt/data/ 

If you're more comfortable with nautilus, use ```
sudo nautilus
``` to run it as root (careful!) to overcome permissions issues.

Then, chown all the files you've just put in /mnt/data so that they're yours:
```
sudo chown -R joebloggs:joebloggs /mnt/data
```


Also, language packs?? Why would you back those up?

---

### Post by hortstu on 2010-02-15
> **jken146 said:**
> So you're trying to copy your personal stuff, which is backed up on an external drive, onto the PC?  If that's right, copy whatever are your personal files into /mnt/data/ 

If you're more comfortable with nautilus, use ```
sudo nautilus
``` to run it as root (careful!) to overcome permissions issues.

Then, chown all the files you've just put in /mnt/data so that they're yours:
```
sudo chown -R joebloggs:joebloggs /mnt/data
```


Also, language packs?? Why would you back those up?

Sorry I shouldn't have called it a language pack... it's a rosetta stone software we lost the disks for.

---

### Post by jken146 on 2010-02-15
:-) ok!

---

### Post by hortstu on 2010-02-15
> **jken146 said:**
> 
If you're more comfortable with nautilus, use ```
sudo nautilus
``` to run it as root (careful!) to overcome permissions issues.

I don't even know what nautilus is... I'll look it up though don't waste your time thanks...

Looks like everything's copying over w/o a problem this time... maybe it's happening in a different order or maybe the fact that it was updating at the same time was interfering... I don't know just speculating.

---

### Post by jken146 on 2010-02-15
nautilus is the GUI file browser.

---

