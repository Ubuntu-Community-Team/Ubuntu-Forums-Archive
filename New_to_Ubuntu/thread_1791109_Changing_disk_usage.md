---
title: "Changing disk usage"
date: 2011-06-26
forum: New to Ubuntu
---

### Post by Wennerholm on 2011-06-26
I've just installed Ubuntu server 11.04. I have two disks and unfortunally, during installation, the second (lagre) disk was dedicated to "swap".
Now, I'd like to use the small disk as "system" and the large disk for "data" (/usr/)

How can I change the configuration?

---

### Post by Gone fishing on 2011-06-26
The basic gist of what to do would be partition the large disk how you want it probably ext4 with a small swap partition say 4 gig (you could do this with gparted). Then modify the fstab to mount the the new drive and partitions where you want them. Note the Ubuntu uses UUIDs and you need to run the sudo blkid command to find the UUIDs of the new partitions.

Why /usr rather than /home? I think I'd mount the new disk/partition as /newhome then copy the home directory into /newhome check everything's fine i.e its all there with the right permissions etc delete the old /home and mount the disk/new partiton as /home or use a simlink.

Obviously you will need to modify the swap entry in your fstab to match the new UUID of the new swap partition

[http://www.cyberciti.biz/faq/linux-finding-using-uuids-to-update-fstab/](http://www.cyberciti.biz/faq/linux-finding-using-uuids-to-update-fstab/)

---

