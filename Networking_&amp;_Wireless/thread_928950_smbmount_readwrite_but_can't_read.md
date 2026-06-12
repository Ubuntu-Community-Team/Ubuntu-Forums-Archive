---
title: "smbmount read/write but can't read ?"
date: 2008-09-24
forum: Networking &amp; Wireless
---

### Post by Tex-Twil on 2008-09-24
Hello,
I reinstalled my OS and I'm trying to set up again my samba client mount. Before it worked fine. The problem is that I mount the samba correctly, I can access it but I can't copy the files from it:

```

igloo ~ # smbmount //ap/usb /extra/  -o guest,noperm,rw,uid=jan

igloo ~ # ll /extra/
total 8776
drwxrwxrwx 1 jan users       0 2008-07-01 22:38 backup
drwxrwxrwx 1 jan users       0 2008-09-24 11:28 beamer
drwxrwxrwx 1 jan users       0 2008-06-15 16:06 bin
drwxrwxrwx 1 jan users       0 2008-07-05 22:06 capture
drwxrwxrwx 1 jan users       0 2008-07-04 16:21 Download
drwxrwxrwx 1 jan users       0 2008-07-04 18:59 etc
drwxrwxrwx 1 jan users       0 2008-06-14 15:35 openwrt
drwxrwxrwx 1 jan users       0 2008-09-11 09:53 public
drwxrwxrwx 1 jan users       0 2008-06-20 22:27 root

```


and then I try to copy:

```

jan@igloo ~ $ cp /extra/Themes/OSX_Cursors_v0.2TMP.tar.gz .
cp: cannot open `/extra/Themes/OSX_Cursors_v0.2TMP.tar.gz' for reading: Permission denied

```

Even if I try as a root it doesn't work. 

From the server side it should be ok 'cos I havent changed the settings and it was working before the reinstallation.

Thanks,
tex

---

