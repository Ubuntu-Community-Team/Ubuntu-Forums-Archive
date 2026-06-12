---
title: "nfs share of ramdisk?"
date: 2007-05-12
forum: Networking &amp; Wireless
---

### Post by RFScheer on 2007-05-12
Here's an interesting problem involving a robot sharing ramdisk images wirelessly.

I followed the wonderful howto at [http://www.vanemery.com/Linux/Ramdisk/ramdisk.html]("http://www.vanemery.com/Linux/Ramdisk/ramdisk.html")

to set up a ramdisk so that the robot's camera would save images to it and they could be retrieved more quickly than from disk.  That works great.

The question is how to view the images remotely from my laptop.  You can't just mount the /dev/ram0 because "it's not a directory" and the mount point directory in the robot file system shows up blank on the laptop.

I've tried various things with nfs but just can't get it working.

???

---

### Post by RFScheer on 2007-05-12
My own reply:)

The problem was due to the mount point not being chosen wisely.  On the robot I had mounted the ramdisk in the /home/me/ramdisk directory but nfs doesn't want to forward a mounted directory like that along with the parent directory, which is what I was trying to do.

So, I just changed the mount point in the robot to /mnt/rd and set the permissions and the sharing directions in the /etc/exports file and it worked fine.  Now, I can mount /mnt/rd on the remote laptop with no problem.

Hope that helps someone!

---

