---
title: "Live USB problems"
date: 2010-11-11
forum: New to Ubuntu
---

### Post by kroq-gar78 on 2010-11-11
Hello Ubuntu Forums Community,

I have tried to run Ubutnu off of Live USB instead of live CD because of the greatly decreased boot times. I have two computers running two versions: desktop (10.10) and laptop (wubi 10.04). Whenever I boot a computer to usb (after burned iso to flash drive after burned on my desktop), it encounters an error saying it cant find some kernel image or something. When I use the same image on my laptop, it magically works. Any ideas on why this is happening?

Thanks in advance.

---

### Post by Hippytaff on 2010-11-12
How did you put the iso to usb?
 
also, is the Md5sum correct?
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by kroq-gar78 on 2010-11-13
the md5sum was fine.

I used startup disk creator on both computers. sorry; after re-reading my post, i don't think is was really clear. when i WROTE the iso to my flash drive using my desktop, it doesn't work. when i write the iso to the flash drive on my laptop, it works.

---

### Post by Hippytaff on 2010-11-13
ok...you need to use something like Unetbootin to make the flash drive bootable :-)
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

### Post by kroq-gar78 on 2010-11-16
shouldn't startup disk creator do the job anyway?

---

### Post by C.S.Cameron on 2010-11-16
I wonder if there could be a problem with your 10.10, (desktop's), version of USB creator???

The 10.10 version works for me but I have heard other people complain about it. You could check for updates.

---

### Post by kroq-gar78 on 2010-11-17
i don't see anything in the update manager or apt. Is there some other way of updating it?

---

### Post by Hippytaff on 2010-11-17
Did you try ```

sudo apt-get upgrade && sudo apt-get update

```

---

### Post by kroq-gar78 on 2010-11-17
yes and seems like a bunch of new updates came out in a day (32). I'll post back after I update. Also, after update, it prints this:

Fetched 2,403B in 2s (1,024B/s)
Reading package lists... Done
N: Ignoring file 'getdeb.list.bck' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
W: GPG error: [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release: The following signatures were invalid: BADSIG 16126D3A3E5C1192 Ubuntu Extras Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
Reading package lists... Done
Building dependency tree       
Reading state information... Done

what's the deal with the GPG error stuff?

EDIT: fixed the GPG stuff w/ this: [http://http://www.ubuntugeek.com/how-to-fix-the-ubuntu-gpg-error-badsig.html]("http://http//www.ubuntugeek.com/how-to-fix-the-ubuntu-gpg-error-badsig.html")

---

