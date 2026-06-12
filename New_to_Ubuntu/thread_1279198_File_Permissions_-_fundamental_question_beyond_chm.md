---
title: "File Permissions - fundamental question beyond chmod"
date: 2009-09-30
forum: New to Ubuntu
---

### Post by thing-fish on 2009-09-30
I've been searching for an answer to something pretty fundamental but every way I can think to ask it just brings back information on chmod and chown :(  Here's what I'm wondering:

When I'm logged in to my user account (assume the name is tfish) and I execute *touch myfile.txt*, *ls -l myfile.txt* lists ```
-rw-r--r-- 1 tfish tfish
```  I understand this means that the file is owned by tfish (me) and the group tfish, and that tfish has read/write while the tfish group and Others just have read.

If I execute *sudo touch myfile2.txt*, *ls -l myfile2.txt*  lists ```
-rw-r--r-- 1 root   root
```  I understand that means that the file is owned by root and the group root, and that root as read/write while the root group and Others just have read.

With that, here are the things I'd like to understand better:

[LIST]
[*]Am I right in thinking that when you create a user, a group named after that user is also created?
[*]Is it always the default case that when a user creates a file that the file will belong to that user's self-named group?
[*]Assuming it is the default, is there a way to have a user create a file but have it belong to a different group *at creation time*? (i.e. not by running chown after the file has been created)
[*]Whether or not that can be accomplished, is it possible to make it so that the default is that when certain users create files that the permission for the Others is read/write instead of just read?
[*]I understand that I can run chown or chmod on a group of files in a folder after those files have been created. However, is there a way to make a folder so that all the files that are created **later** in that folder will inherit specific permissions or ownership?
[/LIST]

I'm asking these things for a variety of reasons, but one specific use case I'm thinking of is that I'm running a media server on Ubuntu and am sharing a folder via Samba.  So as it stands if I rip a CD on another machine on the network and copy it to the folder, it ends up being owned and in the group of the generic samba user.  If I download music while logged in to the ubuntu machine itself, it ends up being owned by and in the group of my account.  Then I'll try to move stuff around with one account or the other and get permission issues!  I've resorted to occasionally running sudo chmod and sudo chown over the shared folder so that I can actually manage this stuff in terms of moving it around and updating metadata and stuff.

Thank you!

---

### Post by kay-man on 2009-09-30
Not sure if i can answer all of that, but I'll give it a shot.

Yes, when you create a user a group with the same name is created. By default, this will be the user's primary group
Normally yes. But you can set the group's sticky bit on the directory, which will cause the directory's group to own files that are created in the directory.
You'll need to set your umask for that. That defines the default permissions on files you create.
Well, sort of, with what I said. But you may need to look into the setfacl tool, which will allow you to create access control lists on files and directories.

So, here it is. Not a ready made plan for your specific situation, but I hope it helps.

I have much the same problem as you, only probably simpler. I use gnucash, and I want all the files it creates accessible by me and my wife. I created a group and set the folder's sticky bit. And then i created a shell script to set the umask first and then start gnucash. That does the trick for me.

Paul

---

