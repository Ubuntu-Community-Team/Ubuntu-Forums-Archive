---
title: "There is not enough room on the disk to save ... I have 5 gigs!!"
date: 2009-01-05
forum: New to Ubuntu
---

### Post by USFMD82 on 2009-01-05
What is going on I am trying to DL something from Firefox and am getting this error
"There is not enough room on the disk to save"
Any other ideas?

```
timber@ubuntu:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/host/ubuntu/disks/root.disk
                      3.5G  2.6G  757M  78% /
tmpfs                 186M     0  186M   0% /lib/init/rw
varrun                186M  212K  185M   1% /var/run
varlock               186M     0  186M   0% /var/lock
udev                  186M  2.7M  183M   2% /dev
tmpfs                 186M     0  186M   0% /dev/shm
/dev/sda2             9.8G  4.4G  5.4G  45% /host
lrm                   186M  2.4M  183M   2% /lib/modules/2.6.27-9-generic/volatile
/dev/sda1              65G   48G   18G  73% /media/windows
overflow              1.0M  1.0M     0 100% /tmp
timber@ubuntu:~$ 

```

---

### Post by TransitMan on 2009-01-06
How large is the file that you want to download?

---

### Post by jerome1232 on 2009-01-06
> **USFMD82 said:**
> What is going on I am trying to DL something from Firefox and am getting this error
"There is not enough room on the disk to save"
Any other ideas?

```
timber@ubuntu:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/host/ubuntu/disks/root.disk
                      3.5G  2.6G  757M  78% /
tmpfs                 186M     0  186M   0% /lib/init/rw
varrun                186M  212K  185M   1% /var/run
varlock               186M     0  186M   0% /var/lock
udev                  186M  2.7M  183M   2% /dev
tmpfs                 186M     0  186M   0% /dev/shm
/dev/sda2             9.8G  4.4G  5.4G  45% /host
lrm                   186M  2.4M  183M   2% /lib/modules/2.6.27-9-generic/volatile
/dev/sda1              65G   48G   18G  73% /media/windows
overflow              1.0M  1.0M     0 100% /tmp
timber@ubuntu:~$ 

```

Depends where are you saving it to?

Your root partition only has 757 MB's free, your windows partition mounted under /host has 5.4 GB's free.

--edit--- and your, what is that, a data drive? /media/windows has 18 GB's of free space try saving the file there.

So if your saving this file to /host/somefolder then yes you should have plenty of free space, but if your saving it to anywhere else you have very little free space left.

---

### Post by USFMD82 on 2009-01-06
I was saving to the desktop, the file was prolly a few megs no more then 10 for sure. How do i make my Desktop have more capacity? Mozilla defaults saving files to the desktop

---

### Post by markp1989 on 2009-01-06
```
overflow              1.0M  1.0M     0 100% /tmp 
``` 

your tmp is filled up, i had a similar problem when i had my tmp in ram, i increased the size, and it stoped the problem .

---

### Post by jerome1232 on 2009-01-06
You would have to expand your virtual wubi disk.

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

[https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20resize%20the%20virtual%20disks?](https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20resize%20the%20virtual%20disks?)

You need lvpm do to it, you may need to free up some space to install lvpm on that full root partition.

Also as a temporary workaround you can just change mozilla's default save location so that's it landing on one of your real partitions that have plenty of free space.

I will point out that you will start running into problems with so little free space on your root partition, you may want to look into expanding it.

---

### Post by avtolle on 2009-01-06
It appears the OP is using a Wubi install. Thus, how large is the virtual disk created under Wubi for the Ubuntu install? Also, while FF does download by default to the desktop, it seems to me that the download may go initially to the tmp directory, which is full. Not a solution, but some observations.

---

### Post by USFMD82 on 2009-01-06
How do I clear my TMP, and I haven't had a chance to check those links yet, but I assume they will allow me to make my TMP larger? Is there anything specific to Xubuntu needed for any of this?

---

### Post by Paqman on 2009-01-06
> **USFMD82 said:**
> How do I clear my TMP

It gets cleared every time you boot. As long as you have free space on your root partition then /tmp shouldn't run out of space (assuming you're mounting /tmp to the same place as /, ie: you aren't mounting it in your RAM)

---

### Post by USFMD82 on 2009-01-09
3.5G  2.6G  757M  78% /
Is this the part that is the desktop? I am confused, I am assuming here.. when I installed ubuntu, I did 4 gb install on a 10GB partition, im guessing the 757 m is all I have left for /. is / the desktop?

because now my explorer is only saying I have 65 mb left free, and I haven't done anything to equal even a gig since i started working on this.. is there a file search option that can show me the files all added over the last few days or files over a certain size or even files by name?

---

