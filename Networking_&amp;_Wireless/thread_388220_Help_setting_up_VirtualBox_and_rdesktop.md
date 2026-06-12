---
title: "Help setting up VirtualBox and rdesktop"
date: 2007-03-19
forum: Networking &amp; Wireless
---

### Post by rianquinn on 2007-03-19
I really like the rdesktop stuff and would love to get it working on my Laptop. I tired Qemu but failed. Its to slow. And Windows crashes all the time with kqemu. VirtualBox is REALLY fast, and easy to setup. I love it.

From what I understand, Qemu works because you can forward the 3389 port to the localhost. Has anyone gotten VirtualBox to work with rdesktop. If not, could someone maybe help me get it working.

My Laptop is a Gateway Tablet (CX210X), and my internet connection is Wireless which is managed using NetworkManager. 

Thanks,
Rian

error:
```

Autoselected keyboard map en-us
ERROR: connect: Connection refused

```

---

### Post by lopop on 2007-03-19
Hi..  I'm also just tring to use the VirtualBox. 

have you click at the "Devices" => Remote Display?  The icon of VRDP (at bottom VirtualBox)  will turn 'Blue'  when it's activated.

But my problem is I can't seamless. It'll open the whole window and not just the program.

 (example for IE)

*terminal*
$  rdesktop -A -s "c:\seamlessrdp\seamlessrdpshell.exe C:\Program Files\Internet Explorer\iexplore.exe" localhost:3389 -u administrator -p password


anybody can help for this?

---

### Post by rianquinn on 2007-03-19
I can confirm this problem. It lets me log in now, but I get the whole window. To add, iexplore never comes up, instead the whole desktop is opened including what ever apps you already had opened.

Does anyone know who to fix this?

---

### Post by kilou on 2007-05-21
You must start the VM, login THEN LOGOFF. If the VM is logged in you'll get the whole desktop diplayed. If the VM is logged off it should work.

---

### Post by jiminycricket on 2007-05-21
I wonder if this a problem with XP being limited to a single remote user.  There's an easy patch to make it unlimited on google.

---

### Post by kilou on 2007-05-21
Have a look at this thread:

[http://ubuntuforums.org/showthread.php?t=433359](http://ubuntuforums.org/showthread.php?t=433359)

Also look in page #11 for ways to open multiple applications on a single rdesktop connection. The XP patch for multiple connections seems to only allows multiple applications to be launched if they are on different user accounts. The method on page 11 above will allow to have multiple open applications on the same account in XP, which is much more convenient.

---

