---
title: "[SOLVED] Sharing  my /windows directory"
date: 2008-06-22
forum: Networking &amp; Wireless
---

### Post by Stolea on 2008-06-22
In my Ubuntu 8.04 setup I have my NTFS windows partition setup as /windows folder. I have to be able to access the files on that folder from my XP machine. I got Samba working and XP can access a folder I create on my Ubuntu desktop. If I try to set up a share for the /windows folder in Ubuntu, it returns [COLOR="Red"]"Could not change the permissions of folder "windows""[/COLOR]
How do I get around that?

---

### Post by Stolea on 2008-06-22
Anyone with any suggestions? Please

---

### Post by superprash2003 on 2008-06-22
did you configure the share by right-clicking and clicking on share folder or by editing the smb.conf file?

---

### Post by Stolea on 2008-06-23
I right-clicked on the /windows folder. This worked fine for a share folder I created on my desktop.

---

### Post by superprash2003 on 2008-06-23
did you uncheck "read only"?

---

### Post by Stolea on 2008-06-23
Where do I do that? I can get the "properties" folder, but if I click on "Permissions" it says I am not the owner and can't change the permissions

---

### Post by plewisfdx on 2008-06-23
When I did a 'ls -l' on my /media/sda1 which is my windows (ntfs) partition it showed 
```
drwxrwxrwx 1 root root 8192 2008-06-21 22:02 sda1

```

so it automounts using owner/group of root, so you (and I) indeed are not the owners.

Can you paste the part of /etc/fstab that includes your windows partition you are trying to share?

Mine is mounted with ntfs-3g which I may have done myself, can't remember.

[https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G](https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G)

---

### Post by superprash2003 on 2008-06-23
when you right click and click on share folder.. and then select SHARE.. you should see "read only".. uncheck that

---

### Post by Stolea on 2008-06-23
> **plewisfdx said:**
> When I did a 'ls -l' on my /media/sda1 which is my windows (ntfs) partition it showed 
```
drwxrwxrwx 1 root root 8192 2008-06-21 22:02 sda1

```

so it automounts using owner/group of root, so you (and I) indeed are not the owners.

Can you paste the part of /etc/fstab that includes your windows partition you are trying to share?

Mine is mounted with ntfs-3g which I may have done myself, can't remember.

[https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G](https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G)

This is my line from fstab:

[COLOR="Teal"]# /dev/sdc5
UUID=80C4ACB5C4ACAF3A /windows        ntfs    defaults,umask=007,gid=46 0       1

[/COLOR]

I set it up as the windows file at the time I installed Ubuntu.

---

### Post by Stolea on 2008-06-23
> **superprash2003 said:**
> when you right click and click on share folder.. and then select SHARE.. you should see "read only".. uncheck that

If I right-click on the /windows folder > Sharing Options > Folder Sharing I have the choice of 3 boxes (2 greyed out at this point). The active box is "Share this folder". If I tick that box it highlight an editable  sub field that says the "Share name: windows."
Selecting "Share this folder" has ungreyed the second box "Allow other people to write in this folder" and the editable sub field "Comment: ....."

There is a 3rd box that stays greyed out that says "Guest access (for people without a user account"

I tick the box "Allow other people to write in this folder" and hit the button "Create share" (I have tried it without the "Allow.." but the outcome is the same.

"Create Share" produces a box that says;
[COLOR="Blue"]Nautilus needs to add some permissions to your folder "windows" in order to share it
The folder "windows" needs the following extra permissions for sharing to work:
  - read permission by others
  - write permission by others
  - execute permission by others
Do you want Nautilus to add these permissions to the folder automatically?[/COLOR]
and boxes "Cancel" and "Add permissions automatically". I choose "Add.." and it produces the [COLOR="Red"]"Could not change the permissions of folder "windows""[/COLOR]
at which point I go and make another cup of coffee:)

---

### Post by superprash2003 on 2008-06-23
ok.. you need to change the permissions for windwos folder.. read this [http://prash-babu.blogspot.com/2008/06/how-to-edit-file-or-folder-permission.html](http://prash-babu.blogspot.com/2008/06/how-to-edit-file-or-folder-permission.html) .. and change permission for windows folder to "create and delete file" under folder access for OTHERS.. then share the folder like how you mentioned..

---

### Post by Stolea on 2008-06-24
When I choose "peter" it immediately changes it back to "root". I tried it a number of times, and even got to the second option the very first time, before it changed itself back.
I am getting the following message in the treminal window as this is happening

[COLOR="Red"]peter@Shop:~$ sudo nautilus
Initializing nautilus-share extension
seahorse nautilus module initialized

** (nautilus:6948): WARNING **: Unable to add monitor: Operation not supported

--- Hash table keys for warning below:
--> file:///

(nautilus:6948): Eel-WARNING **: "nautilus-metafile.c: metafiles" hash table still has 1 element at quit time (keys above)

(nautilus:6948): Eel-WARNING **: "nautilus-directory.c: directories" hash table still has 1 element at quit time
seahorse nautilus module shutdown[/COLOR]

---

### Post by Stolea on 2008-06-24
> **Stolea said:**
> When I choose "peter" it immediately changes it back to "root". I tried it a number of times, and even got to the second option the very first time, before it changed itself back.
I am getting the following message in the treminal window as this is happening

[COLOR="Red"]peter@Shop:~$ sudo nautilus
Initializing nautilus-share extension
seahorse nautilus module initialized

** (nautilus:6948): WARNING **: Unable to add monitor: Operation not supported

--- Hash table keys for warning below:
--> file:///

(nautilus:6948): Eel-WARNING **: "nautilus-metafile.c: metafiles" hash table still has 1 element at quit time (keys above)

(nautilus:6948): Eel-WARNING **: "nautilus-directory.c: directories" hash table still has 1 element at quit time
seahorse nautilus module shutdown[/COLOR]

I just righ-tlicked the /windows folder and just for the hell of it selected sharing option and hit apply. It now is sharing!!!. Don't ask me how or why, but there is some strange glitch here. It doesn't make a blind bit of sense. Could it be that I logged into nautilus with "sudo"??

Even more amazingly, my XP computer can actually see it!!!:)

I won't even question how and why and just be greatfull that it works:)

Thanks for your help.:)

When I am in my terminal window my UPS that the software can't talk to keeps sending the following error:
Broadcast Message from nut@Shop                                                
        (somewhere) at 20:12 ...                                               
                                                                               
UPS mgeups@localhost is unavailable      
Any good idea what to do about it??

---

