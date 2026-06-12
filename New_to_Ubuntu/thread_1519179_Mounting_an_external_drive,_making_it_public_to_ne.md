---
title: "Mounting an external drive, making it public to network"
date: 2010-06-27
forum: New to Ubuntu
---

### Post by breeness on 2010-06-27
Hi,

So thanks to help on this forum, I believe I successfully mounted my external USB drive to the NAS server I set up. How do I check that this has been successfully mounted?

The next step is that I would like to make this external drive public and I can't remember how exactly to make it accessible to my network with all chmod permissions. Could I get some help with that?

Thanks so much guys! I have now written a total of like 10 lines of Linux, so I am about as newb to this as you can get!

---

### Post by papibe on 2010-06-27
Regarding the first part...
What are you running on your server? Is it Ubuntu server? If so...
You can use this to see what is mounted where:
```
mount -l
```
Your external hard drive should be named something like /dev/sdb1 or similar. If it's not mounted, you can see all available hard drives by doing:
```
sudo fdisk -l
```
If you recognize your external drive in that list, you can mount it manually. For example:
```
mount /dev/sdb1 /media/external
```

A couple of times I had to **reboot** my server with the external drive on, so that the drive would be recognized.

I hope it helps.

Obs.: I believe there is a way to automount the drive like in Ubuntu desktop, but I haven't tried it (research "usbmount").

---

### Post by breeness on 2010-06-27
I am running ubuntu server.

It seems to be mounted successfully. Now, how do I make it available to the other systems on the network? Is it like the chmod I did to make the NAS have a public folder? I can't remember how to do that >.<

---

### Post by papibe on 2010-06-27
Not exactly. Once it's shared, chmod will help you to design who sees what.

You have 2 options:

Installing Samba, and creating a samba share. This works very well if you have Windows clients. Review this: [http://amazingrando.wordpress.com/2007/06/03/share-folders-via-samba-without-a-password-easy/]("http://amazingrando.wordpress.com/2007/06/03/share-folders-via-samba-without-a-password-easy/")

Using nfs. This will be a lot faster, but more tricky for Windows machines. Check this tutorial: [http://ubuntuforums.org/showthread.php?t=249889&highlight=nfs]("http://ubuntuforums.org/showthread.php?t=249889&highlight=nfs")


Good Luck.

---

### Post by breeness on 2010-06-27
oh! I have samba!

I already made two folders on the main hard drive accessible by my windows machines, but I don't know how to do it for the mounted external drive?

I have it set at  /mnt/usb_ext/

But I can't figure out how to make it "public"?

---

### Post by papibe on 2010-06-27
Something like this:
```
[Share name]
writable = yes
path = /path/to/directory
public = yes
guest ok = yes
guest only = yes
guest account = nobody
browsable = yes
```

Where "/path/to/directory" is the dir where you mounted the hard drive. Check the details on the link that I gave you above.

Cheers.

---

### Post by breeness on 2010-06-27
that really helped!

But now I seem to have a folder filled with things I don't recognize!!

I wonder if I mounted some mysterious drive? I have nothing else attached...and I can't seem to figure out where my external hard drive is...

THIS IS SO COMPLICATED!! hahaha

---

### Post by papibe on 2010-06-27
It is possible that you got confused about what are you mounting. May be it would help if you shutdown the server, remove the usb drive, reboot, and check with fdisk what exists by its own on the server.

Then plug the drive, and reboot again. Now fdisk should give you a different list of hard drives available, making it easier to recognize the external one.

I hope it helps.

BTW.: managing a server it is indeed more tricky ...and geeky. But when you accomplished your goal, the rewards are... well ... super geeky too, ha ha! ):P

---

### Post by breeness on 2010-06-27
Is it possible that it is not seeing my external drive because of its format?

I found that my boyfriend had plugged his ancient MP3 player into my linux machine (perhaps hoping it would make it onto the server) and that explains the "mystery" files.

So I wonder if it can't "see" my external drive? I have seen some things about the NTFS drives being um more difficult to mount? I can't seem to find one simple solution that makes sense to a newb... Any suggestions? 

Thanks for the help by the way!!

---

### Post by papibe on 2010-06-27
I'm getting to the limit of my expertise here. NTFS should be no problem since Ubuntu server come with the necessary package (ntfs-3g). You can check if it is installed by doing:
```
dpkg -l ntfs-3g
```

BTW, I just tried to mount an NTFS usb drive, and it works.

How often do you update your server? It probably won't solve your problem, but keeping your server updated is always a good idea:
```
$ sudo apt-get update
$ sudo apt-get upgrade
```

and then may be try again...

---

