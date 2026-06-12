---
title: "Boot from a second Hard Drive Help needed"
date: 2010-11-01
forum: New to Ubuntu
---

### Post by Peterfc on 2010-11-01
I made the mistake of installing via Wubi. I have tried for days to remove Ubunut Via the Wubi.
 
I have tried to use Partition Magic to partition my hard drive but when i reboot Partition Magic says error message 501 cross linked files found.

I have tried with a live CD to use Gparted to partition the hard drive. I get a message saying to run Chkdsk/F. This time i get error message 1083.

Instead of trying to sort this all out i only use my machine for Accounts and Payroll. 

Is there a way i can run Ubuntu from a second Hard Drive. I have a 40GB drive that normally is used for Data storage.

I have looked at the search for Second Hard Drive but found no answer.

Thanks for reading my plea for help.

---

### Post by stromdal on 2010-11-01
I'm not entirely sure that I understand your problem, please clarify.

Do you have Win and Ubuntu installed now? Do you want to remove Ubuntu and just run Windows? Or du you only have Ubuntu and want to install it on a different drive?

---

### Post by Peterfc on 2010-11-01
> **stromdal said:**
> I'm not entirely sure that I understand your problem, please clarify.

Do you have Win and Ubuntu installed now? Do you want to remove Ubuntu and just run Windows? Or du you only have Ubuntu and want to install it on a different drive?

Hi Sorry for not being to clear i have removed Ubuntu with "add and remove" from the Control panel but it has left behind some files. 

wubildr.mbr
wubildr
Dir Ubuntu
Dir Winboot
uninstall-wubi



I would need to leave windows as it is due to programs i need to run. 

All i want is a machine i can use can use and using my D Drive is an option i would like to use but it's how do i do that.

Thanks for your reply

---

### Post by oldfred on 2010-11-01
This is lucid but the process is similar.

Dual boot 2 drives, windows & Lucid 10.04
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)

[http://news.softpedia.com/news/Installing-Ubuntu-10-10-160966.shtml](http://news.softpedia.com/news/Installing-Ubuntu-10-10-160966.shtml)
Maverick partition by hand to use free space:
[http://sites.google.com/site/easylinuxtipsproject/partitioning](http://sites.google.com/site/easylinuxtipsproject/partitioning)
[http://www.dedoimedo.com/computers/ubuntu-maverick.html](http://www.dedoimedo.com/computers/ubuntu-maverick.html)

You will want to be sure to install the grub boot loader to sdb not sda. But the new Maverick only gives that choice on manual install. So it is better to manually partition.

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Install with creating partitions screen shots
[http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)

---

