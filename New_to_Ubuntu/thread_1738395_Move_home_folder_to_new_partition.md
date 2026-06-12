---
title: "Move home folder to new partition?"
date: 2011-04-24
forum: New to Ubuntu
---

### Post by Newbie2910 on 2011-04-24
I removed my Windows partitions (machine was set up as dual-boot) and now have one large formatted partition, besides the extended partition where Ubuntu is installed.

The only things on this otherwise-empty partition are the Lost & Found folder and the VirtualBox .vdi file.

I should be able to use all this space for my data, correct?  Few questions:
1. Am I right that this will enhance security, since my data will be on a different partition than the Ubuntu OS?

2. Is there any way that a malicious program running under XP in the VirtualBox could access anything else on this partition, or is it "locked inside" the VirtualBox sandbox?  XP only sees the C: drive space that I allotted to VirtualBox.

3.If moving my Home folder to this partition is a good move, how do I go about doing so?  I guess I can continue operating the way I do now but just copy data over from the Ubuntu partition to this data partition.

---

### Post by doas777 on 2011-04-24
here are instructions on how to do it. [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

1) yes, but not for why you think. the real reason to do this, is so that you can reinstall or export the home easily. mount points do have some security oriented features that may give you more flexibility to secure your rig if you have differant partitions to mount, but this is not usually why people do it. 

2) virtualbox should sandbox the host, but there are some (purely theoretical) malwares that can use malicious drivers to misuse virtualboxes interface with the host, but this is almost an impossible threat at the moment. look into bluepill and purplepill for details. keep in mind though, the malware will affect the guest so if the particular malware can hurt you from within windows, does it matter if it infects the host? my advice is use the virtual for only the things you need to do in windows (for instance, access your bank account only from the host). another option is to run virtuals for specific purposes, and restore them from a snapshot on a regular basis. 

3) see link above

---

### Post by oldfred on 2011-04-24
I do not know if a separate /home increases security, but it makes it easier to reinstall as your user configurations & data are all in /home. But if doing a clean install you may still want to backup custom system settings from /etc and a list of installed applications.

Not sure about security.

For newer users I recommend the separte /home over just root & swap as like to separate operating systems from data. For more advanced users especially those dual booting multiple Linux's in the Debian family I recommend a separate /data partition, put all data folders into the /data and link the folder back to /home. You still need to back up /home for a clean install but it is tiny if you have moved everything out. I still have my .wine which is 3/4 of the 1GB my /home is now. Your VirtualBox may be in /home depending on how you configured it.

I think these are all about the same just using different commands to do the copy.
Uses cp -ax
[http://www.ivankuznetsov.com/2008/04/moving-home-to-its-own-partition.html](http://www.ivankuznetsov.com/2008/04/moving-home-to-its-own-partition.html)
cp without -a and copying as sudo root takes ownership
To move /home uses rsync  (create mount may be missing)
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)
Uses cpio
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

Link is on move home but see post by bodhi.zazen on data partition #6
[http://ubuntuforums.org/showthread.php?t=325048](http://ubuntuforums.org/showthread.php?t=325048)
Shared /data -see post #4 oldfred
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)


Shared Data with Different operating systems, different uid and gid issues - Morbius1
[http://ubuntuforums.org/showthread.php?t=1675381](http://ubuntuforums.org/showthread.php?t=1675381)

---

