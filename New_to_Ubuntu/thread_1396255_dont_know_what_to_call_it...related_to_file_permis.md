---
title: "dont know what to call it...related to file permissions"
date: 2010-02-01
forum: New to Ubuntu
---

### Post by cjohnweb on 2010-02-01
Hello, This is my first post!


So, I have been using Ubuntu 9.10 LTS for a few months or so now. I am familiar with moving about the OS, installing programs, uninstalling, etc etc.

I run apache2, mysql5.1 (i think), php5, vsftpd, openfire xmpp/jabber and a ton of other stuff.....

So there is just this one thing that I am having trouble with:

I FTP in as my regular user account and navigate to /var/www and create a new file or folder....Long story short, I have to ssh in and chmod 0770 / chown www-data:www-data the files so that apache can access the files and server them...otherwise permission denied.

If I want to edit an existing file on the server, I have to ssh and chmod/chown it back to a different user.

When developing websites this is a pain in the butt and just will not work for me anymore. I am so tired of chown and chmod that I havent worked on my server in 2 weeks because it becomes very frustrating and I can't seam to find the answer online at all. I don't really know what to call it besides user permission issue ...but nothing on Google seams to be able to help me. The only things I can think of are to change the accounts that my programs run as....but that doesn't seam like the "correct" way to do it.


Can someone help me understand how to allow users/apache/vsftpd to access, modify, create, etc files without having to change user perms all the time at the terminal / ssh?


I am not worried about security or anything at the moment as I just installed Ubuntu 9.1 LTS specifically to figure out some of this user permissions stuff!!


In the end, I will be running a "hosting" service for myself and a few friends and those other friends / users will not have ssh access....only a web browser and an ftp account.


Any help is appreciated! If this goes by another term or name, please direct me to existing posts.


Thank you!!

---

### Post by samantha_ on 2010-02-01
> **cjohnweb said:**
> Hello, This is my first post!


So, I have been using Ubuntu 9.10 LTS for a few months or so now. I am familiar with moving about the OS, installing programs, uninstalling, etc etc.

I run apache2, mysql5.1 (i think), php5, vsftpd, openfire xmpp/jabber and a ton of other stuff.....

So there is just this one thing that I am having trouble with:

I FTP in as my regular user account and navigate to /var/www and create a new file or folder....Long story short, I have to ssh in and chmod 0770 / chown www-data:www-data the files so that apache can access the files and server them...otherwise permission denied.

If I want to edit an existing file on the server, I have to ssh and chmod/chown it back to a different user.

When developing websites this is a pain in the butt and just will not work for me anymore. I am so tired of chown and chmod that I havent worked on my server in 2 weeks because it becomes very frustrating and I can't seam to find the answer online at all. I don't really know what to call it besides user permission issue ...but nothing on Google seams to be able to help me. The only things I can think of are to change the accounts that my programs run as....but that doesn't seam like the "correct" way to do it.


Can someone help me understand how to allow users/apache/vsftpd to access, modify, create, etc files without having to change user perms all the time at the terminal / ssh?


I am not worried about security or anything at the moment as I just installed Ubuntu 9.1 LTS specifically to figure out some of this user permissions stuff!!


In the end, I will be running a "hosting" service for myself and a few friends and those other friends / users will not have ssh access....only a web browser and an ftp account.


Any help is appreciated! If this goes by another term or name, please direct me to existing posts.


Thank you!!
use 
```

chown _username_ -R

```
for the entire directory

or
```

chmod -R 755

```

The easiest way is to symlink the folder thats inside /var/www to a folder in your home folder.
That would defiantely work, becasue your home folder is by default, owned by you.

---

### Post by warfacegod on 2010-02-01
Possibly:

```
sudo chgrp -R uname:ugroup...
```

---

### Post by cjohnweb on 2010-02-01
Thank you for your response:

Typically after adding a file or w/e I could do:

cd /var/www/
chmod -R -v 0770 *
chown -R -v www-data:www-data *

That is what I am trying to not have to do anymore.


As for a symlink:
If I am the only user, I could symlink /var/www to a place in my user folder and all the files within it would be good to go? Meaning that I could FTP in as my user and create a new file and then view it in a browser and apache2 would be able to read it?

Though I have not tried it yet, to my knowledge the files would still retain their normal permissions / user / group....I am not sure I follow 100%, but I'll give it a try here in a little bit.


Thanks again for your help!!

---

### Post by cjohnweb on 2010-02-06
Quick update:

I found that vsftpd has issues with symlinks.....vsftpd treats it as a file instead of a folder. So I found a command that works:

mkdir /home/user/htdocs
mount   --bind /var/www   /home/user/htdocs


But there is a small catch to this. It needs to be executed after each time you restart. I found that there is a file **/etc/rc.local** - this file is executed upon my system startup *Default with my Ubuntu Server 9.x LTS installation. So I added the **mount** command (above) to this file and it mounts the root folder served by apache (/var/www) to a folder in my home directory (/home/user/htdocs).

I modified my vsftpd config file to restrict users to their home directorys. This way when I FTP in I see a folder called **htdocs** that contains all my website folders.


I had a suggestion from a friend to try and execute the mount code by creating a new file in **/etc/init.d**/ ....
I had too much trouble ...failed miserably....


So now I am have to solve one more issue that I am having. When I FTP in I can read/write new files and folders from the root dir (/home/user/)....but I can not write or modify anything in the htdocs folder (mounted from /var/www to /home/user/htdocs).


This comes down to some sort of user permission or something. I know how to change user/perms/group etc, etc I just don't know what I am supposed to change. How ever it turns out, I would like it to work with multiple users (one account for myself and other accounts will be created for others who should also have ftp access to the website's files and the like).


Thanks for all the help!

---

