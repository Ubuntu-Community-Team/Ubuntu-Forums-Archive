---
title: "Two hard drives, Ubuntu Studio, OSX, boot?"
date: 2009-03-20
forum: New to Ubuntu
---

### Post by [ARB1D3_[00L3R on 2009-03-20
Howdy folks! I haven't seenthis one, but if you have let me know.

I had a Ubuntu Studio machine sitting right next to my Mac OSx.

Ram died and I decided to pop my hard drive from the Ubuntu Studio
into my mac.

Here's the questions:

1) How do I dual boot?

2) I've seen an app that allows switching??? Seen it?

Thanks in advance, yall rule!

carbide cooler

---

### Post by Xiong Chiamiov on 2009-03-23
1. Point GRUB to your OSX partition, just as you would Windows.  There should be an entry in /boot/grub/menu.lst that you can modify.

2. You're probably thinking of either a [KVM](http://en.wikipedia.org/wiki/KVM_switch) or something like [VirtualBox](http://en.wikipedia.org/wiki/Virtualbox).

---

