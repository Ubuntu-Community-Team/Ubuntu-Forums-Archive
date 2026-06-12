---
title: "Connecting to windows network"
date: 2007-09-24
forum: Networking &amp; Wireless
---

### Post by Dwood108 on 2007-09-24
Hello 
when I try to connect to my windows computer Ubuntu can see the windows network and computer but when I try to access  the files on the computer I get "the folder contents could not be displayed" error message.

How can I access these files?

I am using Linuxmint Cassandra (which is based on Ubuntu)

I have been able to access the files before using other versions of Linux.

---

### Post by jasonhr on 2007-09-24
In have just had a hellish 12 hour ordeal doing this.

I started with this how to:-

[http://ubuntuforums.org/showthread.php?t=202605]("http://http://ubuntuforums.org/showthread.php?t=202605")

The real break through was when I did 

$ smbpasswd -a [username]

This added the samba password for each shared account and got me up and running! :guitar:

---

### Post by Dwood108 on 2007-09-25
I followed all the instructions in the link, which seems to have some effect as the windows computer is recognised by its correct  name, but still when I try to access the files on the windows computer I get the error "the folder contents could not be displayed"

Any other ideas?

---

### Post by Dwood108 on 2007-09-25
Further update:

If I go open my home folder and look in the network folder instead of going through the places menu, I can see the computer and can now see the shared drives, which is more than I could before.

However when I try to open the shared drives to view the contents I get the same error message "folder could not be displayed"

If I right click on one of these and show the properties it says 
'contents: unreadable'

is there anything else I can do to get access to these shared folders?

Thanks

---

### Post by jasonhr on 2007-09-25
still sounds like a samba synching thing with unix users. 

Did you do the $ smbpasswd -a [username] bit?

do you have firewalls running on the machines?

If you have firstarter on the feisty machine you can monitor any rejected ip addresses, might help.

---

