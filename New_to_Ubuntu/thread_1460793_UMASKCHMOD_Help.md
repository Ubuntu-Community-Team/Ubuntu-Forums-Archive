---
title: "UMASK/CHMOD Help"
date: 2010-04-23
forum: New to Ubuntu
---

### Post by Thund3rstruck on 2010-04-23
I've recently moved my Windows 2003 File Server to FreeNAS and I'm struggling with some of the permissions concepts in *nix. 

When I created my mount point for my 8TB RAID Array I set the umask to 003 because I wanted the owner and owning group full control of the data on the shares and I wanted other users to have read only access. I spent 4 days migrating the old data to the new shares only to realize today that 'Read' permission in Unix don't allow users to actually read files, only see their names. 

Now, only users in the owning group can actually use the data on the server. I ran a chmod 775 * and that allowed everyone to get the permissions they need but all new files created anywhere in the folder structure still get rwx-rwx-r-- permissions by default. So I have to constantly run the chmod all day long. 

How can I recursively set the umask so all new files get 775? I tried applying umask 002 at the root folder but new files created deep within the folder structure are still inheriting the original 003 umask.

---

### Post by doas777 on 2010-04-23
I believe you want suid and sgid (and perhaps sticky). 
for instance I use sgid for force the group id for certain network shared folders that a group of users interact with. 

here is some info:
[http://www.codecoffee.com/tipsforlinux/articles/028.html](http://www.codecoffee.com/tipsforlinux/articles/028.html)

I'm told that you can extend permissions with ACLs but I have not yet had time to research it. you may find what you need here:
[http://www.beginlinux.com/server_training/server-managment-topics/1038-ubuntu-804-access-control-lists](http://www.beginlinux.com/server_training/server-managment-topics/1038-ubuntu-804-access-control-lists)

---

### Post by mcduck on 2010-04-23
Actually, read permission *does* allow you to read the contents of a file.

I suppose your confusion comes from the way permissions apply to *directories*, in which case you need the execute permission on the directory to be able to list it's contents (read permission only allows you to access files if you know the file path & full path).

So, instead of using umask you'll want to use fmask (which applies to files only) and dmask (directories only), so you can set -rwxrwxr-- for files (if you really want to make allthe files executable for user&group, although you shouldn't really need the execute permission on every file) and drwxrwxr-x on directories

---

### Post by Thund3rstruck on 2010-04-23
> **mcduck said:**
> Actually, read permission *does* allow you to read the contents of a file.

I suppose your confusion comes from the way permissions apply to *directories*, in which case you need the execute permission on the directory to be able to list it's contents (read permission only allows you to access files if you know the file path & full path).

Hmm.. that's not the behavior we are seeing. All users can browse the directories from a mapped share just fine. Double-clicking on any file in any of the directories results in the message: 'Access Denied'. All users can browse the share but only members of the owning group can open files. I have had several users try this, all with the same result, Access Denied. When I run a ls -l command it returns -rwx-rwx-r--. Users in the owning group 'GFSAdmin' can open, create, and delete files just fine but everyone else can only browse and cannot open any files (not even plain-text files).

For a quick fix I have run chmod 775 * to allow regular users to open files but each time an admin copies a new file to the share, it is being set to -rwx-rwx-r-- and I have to manually chmod 775 to allow regular users read access to the file.

---

