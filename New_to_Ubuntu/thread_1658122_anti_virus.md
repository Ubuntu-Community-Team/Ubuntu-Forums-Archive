---
title: "anti virus"
date: 2011-01-02
forum: New to Ubuntu
---

### Post by Karlof on 2011-01-02
Hi forum

I get very confused regarding antivirus for linux

Some experts say you must have antivirus ,others you dont
 
as a newbie, what am I to do to really protect my system.

---

### Post by bioterror on 2011-01-02
> **Karlof said:**
> Hi forum

I get very confused regarding antivirus for linux

Some experts say you must have antivirus ,others you dont
 
as a newbie, what am I to do to really protect my system.

You need Antivirus on linux only for the Windows Partitions if you have them, so that you can scan and keep 'em clean.

Otherwise: No need to worry.
[https://help.ubuntu.com/community/Linuxvirus]("https://help.ubuntu.com/community/Linuxvirus")

---

### Post by expatCM on 2011-01-02
If you forward a lot of jokes to Windows users ....  be nice, kill the virus payload.  If not ....  no major concern.

---

### Post by gmenfan83 on 2011-01-02
> **expatCM said:**
> If you forward a lot of jokes to Windows users ....  be nice, kill the virus payload.  If not ....  no major concern.
what would be a good program to scan something we would send or share prior to sending?Also can they be set to auto-scan so we wouldnt have to remember to do so?

---

### Post by expatCM on 2011-01-02
This article may help you out.
[https://help.ubuntu.com/community/Antivirus](https://help.ubuntu.com/community/Antivirus)

None are perfect at all.  AVG Free may be good but only because they keep their definitions well updated and have a good research team.

---

### Post by howefield on 2011-01-02
> **expatCM said:**
> AVG Free may be good but only because they keep their definitions well updated and have a good research team.

But doesn't have a GUI - it's command line driven. Not that that's a bad thing, just pointing it out for those who may be unaware.

---

### Post by Paqman on 2011-01-02
You already have an excellent antivirus package installed. It's called the Linux kernel.

Just make sure your machine is kept up-to-date with security updates and you won't have to worry about viruses.

---

### Post by theozzlives on 2011-01-02
I like clamav for scanning Windows machines, alas, it also command line driven.

---

### Post by gmenfan83 on 2011-01-02
> **theozzlives said:**
> I like clamav for scanning Windows machines, alas, it also command line driven.
i installed clamav daemon just for the fact that i like to be able to not possibly share and infect with a windows user....what woul;d be the command through clamav to scan for windows machine??

---

### Post by matt_symes on 2011-01-02
Hi

[https://help.ubuntu.com/community/ClamAV](https://help.ubuntu.com/community/ClamAV)

You will be looking at something along  the lines of

```
clamscan -r /path/to/windows/partition
```

Kind regards

---

