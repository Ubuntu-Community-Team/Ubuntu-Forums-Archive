---
title: "0 Space Left?"
date: 2011-05-16
forum: New to Ubuntu
---

### Post by Tsujimoto on 2011-05-16
Okay, I was downloading WoW today and it stopped after 28MB. I know that my Disk Drive has over 80GB left. Why is it saying that I have 0MB left? :confused:

---

### Post by Cfhs_1 on 2011-05-16
> **Tsujimoto said:**
> Okay, I was downloading WoW today and it stopped after 28MB. I know that my Disk Drive has over 80GB left. Why is it saying that I have 0MB left? :confused:

Can you provide more information about your setup? Do you have you /home on a separate partition?

---

### Post by tgm4883 on 2011-05-16
in a terminal do

```
df -h
```

Post the output here

---

### Post by Tsujimoto on 2011-05-16
> **Cfhs_1 said:**
> Can you provide more information about your setup? Do you have you /home on a separate partition?

Well, I have a C drive and a D drive. I put Ubuntu on my D drive and windows by default is on my C drive. Help any?

---

### Post by Tsujimoto on 2011-05-16
Maybe when I went to go install Ubuntu from the start, I only did a 17GB installation, could that be it?

---

### Post by tgm4883 on 2011-05-16
> **Tsujimoto said:**
> Maybe when I went to go install Ubuntu from the start, I only did a 17GB installation, could that be it?

Could be it. We could tell you if you posted the output of the command I posted.

---

### Post by drs305 on 2011-05-16
> **Tsujimoto said:**
> Maybe when I went to go install Ubuntu from the start, I only did a 17GB installation, could that be it?

Posting the requested command would be helpful.

Is this Wubi installation - within Windows? If so, your maximum size is determined when you set it up. It doesn't matter how much space you have on the rest of your drive.

The same thing applies to a normal installation, in that it doesn't matter how much space you have on your *drive*, only how much you have in the partition you are downloading to.

There are some options for dealing with this issue. The Wubi Wiki page discusses ways to resize the installation, although I don't know how easy it is.

For a normal installation, and even a Wubi setup, if the 'partition' or Wubi file should have lots of space remaining, you may have unemptied trash bins, large log files, or made a large backup on your / partition instead of an alternate partition. Here is a link for exploring these possibilities:
[http://ubuntuforums.org/showthread.php?t=1122670]("http://ubuntuforums.org/showthread.php?t=1122670")

---

### Post by Tsujimoto on 2011-05-16
Okay I did it in the terminal and I go this: (Pretty sure it was the installation) 




Filesystem            Size  Used Avail Use% Mounted on
/dev/loop0             17G   16G  8.2M 100% /
none                  1.5G  692K  1.5G   1% /dev
none                  1.5G  240K  1.5G   1% /dev/shm
none                  1.5G  220K  1.5G   1% /var/run
none                  1.5G     0  1.5G   0% /var/lock
/dev/sda3             112G   18G   94G  17% /host




So yeah, probably the installation size was 17GB,making the file system only 17GB.:guitar:

---

### Post by Tsujimoto on 2011-05-16
Well, it was the within Windows install.
Thanks for all your help. I'll just reinstall Ubuntu With a bigger partition. Thanks guys. <3

                         -Tsujimoto

---

### Post by tgm4883 on 2011-05-16
Yep, you installed it with a small partition. I consider it small because you don't have /home on it's own partitions, otherwise that is plenty of space for /

---

### Post by Tsujimoto on 2011-05-16
Well, now that I'm on Windows with Ubuntu uninstalled completetly, looking at the installation sizes, 30gb is the maximum. Is there ANY way possible, to make use of my WHOLE D drive?

---

### Post by compmodder26 on 2011-05-16
You can boot from the live CD and install ubuntu through that instead of using the Wubi installer inside windows.

---

### Post by 3rdalbum on 2011-05-16
> **Tsujimoto said:**
> Well, now that I'm on Windows with Ubuntu uninstalled completetly, looking at the installation sizes, 30gb is the maximum. Is there ANY way possible, to make use of my WHOLE D drive?

Yes, don't use the Windows installer. Instead, boot your computer from the Ubuntu CD (you might need to change a setting in your BIOS to get it to look at the CD drive before booting from the hard drive).

When you boot the CD you'll be given the option of whether you want to try Ubuntu or install Ubuntu. Choose Install. Follow the on-screen instructions to install Ubuntu to the hard disk that you want to install it to.

On Ubuntu there's no such thing as a "D drive"; that's an abstraction that MS-DOS and Windows use and it has no meaning here. To identify which hard disk is the correct one, have a look at the size that's reported in the Ubuntu installer. The 80 gigabyte one is the one you want to install to, from what I understand.

Note that this will first erase the hard disk that you're installing Ubuntu to (the 80 gigabyte one).

---

### Post by Tsujimoto on 2011-05-16
Alright cool. Up and running. Thanks to all. :)

                      -Tsujimoto:guitar:

---

### Post by Tsujimoto on 2011-05-16
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5              47G  2.8G   42G   7% /
none                  1.5G  700K  1.5G   1% /dev
none                  1.5G  240K  1.5G   1% /dev/shm
none                  1.5G  108K  1.5G   1% /var/run
none                  1.5G     0  1.5G   0% /var/lock


Yeah, booting from the cd instead of Windows installer definitely worked. You guys are awesome. Thanks!

                                -Tsujimoto :guitar:

---

