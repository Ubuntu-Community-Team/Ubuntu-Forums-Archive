---
title: "No 'build' directory"
date: 2006-11-18
forum: Networking &amp; Wireless
---

### Post by Lord_Dicranius on 2006-11-18
I've followed 2 different tutorials on installing the Madwifi-ng drivers:
-[Madwifi/UserDocs/FirstTimeHowTo](http://madwifi.org/wiki/UserDocs/FirstTimeHowTo)
-[WifiDocs/Driver/Madwifi](https://help.ubuntu.com/community/WifiDocs/Driver/Madwifi)

During both of these, I keep running into the same error:
```
lorddicranius@icarus:/usr/src/madwifi-ng$ sudo make
/bin/sh: line 0: cd: /lib/modules/2.6.15-27-686/build: No such file or directory
Makefile.inc:69: *** /lib/modules/2.6.15-27-686/build is missing, please set KERNELPATH.  Stop.
```

I went through and made sure I met all the [requirements](http://madwifi.org/wiki/Requirements) as stated on the Madwifi.org site.  What's supposed to be in this 'build' directly anyways?  I'm using Dapper.  Any other information that's needed, please let me know.

Thanks in advance!

---

### Post by Lord_Dicranius on 2006-11-18
So apparently I didn't get everything done before getting to the "sudo make" command.  eternalswd in the Ubuntu IRC channel had me run this command:
```
sudo apt-get install build-essential linux-headers-`uname -r` gcc-3.4 subversion sharutils
```

I thought I seen that before, and ran it (excluding the gcc-3.4 because I already had 4.x installed), but apparently not.  So I ran that command and let gcc-3.4 compile and then the linux-headers-`uname -r` started to compile.  After that, I was able to run "sudo make" successfully.

But then I ran into another problem.  When I try to run:
```
wlanconfig ath0 create wlandev wifi0 wlanmode sta
```

...I get this error:
```
wlanconfig: ioctl: No such device
```

I ran a quick search of the forums and wasn't able to come up with anything.  A quick Google search came up with something, but it was a fix for FC4, and couldn't be applied to Ubuntu.

---

### Post by Lord_Dicranius on 2006-11-18
Not sure what happened again, but I re-ran through all the steps and the command "wlanconfig ath0 create wlandev wifi0 wlanmode sta" and it worked.  Now I'm stuck on trying to get Network Manager (or find another connection manager) to see my wifi card (Proxim Orinoco Gold 8470-FC).  It's only giving me my integrated card as an option to connect to wireless networks.

---

