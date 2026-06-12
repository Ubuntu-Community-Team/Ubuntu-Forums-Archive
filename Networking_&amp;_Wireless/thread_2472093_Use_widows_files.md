---
title: "Use widows files"
date: 2022-02-17
forum: Networking &amp; Wireless
---

### Post by torbentf on 2022-02-17
Hi,
I can list the Windows files I can access in Linux using NAUTILUS:

1.0 TB Volume
Documents on 192.168.110.11
    (smb://192.168.110.11/documents)
+ Other Locations
 
Under Documents on 192.168.110.11 I have a number of directories + the files I am interesrtd in.

I would like to write (fx):

ls smb://192.168.110.11/documents/HC12Sim1000.bas

but the file is no recognized.

Can anybody tell me how it should be done?
torben

---

### Post by CharlesA on 2022-02-17
Just to double check: Is the folder name Documents or documents? Linux is case sensitive, even if Windows is not.

---

### Post by Morbius1 on 2022-02-17
> smb://192.168.110.11/documents
That expression in nautilus creates a mountpoint at:
```
/run/user/$UID/gvfs/smb-share:server=192.168.110.11,share=documents
```

---

### Post by torbentf on 2022-02-17
Hi Morbius1,
This worked:

torben@torben-Aspire-E5-773G:/run/user/1000/gvfs/smb-share:server=192.168.110.11,share=documents$ cat HC12Sim1000.bas

I have been all over the net to find that with no result - how was I supposed to know?

It does not help that I in Windows have the data in two different directories with the same name and the same properties (which fits one of them) and which are both updated by my pgm.

Thank you very much.
torben

---

