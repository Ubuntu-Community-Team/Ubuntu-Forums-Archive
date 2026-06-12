---
title: "i want maximize my ubuntu window in virtual box"
date: 2010-11-01
forum: New to Ubuntu
---

### Post by raja2k9 on 2010-11-01
hi ......i am using ubuntu in virtual box...i cant maximize the window....
i hav installed guest additions and browse thro CD and i find the vboxlinuxadditions-amd64.run file...when i click that...its showing The file is of unknown type.


Note:whn i type sudo nautilus it shows following message but it allows to browse the cd
** (nautilus:1523): WARNING **: Failed to get the current CK session: GDBus.Error:eek:rg.freedesktop.ConsoleKit.Manager.Gen eralError: Unable to lookup session information for process '1523'
(nautilus:1523): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

(nautilus:1523): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

---

### Post by migs73 on 2010-11-01
Open a terminal in Ubuntu (Applications > Accessories > Terminal) and cd (change directory) to the virtual cd rom where the guest additions is mounted, probably```
cd /media/
```type ```
 ls 
```to list the files in that directory (your looking for the VboxLinuxAdditions-amd64.run file) then run the following;
```
sudo sh ./VboxLinuxAdditions-amd64.run
```
It'll then prompt you for your password (the one you set up on install) type it in (nothing will appear on screen, this is normal) and hit enter.
That should get it going.



BTW Welcome to the forums!! :)

---

### Post by migs73 on 2010-11-01
Also do you have DKMS installed on your guest? I was checking my thread from when I had problems with guest additions  ([http://ubuntuforums.org/showthread.php?t=1593674](http://ubuntuforums.org/showthread.php?t=1593674)) when I remembered it.

To find out go to the guest system System > Administration > Synaptic Package Manager (it'll ask for your password). Go to the search box in the corner and type in dkms. If it looks like the screen shot then its installed, if not click on it and 'Mark for installation' then click the green arrow at the top to apply it.

Then try the code in the previous post.

---

### Post by raja2k9 on 2010-11-01
hi ..now i got some other message...whn i try to run it shows...Error in MD5 checksum...how can i correct this...

---

### Post by yeats on 2010-11-01
> hi ..now i got some other message...whn i try to run it shows...Error in MD5 checksum...how can i correct this...
Can you post the full command you've used and the output?

---

### Post by raja2k9 on 2010-11-05
[EMAIL="root@raja-VirtualBox:/media/VBOXADDITIONS_3.2.8_64453"]root@raja-VirtualBox:/media/VBOXADDITIONS_3.2.8_64453[/EMAIL]# ls
32Bit        VBoxLinuxAdditions-amd64.run    VBoxWindowsAdditions.exe
64Bit        VBoxLinuxAdditions-x86.run      VBoxWindowsAdditions-x86.exe
AUTORUN.INF  VBoxSolarisAdditions.pkg
autorun.sh   VBoxWindowsAdditions-amd64.exe
[EMAIL="root@raja-VirtualBox:/media/VBOXADDITIONS_3.2.8_64453"]root@raja-VirtualBox:/media/VBOXADDITIONS_3.2.8_64453[/EMAIL]# sudo sh ./VboxLinuxAdditions-amd64.run
sh: Can't open ./VboxLinuxAdditions-amd64.run

this is what i get now......but smetimes i get error in MD5 checksum

---

### Post by migs73 on 2010-11-05
Try deleting you guest additions and downloading again. I had that same problem with mine

[http://ubuntuforums.org/showthread.php?t=1593674](http://ubuntuforums.org/showthread.php?t=1593674)

---

### Post by BugBuster on 2010-11-05
> **raja2k9 said:**
> [EMAIL="root@raja-VirtualBox:/media/VBOXADDITIONS_3.2.8_64453"]root@raja-VirtualBox:/media/VBOXADDITIONS_3.2.8_64453[/EMAIL]# ls
32Bit        VBoxLinuxAdditions-amd64.run    VBoxWindowsAdditions.exe
64Bit        VBoxLinuxAdditions-x86.run      VBoxWindowsAdditions-x86.exe
AUTORUN.INF  VBoxSolarisAdditions.pkg
autorun.sh   VBoxWindowsAdditions-amd64.exe
[EMAIL="root@raja-VirtualBox:/media/VBOXADDITIONS_3.2.8_64453"]root@raja-VirtualBox:/media/VBOXADDITIONS_3.2.8_64453[/EMAIL]# sudo sh ./VboxLinuxAdditions-amd64.run
sh: Can't open ./VboxLinuxAdditions-amd64.run

this is what i get now......but smetimes i get error in MD5 checksum

I see that you have already switched to the root user..
```
root@raja-VirtualBox$
```

So in that case there is no need to use sudo again.. Try the command again without the sudo. Also is your guest operating system 64 bit? Else run the 32 bit guest additions

---

