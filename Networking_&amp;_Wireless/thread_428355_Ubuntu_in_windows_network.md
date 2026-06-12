---
title: "Ubuntu in windows network"
date: 2007-04-30
forum: Networking &amp; Wireless
---

### Post by Balazs_noob on 2007-04-30
Hi guys
i'm using Ubuntu for about 3-4 days now :)
and happy that i made the changed ;)

but i have a small problemn my borthers XP machine can't 
enter my computer ...

i have installed samba and shared my NTFS drives..

but when he wants to enter my computer
his XP always prompts for a username + password and when i enter
my  username + password it just asks again :S

i have booted several times and re-installed the driver
and cheked the shared drives...

I could always enter his computer from Ubuntu since my install
so it is not a big problem but it would be nice to solve it :D

thanks in advance , Balázs

---

### Post by dolphin_oracle on 2007-04-30
Here's a couple of points I've noticed on my setup at home, which is similar to your situation.

1.  You cannot be logged in to Ubuntu more than once.  So the windows xp needs to log in with a different account than what is running on the ubuntu machine.

2.  The second account needs to be both a ubuntu user (added in Users and Groups under administration) AND a samba user.  From the terminal, type

sudo smbpasswd -a username

to add a samba user.

It will then ask for a password.  Just make sure the password AND the username are the same for Ubuntu and Samba.  Hopefully you should be able to log in then from the XP machine.

Hope this helps.

---

### Post by renzokuken on 2007-04-30
you could always create a new account for your brother and try that.

although it most likely an issue with the way your smb.conf is set up. could you post it?

it should be in /etc/smb.conf (or maybe /etc/samba/smb.conf ) cant remember

---

### Post by Balazs_noob on 2007-04-30
thanks dolphin_oracle  your solution was correct :) 
and thank you renzokuken that you tryed to help :) 

now i only need to figure out how to get my widesceen
monitor to use 1440x900...
but i'm sure there are a lot of threads for that :)

thanks again

Balázs

---

### Post by dolphin_oracle on 2007-04-30
Good luck with your monitor!

---

### Post by krige on 2007-05-01
Hello there,

is there any user friendly graphical interface in Ubuntu 7.04 to share folders visible to a Windows machine and vice versa? Maybe something similar to the Windows right-click on a folder and share? Or do I really need to follow the following steps?
[http://ubuntuforums.org/showthread.php?t=26438](http://ubuntuforums.org/showthread.php?t=26438)

I have only one user in my Linux box, I really wouldn't like to be forced to create a dummy user just to be able to share a folder in the network while my user is logged in. Is there a way to tell samba to give access to a folder to anyone with a specific IP?

---

### Post by renzokuken on 2007-05-01
System -> Admin -> Shared Folders

---

### Post by krige on 2007-05-01
> **renzokuken said:**
> System -> Admin -> Shared Folders

I have done that and had two problems:

1. I have two partitions, one with NTFS and one with FAT32: it lets me share any folder in the NTFS partition but I can't share any folder in the FAT32 partition;

2. if I try to access the Linux machine from a Windows machine, Windows keeps asking me the username and password, even when the user in the Linux machine is logged out.

---

### Post by Zeirus on 2007-05-02
> **krige said:**
> I have done that and had two problems:

1. I have two partitions, one with NTFS and one with FAT32: it lets me share any folder in the NTFS partition but I can't share any folder in the FAT32 partition;

2. if I try to access the Linux machine from a Windows machine, Windows keeps asking me the username and password, even when the user in the Linux machine is logged out.

Try to solve your problem here:

[http://ubuntuforums.org/showthread.php?t=340386&highlight=share+folder](http://ubuntuforums.org/showthread.php?t=340386&highlight=share+folder)

---

### Post by Zeirus on 2007-05-02
> **Zeirus said:**
> Try to solve your problem here:

[http://ubuntuforums.org/showthread.php?t=340386&highlight=share+folder](http://ubuntuforums.org/showthread.php?t=340386&highlight=share+folder)

I've tried and resolved the sharing of Ubuntu in this manner (only for NTFS, i've not FAT32 partition, sorry):

sudo smbpasswd -a 'myusername'
Add a password when prompted (can be different from pc password).

Then from Windows, simply access \\xxx.xxx.xxx.xxx\

When asked for credentials, provide user name, password for samba.

Works magically.

Thanks to Snoochie for the tip... ;)

---

### Post by krige on 2007-05-02
> **Zeirus said:**
> sudo smbpasswd -a 'myusername'
Add a password when prompted (can be different from pc password).

Then from Windows, simply access \\xxx.xxx.xxx.xxx\

When asked for credentials, provide user name, password for samba.

Thanks pal, it worked for the etx3 and ntfs partitions, but I still can't select any folder to be shared in the FAT32 partition from the System / Administration / Shared Folders tool.

---

### Post by dolphin_oracle on 2007-05-02
I had a problem sharing a fat partition as well.  my backdoor workaround was to mount the fat partition inside my regular shared folder.  The work around is good for accessing the drive but doesn't work for writing to it.  The link shows up as just another folder in the already shared folder.

---

### Post by merlinus on 2007-05-02
I have added a ubuntu and samba user who is on a win2000 box.  But I cannot access the share from her computer via network neighborhood.

I installed NetBios on the win box.  Am I missing something else?

I typed \\merlin_smb_server\ , which is specified in smb.conf, in the add new dialog box in network neighborhood on the win machine, but got an error message to the effect that it could not be found.

Many thanks...

-merlin

---

