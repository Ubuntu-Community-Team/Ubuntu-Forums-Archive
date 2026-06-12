---
title: "How do I mount a windows drive??"
date: 2007-03-19
forum: Networking &amp; Wireless
---

### Post by zac_haryy on 2007-03-19
I have searched the forums and Google and haven't came up with a working solution yet. I have tried many different lines in the terminal with nothing working at all. I can find the computer that I want to connect to by browsing for it clicking the :Network Servers" under places. I want to mount this though under "/mnt/media_server/z" but I cant get it to work. I am new with linux so be easy. Also there will have to be a u/p in the line of code. If somebody could just show me the line of code that I need to do this that would be great. The drive that I am trying to mount is "//192.168.0.50/Z$" or "//192.168.0.50/Z" or "//media_server/Z$" nothing works for me though. Please let me know what to do. Thanks!

-haryy

---

### Post by mysticrider92 on 2007-03-19
I have never tried to mount a Windows box from inside Linux, but I think you could try 'sudo mount 192.168.0.50 /mnt/media_server/z'. That may or may not work. Otherwise, you will probably need to install Samba on the Linux machine. I can't really help you in that case.

[edit] I think you will need to install ntfs-3g (sudo apt-get install ntfs-3g) before the first command will work. Then you could use 'sudo ntfs-3g 192.168.0.50/z /mnt/media_server/z'.

---

### Post by zac_haryy on 2007-03-19
Tried this and it doesnt work. I did this in Fedora Core 6 and it worked fine, I dont remember what I used to do it thought. Anyways I have samba installed and I am pretty sure that you do not need to mount it as an NTFS drive since it is a network drive.

---

### Post by zac_haryy on 2007-03-20
Anybody have any ideas that I can try at all. Any help will help me out. Thanks!!


-haryy

---

