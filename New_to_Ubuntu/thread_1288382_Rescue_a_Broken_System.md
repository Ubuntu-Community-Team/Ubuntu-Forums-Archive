---
title: "Rescue a Broken System"
date: 2009-10-11
forum: New to Ubuntu
---

### Post by arnold.pietersen on 2009-10-11
Hi 

I broke my system after messing around with fsck and some inodes got deleted.  Now my system gives me an "Error 2" message when I boot up.

When I boot up from a USB, I select the "Rescue a broken system" option.  A window comes up with the title Boot Loader and /install/vmlinux with an OK button.  Nothing happens after I have pressed Enter.

Any help appreciated.

Thanks in advance

---

### Post by Nevart on 2009-10-11
Well I had this problem too, and what I did was I installed Ubuntu onto another computer and then backed up the system files, like /etc/ and /bin/ and so on, onto a USB disk.

Then I booted up another linux (thing it was Slax) from a USB and copied those files from the other USB over the top of the corrupted files on the HDD linux partition and it was back to working when I rebooted.

Only drawbacks to this are:

1) Need to have a 2nd computer available
2) Need to have some USB or CD bootable distro you can run temporarily

The reason you shouldn't do it in Ubuntu is that Ubuntu might be aware of what you're doing and try to stop you.

---

### Post by arnold.pietersen on 2009-10-12
Hi Nevart

Thanks for your reply.

I booted up using a live CD and discovered that of my 60GB HDD I had 50GB free space.  The last time I had about 14GB of free space.  My Home folder was empty, the boot folder did not even exist.  I then ran the following command:

sudo e2fsck -yfv /dev/sda1

Now I have a lost+found directory with thousands of files and folders with numbers.  When I venture into some of the folders I can see my data files, but there is such a lot of them

I am now in the process of backing up the lost+found directory to an external HDD.

I was wondering,if there is any way how one can get the names of the files and folders back.

Thanks for any help.

---

