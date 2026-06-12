---
title: "Turn off file/folder ownership on data drives"
date: 2011-01-03
forum: New to Ubuntu
---

### Post by SentientFluid on 2011-01-03
I am running Ubuntu 10.04 with 2 user accounts (my wife and I). I have multiple drives that contain shared data but whenever data is copied/created by one user, that user is automatically set as the owner and group.

For example: My wife copies photos from our camera to a folder on one of the data drives. The permissions are automatically set so she is the owner/group so I don't have access to them. The same thing happens if I copy the photos from my account.

I can manually over ride them using the Properties dialog in her user or by using chown/chmod in my user, but isn't there a way to make it so everything saved to this drive is always accessible by both of us?

---

### Post by bodhi.zazen on 2011-01-03
This is an overview for how to share a directory :

[http://www.cyberciti.biz/faq/linux-setup-shared-directory/](http://www.cyberciti.biz/faq/linux-setup-shared-directory/)

Basically, change you default user from your log in name(s) so something else, and use that something else for the share w or w/o setting the sticky bit.

Another perhaps better option is to use acl (access control lists).

[http://www.suse.de/~agruen/acl/linux-acls/online/](http://www.suse.de/~agruen/acl/linux-acls/online/)
[http://studentwebsite.blogspot.com/2009/06/how-to-setup-acl-access-control-list-in.html](http://studentwebsite.blogspot.com/2009/06/how-to-setup-acl-access-control-list-in.html)

You can do this from the command line or with graphical tools.

[http://www.linux.com/archive/feature/138169](http://www.linux.com/archive/feature/138169)

Eiciel is in the repos.

---

### Post by sisco311 on 2011-01-03
> **bodhi.zazen said:**
> This is an overview for how to share a directory :

[http://www.cyberciti.biz/faq/linux-setup-shared-directory/](http://www.cyberciti.biz/faq/linux-setup-shared-directory/)

Basically, change you default user from your log in name(s) so something else, and use that something else for the share w or w/o setting the sticky bit.

Another perhaps better option is to use acl (access control lists).

[http://www.suse.de/~agruen/acl/linux-acls/online/](http://www.suse.de/~agruen/acl/linux-acls/online/)
[http://studentwebsite.blogspot.com/2009/06/how-to-setup-acl-access-control-list-in.html](http://studentwebsite.blogspot.com/2009/06/how-to-setup-acl-access-control-list-in.html)

You can do this from the command line or with graphical tools.

[http://www.linux.com/archive/feature/138169](http://www.linux.com/archive/feature/138169)

Eiciel is in the repos.

+1

@OP:
You may also want to check out [thread=1460472]bindfs[/thread].

EDIT:
Here is a good guide about Unix/Linux file permissions:
[http://content.hccfl.edu/pollock/aunix1/filepermissions.htm](http://content.hccfl.edu/pollock/aunix1/filepermissions.htm)

and a youtube video about ACLs:
[http://www.youtube.com/watch?v=6piQXXHTmqk](http://www.youtube.com/watch?v=6piQXXHTmqk)

---

