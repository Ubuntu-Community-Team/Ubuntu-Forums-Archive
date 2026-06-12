---
title: "GRUB install fails"
date: 2011-06-23
forum: New to Ubuntu
---

### Post by chartguy on 2011-06-23
Okay, I'm a total Ubuntu novice, so I apologize in advance if this is a stupid question.

I assembled a two-CPU (16 core) AMD system, with 32 GB of RAM. It has four 1TB drives. Anyway, I put Ubuntu 11.04 (64-bit) on a USB stick. 

It boots fine off the USB key, but when I try to install to hard disk, I get 

Unable to install GRUB in /dev/sda
Executing 'grub-install/dev/sda' failed.
This is a fatal error.

I've tried several times, and that's how it always ends.

Am I doing something wrong? Do I need to be doing something else, differently?

---

### Post by oldfred on 2011-06-24
Welcome to the forums.

Do you have RAID or LVM? Or were drives ever in a RAID set? That can interfere with grub.

Also do you have a BIOS that locks boot sector/MBR?
BIOS & disable "Boot Sector Virus Protection"
Other BIOS settings - Security or locked down Boot sector, Bitlocker

Have you installed and the error is from the install?

---

### Post by chartguy on 2011-06-24
There is a Promise RAID on the MB. I tried to get it to work, but the Ubuntu sees four individual drives. I seem to have painted myself into a corner.

---

### Post by oldfred on 2011-06-24
Are you still running the RAID? 
Also for installing on fakeraid (motherboard raid), this might help you:
[https://help.ubuntu.com/community/FakeRaid](https://help.ubuntu.com/community/FakeRaid)

Only if you do not want the RAID. But drives may still have internal settings:
Presence1960 on remove old raid setting from HD
[http://ubuntuforums.org/showthread.php?t=1325650](http://ubuntuforums.org/showthread.php?t=1325650)
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb
Also check BIOS for raid settings
More discusion:
[http://wwww.ubuntuforums.org/showthread.php?p=9274738#post9274738](http://wwww.ubuntuforums.org/showthread.php?p=9274738#post9274738)

---

### Post by chartguy on 2011-06-24
I'm afraid the FakeRaid page does not exist.

I'll see if I can turn it off, since Ubuntu does not see a single volume, rather four drives, even with RAID turned on.

Thank you!

---

### Post by Quackers on 2011-06-24
> **chartguy said:**
> I'm afraid the FakeRaid page does not exist.

I'll see if I can turn it off, since Ubuntu does not see a single volume, rather four drives, even with RAID turned on.

Thank you!
If you look at the page that does appear on oldfred's link you will should see other links to what you want.
Isn't Promise hardware raid? Not sure.

---

### Post by chartguy on 2011-06-24
> **Quackers said:**
> If you look at the page that does appear on oldfred's link you will should see other links to what you want.
Isn't Promise hardware raid? Not sure.

[https://help.ubuntu.com/community/FakeRaid](https://help.ubuntu.com/community/FakeRaid) 
reports "This page does not exist yet. You can create a new empty page, or use one of the page templates."

It is a Tyan S8230GM4NR motherboard. 
[http://www.tyan.com/product_SKU_spec.aspx?ProductType=MB&pid=665&SKU=600000192](http://www.tyan.com/product_SKU_spec.aspx?ProductType=MB&pid=665&SKU=600000192)
It has a Promise RAID controller on the motherboard. The controller appears not to be ready for prime time, so I'm going to try to disable it, and see if that works.

---

### Post by Quackers on 2011-06-24
I take it that you have nothing installed then, as deleting the raid array would destroy anything already on there.

---

### Post by oldfred on 2011-06-24
I know about nothing on RAID.

If you start writing from Ubuntu as separate disks I think you break the RAID. How many of your 4 disks were in the RAID set? If one or more were not then I would use that one for Ubuntu.

From the non-existing link, I found this one that has some info:
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

Install these, you may or may not have some installed on the liveCD, then run boot script.

#Install these before running script:
#Is able to search LVM partitions if the LVM2 package is installed
# ("sudo apt-get install lvm2" in debian based distros)
# Is able to search Linux Software Raid partitions (MD Raids) if
# the "sudo apt-get install  mdadm" package is installed.
[]("http://grub.enbug.org/LVMandRAID")sudo apt-get install mawk

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

---

### Post by YesWeCan on 2011-06-24
> **chartguy said:**
> [https://help.ubuntu.com/community/FakeRaid](https://help.ubuntu.com/community/FakeRaid) 
reports "This page does not exist yet. You can create a new empty page, or use one of the page templates."

It is a Tyan S8230GM4NR motherboard. 
[http://www.tyan.com/product_SKU_spec.aspx?ProductType=MB&pid=665&SKU=600000192](http://www.tyan.com/product_SKU_spec.aspx?ProductType=MB&pid=665&SKU=600000192)
It has a Promise RAID controller on the motherboard. The controller appears not to be ready for prime time, so I'm going to try to disable it, and see if that works.
This looks like a real hardware RAID controller: [http://www.tyan.com/manuals/AMDSP5100_Promise_SATA_RAID_Guide_v100.pdf](http://www.tyan.com/manuals/AMDSP5100_Promise_SATA_RAID_Guide_v100.pdf)
It would be nice to use it.

---

