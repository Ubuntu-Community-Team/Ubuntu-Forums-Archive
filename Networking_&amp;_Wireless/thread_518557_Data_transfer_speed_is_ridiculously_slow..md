---
title: "Data transfer speed is ridiculously slow."
date: 2007-08-06
forum: Networking &amp; Wireless
---

### Post by applegrew on 2007-08-06
I am using Kubuntu Feisty Fawn. It is fully updated (I have backports enabled). My laptop's config is...
Intel Centrino Duo
HD 100GB (partitioned into 3 parts - the 3rd hosts Linux)
My NIC is well supported by ubuntu. It is running at 100Mbps (as it should). (Make: Intel PRO/100 VE)
Below is the output of
```
sudo hdparm -tT /dev/sda
```
output
```
/dev/sda:
 Timing cached reads:   2132 MB in  2.00 seconds = 1066.13 MB/sec
 Timing buffered disk reads:  120 MB in  3.05 seconds =  39.41 MB/sec

```

_Now the problems:-_
During data transfer through LAN (either directly connected to the other computer or through switches and hubs), the data transfer rate is very very very dismal.:mad: The data transfer rate starts at around 2MBps then it swiftly decreases to 60kBps and even less. For example yesterday I tried to transfer 1.8GB of data and it took 2+ hrs just to complete 60% and it said that another 3hr is left!! I had to cancel the transfer. Never ever in Windows I faced such ridiculous speed.

What's more the data transfer rate from one drive to another on the same computer takes around twice as much time in Kubuntu as it would take in Windows.

I have seen similar threads in this forum and the from the replies it seems everybody considers it a network problem. I am pretty sure it is not. Could it be driver problem? Pls help! I don't want to switch back to Windows.[-o<

---

### Post by noob12 on 2007-08-06
Is this in Nautilus via a Samba connection?

---

### Post by applegrew on 2007-08-06
> **noob12 said:**
> Is this in Nautilus via a Samba connection?
It is Konqueror via Samba

---

### Post by applegrew on 2007-08-06
> **noob12 said:**
> Is this in Nautilus via a Samba connection?

It is Konqueror via Samba.

---

### Post by applegrew on 2007-08-06
somebody help!

---

### Post by noob12 on 2007-08-06
Can you try a transfer, of about 100MB, using **smbget** or using **smbclient** and see if the behavior is significantly different?

---

### Post by applegrew on 2007-08-06
i tried smbget. It gave an avarage speed of 6-7 MBps. What's more I tried copying the same file again using Konqueror and got avg speed of 5-6 MBps. It's acting ok now, but I am sure it wil act weird again.

---

### Post by najames on 2007-08-11
Thanks for posting this.  I was actually considering switching from Feisty Ubuntu to Kubuntu because I also have this exact same problem in Ubuntu.  File transfers on Samba shares using Nautilus drag and drop are at 20-200KB per second, stopping often, with tons of resent packages it looks like.  It takes more than a hour to transfer a dozen mp3s.

If I use the smbget command, I can transfer a 671MB CD ISO in under 2 minutes to the same PC. 

Something is definately broken here.

Maybe try using another smb GUI client and see if it works, like Komba2 for example.

UPDATE:
I have installed pyneighborhood kinda sort like here: 
[http://grumpymole.blogspot.com/2006/11/xubuntu-browsing-samba-shares-with.html](http://grumpymole.blogspot.com/2006/11/xubuntu-browsing-samba-shares-with.html)

Installed mc , also known midnight commander (wow, flashback to Windows 3.0-3.1)

I reconfigured the output directory to /home/username/transfers and set permissions to allow R/W for anyone.  I had to do the sudo commands to allow it to run as root.  Now all my shares were connected and mounted in the nice GUI.  If I right click on the shared LAN share directory on my server a really ancient looking interface pops up (mc) and I could kinda point and click to do transfers.  Speed is nowhere near smbget, but it is MUCH faster than using Natilus, maybe 2MB per second instead of the 8-200KB per second in Nautilus.  There needs to be a better user interface, this one sucks, it sometimes gets blocky overwrites where you can't see the screen, and may lock up.  I could actually live with this IF there was a decent interface like the pyneighborhood GUI.  More researching.

---

### Post by applegrew on 2007-08-11
I will try your pointed you software, but if smbget is the fastest way to transfer data then I will rather write a script to make using smbget easier than using a slower method.

---

