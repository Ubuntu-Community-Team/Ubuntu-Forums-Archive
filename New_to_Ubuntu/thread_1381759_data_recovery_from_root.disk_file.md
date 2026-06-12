---
title: "data recovery from root.disk file"
date: 2010-01-15
forum: New to Ubuntu
---

### Post by princejohn on 2010-01-15
i have been using ubuntu for the past one year and the latest one since it released, but i would not call myself a very advanced user. the problem started three days back. and i think it was after running an update that ubuntu would not boot and show just "grub" ( i use a computer which has dual booting option windows vista being the first and ubuntu the second on a separate partition, and it is shared with different users). as i was researching to resolve this issue i came across a post saying that all the important data is saved in the root.disk file so i backed up the entire ubuntu folder into a different partition. unfortunately the next day i came i found that one of the users had deleted ubuntu from windows as it was installed from within windows. so now i am left with only the backup of all the files i have in a separate partition. 

I have reinstalled ubuntu 9.10 now. is there any way i can get access to my files atleast the documents and other important files from the backup that i have...

please help will need step by step advise on this

thanks in advance.

---

### Post by oldfred on 2010-01-15
the wubi site has these instructions:

[https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20migrate%20to%20a%20real%20partition,%20and/or%20get%20rid%20of%20Windows%20entirely?](https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20migrate%20to%20a%20real%20partition,%20and/or%20get%20rid%20of%20Windows%20entirely?)

Boot the Ubuntu Desktop CD, or another LiveCD, then mount the windows partition: 

sudo mkdir /win
sudo mount /dev/sda1 /winReplace sda1 with the appropriate device (a = disk, 1 = partition number), then mount the virtual disk therein 

sudo mkdir /vdisk
sudo mount -o loop /win/ubuntu/disks/root.disk /vdisk

---

### Post by yahonto on 2010-12-17
Tell me, please.
My file d: \ ubuntu \ disks \ root.disk was deleted. This section was ubuntu, which I need. Can I recover it?

---

