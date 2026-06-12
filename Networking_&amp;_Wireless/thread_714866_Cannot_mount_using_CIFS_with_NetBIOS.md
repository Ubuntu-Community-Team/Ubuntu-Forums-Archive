---
title: "Cannot mount using CIFS with NetBIOS"
date: 2008-03-04
forum: Networking &amp; Wireless
---

### Post by MrClearPore on 2008-03-04
Hello all.

I recently installed the latest **samba** -3.0.28- from the source package.  I did not use **aptitude** to install it this time, but I used to in the past.  The installation went smoothly; I received no apparent errors, and I was able to start the **smbd, nmbd, and winbindd** daemons without any problems either.  I even tested it by sharing a folder on my local network successfully.  So far so good.  However, the only thing I *cannot* do with the source-package version of **samba** that I *could* do with the aptitude version of samba, was accessing shared folders on a Windows network using the **CIFS** file system with **NetBIOS** names.

Here's an example that *used* to work before:
```
sudo mount -t cifs -o user=guest,rw,iocharset=utf8 //BEA/D /media/share
```
That used to mount fine.  Now when I enter the above, I get this error:
> mount: wrong fs type, bad option, bad superblock on //BEA/D,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


After I type **dmesg | tail** I get this:
> CIFS VFS: cifs_mount failed w/return code = -22

If I replace BEA with its IP address, I can mount it fine that way!  So it seems there's a problem with the **NetBIOS**.  As I mentioned above, I have the **winbindd** daemon running, so it should be able to convert NetBIOS names to IP addresses properly.  To test it out, I used the included program **wbinfo** and checked to see if the winbindd daemon was doing its job:

```
wbinfo --WINS-by-name=bea
```
> 192.168.1.5     bea

```
wbinfo --WINS-by-name=ryan
```
> 192.168.1.3     ryan

The reverse also works (converting IP address to NetBIOS name).

So what is going on here?  It looks like I should be able to use NetBIOS when mounting a share using **CIFS**, espcially since I can get it working with the IP address.  And since I can mount a share error free using the IP address, then I know that the structure of the mount command itself is fine (no errors on the line, no bad super blocks on the share, etc).

Any ideas?  By the way, when I configured samba, I enabled the **--with-smbmount** option.  I *am* able to mount fine using the **-t smbfs** (as opposed to -t CIFS), both with a NetBIOS name, and an IP address, so the problem is ONLY with NetBIOS on the **CIFS** file system.

Any help is appreciated!  Thanks in advance.

---

### Post by averagejoe1179 on 2008-06-20
hi, i had the same problem,
also, there does not appear to be much documentation online for such an issue

as it turns out, mount (at least the version that came with your distro) is compatible with a wins lookup for the cifs file system

instead, use the tool that came with you're samba package - **mount.cifs**
you will find it in *samba/sbin/mount.cifs*, next to the samba daemons

usage is easy - if you're confused simply press enter without any options and a help message will be printed

example of mount.cifs usage;
```
mount.cifs //tequila/shared /home/foo/shared -o user=vivalamexico,pass=oddduckout
```

this will mount the share *"shared"* from the *tequila* server to your */home/foo/shared directory*, using the *vivalamexico* samba account with the password *oddduckout*

there is yet no way to make mount.cifs work with your /etc/fstab 
however, anything mounted by mount.cifs is considered as much of a partition as anything mounted by mount, so it may be handy to add your cifs shares, for ease of unmounting, etc.
```

/etc/fstab entrys look like this:
//tequila/shared  /home/foo/shared  cifs  username=vivalamexico,password=oddduckout 0 0
```

(think thats right, working from memory)
enjoy, hope, mount.cifs does the trick for you

---

### Post by MrClearPore on 2008-07-03
Thanks for the information :)
I decided to go back to using the repository version of Samba, but if I ever decide to tinker around with the source version in the future, I'll make sure to try out your suggestion, and I'll let you know how it went.

Ryan.

---

