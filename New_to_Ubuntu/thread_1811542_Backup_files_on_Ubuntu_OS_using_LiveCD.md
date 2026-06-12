---
title: "Backup files on Ubuntu OS using LiveCD"
date: 2011-07-25
forum: New to Ubuntu
---

### Post by freemankofi on 2011-07-25
Hi,
Not sure if it's possible or probably a stupid question.

I have an issue of booting my ubuntu 11.04 (64bit). I have read suggestions on how to fix a 'blank with cursor' issue which is my problem.

But before I start anything or probably re-install ubuntu, I WANT to BACKUP my current files on Ubuntu. Can I use LiveCD to do it? Please note that all suggestions are rather for window dead machine BUT my case is different from it since I am using **[COLOR="Red"]Ubuntu OS[/COLOR]**.

I am now downloading liveCD and want to make sure that it'll work before wasting my time on it.

Thanks in advance
Freeman

---

### Post by wildmanne39 on 2011-07-25
Hi, yes you can use a livecd to back up your files. You may have to open disk utility first and mount your ubuntu partitions then use these instructions to run nautilus in root so you will have permission to copy the files.

Livecd use a root

```
sudo -i nautilus
```
opens the root file browser window in the live cd, no password required.

---

### Post by amjjawad on 2011-07-25
> **freemankofi said:**
> Hi,
Not sure if it's possible or probably a stupid question.

I have an issue of booting my ubuntu 11.04 (64bit). I have read suggestions on how to fix a 'blank with cursor' issue which is my problem.

But before I start anything or probably re-install ubuntu, I WANT to BACKUP my current files on Ubuntu. Can I use LiveCD to do it? Please note that all suggestions are rather for window dead machine BUT my case is different from it since I am using **[COLOR="Red"]Ubuntu OS[/COLOR]**.

I am now downloading liveCD and want to make sure that it'll work before wasting my time on it.

Thanks in advance
Freeman

Any LiveCD will do the needful depends on what you really want.

Are you planning to create a clone to your system? or just copy your important files?

---

### Post by freemankofi on 2011-07-25
Thanks.

I am just Backing up my files unto an external drive (only important ones). I realised that I can run it(Ubuntu) on recovery 'failSafeX' mode hopefully, that will allow me to access external hard disk. I'll try that since currently my external drive isn't with the computer with an issue.

---

### Post by amjjawad on 2011-07-25
> **freemankofi said:**
> Thanks.

I am just Backing up my files unto an external drive (only important ones). I realised that I can run it(Ubuntu) on recovery 'failSafeX' mode hopefully, that will allow me to access external hard disk. I'll try that since currently my external drive isn't with the computer with an issue.

If all what you want is to copy your important file, then ANY LiveCD will do the needful, even [**SliTaz**]("http://www.slitaz.org/en/") one :)

Once you boot from the LiveCD, go to your /home and find your files there, unless you keep them some where else.

Good luck :)

---

