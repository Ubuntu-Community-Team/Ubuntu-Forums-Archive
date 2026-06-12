---
title: "File Systems"
date: 2009-06-26
forum: New to Ubuntu
---

### Post by carl_76 on 2009-06-26
Hi.

I'm switching from Windows to Ubuntu and I'm planning on encrypting the disk partitions during installation.  

Is it correct to assume that I have to use one of the linux partitions systems, such as ext3, for the disks?

If I want to email a file to someone using a Windows system do I have to de-encrypt it and convert the file system before sending it?

Thanks in advance for the help.

---

### Post by HavocXphere on 2009-06-26
I think you can also use FAT32 (i.e. windows readable).

I'd recommend going with ext3 or 4 though. (Makes sure you keep backups if you use ext4 as there have been reports of it going wrong in the past)

EDIT: Missed the encryption part. Not sure about that. For full disk encryption you'll need either dm-crypt or truecrypt. i.e 3rd party apps. Can't really comment on what they can and cannot do.

---

### Post by jerome1232 on 2009-06-26
When using full disk encryption all of your files are encrypted/de-crypted on the fly as they are being read/written to disk.

If you email a friend your file system has absolutely nothing to do with your friend being able to read the file. It's sent via network protocols that all computers involved understand (your computer, the servers/routers that route the message and your friends computer that finally receives it).

The only way file systems would matter is if you have say an external drive formatted as ext4 and copied a file from your computer on to it, then hooked the external drive up to a Windows computer.

The Windows computer won't understand how to read from the ext4 drive. If the drive was formatted as fat or ntfs you would be fine since both OS's know how to access these file systems.

The drive that you installing Ubuntu on it MUST be a native linux format (no ntfs or fat).

---

### Post by superprash2003 on 2009-06-27
take a look at [http://fs-driver.org/](http://fs-driver.org/) , if thats what you mean

---

