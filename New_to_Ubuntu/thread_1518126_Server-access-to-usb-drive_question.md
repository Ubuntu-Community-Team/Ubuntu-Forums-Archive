---
title: "Server-access-to-usb-drive question"
date: 2010-06-26
forum: New to Ubuntu
---

### Post by breeness on 2010-06-26
Hi,

Apologies ahead of time if I have no idea what I'm talking about, but I am pretty sure I have little idea of what I am talking about.

Today, I used Ubuntu server on an 8-yr-old PC to create a home NAS. It's working nicely in that I have public folders that I can see and write to. I want to put my media (music, videos, etc) as well as some pretty large illustrator and photoshop files on it for access from all my computers. 

However, it's so painfully slow. On top of that, it often disconnects in the middle of transfers. It's kinda frustrating.

I was thinking it might be faster to transfer my stuff to a little external usb drive I have and then plug it into the NAS. However, how do I get the server to copy everything onto the hard drive?

I tried searching, but kept finding solutions on how to install ubuntu onto a usb drive :P

Cheers ahead of time for any help!!

Thanks!

---

### Post by mikewhatever on 2010-06-26
You'll have to mount the external usb drive first. 
Run **sudo fdisk -l** to check for partition names, probably sdb1, sdb2, etc. 
Then create a mount pont: **sudo mkdir /mnt/ext_usb**. 
Then mount: **sudo mount /dev/sdXY /mnt/ext_usb**.

---

### Post by breeness on 2010-06-26
great, I will try that. It won't format it will it?

---

### Post by mikewhatever on 2010-06-26
No. :p

---

### Post by breeness on 2010-06-27
Thanks for that!

So once I mount the drive, how can I just copy it? Or should I do that using one of my GUI OSes?

---

### Post by mikewhatever on 2010-06-27
Copy what? Data to/from it? The drive is attached to the mount point you created. If there is no GUI, use 'cp' to copy, if there is, drag and drop or copy/paste.

---

