---
title: "Formatting in general"
date: 2009-11-22
forum: New to Ubuntu
---

### Post by LinuxFox on 2009-11-22
I hope this is the correct forum to ask this, it's more of a general question about formatting.  I remember formatting an old MP3 player that's like a USB stick.  I want to know if formatting it completely erases everything, or does it leave files hidden away.

I was talking to a friend about formatting today, and I found out hard drives leave traces of data hidden after formatting, and I wanted to know if this is true for flash devices like USB sticks or MP3 players.

---

### Post by wilee-nilee on 2009-11-22
> **LinuxFox said:**
> I hope this is the correct forum to ask this, it's more of a general question about formatting.  I remember formatting an old MP3 player that's like a USB stick.  I want to know if formatting it completely erases everything, or does it leave files hidden away.

I was talking to a friend about formatting today, and I found out hard drives leave traces of data hidden after formatting, and I wanted to know if this is true for flash devices like USB sticks or MP3 players.

Be very careful with this if the firmware is MScentric you may lose the device altogether this happened to me with a mp3 player.

I have never owned a USB device yet that didn't have something that couldn't be removed, sometimes it is of no importance other times it is.

---

### Post by Locke_99GS on 2009-11-22
Formatting erases/changes the partition tables on a drive, leaving the data in tact. You can't normally get to this data after formatting without some forensic tools. If you want the data to be completely gone, it needs to be "shredded", where the space is written over numerous times with 1's, 0's, or random data before being deleted.Data removed in this method cannot be retreived.

---

### Post by wilee-nilee on 2009-11-22
> **Locke_99GS said:**
> Formatting erases/changes the partition tables on a drive, leaving the data in tact. You can't normally get to this data after formatting without some forensic tools. If you want the data to be completely gone, it needs to be "shredded", where the space is written over numerous times with 1's, 0's, or random data before being deleted.Data removed in this method cannot be retreived.

Some are locked up and can't be removed, or over written without some serious voodoo that I have no knowledge of.

---

### Post by LinuxFox on 2009-11-22
> **Locke_99GS said:**
> Formatting erases/changes the partition tables on a drive, leaving the data in tact. You can't normally get to this data after formatting without some forensic tools. If you want the data to be completely gone, it needs to be "shredded", where the space is written over numerous times with 1's, 0's, or random data before being deleted.Data removed in this method cannot be retreived.Ok thanks, just the discussion I had today got me wondering about this.

wilee-nilee, thanks for the warning, but I don't have to worry.  The player uses no firmware.  Like it's like a flash memory stick.

---

### Post by Cheesemill on 2009-11-22
> **Locke_99GS said:**
> Formatting erases/changes the partition tables on a drive, leaving the data in tact. You can't normally get to this data after formatting without some forensic tools. If you want the data to be completely gone, it needs to be "shredded", where the space is written over numerous times with 1's, 0's, or random data before being deleted.Data removed in this method cannot be retreived.

You don't need to overwrite it several times, just one pass of 0's will leave it unrecoverable.

---

