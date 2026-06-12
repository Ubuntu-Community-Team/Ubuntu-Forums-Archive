---
title: "grub rescue"
date: 2011-02-23
forum: New to Ubuntu
---

### Post by purplequark on 2011-02-23
Yes, I know, there are a thousand threads about 'grub rescue' and I swear I've searched them all.  Still stuck.

Had issues with ubuntu, issue was fixed but I ended up with three copies of Ubuntu on separate partitions on my machine.  I should have just left it alone but I didn't, I apparently deleted the partition that Grub was installed on while I was 'cleaning'. 

Now I boot my machine and get the error 'no such partition', then 'grub rescue>'
ls shows that my data is still there, (hd0,1) but I'm stuck.  Can't find the command to get this freaking machine to load my stuff :( 

I cannot boot from my live cd now, boot option set to boot from cd but it goes to the grub rescue prompt instead.  I can load from my windows cd but I don't have windows installed...  Tried to set boot to load from cd only (disabled hd) and it gives me a disk error .

Right now, it looks like my only option is to completely format my machine and reinstall windows.... thought I'd try you guys first, just in case...

---

### Post by Gixxy on 2011-02-23
What version of grub?

---

### Post by jeremyjjbrown on 2011-02-23
> **purplequark said:**
> Yes, I know, there are a thousand threads about 'grub rescue' and I swear I've searched them all.  Still stuck.

Had issues with ubuntu, issue was fixed but I ended up with three copies of Ubuntu on separate partitions on my machine.  I should have just left it alone but I didn't, I apparently deleted the partition that Grub was installed on while I was 'cleaning'. 

Now I boot my machine and get the error 'no such partition', then 'grub rescue>'
ls shows that my data is still there, (hd0,1) but I'm stuck.  Can't find the command to get this freaking machine to load my stuff :( 

I cannot boot from my live cd now, boot option set to boot from cd but it goes to the grub rescue prompt instead.  I can load from my windows cd but I don't have windows installed...  Tried to set boot to load from cd only (disabled hd) and it gives me a disk error .

Right now, it looks like my only option is to completely format my machine and reinstall windows.... thought I'd try you guys first, just in case...

Have you tried a different live cd?

---

### Post by purplequark on 2011-02-23
yes, I tried a new live cd.  It's grub2

---

