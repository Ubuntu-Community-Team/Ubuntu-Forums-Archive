---
title: "dual boot: overwriting ubuntu with a different version"
date: 2011-06-17
forum: New to Ubuntu
---

### Post by mushypeas on 2011-06-17
I have Win 7 and dual booted with Natty.

Natty's sound wasn't working so I have overwritten with ubuntu 10.04 but grub menu a mess. 

When I overwrite with an install; which partitions should I delete? all apart from windows? Just the existing ubuntu one? the swap one too? etc?

Thanks in advance

---

### Post by nzjethro on 2011-06-17
> **mushypeas said:**
> I have Win 7 and dual booted with Natty.

Natty's sound wasn't working so I have overwritten with ubuntu 10.04 but grub menu a mess. 

When I overwrite with an install; which partitions should I delete? all apart from windows? Just the existing ubuntu one? the swap one too? etc?

Thanks in advance

First up, back-up everything important. Even if you everything right, there's a chance of losing stuff.
What you delete is up to your preferences and your setup. Obviously delete your natty / partition, and delete your natty /swap too. If you have a /home partition separate from /, you can keep that, and let 10.04 use it as the /home partition, or else you can back up and wipe it, and let 10.04 create a new one. If you don't have a separate /home partition, save everything you want from /, and wipe everything (apart from windows, don't touch windows).

Don't forget, when you finish installing, run
```
update-grub
```
This will re-write your grub.cfg, and thus your Grub menu won't be a mess, and you will be able to boot properly.

---

### Post by wildmanne39 on 2011-06-17
Hi, if you do a complete install including installing grub then you should not have to run
```
sudo update-grub
```

---

### Post by _0R10N on 2011-06-17
I don't think that deleting the partitions should be required. Just reinstall over the existing partition and that's it. As an additional step, he/she may try formatting the natty partition.

---

### Post by mushypeas on 2011-06-18
I have a partition on sda 1 with 104mb. Any idea what that is? Windows r ubuntu? I have my 400gb windows partition and have deleted swap and ubuntu partition but not sure whether to delete this 104mb one?

Thanks in advance

---

### Post by wildmanne39 on 2011-06-18
> **mushypeas said:**
> I have a partition on sda 1 with 104mb. Any idea what that is? Windows r ubuntu? I have my 400gb windows partition and have deleted swap and ubuntu partition but not sure whether to delete this 104mb one?

Thanks in advance
Hi, I figure that is your boot partition for windows but lets be sure  post the information from this script so we can see where everything is located:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans

Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.

---

### Post by Elfy on 2011-06-18
> **_0R10N said:**
> I don't think that deleting the partitions should be required. Just reinstall over the existing partition and that's it. As an additional step, he/she may try formatting the natty partition.

This.

Mucking about with 100Mb partition is probably a waste of time - unless you've run out of primary partitions. 

In future if you want to reinstall over the top of an existing install - choose Advanced/Manual/Something Else (or whatever the devs have decided to call it this time around) - pick your partition - change or edit it - format and put / as the mountpoint. Done

In addition if you _don't_ have a _seperate_ /home partition then don't format and your home will be safe. (At least that was the current way)

---

### Post by mushypeas on 2011-06-18
thanks. worked great. Ubuntu 10.04 LTS 64 bit working like a dream on desktop and Natty 32 bit working like a dream on netbook

---

