---
title: "Inatalation"
date: 2009-08-09
forum: New to Ubuntu
---

### Post by ventma on 2009-08-09
I have a hard disc partitioned by windows: C & D; may I installed Ubuntu in D?, if not how may I installed it keeping both OS?
May I installed Ubuntu from a memory device?

---

### Post by Nburnes on 2009-08-09
If your new to Ubuntu why not try it out in Wubi first?

It installs Ubuntu into virtual disks so there is no partitioning or anything. Its quite good grounds to get started on.

[www.wubi-installer.org](www.wubi-installer.org)

---

### Post by ventma on 2009-08-10
> **ventma said:**
> I have a hard disc partitioned by windows: C & D; may I installed Ubuntu in D?, if not how may I installed it keeping both OS?
May I installed Ubuntu from a memory device?

I am not new, I am using ubuntu as my OS in my PC, but now I have bought a laptop and I would like to keep using ubuntu. I just want a reply to my questions if it's possible, it's so difficult?.

---

### Post by ubudog on 2009-08-10
> **ventma said:**
> I have a hard disc partitioned by windows: C & D; may I installed Ubuntu in D?, if not how may I installed it keeping both OS?
May I installed Ubuntu from a memory device?

Yes.  In the "partitioner" on the live cd, you can choose to install it on that partition.  :)

---

### Post by Schendje on 2009-08-10
You can also boot into the Live CD first, then use GParted to delete the D: partition.

Then, install it on the empty space where D: was, that way you can have an ext3/ext4 filesystem.

At least that's what I would do.

---

### Post by kansasnoob on 2009-08-10
> **Schendje said:**
> You can also boot into the Live CD first, then use GParted to delete the D: partition.

Then, install it on the empty space where D: was, that way you can have an ext3/ext4 filesystem.

At least that's what I would do.

What makes you think D is empty?

---

### Post by kansasnoob on 2009-08-10
> **ventma said:**
> I have a hard disc partitioned by windows: C & D; may I installed Ubuntu in D?, if not how may I installed it keeping both OS?
May I installed Ubuntu from a memory device?

You're making that very hard to understand.

Are C & D each home to different Windows OS's?

Or is one for data?

Or for a restore partition?

Simply not enough info. And yes it's important enough that there is no "one size fits all" answer!

---

### Post by Schendje on 2009-08-10
> **kansasnoob said:**
> What makes you think D is empty?
Well I wasn't sure, but all this talk about "installing in that partition" made me think he wanted to get rid of D: and simply use it entirely for Ubuntu.

Could be really wrong though. :P

---

### Post by ventma on 2009-08-16
> **kansasnoob said:**
> You're making that very hard to understand.

Are C & D each home to different Windows OS's?

Or is one for data?

Or for a restore partition?

Simply not enough info. And yes it's important enough that there is no "one size fits all" answer!

[COLOR="Purple"][/COLOR]
[COLOR="Purple"]
D is for data, Windows OS is in C.
My other question was: may I install it from a flash memory, I have no CD reader in my notebook

---

### Post by ventma on 2009-08-16
> **ubudog said:**
> Yes.  In the "partitioner" on the live cd, you can choose to install it on that partition.  :)

Thank you very much. I have no reply to my other question: may I install it from a flash memory? I have no CD reader in my notebook

---

### Post by harry2006 on 2009-08-16
yeh, you can boot to the live version and then install right from the desktop...

---

### Post by Megaptera on 2009-08-16
Is this of any help?
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by camaron1 on 2009-08-16
> **ventma said:**
> Thank you very much. I have no reply to my other question: may I install it from a flash memory? I have no CD reader in my notebook

Yes, follow this link: [https://help.ubuntu.com/community/Installation/FromUSBStick]("https://help.ubuntu.com/community/Installation/FromUSBStick")

---

