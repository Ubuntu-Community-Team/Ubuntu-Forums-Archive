---
title: "Linkstation NAS, CIFS, Heron"
date: 2008-06-06
forum: Networking &amp; Wireless
---

### Post by rp3 on 2008-06-06
Hey guys and gals...

I recently upgraded to Heron and all seemed fine until yesterday when I did some updates.  My connection to the Linkstation no longer works?  I had the fstab working, etc.. but now it fails with 
[  661.532357]  CIFS VFS: Error connecting to IPv4 socket. Aborting operation
[  661.532364]  CIFS VFS: cifs_mount failed w/return code = -111

So I found this post that is a like a how to on CIFS and mounting and it didn't help either so I am posting my stuff, so hopefully I can get some help.

Here is my fstab
//linkstation/pictures /mnt/linkpics cifs username=XxX,password=XxX	0	0
I know it's not very secure but inside my house is, so no worries.  This generates the above error or this when i do a 'sudo mount -a' command.
mount error 111 = Connection refused
Refer to the mount.cifs(8) manual page (e.g.man mount.cifs)


So what can I do.  Like others all my music and pictures are on this device.  I will be out of town for the weekend so hopefully when I get back I will have some fixes maybe?

Oh and a couple other things.

sambafs is installed.  Like I said it worked before???  I also see this in the dmesg
[   55.530416]  CIFS VFS: Error connecting to IPv4 socket. Aborting operation
[   55.530421]  CIFS VFS: cifs_mount failed w/return code = -101

Hope that helps?

Thanks,

Rp

---

### Post by dmizer on 2008-06-06
take a look at the second link in my sig.

log in and make sure that you have an internet connection.  then run this command:
```
sudo mount -a
```
and let me know if you have access to your shares then.

---

### Post by rp3 on 2008-06-06
> **dmizer said:**
> take a look at the second link in my sig.

log in and make sure that you have an internet connection.  then run this command:
```
sudo mount -a
```
and let me know if you have access to your shares then.

Ok will give it a go when I get back, I am heading to the Nascar Trucks and IRL race this weekend in Dallas, so Sunday when I get back I will give it a go.

Thanks!

---

### Post by rp3 on 2008-06-08
> **dmizer said:**
> take a look at the second link in my sig.

log in and make sure that you have an internet connection.  then run this command:
```
sudo mount -a
```
and let me know if you have access to your shares then.

Ok couple questions.

I have the NAS in the /etc/hosts file so the name is known and I can ping it.  Also have SAMbafs installed.  This used to work?  Why do I need WINS stuff loaded?

Hmmm, I guess I can try that, but not sure why I need that, what changed between Gutsy and Heron that requires this?  Just curious.

Also if I had smbfs installed from Gutsy, I assume it still works in Hardy, maybe this is my problem?  How does one verify smbfs is working.  when I do a "apt-get install smbfs" i get a already installed message?

---

### Post by dmizer on 2008-06-09
> **rp3 said:**
> I have the NAS in the /etc/hosts file so the name is known and I can ping it.  Also have SAMbafs installed.  This used to work?  Why do I need WINS stuff loaded?

Hmmm, I guess I can try that, but not sure why I need that, what changed between Gutsy and Heron that requires this?  Just curious.
i'm happy to explain.

/etc/hosts is insufficient because cifs does not query /etc/hosts for name resolution, it queries netbios which is resolved through winbind/wins.

> **rp3 said:**
> Also if I had smbfs installed from Gutsy, I assume it still works in Hardy, maybe this is my problem?  How does one verify smbfs is working.  when I do a "apt-get install smbfs" i get a already installed message?
smbfs will have been removed during the distribution upgrade process.  you cannot get smbfs operational in hardy unless you compile it.  howto here: [http://ubuntuforums.org/showthread.php?t=707370](http://ubuntuforums.org/showthread.php?t=707370)

in hardy, when you do:
```
sudo apt-get install smbfs
```
you are only installing the smbfs [metapackage](https://help.ubuntu.com/community/MetaPackages?).  this metapackage used to contain the actual smbfs package, but in hardy, it only installs cifs and its dependencies (like winbind and smbtree).

---

### Post by rp3 on 2008-06-09
> **dmizer said:**
> i'm happy to explain.

/etc/hosts is insufficient because cifs does not query /etc/hosts for name resolution, it queries netbios which is resolved through winbind/wins.


smbfs will have been removed during the distribution upgrade process.  you cannot get smbfs operational in hardy unless you compile it.  howto here: [http://ubuntuforums.org/showthread.php?t=707370](http://ubuntuforums.org/showthread.php?t=707370)

in hardy, when you do:
```
sudo apt-get install smbfs
```
you are only installing the smbfs [metapackage](https://help.ubuntu.com/community/MetaPackages?).  this metapackage used to contain the actual smbfs package, but in hardy, it only installs cifs and its dependencies (like winbind and smbtree).

Ok, thanks for taking the time, I will work on this today and let you know.

:)

Ok installed Samba and it works now, but not sure what exactly fixed it, I think there were a couple of things not working, it seems like my NAS was not working correctly so after a reboot, and a reboot on this machine, it all seems to work now.  Now off to do the other machines ...

Thanks for the patience and help..


ok now it just gets wierd, I did the "sudo aptitude install smbfs" on the second machine and didn't do the wins stuff, then just tried to see if I could see the NAS and I could.  So no compile of SAMBA required for me?  At least on this machine.  have a couple more to do...  Hmmmm but either way all is well now ;).. As this machine serves my house for music and video from that NAS so it was important to get it up and running, and now it is.

kewl.

Thanks,

---

