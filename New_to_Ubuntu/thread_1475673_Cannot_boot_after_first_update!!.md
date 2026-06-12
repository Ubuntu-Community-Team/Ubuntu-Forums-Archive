---
title: "Cannot boot after first update!!"
date: 2010-05-07
forum: New to Ubuntu
---

### Post by _nikolaos on 2010-05-07
This is very undesirable. Working in Gnome, I downloaded the first updates as asked, and rebooted.

Booting failed.

This is what I see:

```

fsck from util-linux-ng 2.17.2

[B]udevd[351]: SYSFS{}= will be removed in a future udev version, please use ATTR= to match the event device, or ATTRS{}= to match a parent device, in /etc/udev/rules.d/56-hpmud_support.rules:10

udevd[351]: SYSFS{}= will be removed in a future udev version, please use ATTR= to match the event device, or ATTRS{}= to match a parent device, in /etc/udev/rules.d/z80_user.rules:1

udevd[351]: BUS= will be removed in a future udev version, please use SUBSYSTEM= to match the event device, or SUBSYSTEMS{}= to match a parent device, in /etc/udev/rules.d/z80_user.rules:1

[/B]init: ureadahead-other main process (695) terminated with status 4

```

And there is no progress.

What's happened?

---

### Post by tuxmaster on 2010-05-07
I had the same error messages. To eliminate them just do the following:

You need to boot with an boot cd and go to the rescue mode. There mount  your root file system / and so you are able to edit files.
 
Edit the files at the end of the message lines with vi and replace SYSFS  with ATTR and BUS with SUBSYSEM everywhere in theses files.

like this:

```
:%s/SYSFS/ATTR/g
       and
:%s/BUS/SUBSYSTEM/g
```To fix the "no boot" problem you should try to comment out all file systems in /etc/fstab you don´t need at boot time (like external shares ore removable storage). If this does not work then try to change the entries in /etc/fstab from [FONT=Courier New]**"UUID=..."**[/FONT] to something like [FONT=Courier New]**"/dev/sd..."**[/FONT].

The example below should help ...

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
#Entry for /dev/sdb1 :
UUID=e630e0ca-bb8e-46c8-89f2-059f2ed706e2    /    ext3    relatime,errors=remount-ro    0    1
#Entry for /dev/sdb2 :
UUID=19b5c973-f002-459c-ba11-7edd2cb584fa    none    swap    sw    0    0
...
```change the entries above to:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>   <options>       <dump>  <pass>

proc    /proc    proc    defaults    0    0
#Entry for /dev/sdb1 :
/dev/sdb1    /    ext3    relatime,errors=remount-ro    0    1
###UUID=e630e0ca-bb8e-46c8-89f2-059f2ed706e2    /    ext3     relatime,errors=remount-ro    0    1
#Entry for /dev/sdb2 :
/deb/sdb2    none    swap    sw    0    0
###UUID=19b5c973-f002-459c-ba11-7edd2cb584fa    none    swap    sw    0    0
...
```Good luck ;)

Regards Tom

---

### Post by christopherbalz on 2010-05-08
I had the same problem.  The issue was old entries in fstab that I did not need.  I did not bother with the SYSFS messages, as everything works - probably a future update will clean that up.

Here is the diff from my old fstab as it was directly after the upgrade from Ubuntu 9.10 to Ubuntu 10.04, and my current one (showing commands to get diff):

```
//cbalz-tp-r51-0/.../~ $ cd /etc
//cbalz-tp-r51-0/.../etc $ diff fstab fstab
fstab            fstab_backup     fstab.BAK        fstab-bak-may-8  fstab.pre-uuid   
//cbalz-tp-r51-0/.../etc $ diff fstab fstab-bak-may-8
8c8
< # UUID=e382a19f-c641-45d6-b353-b4498473c53b  none            swap         sw                                   0  0  
---
> UUID=e382a19f-c641-45d6-b353-b4498473c53b  none            swap         sw                                   0  0  
11c11
< # UUID=689CBBA69CBB6CE6                      /media/windows  ntfs         nls=utf8,umask=0222                  0  0  
---
> UUID=689CBBA69CBB6CE6                      /media/windows  ntfs         nls=utf8,umask=0222                  0  0  
```

Basically there was an entry for an old Windows partition which I had removed a couple years ago, and a swap partition that I was no longer using.  Not sure why that entry was there as I already had a swap partition.

---

### Post by _nikolaos on 2010-06-13
Firstly I thought it was due to a single problem that prevented normal booting. But, after I read your answers, I realized there were actually two problems causing bad linux boot-loading.

The first, which was about *udev*, I did the suggested replacements (after having kept files' copies) in 

/etc/udev/rules.d/z80_user.rules
/etc/udev/rules.d/56-hpmud_support.rules

and message doesn't appear during booting.

As for the second one, it is a mess with **/etc/fstab**. It cannot mount my filesystems automatically on boot. I also discovered that by pressing "S" the system skips any mounting attempts and goes on quickly. I am mounting things manually after logging in and I am satisfied with this now.

So I consider this thread as solved. Thanks for your response.

---

