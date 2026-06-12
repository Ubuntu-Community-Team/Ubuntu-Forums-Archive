---
title: "Can't unmount USB drive"
date: 2011-05-25
forum: New to Ubuntu
---

### Post by nifty542 on 2011-05-25
Hi, all

Am just experimenting with Lubuntu and Xubuntu. I have one problem, so far: I can't eject a USB drive. I click on safely remove, but the drive keeps running.
I have seen this posted elsewhere, but didn't understand the post.
I don't have the problem with Ubuntu- could it be something to do with the other desktops?
Thanks, in advance

Nifty

---

### Post by ivanovnegro on 2011-05-25
I for one dont have this problem on Xubuntu, so I dont think it has to do with Xfce or LXDE.
It has to be something else.

---

### Post by nifty542 on 2011-05-25
Hi

Thanks for the reply. Still can't find an answer to the problem, though!

Regards

Nifty

---

### Post by Rex Bouwense on 2011-05-25
Nifty, you have an interesting problem.  Can you unmount it using the terminal?  How about sudo?  If you cannot unmount the device, can you still write to it?

---

### Post by nifty542 on 2011-05-25
Hi, Rex
Thanks for the reply. Sorry, but I don't know how to unmount from the terminal! That's why I didn't understand the post I googled- it had many lines of output.
Thanks, again

Nifty

---

### Post by Toz on 2011-05-25
I've run into this problem a couple of times. In my case, there was always something/program holding a file/connection open to the drive that was preventing the unmount. IIRC, once it was that I had Thunar open displaying the contents of the drive. A second time was some wierd sort of defunct process that was keep it open. 

You can use the lsof command to see what process has it open. To see the device name of the usb drive , type: ```
mount
```(in my case /dev/sdc1). Then type in the following in a terminal window:```
lsof /dev/sdc1
```This will show what program/process has the open file. You can then look at closing off the program or killing the process.

---

### Post by Rex Bouwense on 2011-05-25
Nifty try
sudo umount /dev/sdb1
assuming sdb1 is your flash drive

---

### Post by Ghost|BTFH on 2011-05-25
I'm going out on a limb to suggest that perhaps you're still a little new to Linux in general and start from there.

1) Most common mistake made by newbies (and even more experienced users - especially when tired) is they're sitting in a directory on the drive they're trying to eject and the system sees this and says, "I can't eject it, the drive's busy!"

2) To eject from the command line, open a terminal and type in:

```
sudo eject /path/to/device
```

Example:

A drive mounted as /media/monkeys would be ejected with:

```
sudo eject /media/monkeys
```

I hope that helps.

Cheers,
Ghost|BTFH

---

### Post by nifty542 on 2011-05-26
Hi, all
Many thanks for the replies. Work has got in the way, somewhat!
I shall try the solutions above and get back.
At the moment, getting used to configuring the panel in Lubuntu.

Regards
Nifty

---

### Post by nifty542 on 2011-05-26
Hi, all

Well, feeling a bit stupid now. I couldn't unmount using safely remove, and tried the sudo command, which didn't work. Then I clicked on the disc utility-it had the option to power down, and this worked. 
Sorry, folks- should have thought of this!
Regards
David

---

