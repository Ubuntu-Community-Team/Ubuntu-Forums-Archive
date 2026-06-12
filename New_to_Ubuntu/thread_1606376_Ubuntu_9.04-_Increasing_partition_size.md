---
title: "Ubuntu 9.04- Increasing partition size"
date: 2010-10-26
forum: New to Ubuntu
---

### Post by Wellis on 2010-10-26
:confused: Using GParted on a live Ubuntu 9.04 disc, I have provided an unallocated partition between /dev/sda2 (ntfs windows XP) and /dev/sda3 (ubuntu). However I am unable to unmount and therefore extend the Ubuntu partitions. Each of the Ubuntu partitions show two keys (greyed out)-locked? Information suggests that it is necessary to unmount them manually, but how?

---

### Post by uRock on 2010-10-26
You should be able to right-click and select unmount.

---

### Post by pqwoerituytrueiwoq on 2010-10-26
you must resize the partition from the live cd or another or another bootable partition

---

### Post by TeoBigusGeekus on 2010-10-26
```
sudo umount /dev/sda3
```
Does it do anything?

---

### Post by uRock on 2010-10-26
> **pqwoerituytrueiwoq said:**
> you must resize the partition from the live cd or another or another bootable partition
> **Wellis said:**
> :confused: Using GParted on a live Ubuntu 9.04 disc,<snip>:)

---

### Post by drs305 on 2010-10-26
Also check the swap partition - it must also be unmounted even with the LiveCD. Select the swap partition, then Partition > swapoff.

---

### Post by pqwoerituytrueiwoq on 2010-10-26
> **uRock said:**
> :)
the way i read it implied he made the unallocated space then tryed to resize it after booting to the install

---

### Post by uRock on 2010-10-26
> **pqwoerituytrueiwoq said:**
> the way i read it implied he made the unallocated space then tryed to resize it after booting to the install
Which is likely now that you mention it.

---

### Post by Wellis on 2010-10-27
> **uRock said:**
> You should be able to right-click and select unmount.
Am very much a novice, so do not know what I am looking for in the log file viewer.

---

### Post by Wellis on 2010-10-27
> **TeoBigusGeekus said:**
> ```
sudo umount /dev/sda3
```
Does it do anything?
How do I use "sudo"?

---

### Post by TeoBigusGeekus on 2010-10-27
Open a terminal, type
```
sudo umount /dev/sda3
```
and press enter.

---

### Post by Wellis on 2010-10-27
> **drs305 said:**
> Also check the swap partition - it must also be unmounted even with the LiveCD. Select the swap partition, then Partition > swapoff.
Sorry but I am a beginner, Where do I find the swap partition?

---

### Post by drs305 on 2010-10-27
> **Wellis said:**
> Sorry but I am a beginner, Where do I find the swap partition?

When you are running GParted and are looking at the partitions, one of the listings in the "Filesystem" column will be listed as "linux-swap". That is your swap partition. To unmount it, highlight it in the lower section, then in the GParted menu select "Partition" > "swapoff".

---

### Post by Wellis on 2010-10-27
Thank you, but it still  leaves /dev/sda3 etc locked.

---

### Post by Wellis on 2010-10-27
The response is- /dev/sda3 is not mounted (according to mtab)

---

### Post by Wellis on 2010-10-27
> **Wellis said:**
> Am very much a novice, so do not know what I am looking for in the log file viewer.
Have right clicked but unmount is greyed-out

---

### Post by drs305 on 2010-10-27
If you post a screen shot of your gparted window perhaps someone will be able to assist you. You add an image (<100MB please) by clicking the lower "Manage attachments" button while you are writing a post.

---

### Post by Wellis on 2010-10-27
> **drs305 said:**
> If you post a screen shot of your gparted window perhaps someone will be able to assist you. You add an image (<100MB please) by clicking the lower "Manage attachments" button while you are writing a post.

Please excuse my incompetence but I have found the Manage attachments, but now need to know how to attach an image of the gparted window.

---

### Post by drs305 on 2010-10-28
> **Wellis said:**
> Please excuse my incompetence but I have found the Manage attachments, but now need to know how to attach an image of the gparted window.

When you click the "Manage Attachments" button, a new window will open. Press one of the "browse" buttons and it will open a file manager so you can find the image you want to upload. Select the image, then press "Upload" and it will attach itself to your post.

To take a screenshot in Ubuntu, one way is to use the menu: Applications, Accessories, Take Screenshot (or the command gnome-screenshot --interactive).

---

### Post by Wellis on 2010-10-28
> **drs305 said:**
> When you click the "Manage Attachments" button, a new window will open. Press one of the "browse" buttons and it will open a file manager so you can find the image you want to upload. Select the image, then press "Upload" and it will attach itself to your post.

To take a screenshot in Ubuntu, one way is to use the menu: Applications, Accessories, Take Screenshot (or the command gnome-screenshot --interactive).
Thank you to every one, I have now successively increased the Ubuntu partition and learned a lot in the process.

---

### Post by Wellis on 2010-10-28
Solved!!!!

---

### Post by ArgusVision on 2010-10-28
Ok. Great! Please mark it SOLVED with the Thread Tool link to the top right of the first post. Thanks.

---

