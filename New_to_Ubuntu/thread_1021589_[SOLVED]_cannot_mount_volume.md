---
title: "[SOLVED] cannot mount volume"
date: 2008-12-25
forum: New to Ubuntu
---

### Post by 007casper on 2008-12-25
I have an old hard drive that I use externally to transfer files.  Now, whenever I use my usb connection to connect my external hard drive I get a message that says "unable to mount drive" and continues...

Cannot mount volume
Unable to mount the volume 'Storage'.
Details: $LogFile indicates unclean shutdown (0,0) Failed to mount ´/dev/sdb5': Operation not supported Mount is denied because NTFS is marked to be in use. Choose one action: Choice 1: If you have Windows then disconnect the external devices by cliking on the 'Safely Remove Hardware' icon in the windows taskbar then shutdown Windows cleanly.  Choice 2: If you dont have windows then can use the "force" option for you own responsibility. For example type on the command line: mount -t ntfs-3g/dev/sdb5/media/Storage -o force Or add the option to the relevant row in the /etc/fstab file: /dev/sdb5/media/Storage ntfs-3g force 0 0
-
then I get this message right after
-
DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
-
I guess the first warning is telling me the options I have in order to mount the drive, but I am not sure how to go about it.  I just dont want to mess up anything in the external hard drive, or the ubuntu platform. I never used to have this problem.  

It used to work before...

---

### Post by natehall on 2008-12-25
I made the mistake once of formatting an usb stick with a Linux ext3 file system. After that Ubuntu would no longer recognize the stick! Looks like you have something similar in play. Try 

                           sudo fdisk -l

 and post it here.( This should list all your partitions)

---

### Post by xjcannonx on 2008-12-25
Do you have a windows machine. has this external drive been connected to it?

If so you will need to plug it back into windows and 'safely remove' it from there.

This is the best way to do it, if this doesnt work, there are other ways, but lets try this one first...

---

### Post by 007casper on 2008-12-25
Yes I have a windows machine.  I plugged it back to XP and it wouldnt let me "safely remove the harddrive" so I turned off the computer with the external drive attach to it.  Then, unplugged the usb, and connect it to the server that has ubuntu... pronto... awesome it works.

---

### Post by aquamammal on 2008-12-28
What if you don't have a Window's machine?

Haha, I have the same problem.

---

### Post by xjcannonx on 2008-12-30
Do you mean you have another OS that your drive was connected to? I guess you could try something similar on that machine

---

