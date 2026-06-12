---
title: "How can I format the whole system to NFTS?"
date: 2010-07-06
forum: New to Ubuntu
---

### Post by WILL_CHAN on 2010-07-06
Hello everyone,
My laptop originally came with Window Vista pre-installed, then I completely formatted it to install Ubuntu. So now I only have one drive. The thing is that now I just bought a new PC and I want to sell this one to my brother but I can't reformat it back to NFTS so that I can install Windows 7.
I tried to google and install 
```
sudo apt-get install gparted ntfsprogs
```
But when I started gparted, the option "format" was unavailable. And it makes sense to me 'cause as I understand the current drive cannot format itself.
So is there a solution to this problem? 
Thanks,

---

### Post by Zzl1xndd on 2010-07-06
During the Windows install process it will let you reformat the drive. Just pop in the disk and start installing.

---

### Post by HermanAB on 2010-07-06
If Windows tells you that the disk is corrupted and won't install, then overwrite the first part of the disk with zeroes.  Boot off a Live CD, then do:

# dd if=/dev/zero of=/dev/sda bs=1000, count=1000

The disk will then appear to be blank and Windows will complain no more.

---

### Post by stmiller on 2010-07-07
Yeah don't try to do it in Ubuntu. 

During the Windows install Windows will see that drive and let you format it then.

---

### Post by WILL_CHAN on 2010-07-21
Hi guys,
Sorry for late reply since I have to wait for my order( the adapter ). Now I can turn my laptop on again. The problem is when I launched to the Installation part using Live CD:
1. Configuration Windows - DONE
2. Installing Windows - error : it shows me 2 drives:
```

Disk Partition 1  287.0 GB  Primary
Disk Partition 2  11.0 GB   Logical 

``` 
When I click on "advance drive option". It shows me 6 options :
1. Refresh
2. Delete
3. Format
4. New
5. Load Drive
6. Extend

And only 2 options are available, they are "Delete" and "Refresh". So what can I do now?

Thanks,

---

### Post by WILL_CHAN on 2010-07-21
Hi,

Got it solved ;). Delete -> New -> Format ;) ! Thanks a lot for all your guys help.

Thanks,

---

