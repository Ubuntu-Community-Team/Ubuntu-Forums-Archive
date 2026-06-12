---
title: "Re-install or Resize?"
date: 2009-05-05
forum: New to Ubuntu
---

### Post by ke6rj on 2009-05-05
Newbie here. Installed jounty 9.04 on my Dell laptop. Install did not go right. Would love to reinstall. Was out of disk space on the second day. 
On the “Prepare disk space” screen, I had chosen the first option. This I thought would give me the dual boot. The option I clicked on was:
“Install them side by side, choosing between them at start up”.
Now wish I chosen:
“Specify partitions manually (advanced). After I ran our of disk space, I tried to reinstall but chickened out, afraid I might mess up my Win XP partition. I got as far as the partition screen which showed:
/dev/sda	Type 	Size	Used
/dev/sdal1	fat 16	164 MB	33 MB
/dev/sda2	ntfs	150752 MB 49344 MB
/dev/sda5	ext3	2500 MB	2396 MB
/dev/sda6	swap	180 MB	0 MB
/dev/sda3	fat32	6440 MB	2012 MB

I understand there is also a re-size option. However I don’t know which is preferable and / or easier. 

If I do reinstall from a live CD, do I only reformat only ext3 or also any of the other partitions and which ones? Any help will be VERY MUCH appreciated.
Harry

---

### Post by zeroseven0183 on 2009-05-05
I'm also doing dual-boot on my office laptop. What I did is to install Ubuntu inside Windows, choose drive C and allot at least 10GB for the partition. So what you need to do is boot to Windows XP then run wubi as if installing another software.

For me, this is the safest way if you do not want to mess your Windows configuration.

You should be able to see the choices on the next restart after the Ubuntu installation.

---

### Post by Didius Falco on 2009-05-05
> **ke6rj said:**
> Newbie here. Installed Jaunty 9.04 on my Dell laptop. Install did not go right. Would love to reinstall. Was out of disk space on the second day. 
On the “Prepare disk space” screen, I had chosen the first option. This I thought would give me the dual boot. The option I clicked on was:
“Install them side by side, choosing between them at start up”.
Now wish I chosen:
“Specify partitions manually (advanced). After I ran our of disk space, I tried to reinstall but chickened out, afraid I might mess up my Win XP partition. I got as far as the partition screen which showed:
/dev/sda    Type     Size    Used
/dev/sdal1    fat 16    164 MB    33 MB
/dev/sda2    ntfs    150752 MB 49344 MB
/dev/sda5    ext3    2500 MB    2396 MB
/dev/sda6    swap    180 MB    0 MB
/dev/sda3    fat32    6440 MB    2012 MB

I understand there is also a re-size option. However I don’t know which is preferable and / or easier. 

If I do reinstall from a live CD, do I only reformat only ext3 or also any of the other partitions and which ones? Any help will be VERY MUCH appreciated.
Harry

I'd say a reinstall would be the easiest, especially since you just installed it. There can't be much in there you need to save at this stage.

I see you have a Fat 16 partition at the very front of the drive (sda1), followed by an NTFS partition in sda2, and a Fat 32 partition in sda3.

Your Ubuntu (sda5) and swap partitions (sda6) are in an extended partition.

Do you know what is in the fat 16, fat 32 and ntfs partitions? If so, post that info. If not download the little (57k) script in my signature to your desktop:

Then open a terminal and type:

```
sudo bash ~/Desktop/boot_info_script*.sh
```

The script will gather a lot of information that will help figure out the problem into a file named RESULTS.txt

Open that file, select all and paste it in this thread, then put code tags (the # on the toolbar) around it.

It'll help to figure out the answer faster...

Regards,

Didius

---

### Post by ke6rj on 2009-05-05
> **zeroseven0183 said:**
> I'm also doing dual-boot on my office laptop. What I did is to install Ubuntu inside Windows, choose drive C and allot at least 10GB for the partition. So what you need to do is boot to Windows XP then run wubi as if installing another software.

For me, this is the safest way if you do not want to mess your Windows configuration.

You should be able to see the choices on the next restart after the Ubuntu installation.
Thank you for helping. I will try to get the script. I'm doing this posting on the XP side. So I won't be able to do any pasting unless I figure it out, what I don't know how to do. It sounds something I think I will venture doing and that is reformat the Ubuntu (sda5) and swap partitions (sda6), which are in an extended partition. After reformating those partions I should then be able to proceed with the manual install. Am I right? Sorry to be such a neophite. However I'm learning.

---

### Post by Didius Falco on 2009-05-05
> **ke6rj said:**
> Thank you for helping. I will try to get the script. I'm doing this posting on the XP side. So I won't be able to do any pasting unless I figure it out, what I don't know how to do. It sounds something I think I will venture doing and that is reformat the Ubuntu (sda5) and swap partitions (sda6), which are in an extended partition. After reformating those partions I should then be able to proceed with the manual install. Am I right? Sorry to be such a neophite. However I'm learning.

That's still going to leave you short on space. That's why I was asking what was on the fat16, fat32 and ntfs partitions.

Ubuntu will work just fine from a logical partition inside an extended partition.

When you start the Gparted partitioner from the Administration menu, you'll notice that sda4 is a "box" that holds the Ubuntu and Swap partitions. What you'll need to do is resize the partition(s) adjacent to the Extended partition, then resize the Extended partition to take up the new space.

Then you can either resize the Ubuntu partition to use that extra space, or just delete the Ubuntu and Swap partitions and make new ones.

You should go into Windows before you do anything and thoroughly defrag all your Windows type partitions, to help protect against data loss.

It happens rarely, but it does happen, and you don't want to be that 1 in a million that catches that bullet.

You should backup your windows data first too. I know everyone says that - but they say it for a reason...

Good luck, and come back if you need anything else.

Regards,

Didius

---

### Post by ke6rj on 2009-05-06
Thank you again, Didius. I'll quit for tonight and think about this the day after tomorrow. Doctors visit tomorrow and travel day. BTW, I will be attending the SW Computer Conference in San Diego end of this month. Maybe I just wait until then and get an expert user to help me do this right. Sorry, but I'm timid and sure do not want to mess up my XP. 
Harry

---

