---
title: "Boots into GRUB4DOS - can't get Ubuntu started"
date: 2009-09-10
forum: New to Ubuntu
---

### Post by torbengb on 2009-09-10
Hi! My situation is very similar to [this one]("http://ubuntuforums.org/showthread.php?t=1077456"), but as solution I'd like to not reinstall Ubuntu but rather fix the current installation. 

Here are some details:
I installed Ubuntu using Wubi, and then I've started using it for some days without problems, booting into Win&Ubuntu alternatingly several times. Now when I choose to boot into Ubuntu, I only get as far as a command-line interface named "GRUB4DOS". 

- how can I fix my install so Ubuntu boots properly again?
- what likely caused this error? (so I can avoid it in future)

The last change I recall doing inside Ubuntu was to add my NTFS Windows drive to the /etc/init.d/.... file and successfully reading&writing to that drive. I wouldn't expect this to interfere with boot setup though.

Regards,
Torben

---

### Post by ottosykora on 2009-09-10
I met same problem.
In my case I made a wubi install on a system with more operating systems and also two linux partitions with suse and knoppix, a linux partitons with home and swap.

I installed the wubi ubuntu into a logical partition on second hard drive with lot of logical drives , the target partiton was nr 12 on that second drive.

I never managed to make it work. To me it did look like the grub4dos was not able to boot the /boot file in a logical partition on second drive.
First I have seen that the grub 'bash' lands with all settings on the C: drive and not getting the info from the file to be read from the root of the c:
But in some occassions I noticed that all the settings were to the right place, but still no boot.

On one installation, I came into problems not beeing able to boot because there was a boot pratiton present. Then deleting the /host/disks/swapfile.disk did kind of cure the problem, setting the swpa to the partiton later.

---

### Post by torbengb on 2009-09-10
Additional info: I have only one disk with only one partition (Windows NTFS) and Wubi is installed on that.

---

### Post by Nealak on 2009-09-19
Same problem. I've been running Intrepid for the past few months and the GRUB4DOS thing just appeared yesterday morning after a powercut. As I pretty much only used Ubuntu since April I don't really want to lose all my files and work... Guess its not looking that hopeful at the moment though.

---

