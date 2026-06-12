---
title: "fstab problem"
date: 2011-06-19
forum: New to Ubuntu
---

### Post by mahuhu on 2011-06-19
Hey all

   I'm going through the processes of learning/understanding the CLI by going through tutorials on different sites to get a few different ways of doing things rather than just sticking by one persons way of doing things and so far so good, it all seems logical.

  What is confusing me is i have got to 'Editing and understanding fstab' on one particular site [http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)
But instead of the nice neat rows of understandable text i get

/etc$ **cat fstab**

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=********-****-****-****-************ /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=********-****-****-****-*********eda none            swap    sw              0       0
 
i've got no idea what this means (i've blanked out the numbers/letters that UUID= as i'm not sure if i should be printing them online or not, if they are needed i can always put them on a later post.
  can someone tell me why this is coming up and how to change it /use a command to make it legible pls

---

### Post by s1baker on 2011-06-19
I'm a nooby, but I have been going through all of this "fstab" "blkid" UUID" stuff the past few days, and beings that no one has replied yet I will tell you what little I know, until some one more knowledgeable comes on.
The UUID is simply a very unique identifier given to devices that are so random that they probably won't be duplicated anywhere. If you go into your terminal and type "sudo blkid" ( without the quotes of course, you will get these unique identifiers for the partitions on your HD. The "fstab" file in your /etc directory is a file that is read at boot and the identifiers in the fstab file must match what you are shown by doing the blkid command.
On the file that you displayed ( the fstab file ), the # at the beginning of a lines do not mean anything to the computer, they are only remarks for humans to read, you can put anything after them that you want.

For example, your post of this:
```
UUID=********-****-****-****-************ / ext4 errors=remount-ro 0 1
```
would mean that the unique identifier ****whatever is for "/"
which is the root directory and "ext4" is the type of file system that is for this UUID. I don't know what the "errors=remoutsetcetcetc" mean.

You also have a UUID for the swap partition and some people have more that 2 partitions and the fstab file would need to know about each of them so data could be correctly wrote to the right place.

---

### Post by jtarin on 2011-06-19
You can make it humanely readable but its not as effective as BLKID and I would dissuade you from trying.Here's another[ link ]("https://help.ubuntu.com/community/Fstab")providing fstab formats.

---

### Post by mahuhu on 2011-06-19
Thanks for that. Link was helpful.

---

### Post by dFlyer on 2011-06-19
I believe your drive is encrypted.

---

### Post by jtarin on 2011-06-19
> **dFlyer said:**
> I believe your drive is encrypted.Hi, dFlyer......how do arrive at that conclusion?

---

