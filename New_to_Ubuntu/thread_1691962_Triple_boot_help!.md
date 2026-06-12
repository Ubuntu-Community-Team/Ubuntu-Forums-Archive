---
title: "Triple boot help!"
date: 2011-02-20
forum: New to Ubuntu
---

### Post by Indian_Guy101 on 2011-02-20
Until today, I had a working dual boot between Windows XP Professional and Ubuntu 10.04. My harddrive was partitioned like this: 100 gb to Windows, 100 gb, to ubuntu, 100 gb unallocated. 

I then decided that I wanted to use this OS called Excelixis (Its basically a modified Xubuntu). I installed it and in the partitioner, selected use largest continuous free space. 

After the installation, when I booted up, I noticed that Ubuntu 10.04 did not show up in the menu; all i could boot too was Excelixis, memtests, and Windows XP. I also noticed that it was not using grub2 like before, and thought maybe this was causing the error. Please help me to fix this!

---

### Post by oldfred on 2011-02-20
Depending on what version of grub (0.97) legacy they installed and if your Ubuntu partition is ext4, you may not be able to boot it. The best choice it to reinstall grub2. It should find you new install and let you boot it. 

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202]("https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202")

If you need specific instructions, post this:
Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code] paste here [ /code] tags.

---

### Post by Indian_Guy101 on 2011-02-20
I am pretty sure that my ubuntu 10.04 partition was ext3. I would reinstall grub2, but excelixis is not able to connect to the internet for whatever reason...

---

### Post by oldfred on 2011-02-20
Do you have liveCD? You should have repair CDs for every installed system.

Cannot help with not connecting. Did you check connections?

This is a simple grub legacy boot stanza adjust to your drive & partitions. Remember old grub counts partitions from 0 where grub2 counts from 1.

title    Most Current Ubuntu on sdc5
root    (hd2,4)
linux   /vmlinuz root=/dev/sdc5 ro quiet splash
initrd  /initrd.img

---

### Post by Indian_Guy101 on 2011-02-20
Sorry for double post. I read that guide that you posted, but I am still kind of confused. The linux partition that he is using in the video would be my Ubuntu 10.04 partition right?

---

### Post by oldfred on 2011-02-20
Video?

Yes your Ubuntu partition.

---

### Post by Indian_Guy101 on 2011-02-20
Ok thanks... Yeah I was talking to someone about a video while posting this... that might have been the cause of the small error in my last post... lol.

---

