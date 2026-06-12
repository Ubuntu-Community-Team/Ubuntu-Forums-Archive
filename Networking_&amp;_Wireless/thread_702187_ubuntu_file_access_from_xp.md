---
title: "ubuntu file access from xp"
date: 2008-02-20
forum: Networking &amp; Wireless
---

### Post by Joe Marroso on 2008-02-20
I am new to Linux, completely self taught, but fearless when it comes to computers. I recently installed 7.10 and activated the Samba package.

Here is the problem, I am trying to put the 7.10 desktop on my home network.  I can see and access the windows computers from ubuntu.  I can see the designated "shared file" on ubuntu, but when I click on it, I get a user/pswd box.  None of the username/passwords that I put into the Terminal (sudo passwd...) work.

This is very vexing.  I have tried many "work arounds" but I can't get past the user/pswd box.

Thank You
joe

---

### Post by ruy_lopez on 2008-02-20
Did you create a "smbpasswd" entry?

replace <username> with your Windows username, if you don't use a password to log into windows, leave the password blank.

```
sudo smbpasswd -a <username>
sudo smbpasswd -e <username>
```

then restart samba.

---

### Post by Joe Marroso on 2008-02-20
This info may be relevant:

joe@joe-desktop:~$ sudo ifconfig
[sudo] password for joe:
eth0      Link encap:Ethernet  HWaddr 00:50:BA:C4:01:3C  
          inet addr:192.168.1.40  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::250:baff:fec4:13c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:612 errors:0 dropped:0 overruns:0 frame:0
          TX packets:494 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:86134 (84.1 KB)  TX bytes:62401 (60.9 KB)
          Interrupt:11 Base address:0x6000 

eth1      Link encap:Ethernet  HWaddr 00:0D:87:52:E6:52  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11 Base address:0xec00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:203 errors:0 dropped:0 overruns:0 frame:0
          TX packets:203 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:18932 (18.4 KB)  TX bytes:18932 (18.4 KB)

joe@joe-desktop:~$

---

### Post by ruy_lopez on 2008-02-20
See this thread:

[http://ubuntuforums.org/showthread.php?t=202605&highlight=share]("http://ubuntuforums.org/showthread.php?t=202605&highlight=share")

If you are being prompted for a password, it's probably nothing to do with your network settings.

---

### Post by Joe Marroso on 2008-02-20
Continued

When the Windows network permission box appears after clicking on the shared folder on ubuntu, the username changes to the name of my ubuntu computer (Joe-Desktop).  No matter what I write in, it changes to joe-desktop/XXXX.

I can see the unbuntu by IP address search or mshome workgroup in the explorer.

---

### Post by Joe Marroso on 2008-02-20
Ok Ruy

The key was that my xp did NOT have a resident password.  So I used the -e command with <enter> as the password.  It works.

Before closing out this thread, what is the command to keep my shared file shared after re-booting?

Thanks again
joe

---

### Post by Joe Marroso on 2008-02-20
Ooops.  Spoke too soon.

I can access ubuntu shared files from my XP.

But, after playing with "Properties" on the shared folder, I am still unable to transfer files from xp to ubuntu.  Are their samba codes I need to install to prepare for this.

---

