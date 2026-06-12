---
title: "Iomega Network Drive 320 Gb and Samba"
date: 2007-12-29
forum: Networking &amp; Wireless
---

### Post by luca.b on 2007-12-29
Hello. For Christmas I received an Iomega Home Network Drive (320 Gb model, MDHD320-N), which apparently shares its folder via Samba (I think it runs some embedded Linux).

I have been trying two methods to mount its shares in Linux, with mixed results:

a. Using cifs as filesystem I can't mount anything at all, since I get a kernel oops (whether this is related to the NVIDIA kernel driver - I have read a bug report about it - or not I don't know);
b. With smbfs I can actually mount the share but I can't transfer much to it. WHen I try, I get a hang in the application which tries to access and lines like these appear in the kernel log:

```
[ 1710.745455] smb_setup_bcc: Packet too large 7662 > 4096
```

After that I get timeouts on everything, like this:

```
[ 1740.705664] smb_add_request: request [d95b0200, mid=40] timed out!
```

I have tried googling about the problem or looking in bug reports, but I haven't got any clues. 
Can someone help? Thanks a lot!

---

