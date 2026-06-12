---
title: "accessing NTFS Drives from SSH"
date: 2008-02-13
forum: Networking &amp; Wireless
---

### Post by biasedopiniondrummer on 2008-02-13
I've created a remote connection from my laptop running ubuntu gutsy to my desktop running gutsy. how do i use the ssh connection to access files stored on separate ntfs partitions? this is a dual boot machine with windows xp. Thanks Guys!

---

### Post by pdub on 2008-02-13
I assume that you can access the ntfs drives/partitions when you are logged in locally. 

From the remote machine you can click on the desktop (anywhere) and then hit ctrl+l (That is a lower case L).

Then type ssh://ip_address_of_remote_computer, i.e - ssh://192.168.0.1

This should pop-up a login prompt. Once you login you will have a Nautilus window to your remote machine. Then you can navigate to your ntfs drive, where ever that may be on your system

---

### Post by biasedopiniondrummer on 2008-02-15
Thanks! I had the SSH connection set up but didn't know where to navigate to find the hard drives. it was in the /media directory. thanks! its working great!

---

