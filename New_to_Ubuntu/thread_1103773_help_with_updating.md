---
title: "help with updating"
date: 2009-03-23
forum: New to Ubuntu
---

### Post by searayman on 2009-03-23
I was doing a normal update in ubuntu for the kernal it looks liek but it wont update:

E: /var/cache/apt/archives/linux-image-2.6.27-7-generic_2.6.27-7.16_i386.deb: unable to make backup link of `./boot/vmlinuz-2.6.27-7-generic' before installing new version

any ideas?

---

### Post by iaculallad on 2009-03-23
What error displays when your issue the command below:

```
sudo apt-get update && sudo apt-get upgrade
```

?

---

### Post by searayman on 2009-03-23
> **iaculallad said:**
> What error displays when your issue the command below:

```
sudo apt-get update && sudo apt-get upgrade
```

?

The following packages will be upgraded:
  linux-image-2.6.27-7-generic
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory
mikejones@ubuntu:~$

---

### Post by iaculallad on 2009-03-23
Execute the terminal command below:

```
sudo pkill apt
```

Then:

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by blandman3 on 2009-03-23
if those codes don't work try re-booting ubuntu in recovery mode, and choose the dpkg option.  This should repair anything, and the update should update.

---

### Post by searayman on 2009-03-23
> **iaculallad said:**
> Execute the terminal command below:

```
sudo pkill apt
```

Then:

```
sudo apt-get update && sudo apt-get upgrade
```

I know got this:

Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-2.6.27-7-generic_2.6.27-7.16_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
mikejones@ubuntu:~$

---

### Post by GepettoBR on 2009-03-23
Maybe there was something wrong with the downloaded package?

Run ```
sudo apt-get clean && sudo apt-get update && sudo apt-get upgrade
```

btw I suggested apt-get because everyone else did, but I personally prefer using aptitude.

---

### Post by searayman on 2009-03-23
> **GepettoBR said:**
> Maybe there was something wrong with the downloaded package?

Run ```
sudo apt-get clean && sudo apt-get update && sudo apt-get upgrade
```

btw I suggested apt-get because everyone else did, but I personally prefer using aptitude.

again didnt work:

Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-2.6.27-7-generic_2.6.27-7.16_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
mikejones@ubuntu:~$

---

### Post by GepettoBR on 2009-03-23
Have you tried blandman's suggestion?

---

