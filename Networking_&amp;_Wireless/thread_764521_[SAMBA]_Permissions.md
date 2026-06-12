---
title: "[SAMBA] Permissions"
date: 2008-04-24
forum: Networking &amp; Wireless
---

### Post by Roguespider13 on 2008-04-24
I have a home file server setup. It is working and I can put files on the server, however I want to make changes to the way it does permissions and I've been having trouble.

I would like to set things up dealing with 3 users: 1 Ubuntu, 2 windows users. WinUser1 would have the ability to create files and modify them as needed (but not delete them). WinUser2 would be only for reading files. UbuUser has the same permissions as WinUser1 except he would be the only person who could delete files. This is mainly to prevent accidental deletions.

Now I really haven't found a way to do that in SAMBA so I looked elsewhere and found sticky bits. I've tried using it but I just can't get things to work. Can anyone help?

---

### Post by SpaceTeddy on 2008-04-24
if you want more than one user, you will need to enable acl support in your filesystem and let samba handle the file permissions via that one (i think that is the only way)

i'll assume you use ext3 as the fs for the server - in that case, you should install the acl support for the filesystems with
```
sudo apt-get install acl
```
that will give you the commands "getfacl" and "setfacl"

next you specificially need to enable acl on your harddrive. Since i do not know how many partitons or drives you have, i'd say enable acl's on all ext3 drives.
**CAUTION: doing the next steps wrong will most likely render your system useless !!!**

so, edit the /etc/fstab file and add the acl option to all required drives. As an example, i will print out my fstab here:
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=64237eb5-badc-2349-bb6d-a94f98456f69 /               **ext3**    defaults,errors=remount-ro[COLOR="Blue"],acl[/COLOR] 0       1
# /dev/sda2
UUID=46392629-03a4-4f0f-7545-63524472bdef /home           **ext3**    defaults,[COLOR="Blue"]acl[/COLOR]        0       2
# /dev/sda1
UUID=1A346C0E346BEAE9 /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda4
UUID=205cb155-9cc0-4531-9a4e-cf905dad0fb1 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

**do not copy this file over - this is just an example !**

the bold bits show which lines to edit (all with ext3 in them), the blue is what you need to add in order to active acl. Once that is done, check and recheck that there are no spaces, juct a comma inbetween the options. 
**make sure that this is right !**
now, you have been warned - use this command to edit the file:
```
gksu gedit /etc/fstab
```
then reboot your system. If it still starts, you're set. next, check with this command if acl support got enables:
```
mount |grep acl
```
you should see something like:
> mount |grep acl
/dev/sda5 on /mnt/sda5 type ext3 (rw,**acl**)
/dev/sdb5 on /mnt/sdb5 type ext3 (rw,**acl**)

which means those drives now have full acl support. 

right - next thing is to read up on how the acl's work with this
```
man getfacl
man setfacl
```
then set the file permission and make sure that there is no anonymous connections to the samba server - everybody needs to authenticate...

i know the end is a bit short, but i am not even sure if there is an easier way to do it. That's just the only way i have done it before :)

try this, and if you run into problems, just ask about them
hope it helps :)

---

### Post by g_zoli on 2009-06-01
Hello! 

I have followed this how-to, but i don't have success.


If I set samba share properties of directory they would give read permisson for all other user. But I would give read just a few people with ACL configuration.

If the target directory is in my home, there is not readable for other people, instead of ACL setting.


If one user browse my shared files in network, they dont see the directory which have acl (read) permisson for they. 

my samba conf:
[http://paste.ubuntu.com/181294/](http://paste.ubuntu.com/181294/)

How should I setting the share and properties, for the simple gui-based share for more usert ? (I would like use ACL for more partner user.)

Pls, help me!





> **SpaceTeddy said:**
> if you want more than one user, you will need to enable acl support in your filesystem and let samba handle the file permissions via that one (i think that is the only way)

i'll assume you use ext3 as the fs for the server - in that case, you should install the acl support for the filesystems with
```
sudo apt-get install acl
```that will give you the commands "getfacl" and "setfacl"

next you specificially need to enable acl on your harddrive. Since i do not know how many partitons or drives you have, i'd say enable acl's on all ext3 drives.
**CAUTION: doing the next steps wrong will most likely render your system useless !!!**

so, edit the /etc/fstab file and add the acl option to all required drives. As an example, i will print out my fstab here:

**do not copy this file over - this is just an example !**

the bold bits show which lines to edit (all with ext3 in them), the blue is what you need to add in order to active acl. Once that is done, check and recheck that there are no spaces, juct a comma inbetween the options. 
**make sure that this is right !**
now, you have been warned - use this command to edit the file:
```
gksu gedit /etc/fstab
```then reboot your system. If it still starts, you're set. next, check with this command if acl support got enables:
```
mount |grep acl
```you should see something like:

which means those drives now have full acl support. 

right - next thing is to read up on how the acl's work with this
```
man getfacl
man setfacl
```then set the file permission and make sure that there is no anonymous connections to the samba server - everybody needs to authenticate...

i know the end is a bit short, but i am not even sure if there is an easier way to do it. That's just the only way i have done it before :)

try this, and if you run into problems, just ask about them
hope it helps :)

---

### Post by g_zoli on 2009-06-01
I try solve my share problem, but I don't have good luck. 

I set acl for my home folder, I add 'acl' to fstab too.
I log on my desktop as aniko -user and see this: 

aniko@ubul:/home$ ls
aniko  elek  zoli
aniko@ubul:/home$ getfacl zoli/
# file: zoli/
# owner: zoli
# group: zoli
user::rwx
user:aniko:r--
group::r--
mask::r--
other::---

aniko@ubul:/home$ cd zoli/
-su: cd: zoli/: Hozzáférés megtagadva
aniko@ubul:/home$ 

'Hozzáférés megtagadva' = permission denied 

What sould be the problem?

---

### Post by dmizer on 2009-06-01
> **Roguespider13 said:**
> WinUser1 would have the ability to create files and modify them as needed (but not delete them).

You do realize that all this individual has to do is ctrl+a, del, ctrl+s and your file is gone in all but name.

There is no way I am aware of to allow "edit file" while preventing "delete file" permissions. I'm not really sure this is even possible in Windows.

---

### Post by MikeEvans on 2009-06-01
windows/ntfs does have a delete permission.  You can allow writing to a file and not deleting. Samba tries to emulate this behavior but its not perfect.  Someone can still delete the file if they know the other way. Look at the "acl check permissions" property in the smb.conf manual.  Here it is:

> acl check permissions (S)

    This boolean parameter controls what smbd(8)does on receiving a protocol request of "open for delete" from a Windows client. If a Windows client doesn't have permissions to delete a file then they expect this to be denied at open time. POSIX systems normally only detect restrictions on delete by actually attempting to delete the file or directory. As Windows clients can (and do) "back out" a delete request by unsetting the "delete on close" bit Samba cannot delete the file immediately on "open for delete" request as we cannot restore such a deleted file. With this parameter set to true (the default) then smbd checks the file system permissions directly on "open for delete" and denies the request without actually deleting the file if the file system permissions would seem to deny it. This is not perfect, as it's possible a user could have deleted a file without Samba being able to check the permissions correctly, but it is close enough to Windows semantics for mostly correct behaviour. Samba will correctly check POSIX ACL semantics in this case.

    If this parameter is set to "false" Samba doesn't check permissions on "open for delete" and allows the open. If the user doesn't have permission to delete the file this will only be discovered at close time, which is too late for the Windows user tools to display an error message to the user. The symptom of this is files that appear to have been deleted "magically" re-appearing on a Windows explorer refresh. This is an extremely advanced protocol option which should not need to be changed. This parameter was introduced in its final form in 3.0.21, an earlier version with slightly different semantics was introduced in 3.0.20. That older version is not documented here.

    Default: acl check permissions = True 

Note: i just tried testing this and I cant seem to set the deny delete permission from a windows client..  so i might be wrong.  I'll do some more testing tomorrow and post back with findings. im in the process of integrating a samba server into a windows domain

---

### Post by MikeEvans on 2009-06-02
So it looks like dmizer is correct.  I created a file on a windows server owned by the domain administrator with full control to everyone and the delete permission specifically denied to my username.  From a windows client I was still able to delete the file with my username.  Only by blocking write permission was I able to stop the deletion. I wonder what the point of the delete permission is on the windows acl's.

---

### Post by dmizer on 2009-06-02
> **MikeEvans said:**
> So it looks like dmizer is correct.  I created a file on a windows server owned by the domain administrator with full control to everyone and the delete permission specifically denied to my username.  From a windows client I was still able to delete the file with my username.  Only by blocking write permission was I able to stop the deletion. I wonder what the point of the delete permission is on the windows acl's.

Thanks for confirming that. I no longer have no Windows clients or servers to test on. :)

---

### Post by albinootje on 2009-06-02
> **dmizer said:**
>  There is no way I am aware of to allow "edit file" while preventing "delete file" permissions. I'm not really sure this is even possible in Windows.

In "plain" Linux it is easy.

You just give the user rw access --only-- on the group level (and not ownership), then the user can edit the file but not remove it.

I assume it is possible in Samba too, as Samba has loads and loads of options (Has caused me headaches several times in the past, and I'm too tired+busy now to search through the huge Samba documentation).

---

### Post by albinootje on 2009-06-02
> **g_zoli said:**
> 
I have followed this how-to, but i don't have success.


Here's a different approach mentioned (in comment #3) :
[http://ubuntuforums.org/showthread.php?t=1162457](http://ubuntuforums.org/showthread.php?t=1162457)

---

### Post by MikeEvans on 2009-06-03
Further testing in pure windows have lead to inconsistencies with my above statements. I did find this interesting blog post by someone who seems to understand windows access control at a low level and touches on the inconsistencies im seeing.

[http://xato.com/hardening/pointless-permissions]("http://xato.com/hardening/pointless-permissions")

OP, sorry im getting off topic with windows specific permission issues.  My approach to samba has been to make it work like cifs/ntfs but but now im seeing there are some fundamental differences that I was unaware of.  

Another approach that may work for you is keeping the files in a read only directory. Your windows users can make their edits and save a copy into another folder. The linux user or a linux script can merge the changes or make a simple revision structure.

---

