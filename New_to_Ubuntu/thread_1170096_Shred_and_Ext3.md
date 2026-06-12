---
title: "Shred and Ext3"
date: 2009-05-25
forum: New to Ubuntu
---

### Post by echo314 on 2009-05-25
I understand that shred goes beyond a simple rm, by actually overwriting the data (instead of merely marking it as free space). However, I've read that it may be of limited usefulness on a journaling file system such as Ext3, because the file may be referenced to in other locations. Some articles I read indicated it had to do with some journal=data setting that is NOT on by default, but others indicated that on any Ext3 system shred was ineffective. 

I'd like probe this issue further, all comments and links are welcome. Thank you.

---

### Post by Boondoklife on 2009-05-25
Well I would think overwriting the data enough times would do just fine, assuming you are overwriting the entire disc, if you are instead just overwriting the freespace then I could see the possibility for an issue to arise. That said, If you are really worried about someone geting to your data, why not look into an encrypted volume, which in a worst case scenario you could overwrite and call it a day?

Big brother fanatics will tell ya to watch yourself either way, myself I just rely on the tinfoil hat I'm wearing and a good ol' sledge hammer out back for recovery prevention.

---

### Post by echo314 on 2009-05-25
First off, I meant to refer to shredding files, or at most directories with /dir/*

Second, I feel comfortable with encrypting files with GnuPG, but I have not yet get whole disk encryption down. Admittedly I have not looked into the issue for a few months, but there seemed to be too much software to choose from...TrueCrypt, something called LUKS or similar, GnuPG, I'm not sure how it all fits together.

---

### Post by doas777 on 2009-05-25
I've always been told that journaling file systems are a gold mine for a forensics specialist, so i've usually selected ext2 for drive that contain data that i might want to wipe.

---

### Post by Boondoklife on 2009-05-25
> **echo314 said:**
> First off, I meant to refer to shredding files, or at most directories with /dir/*

Second, I feel comfortable with encrypting files with GnuPG, but I have not yet get whole disk encryption down. Admittedly I have not looked into the issue for a few months, but there seemed to be too much software to choose from...TrueCrypt, something called LUKS or similar, GnuPG, I'm not sure how it all fits together.

I love TrueCrypt myself but go with what works best for you. Shredding is basically just that from my understanding, you are just repeatedly overwriting the area with random data. Kinda reminds me of that damn gateway program back in the day that write 0's to the drive to test it.

But as I said if you are just overwriting free space, this would include areas where the files were deleted then it is possible that there could be a remainder some where else. Best bet is to just look into a mountable truecrypt container and store your data there. then when you need to trash it, you simply trash what is in it as that should contain all of the data that had to do with it and leave your os un touched.

---

### Post by doas777 on 2009-05-25
> **maletek said:**
> Well I would think overwriting the data enough times would do just fine, assuming you are overwriting the entire disc, if you are instead just overwriting the freespace then I could see the possibility for an issue to arise. That said, If you are really worried about someone geting to your data, why not look into an encrypted volume, which in a worst case scenario you could overwrite and call it a day?

Big brother fanatics will tell ya to watch yourself either way, myself I just rely on the tinfoil hat I'm wearing and a good ol' sledge hammer out back for recovery prevention.

I heard once (heresay of course) that the mi6 specification for destruction of a hdd is to have it ground into dust, that is then exposed to strong magnetic feilds. after that it is locked in a mag-shielded box, and locked in a concrete bunker 40foot underground.

sounds kinda out there, but for comparision, i attended a security conference once, where a speaker from the NSA described how you might prepare a severed arm for use in bypassing fingerprint scanning sensors. the crux of the situation seemed to be that once you severed the arm, the blood loss would deform the thumb/finger. lol. these guys think of everything....

encryption is not a catch-all. most of the time, all that needs be done to break encryption is to find someone who knows the password, and apply some serious duress. the courts do it regularly. 
 
or you can just put on your tinfoil hat. mine is shiney!

---

### Post by unutbu on 2009-05-25
This is a quote from the shred man page:

```
The following are examples of file systems on which shred is not effective, or
is not guaranteed to be effective in all file system modes:

*  log-structured  or journaled file systems, such as those supplied with AIX and
Solaris (and JFS, ReiserFS, XFS, **Ext3**, etc.)

...

In the case of ext3 file systems, the above disclaimer applies (and shred is thus
of limited effectiveness) **only in data=journal mode**, which journals file data  in
addition to just metadata.  In both the data=ordered (default) and data=writeback
modes, shred works as usual.  Ext3 journaling modes can be changed by adding  the
data=something  option  to  the mount options for a particular file system in the
/etc/fstab file, as documented in the mount man page (man mount).

```
This seems to side with those who claim shred works fine with ext3 as long as the ext3 filesystem isn't mounted with the "data=journal" option.

---

### Post by doas777 on 2009-05-25
> **unutbu said:**
> This is a quote from the shred man page:

```
The following are examples of file systems on which shred is not effective, or
is not guaranteed to be effective in all file system modes:

*  log-structured  or journaled file systems, such as those supplied with AIX and
Solaris (and JFS, ReiserFS, XFS, **Ext3**, etc.)

...

In the case of ext3 file systems, the above disclaimer applies (and shred is thus
of limited effectiveness) **only in data=journal mode**, which journals file data  in
addition to just metadata.  In both the data=ordered (default) and data=writeback
modes, shred works as usual.  Ext3 journaling modes can be changed by adding  the
data=something  option  to  the mount options for a particular file system in the
/etc/fstab file, as documented in the mount man page (man mount).

```This seems to side with those who claim shred works fine with ext3 as long as the ext3 filesystem isn't mounted with the "data=journal" option.

Good looking out. +1.

---

### Post by Boondoklife on 2009-05-26
> **doas777 said:**
> I heard once (heresay of course) that the mi6 specification for destruction of a hdd is to have it ground into dust, that is then exposed to strong magnetic feilds. after that it is locked in a mag-shielded box, and locked in a concrete bunker 40foot underground.

sounds kinda out there, but for comparision, i attended a security conference once, where a speaker from the NSA described how you might prepare a severed arm for use in bypassing fingerprint scanning sensors. the crux of the situation seemed to be that once you severed the arm, the blood loss would deform the thumb/finger. lol. these guys think of everything....

encryption is not a catch-all. most of the time, all that needs be done to break encryption is to find someone who knows the password, and apply some serious duress. the courts do it regularly. 
 
or you can just put on your tinfoil hat. mine is shiney!

Hehe, well I personally love to see when the people in charge get paranoid cause the sky is the limit for them. true encryption is not a catch all but it can be a great tool if used correctly, plausible deniability =P

---

### Post by Paqman on 2009-05-26
There's a lot of paranoia that surrounds secure deletion. Bottom line is that on an Ubuntu system any utility that overwrites the data 2-3 times will render that data destroyed.

As mentioned above the default way that ext3 is set up does not prevent shred from working. Additionally, the default overwrite setting of 25 passes is overkill, and a complete waste of time. The guy who pretty much wrote the bible of secure deletion, Peter Gutmann said:

> 
In the time since this paper was published, some people have treated the 35-pass overwrite technique described in it more as a kind of voodoo incantation to banish evil spirits than the result of a technical analysis of drive encoding techniques.
<snip>
For any modern PRML/EPRML drive, a few passes of random scrubbing is the best you can do.


So go for a 3-pass shred and you can rest assured your data is gone.

---

### Post by Boondoklife on 2009-05-26
Oooo voodoo, is that part of the obeah man package? wonder if there is a voodoo command to resurrect lost souls er data heh.

---

