---
title: "having a problem with the way the ubuntu trash folder works"
date: 2011-05-15
forum: New to Ubuntu
---

### Post by wjkraymond on 2011-05-15
Hi everyone, this is my first post. (excited)

Ok, so here's my story. I have a 320GB hard disk on my lappy.
i'm currently dual booting with windows7 and ubuntu 11.4
my windows partition is 50GB while ubuntu is 30GB. 

The remaining disk space is used for a partition where i keep all my files, docs, pics, videos etc. (windows recognize it as E drive, while ubuntu detects it as /media/sda3)

I only use the windows and ubuntu partition to install programs. all my user files are in the E drive. 

Now here's the problem. In ubuntu, when i delete a file from , an error message appear, "Cannot to move file to trash, do you want to delete immediately?"

I din't find this to be a big problem at first, but when i accidentally delete something, i cant retrieve it from the trash since it was deleted permantly. In windows, if this happens, i can easily find it in recycle bin.

I hope that the ubuntu trash works the same as in windows.
Where i can find back the files i've deleted, who knows when i might need them again.

i tried google and the closest thing i can get is this
[http://superuser.com/questions/51949/nautilus-cannot-move-to-trash](http://superuser.com/questions/51949/nautilus-cannot-move-to-trash)
it says that ubuntu only move deleted files from local mounts to trash. i'm not sure why my E drive is not consider local mounts. 

So, if anyone can help me with this issue, which is enable deleted files to be transfer to trash folder, please advice.

thank you very much!

---

### Post by jtarin on 2011-05-16
In a terminal issue the command. Copy and paste here. ```
gksudo gedit /etc/fstab
```
> "Cannot move file to trash, do you want to delete immediatelyNormally this is only seen when the file is too large for the Trash. If it's a file you think you want to recover later just move it to another location.
Try this.....take a problem file, move it to the Ubuntu desktop and see if it exhibits the same behavior upon deletion.

---

### Post by wjkraymond on 2011-05-16
Hi, thanks for the reply.
I did copy and paste the line you suggested into a terminal.
It opens a text file with the following. i will paste it in bellow.

[SIZE="2"]# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc        proc  nodev,noexec,nosuid  0  0  
# / was on /dev/sda5 during installation
UUID=46a4c35d-e7e3-4a44-81f9-68741cb6a5ad  /            ext4  errors=remount-ro    0  1  
# swap was on /dev/sda6 during installation
UUID=5838109b-11f8-40be-835d-70161de3d353  none         swap  sw                   0  0  
/dev/sda2                                  /media/sda2  ntfs  defaults             0  0  
/dev/sda3                                  /media/sda3  ntfs  defaults             0  0  [/SIZE]

I have no idea what this text file means.

For the files that unable to be sent to trash, its EVERY file in the d drive. no matter the size or the file type. if i copy it to the ubuntu desktop, i can press delete, and it will be sent to trash as usual. but if delete from the original location in E drive, it cant be sent to trash.

---

### Post by Wim Sturkenboom on 2011-05-16
[http://ubuntuforums.org/archive/index.php/t-1451714.html](http://ubuntuforums.org/archive/index.php/t-1451714.html) might be of help; found using [google for linux second hd trash](http://www.google.co.za/#hl=en&source=hp&biw=1253&bih=826&q=linux+second+hd+trash&oq=linux+second+hd+trash&aq=f&aqi=&aql=&gs_sm=e&gs_upl=1452l7103l0l21l21l0l5l0l0l350l3216l3.5.6.2&fp=c15f22988360aa7) ;)

---

### Post by wjkraymond on 2011-05-16
hi wim,
thanks for the link. i read it and its the same problem i'm having.
sorry for making such a long story, i should summarize my problem as wanting a trash in a second hd.

i was happy to found a thread that can solve my problem, but my happiness was short lived.

i read carefully the instruction, what mr Egalvin suggested in that thread was to use 
"gksu gedit /etc/fstab"

and replace 
"/dev/sdb1 /media/Public ntfs-3g defaults,locale=en_US.UTF-8 0 0" 

with
"/dev/sdb1 /media/Public  ntfs utf8,umask=007,uid=1000,gid=1000 0 2"

however, i cant find the line to do the replacement. I'll paste my file at the bottom of this post.
The closest line i have that seems similar is

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc        proc  nodev,noexec,nosuid  0  0  
# / was on /dev/sda5 during installation
UUID=529b088a-37c6-4269-ae46-ceca4f5ab9d6  /            ext4  errors=remount-ro    0  1  
# swap was on /dev/sda6 during installation
UUID=6f611b3a-832c-4464-9d80-766d2fc5a9ea  none         swap  sw                   0  0  
/dev/sda2                                  /media/sda2  ntfs  defaults             0  0  
[COLOR="Lime"]/dev/sda3                                  /media/sda3  ntfs  defaults             0  0  [/COLOR]

Is this because ubuntu 11.4 is different? from the time of that thread, i think they are using 10.4 at that time.
so should i just go ahead and replace the last line?
will it cause damage to my laptop?

---

### Post by Morbius1 on 2011-05-16
Change this:
> /dev/sda3 /media/sda3 ntfs defaults 0 0 To this:
> /dev/sda3 /media/sda3 ntfs defaults,uid=1000 0 0 Unmount the currently mounted partition:
```
sudo umount /media/sda3
```Run the following command to check for errors and mount the modified line in fstab ( this saves you a reboot ):
```
sudo mount -a
```Then check to see it's doing what you want it to do.

---

### Post by wjkraymond on 2011-05-16
OMG morbius1,

Thank you so much, it totally works!!
This is amazing, i nv expected such a quick reply

Thanks again!!!
ubuntu rocks even harder now.

So Happy ^^

erm, i guess now all that's left is to figure out how to mark this as "solved".

---

### Post by wjkraymond on 2011-05-16
i've read in the forum rules that i must mark the topic as "solved" and thank the people that help me.
Thanks everyone for your suggestions.

sorry for being such a noob, :confused:but i gotta ask, how am i suppose to announce this topic as solved? or did my previous post already proved it solved?

Sorry, i found it, just click the "thread tools", and the last option "mark as solved" lol...silly me.

---

### Post by wjkraymond on 2013-02-22
> **Morbius1 said:**
> Change this:
To this:
Unmount the currently mounted partition:
```
sudo umount /media/sda3
```Run the following command to check for errors and mount the modified line in fstab ( this saves you a reboot ):
```
sudo mount -a
```Then check to see it's doing what you want it to do.



hello morbious1, i hope you're still active in this forum and able to help me.

after skipping many release, i decided to update my ubuntu to 12.10.

i'm liking it so far, with the new unity and all.
but i lost the trash folder in my ntfs partition.

the instructions that i tried before are different now.
what i mean is the fstab in 12.10 is different from previous versions.

here is what i have in my fstab:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

#Entry for /dev/sda5 :
UUID=aaa3ef75-13e9-4afd-a1a6-a79ba1902d50	/	ext4	errors=remount-ro	0	1
#Entry for /dev/sda3 :
UUID=6CD808E4D808AE80	/media/Raymond	ntfs-3g	defaults,locale=en_US.UTF-8	0	0
#Entry for /dev/sda1 :
UUID=968A418F8A416D35	/media/System_Reserved	ntfs	defaults,nls=utf8,umask=0222	0	0
#Entry for /dev/sda6 :
UUID=502896ee-d330-4b7f-bf53-ef6ccc8ced5a	none	swap	sw	0	0

```

what should i alter to have deleted files in that ntfs partition moved to trash instead if permanently deleted?

---

### Post by Morbius1 on 2013-02-23
Do you mean this?
> UUID=6CD808E4D808AE80    /media/Raymond    ntfs-3g    defaults,locale=en_US.UTF-8    0    0Since it lists ntfs-3g explicitly I smell ntfs-config at work here. It's best not to use that utility. Anyway to fix the immediate problem just add the uid=1000 to the list of options again:
> UUID=6CD808E4D808AE80    /media/Raymond    ntfs-3g    defaults,[COLOR=Blue]**uid=1000**[/COLOR],locale=en_US.UTF-8    0    0But a lot has changed since you posted last and the current way of doing this sort of thing looks more like this:
> UUID=6CD808E4D808AE80    /media/Raymond    ntfs-3g    defaults,[COLOR=Blue]**uid=1000****,windows_names**[/COLOR],locale=en_US.UTF-8    0    0The uid=1000 gets you your trash problem resolved and the "windows_names" option prevents you from creating a file in the partition with a file name that Windows cannot interpret.

---

### Post by wjkraymond on 2013-02-23
> **Morbius1 said:**
> Do you mean this?
Since it lists ntfs-3g explicitly I smell ntfs-config at work here. It's best not to use that utility. Anyway to fix the immediate problem just add the uid=1000 to the list of options again:
But a lot has changed since you posted last and the current way of doing this sort of thing looks more like this:
The uid=1000 gets you your trash problem resolved and the "windows_names" option prevents you from creating a file in the partition with a file name that Windows cannot interpret.

Thank you so much Morbius1,

i did as you told and it worked just like before.
thank you so much for the prompt reply.
:D:D:D:D

---

