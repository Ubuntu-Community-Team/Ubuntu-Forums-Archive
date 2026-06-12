---
title: "Replacing Ubuntu on the same partition"
date: 2011-02-04
forum: New to Ubuntu
---

### Post by tokintmash on 2011-02-04
Hi,

I had XP and Ubuntu 10.04 32/bit on dual boot. I wanted to replace my current Ubuntu with 10.10 64/bit.

I chose the partition where 10.04 was installed. It was marked as "do not use this partition" I chose to format it but I was not sure what file format to choose, as there were many. So I chose "Ext4 journaling" and chose "/" as a mounting point.

So now when I boot I get a grub rescue error or something. Where did I go wrong?

Is there any way to fix this?

Cheers

mac

---

### Post by Paqman on 2011-02-04
> **tokintmash said:**
> 
I chose the partition where 10.04 was installed. It was marked as "do not use this partition" I chose to format it but I was not sure what file format to choose, as there were many. So I chose "Ext4 journaling" and chose "/" as a mounting point.

So now when I boot I get a grub rescue error or something. Where did I go wrong?


Sounds like you did exactly what you should have, but for some reason Grub didn't get installed. You might want to try [reinstalling Grub]("https://help.ubuntu.com/community/Grub2#Reinstalling GRUB 2").

---

### Post by tokintmash on 2011-02-04
Thank you!

---

