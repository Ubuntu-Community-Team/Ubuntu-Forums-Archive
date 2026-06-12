---
title: "Should I format / as ext4 and /home as ext3?"
date: 2009-12-09
forum: New to Ubuntu
---

### Post by EssexEagle on 2009-12-09
I have Kubuntu 9.04 installed on my laptop with separate / and /home partitions, both formatted as ext3, but am going to do a fresh install of Kubuntu 9.10 (leaving the /home partition untouched, of course).  I understand that the default filesystem for Karmic is ext4 but would it cause problems to format / as ext4, whilst leaving /home as ext3?  [This thread]("http://ubuntuforums.org/showthread.php?p=8396825") suggests that it might do...  Or, is there any need to switch to ext4 at all - would it be simpler just to keep / as ext3?  (Assuming ext3 is still an option?)

Advice would be appreciated :-)

---

### Post by marco123 on 2009-12-09
If in doubt, and you don't feel like backing up your /home to an external drive then copying it back over, I'd say leave them both ext3.  There's no major reason to change to ext4 in my opinion.

Marco.

---

### Post by EssexEagle on 2009-12-09
> **marco123 said:**
> If in doubt, and you don't feel like backing up your /home to an external drive then copying it back over, I'd say leave them both ext3.  There's no major reason to change to ext4 in my opinion.

Marco.

Thanks for your help!

---

### Post by warfacegod on 2009-12-09
I have noticed some performance increases with ext4. And, yes ext3 is available for 9.10. During your install, use manual partition. When you select the partition (choose wisely as in not your home folder) and create a new table there is a drag down menu with a number of different filesystems. Make sure you make it the / partition.

---

### Post by whoop on 2009-12-09
I have ext2, ext3, ext4 and ntfs all mounted in my OS, no problems at all. Well, not concerning my file systems anyway ;)

---

### Post by happyhamster on 2009-12-09
/ as ext4 (instead of ext3) will cause some speed improvements; a quicker boot for example, and applications will take less time to start, etc.
/home as ext4 doesn't lead to a significant improvement in such matters though (because there aren't that much system-related files in /home; only some user-configuration files). When manipulating data, you'll see some increase in speed though. You'll usually also see a major decrease in time to run a disk-check.

That said, ext4 still has some weird bugs/bug-reports/bug-fixes going on related to data-corruption (most of which are uncommon corner-cases). Going for a /=ext4, /home=ext3, or even just /=ext3, /home=ext3 isn't a bad choice at all IMHO.

I'm using the /=ext4, /home=ext3 scheme BTW (/=ext4 because I like the increase in speed and I don't really care should ext4 bork my system; I'll just re-install (and keep /home of course). And /home=ext3 because I don't want to worry about any important data being corrupted.)

Example of a current ext4 bug:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/453579](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/453579)

Speed regression in future kernel because of ext4 bug-fix:
[http://www.phoronix.com/scan.php?page=article&item=linux_perf_regressions&num=2](http://www.phoronix.com/scan.php?page=article&item=linux_perf_regressions&num=2)

---

### Post by raymondh on 2009-12-09
Likewise ... on my test machine, I use ext4 for root and ext3 for /home.  On my "everyday-systems", I use ext3.

The speed is there.

---

### Post by sweet_cogito on 2009-12-09
The only real boon to switching to ext4 is that it is slightly better and is supposed to handle improper unmounting somewhat better.  For most people, the difference will probably be negligible as there a number of other factors other than filesystem access speed that influence how fast something happens.  If you want to make the switch, make sure you backup, but making the switch is hardly necessary.

---

### Post by falconindy on 2009-12-10
Long version: Ext4 still has potential for data loss as it uses delayed allocation and lazily syncs memory caches only when it feels so inclined. Essentially, if you ever had a have hard lockup, you might reboot to find that some of your files are missing. In the 2.6.32 kernel, there was some work done to limit to behavior. Instead of correcting it entirely, there was just a huge regression in FS performance.

Short version: Ext4 sucks.

---

### Post by EssexEagle on 2009-12-10
Thanks everyone for your advice.  For now I have installed Karmic using ext3 for the / partition.

---

