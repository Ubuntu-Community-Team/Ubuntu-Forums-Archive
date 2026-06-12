---
title: "giving a user write (root) permissions to other users' files"
date: 2009-02-20
forum: New to Ubuntu
---

### Post by MiniMe on 2009-02-20
Hello,
I have a server hosting several websites with specific users that can control the folder for their website. I'd like an administrative user that can modify any of their files but I don't want to work as root.

Is there a way I can achieve this?

Thanks in advance.

---

### Post by RealG187 on 2009-02-20
In Nautilus goto properties of the folder and use the permissions tab. Change the options to "read and write" and "create and delete files"

I think there is also a command for this something like chmod

---

### Post by Hospadar on 2009-02-20
You could join that user's group, and then set the group permissions for that user's files that you need to edit to be group-writeable
To learn about group management: [http://www.cyberciti.biz/faq/howto-linux-add-user-to-group/](http://www.cyberciti.biz/faq/howto-linux-add-user-to-group/)
to recursively change the permissions of a folder to be group-writeable,

chmod g+w -R name_of_folder

Also you could change the group ownership of the files and folders you need to be able to modify, and then similarly add group write permissions.  To change group ownership

chown :your_username -R name_of_folder

You might want to 
man chmod
man chown

And google up about user permissions

---

### Post by MiniMe on 2009-02-20
Thanks for the replies. Hospadar, my concern is if I have let's say I have 100 new users per day. Wouldn't your solution require a lot of manual labour? Is there a way to automate the process or do it in another way?

Thanks again.

---

