---
title: "Grub won-t install"
date: 2011-03-18
forum: New to Ubuntu
---

### Post by perfecti0n on 2011-03-18
Hello!

I have a problem with recovering Ubuntu after installing Windows on another partition.
I followed the instructions on help.ubuntu.com but I ran into some problems.

After running
```
sudo grub-install --root-directory=/media/693f6e0d-709a-4edc-8ffd-70674b32df01 /dev/sda1

```I get
> 
/usr/sbin/grub-setup: warn: Attempting to install GRUB to a partition instead of the MBR.  This is a BAD idea..
/usr/sbin/grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and their use is discouraged..
/usr/sbin/grub-setup: error: if you really want blocklists, use --force.
I tried googling for some solutions but all the talk was a bit too advanced for me.
Mind that I have only been using Ubuntu for 2 months now.
I did, however, use the boot info script so I am attaching the results from that.

So my question is > Is there a solution for this or do I just run with the --force parameter and hope for the best?

---

### Post by Dutch70 on 2011-03-18
```
sudo grub-install --root-directory=/media/693f6e0d-709a-4edc-8ffd-70674b32df01 [COLOR="Red"]/dev/sda1[/COLOR]
```

Shouldn't the part in red have been /dev/sda, not /dev/sda1

---

### Post by perfecti0n on 2011-03-18
Worked like a charm :) I automatically put the sda1 there because I got that from the fdisk -l.

Thank you, mate!

---

### Post by Dutch70 on 2011-03-18
> **perfecti0n said:**
> Worked like a charm :) I automatically put the sda1 there because I got that from the fdisk -l.

Thank you, mate!

You're quite welcome. Glad to hear you got it working.

---

