---
title: "NFS Root rebooting loop"
date: 2008-09-16
forum: Networking &amp; Wireless
---

### Post by click170 on 2008-09-16
I've configured a system according to the crude howto at [https://help.ubuntu.com/community/DisklessUbuntuHowto](https://help.ubuntu.com/community/DisklessUbuntuHowto) but I've reached a problem I'm having trouble solving.

The tftp server is set up, the nfs exports are set up, and the machine boots the kernel from tftp and begins the boot process, up until bringing up eth0.

The first message is eth0: link up, and then it spits out various ip addresses (address, gateway, broadcast, dns0, dns1, netmask), the domain, the rootserver, and a field for 'rootpath:' as well but rootpath is blank.

I have configured /etc/initramfs-tools/initramfs.conf with the correct host and mount information, as well as setting BOOT to nfs instead of local, I have tried adding 'rootpath=' to the append line in the pxelinux.cfg default file, but that didn't solve it... I'm at a loss.  I have also just read through the entire man page on my dhcp server to see if there is a rootpath option that I missed, but there was nothing.  

Currently, the machine boots the kernel, brings up the interface, and then attempts to mount the nfs directory.  Checking the logs on the nfs server, I can see that it is successfully mounting the correct directory, but after that log message appears, there is another below it;

" refused unmount request from 192.168.1.3 for /root (/): not exported "


Does anyone know what I'm doing wrong?  I'm frustrated with how the HowTo that I am trying to use seems to be ***-backwards in places, and yet it's one of the only pages that comes up in a search.

Edit:  I should clarify that after the changes to initramfs.config, I redit mkinitramfs and moved the newly created file to the tftp server in place for booting.  The HowTo doesn't say to do this in that order, but it doesn't make sense to me not to since it wouldn't take effect if you didn't.  Also, I saw it used on [http://developer.novell.com/wiki/index.php/HOWTO:_Convert_Ubuntu_to_Diskless](http://developer.novell.com/wiki/index.php/HOWTO:_Convert_Ubuntu_to_Diskless) which albeit is rather old and outdated, was at least easier to understand then the one above.

---

### Post by click170 on 2008-09-16
Alright, I concede my own idiocy.  Once again, another problem between keyboard and chair.

"refused unmount request from 192.168.1.3 for /root (/): not exported"

For anyone running into a similar problem or error message, for me this was caused by my forgetting to `cp -ax / /mnt/`, as I had been doing this with Debian for several other systems and the repetition must have made me skip a step for this particular instance.  After copying the files from the Ubuntu root to the /nfsroot section, the boot process proceeded normally.

What really confused me about this obstacle was the error message I was trying to track down, the one above.  The symptoms were that when the kernel was booted and it was bringing up drivers for the various devices, it brought up eth0, printed out some info it recieved (ip addresses, etc) and then attempted the mount.

I should have clued in to the logs on the NFS server;
Sep 16 14:53:25 bob mountd[4724]: authenticated mount request from 192.168.1.3:969 for /nfsroot (/nfsroot)
Sep 16 14:53:30 bob mountd[4724]: refused unmount request from 192.168.1.3 for /root (/): not exported

The last message had me thinking it was trying to do something like mount/unmount it's root drive, but that's not shared in the exports file.
It turns out that the first message indicates that it successfully mounted the export, and I can only guess that when there were no files in '/' after mounting the export, it incorrectly attempted to unmount it producing the last error message seen above.

Hopefully nobody else will have this problem, but if they do, this page might help.

---

