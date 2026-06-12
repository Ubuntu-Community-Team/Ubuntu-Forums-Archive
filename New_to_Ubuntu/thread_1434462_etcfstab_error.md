---
title: "etc/fstab error"
date: 2010-03-20
forum: New to Ubuntu
---

### Post by 440corbon on 2010-03-20
I was setting up my raid and messed up my fstab. If any one could tell me the proper way to get my disks udid and a way to get into my fstab file and edit it I would be appreciative. Wife needs puter for school and I am having issuses getting her winblows puter to work wireless.

---

### Post by r-senior on 2010-03-20
You can get your disk UUIDs by running:

$ sudo blkid

Can you actually get to the /etc/fstab to edit it?

---

### Post by 440corbon on 2010-03-20
Thank you senior. I am not sure if I can get to my fstab to fix it . I'm running the live cd right now. I can see my files and open them but not sure on how to edit them. If I can get it to change to my home name in terminal i can get to gedit and edit my fstab.

---

### Post by r-senior on 2010-03-21
Have you made any progress?

Probably the easiest way to get access to your old /etc/fstab is to fire up a live CD. Your existing partitions should show up as mountable drives in Nautilus and you should be able to find the old /etc quite easily.

If it's only the UUIDs that you have messed up, it should just be a matter of getting the right values into /etc/fstab and then booting normally.

---

### Post by spiderbatdad on 2010-03-21
You can edit your filesystem from the live cd. If you open a terminal, become root with:
```
$ sudo -i
```
Next list your partitions:
```
# fdisk -l
```
You should see something like:
```
/dev/sda1               1         784     6297448+  12  Compaq diagnostics
/dev/sda2   *         785        6766    48046875    7  HPFS/NTFS
**/dev/sda3            6767       12845    48829567+  83  Linux**
/dev/sda4           12846       19457    53110890    5  Extended
/dev/sda5           19235       19457     1791216   82  Linux swap / Solaris

```
In this case, you would be interested in the Linux partition, not the swap space.
Mount the partition to the directory /media:
```
# mount /dev/sda3 /media
```

At this point feel free to use your file browser to navigate to /media in the filesystem directories and locate /etc/fstab. To use gedit to edit the file while your terminal is still logged in as root...:
```
# exit
$ gksu nautilus 
``` Navigate to the appropriate file again in the /media directory and nautilus will open fstab with gedit as root.

---

### Post by 440corbon on 2010-03-23
thank you I will try that out tonight spider. I know I didn't break anything too bad. I couldn't remember how to log in as root. I wasn't able to change etc/fstab. I will edit file tonight after work and let you guys know how I made out. Thanks

---

### Post by 440corbon on 2010-03-24
ok back up and running. thanks guys. I had an extra line in there from something. I have no clue what. Anywho the wifes lappy is running great now the server is running and my desktop is running, I need to break something. This is no fun. lol
Again thank you

---

