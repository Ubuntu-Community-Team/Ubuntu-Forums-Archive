---
title: "Can't change permissions on &quot;includes&quot; folder"
date: 2011-03-02
forum: New to Ubuntu
---

### Post by Daanii on 2011-03-02
I have Ubuntu 10.10 running on a BeagleBoard that has an ARM processor. The version I have appears to lack some of the default utilities, so I have had to install them. But things work well now. 

But I need to add some "include" files for compiling in C. When I download the files, I try to copy the files from my downloads folder into the /usr/lib/avr/include folder. I get an "Error while moving "Spi.h"." 

If I ask to show more details, I get "Error moving file: Permission denied"

If I open up the Properties for that "include" folder and look at permissions, it says Owner: root, and Group: root, and the options under those are grayed out. 

At the bottom, it says "You are not the owner, so you cannot change these permissions." 

Is there any way to change these permissions? Thanks.

---

### Post by spook1980 on 2011-03-02
sudo nautilus
then navigate to the folder who;'s permissions u wish to change n change em it's just that simple

---

### Post by mcduck on 2011-03-02
The thing here is that you *shouldn't* change the permissions or ownership of any of the system directories. That's unsafe, and an easy way to break your system. In worst cases to inoperable and unrepairable state. The security in Linux is based on strict ownerships and permisisons, and every user and service only having the privileges it needs. And Linux pretty much depends on certain files and directories having certain ownerships and permissions.

Instead you should change *your own* permissions so you can complete whatever task you need to do at the moment. And that's what the "sudo" command is for.

So, instead of doing what the above poster suggested, you should run "gksudo nautilus" to open the file manager as root user, and then use that to copy the files to /usr/lib/avr/include. And leave the permissions and ownership of that directory as they are now.

You may also want to read this: [https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

---

### Post by Daanii on 2011-03-02
> **spook1980 said:**
> it's just that simple

And so it was. All changed now. Thanks very much.

---

### Post by Daanii on 2011-03-02
> **mcduck said:**
> You may also want to read this: [https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

I'll take a look at that. Thanks.

---

### Post by spook1980 on 2011-03-04
> **Daanii said:**
> I'll take a look at that. Thanks.

no problem
if u could though please mark this thread as solved to help other users with the same problem.

---

### Post by Eddieduce on 2011-04-12
:confused:I have the same issue with trying to change permissions for folder but even though I try it won't allow it to go through.

Attempt-01:

sudo chmod o+rw /tftpboot/ltsp/i386/pxelinux.cfg

NOTE: Permissions remain as read only.


Attempt+02:

sudo nautilus

NOTE: I navigated to properties and then Permissions. Went to the Others section and changed File access: to read and write.  It automatically reverts back to "---".


I used chmod in the past (if I recall correctly) and it worked ONCE.  I did a system OS reinstall for other reasons but, despite writing down the command and path, it does not work.

I also tried the numerical command options but it did not go through.

:confused:

---

### Post by mcduck on 2011-04-12
> **Eddieduce said:**
> :confused:I have the same issue with trying to change permissions for folder but even though I try it won't allow it to go through.

Attempt-01:

sudo chmod o+rw /tftpboot/ltsp/i386/pxelinux.cfg

NOTE: Permissions remain as read only.


Attempt+02:

sudo nautilus

NOTE: I navigated to properties and then Permissions. Went to the Others section and changed File access: to read and write.  It automatically reverts back to "---".


I used chmod in the past (if I recall correctly) and it worked ONCE.  I did a system OS reinstall for other reasons but, despite writing down the command and path, it does not work.

I also tried the numerical command options but it did not go through.

:confused:

Are the files on a non-linux filesystem (like FAT or NTFS)? Those filesystems lack support for ownerships and permissions as they are used on Unix/Linux systems, and therefore permissions are set for the whole filesystem at the time it's mounted and can't be changed using chown or chmod.

---

### Post by wildmanne39 on 2012-08-06
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

