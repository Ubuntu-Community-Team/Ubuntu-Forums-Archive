---
title: "How to use chkrootkit"
date: 2009-04-15
forum: New to Ubuntu
---

### Post by mikodo on 2009-04-15
Hi,

 With chkrootkit installed into Hardy, how do I run it in sudo?

P.S, I think I have the answer, In sudo chkrootkit --help I found:

sudo chkrootkit -d

If you read this and know I am wrong, please direct me correctly.



Thanks,

mikodo

---

### Post by UbuntuNerd on 2009-04-16
look in this Thread: [http://ubuntuforums.org/showthread.php?p=7026113](http://ubuntuforums.org/showthread.php?p=7026113)

---

### Post by mikodo on 2009-04-16
Thank you for the reply on how to mark a thread as solved.

I did find out how to run chkrootkit from other sources.

sudo chkrootkit

From your direction to the thread I started earlier, the only thing I see is to run chkrootkit -help which provides:

-desktop:~$ chkrootkit -help
Usage: /usr/sbin/chkrootkit [options] [test ...]
Options:
        -h                show this help and exit
        -V                show version information and exit
        -l                show available tests and exit
        -d                debug
        -q                quiet mode
        -x                expert mode
        -r dir            use dir as the root directory
        -p dir1:dir2:dirN path for the external commands used by chkrootkit
        -n                skip NFS mounted dirs
 


From this I don't see how to update chkrootkit, can you tell me how?

Thank you for your interest,

mikodo

---

### Post by UbuntuNerd on 2009-04-17
to update in a terminal
```
sudo chkrootkit --update
```

---

### Post by egalvan on 2009-04-17
> **UbuntuNerd said:**
> to update in a terminal
```
sudo chkrootkit --update
```

Ran this on my system (Hardy 8.04.2) and got this:

```
$ sudo chkrootkit --update
Usage: /usr/sbin/chkrootkit [options] [test ...]
Options:
        -h                show this help and exit
        -V                show version information and exit
        -l                show available tests and exit
        -d                debug
        -q                quiet mode
        -x                expert mode
        -r dir            use dir as the root directory
        -p dir1:dir2:dirN path for the external commands used by chkrootkit
        -n                skip NFS mounted dirs

```

Is there another way to update chkrootkit?

Thanks

---

### Post by UbuntuNerd on 2009-04-17
I don't know of any other way but that doesn't mean there isn't another way.
 
I also read somewhere that you can create a cron script to update on a daily or weekly basis but Im not 100 percent sure

---

### Post by egalvan on 2009-04-17
> **UbuntuNerd said:**
> I don't know of any other way but that doesn't mean there isn't another way.
 

OK, sorry, I guess my question should have been...

does
```
sudo chkrootkit --update
```
work for you?

---

### Post by brian_p on 2009-04-17
> **egalvan said:**
> 

```
sudo chkrootkit --update
```
work for you?

checkroot does not have a --update option. So it cannot work.

---

### Post by mikodo on 2009-04-17
> **brian_p said:**
> checkroot does not have a --update option. So it cannot work.

I guess this is the answer.

Thanks,

Mikodo

---

### Post by eugenevdm on 2011-04-10
What's the verdict, how does one update chkrootkit?

---

### Post by Skorzen on 2011-04-10
> **eugenevdm said:**
> What's the verdict, how does one update chkrootkit?

Using a repository with the most recent version, or compiling from source:
[ftp://ftp.pangeia.com.br/pub/seg/pac/chkrootkit.tar.gz](ftp://ftp.pangeia.com.br/pub/seg/pac/chkrootkit.tar.gz)

---

