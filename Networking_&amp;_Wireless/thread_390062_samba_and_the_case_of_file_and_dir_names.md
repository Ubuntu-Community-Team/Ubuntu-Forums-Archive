---
title: "samba and the case of file and dir names"
date: 2007-03-21
forum: Networking &amp; Wireless
---

### Post by trico on 2007-03-21
I'm finding that certain file names and directory names aren't rendered properly when going from windows xp to Samba.  It has to do with case.  Here are some examples:

From my XP system to Samba on Ubuntu - 
If I create a directory ...
mkdir \\trico\win_data\ALLCAPS
and then say...
dir \\trico\win_data
I'll see ...
allcaps

Lower case, not upper case.

Likewise a file named ALLCAPS.pdf, when stored on Samba will be allcaps.pdf.  And a file named SOMECAPS123.pdf will be named somecaps123.pdf.

Curiously, the more complex renderings like BiCaps.pdf are rendered on Samba as BiCaps.pdf.

My question - is there a setting someplace in Samba to fix this?  I'd really rather that ALLCAPS in xp be rendered as ALLCAPS in samba.  Having it change like makes programming difficult.

trico

---

### Post by bernied on 2007-03-21
Is this what you're looking for (when all else fails, read the manual):
```

$ man smb.conf
...blah blah blah...
NAME MANGLING
       Samba supports name mangling so that DOS and Windows  clients  can  use
       files  that  don't  conform  to  the  8.3 format. It can also be set to
       adjust the case of 8.3 format filenames.

       There are several options that control the way mangling  is  performed,
       and  they  are  grouped  here  rather  than  listed separately. For the
       defaults look at the output of the testparm program.

       All of these options can be set separately for each service  (or  glob-
       ally, of course).

       The options are:

       case sensitive = yes/no/auto
          controls whether filenames are case sensitive. If they aren't, Samba
          must do a filename search and match on  passed  names.  The  default
          setting of auto allows clients that support case sensitive filenames
          (Linux CIFSVFS and smbclient 3.0.5 and above currently) to tell  the
          Samba server on a per-packet basis that they wish to access the file
          system in a case-sensitive manner (to support  UNIX  case  sensitive
          semantics).  No  Windows or DOS system supports case-sensitive file-
          name so setting this option to auto is that same as setting it to no
          for them. Default auto.

       default case = upper/lower
          controls  what the default case is for new filenames (ie. files that
          don't currently exist in the filesystem). Default  lower.  IMPORTANT
          NOTE:  This  option  will be used to modify the case of all incoming
          client filenames, not just new filenames if the options case  sensi-
          tive  =  yes,  preserve case = No, short preserve case = No are set.
          This change is needed as part of the optimisations  for  directories
          containing large numbers of files.

       preserve case = yes/no
          controls  whether new files (ie. files that don't currently exist in
          the filesystem) are created with the case that the client passes, or
          if they are forced to be the default case. Default yes.

       short preserve case = yes/no
          controls  if  new files (ie. files that don't currently exist in the
          filesystem) which conform to 8.3 syntax, that is all in  upper  case
          and  of  suitable  length,  are  created  upper case, or if they are
          forced to be the default case. This option can be used with preserve
          case  =  yes  to  permit  long filenames to retain their case, while
          short names are lowercased. Default yes.

       By default, Samba 3.0 has the same semantics as a Windows NT server, in
       that  it is case insensitive but case preserving. As a special case for
       directories with large numbers of files, if the case options are set as
       follows,  "case sensitive = yes", "case preserve = no", "short preserve
       case = no" then the "default case" option will be applied and will mod-
       ify all filenames sent from the client when accessing this share.
...blah blah blah
```

---

### Post by trico on 2007-03-21
Well.... yes.  That's what I'm looking for.

I looked at "man samba", not "man smb.conf".  (sigh)

From the description, what I'm trying to do should work - and it does on an ext3 partition.  If the share is pointing to a FAT32 partition, however, it's not working right.  

I guess I'll have to rethink my partitions.

trico

---

### Post by bernied on 2007-03-21
What is the fstab line for that partition? The problem might be there.
```
cat /etc/fstab | grep fat
```

---

### Post by trico on 2007-03-21
It's
UUID=4187-66F9  /media/hdd3     vfat     defaults,utf8,umask=007,gid=46 0      1

---

### Post by bernied on 2007-03-22
OK, this is a vague memory and maybe not true, but somewhere I heard that utf8 doesn't work well with fat filesystems. Try taking that option out.

---

### Post by trico on 2007-03-22
Tried it.  It didn't seem to make any difference.

Here's what I'm doing to test it.  From a Command Prompt on my XP system, I say...
rmdir \\trico\win_data\allcaps
mkdir \\trico\win_data\ALLCAPS
dir \\trico\win_data

And I check to see if it's reporting 'allcaps' or 'ALLCAPS' as the directory name.

Doing this on a ext3 file system results in ALLCAPS, while on a vfat file system I get allcaps.

trico

---

### Post by bernied on 2007-03-22
sorry, I'm out of ideas, for now. I might try to reproduce this, later.

---

### Post by trico on 2007-03-22
We've made a bit if progress, I think. 

I've realized that the problem doesn't have anything to do with samba.  It has to do with vfat.  You probably already knew that - and that's why you were asking about the fstab for the vfat.

So here's a simpler test with Samba out of the way ...

If I open a terminal window and go to a directory on the vfat drive, and say:
>mkdir ALLCAPS
>mkdir SomeCaps
>ls
allcaps SomeCaps

So the vfat is case insensitive, as it should be - but not case preserving, not all of the time,  As it also should be.

trico

---

### Post by trico on 2007-03-22
Yay! Success!

I downloaded the Kernel souce and found a description of the config information for vfat.  If I add shortname=winnt to the list of options for the vfat file system in the fstab - it fixes the problem.

As I played with the problem, I found that while mkdir ALLCAPS would produce a directory named allcaps, if I said mkdir ALLCAPSALLCAPS I would get a directory named ALLCAPSALLCAPS.  The problem was with names that were 8 characters or shorter.  

We can declare this problem solved.

trico

---

### Post by bernied on 2007-03-22
hooray!
So it was in the kernel and its handling of vfat filesystems, nothing that could be corrected using samba or mount options. It's good to learn eh?

---

### Post by trico on 2007-03-23
Yes, exactly - on both fronts.  :-)  

Though... all is not joyful here in Minnesota.  I am still experiencing a problem of apparant lower-casing of names by vfat.  It's in my 'production' code and I havn't figured out how to make it do it in a test case scenario yet.  

Whereas the earlier problem was with directory names being lowercased, this is with filenames being lowercased.  In both instances the problem is occuring with names that fit the original 8.3 format for DOS - but now the directories are fine and just the files are acting up.

Yet, when I try the same thing with a simpler test case - the file system is NOT changing the name to lower case characters.  Puzzeling.  It may be a bug somewhere in my program.  

trico

PS: The program in question is a Python backup program of my own design, making use of rsync.py from vivian desmet.  It's an rsync (semi) clone written in python that will run on XP.

---

