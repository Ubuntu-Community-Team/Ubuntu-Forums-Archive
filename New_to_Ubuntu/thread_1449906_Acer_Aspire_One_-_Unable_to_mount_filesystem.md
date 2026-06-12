---
title: "Acer Aspire One - Unable to mount filesystem"
date: 2010-04-08
forum: New to Ubuntu
---

### Post by Little Blue on 2010-04-08
Hi,

I've been running 9.10 UNR on my ZG5 SSD acer aspire one since about christmas (the laptop itself is about a year old), and its been working great, but today its stopped booting properly.

Specifically, it boots, performs a fsck, and drops into a maintenance shell reporting the mount of the file system failed. It still mounts the file system in a read only state though. Booting onto a usb live disk works fine, and I can mount the ssd drive perfectly fine, read-write and everything (albeit sudo'd as I'd expect I guess).

This implies to me a reinstall should fix this issue, but I'd prefer not having to reinstall until after lucid. Any idea if there's a way I can track down the exact cause and fix without having to reinstall or is that more or less the only way?

As an aside, it did get a slight shock from the mains plug socket when I was unplugging it earlier today (it was in a very stiff extension rack with no independent switches, so effectively struggled to pull it out of a live socket...), since ssd's are supposedly very sensitive to power spikes (from what I've heard anyway) is this likely to have caused any of this?

Many thanks.

---

### Post by TeoBigusGeekus on 2010-04-08
Any specific messages from the fsck?

---

### Post by cogier on 2010-04-08
Once you are dropped into a maintenance shell try running fsck from there. This fixed a problem I had when the BIOS battery died. I think it is something to do with fsck running on an unmounted disk.

---

### Post by Little Blue on 2010-04-08
> **TeoBigusGeekus said:**
> Any specific messages from the fsck?
it didn't raise anything, nor is there anything in /var/log/fsck (though if it weren't mounted during those boot up fsck's perhaps there wouldn't be anyway)

> **cogier said:**
> Once you are dropped into a maintenance shell try running fsck from there. This fixed a problem I had when the BIOS battery died. I think it is something to do with fsck running on an unmounted disk.
hmm, trying that I get messages about unconnected directory inodes, wrong ref counts, wrong free blocks count (I feel a google search coming to try and work out what these messages mean), and then on reboot it boots up fine!

ok, thank you so much! Worked a treat!

I wonder why it happened though since its fsck'd before during bootup with no issues...

---

### Post by cogier on 2010-04-09
I am glad it worked for you. I think that that the system mounts the disk and does a fsck which is hampered by the fact it is mounted. When you are dropped into a shell the disk is no longer mounted and fsck can do more.

---

