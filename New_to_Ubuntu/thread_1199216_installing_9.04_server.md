---
title: "installing 9.04 server"
date: 2009-06-28
forum: New to Ubuntu
---

### Post by gurt on 2009-06-28
I'm yet another XP guy trying out ubuntu. The reason I'm going for the server is that I need to use Dynagen (which is a router simulation app) and I need to use as much of system's 4G of RAM as I can. I understand that 64-bit server is the way to go -- so I've been told. 

At this stage I installed ubuntu and I'm looking at a prompt. I know that I need to install some packages....that only took about 2 hours to figure out. 
But it seems I need to be online to install my wireless NIC driver. Hmmm. That's a bit of a prob. So let's say I can put the drivers that I need to install on a USB stick -- dang, Do I need a driver for that too? 

Even if I get the driver for the stick installed, how do I access the stick? It's not like 'cd g:'?
Ugh. Any advice on how to get things up and running? Perhaps some advice from a windows guy who's made the leap?

Ta

---

### Post by yang925 on 2009-06-28
you might have to mount it by hand. in the desktop editions its automaticly mounted. im not sure about server.  Once mounted the device will be under /media/devname. after you plug it in you might try:

sudo mount /dev/sda /media/sda

after that cd /media/sda

if it complains that /media/sda dosn't exist create it with:

sudo mkdir /media/sda

and the try mounting it again.

---

### Post by cariboo on 2009-06-28
Using the 64-bit desktop would work just as well for what you need. You've already got the server version installed, so we'll work with that. Jaunty server comes with most wireless drivers installed by default. We have to know what wireless device you are running. If you have your usb thumb drive handy, you have to mount it before you can transfer anything to it. plug  your device in and at the prompt type:

```
dmesg | tail -n15
```

you should get an output that looks something like this:

```
27487.601088] sd 4:0:0:0: [sdb] Write Protect is off
[27487.601094] sd 4:0:0:0: [sdb] Mode Sense: 43 00 00 00
[27487.601097] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[27487.967062] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[27487.967069]  sdb: **sdb1**
[27487.968135] sd 4:0:0:0: [sdb] Attached SCSI removable disk
```

In the above example I have bolded the device number. To mount your device at the prompt type:

```
sudo mount /dev/sdb1 /mnt
```

You will be asked for the password you created during installation, it will not be echoed back when you type it in. This command mounts your usb thumb drive so that you can write a file to it. You will have to substitute the device number you got when running dmesg.

Next at the prompt type:

```
sudo lshw -C network > /dev/sdb1/network.txt
```

again substitute your device label for the above. This command will list all your network devices and write the results to a file called network.txt on your thumb drive.

To remove/unmount your thumb drive, at the prompt type;

```
sudo umount /mnt
```

and wait for the prompt to return. You can now plug your thumb drive in a computer with a network connection, and paste the results of the lshw command in your next post.

---

### Post by gurt on 2009-06-28
> **cariboo907 said:**
> Using the 64-bit desktop would work just as well for what you need. 

I've decided to give desktop 64 a try. I'm having problems with the wireless. I'll post separately. Thanks for all the good info!

---

