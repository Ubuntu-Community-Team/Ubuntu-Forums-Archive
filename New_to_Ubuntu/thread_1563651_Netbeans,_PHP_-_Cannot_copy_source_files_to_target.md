---
title: "Netbeans, PHP - Cannot copy source files to target folder"
date: 2010-08-29
forum: New to Ubuntu
---

### Post by hamofgrey on 2010-08-29
Hi

I am trying to use Ubuntu as my programming/development environment thingy. I want to be able to used Netbeans to create web apps using PHP. All has gone swimmingly except one part...

I want to copy the source files located at:
/home/graham/Projects/blog

to a sub-folder located off apache's root doc dir, the location I want the source files to be copied to is:
/var/www/blog


This basic idea is I want to be able to write my web-app and easily refresh it in Firefox.

When ticking the box to copy the source files in the Project properties I get the error, "Target Folder cannot be created."

I thought this must be a permissions problem so I did the following:

```
sudo su
cd /var/www/blog
chown root /var/www/blog
chmod ug+rwx /var/www/blog -v
chgrp graham /var/www/blog -v
```

This however does not solve the problem even though the permissions appear to have been correctly changed :-(

ls -l produces:

drwxrwxr-x 2 root graham 4096 2010-08-29 17:18 blog

Does anyone have any ideas?!?

Thanks for your help

---

### Post by theDaveTheRave on 2010-08-31
hamofgrey,

I had this same problem when I started developping JSP stuff using the apache Tomcat server.

My solution was to create a 'hard link' to the folder that holds the code on my /home folder.

so you would create a 'hard link' from < /home/graham/Projects/blog > and place this inside < /var/www/blog >

I did all this from within Nautilus, select the folder you want the link to be, right click your mouse, and select the link option

It is important to use a 'hard link' rather than a 'symbolic' one, this is because the needs to believe that a copy of file exists in the new location (done with a hard link), not just a pointer to send the system to the original location (a symbolic link).

Now you just need to start nautilus with root permisions

```
 gksudo nautilus
```

find the 'hard linked folder' and copy it into the /var/www/blog directory.

*** important *** remember to exit the 'root nautilus' when you are done.

This is a nice procedure as it means you can easily edit your files from within your own user base, and see the changes as the occur within the web pages. Once you are happy everything works as it should you can then either delete the version in the /home folder (remember the system thinks the file exists in the other location so it will only remove the reference to it, it will still be accessible from the /var/www/blog folder), or (better still) create a 'true copy' (ie not a hard linked one) in the /var/www/blog folder so as it cannot be accidentally overwritten by you - of course you will need to remember to point your application to the new name of the folder (if you change it).

Again the beauty of this is you can continue to develop and expand the functionality of the system, without 'buggering up' a known working web page.

Hope that works out...

David.

ps. if there are any Guru's out there who think this is a bad solution please let me know, as I've done it lots of times, and it certainly works for ease of access to my JSP stuff. I'm sure however that there is a technically better way around doing it.


pps. you can from the command line create the link from the source file directly into the target directory, but I've always done it via nautilus, it's less scary!

---

### Post by zaphod777 on 2010-08-31
> **hamofgrey said:**
> Hi

I am trying to use Ubuntu as my programming/development environment thingy. I want to be able to used Netbeans to create web apps using PHP. All has gone swimmingly except one part...

I want to copy the source files located at:
/home/graham/Projects/blog

to a sub-folder located off apache's root doc dir, the location I want the source files to be copied to is:
/var/www/blog


This basic idea is I want to be able to write my web-app and easily refresh it in Firefox.

When ticking the box to copy the source files in the Project properties I get the error, "Target Folder cannot be created."

I thought this must be a permissions problem so I did the following:

```
sudo su
cd /var/www/blog
chown root /var/www/blog
chmod ug+rwx /var/www/blog -v
chgrp graham /var/www/blog -v
```

This however does not solve the problem even though the permissions appear to have been correctly changed :-(

ls -l produces:

drwxrwxr-x 2 root graham 4096 2010-08-29 17:18 blog

Does anyone have any ideas?!?

Thanks for your help

What you need to do here is also change the group and access on /var/www and /var otherwise you won't be able to access the folder.

But you could also just right a small bash script to copy the files to the location and put it on your desktop. Just click it and it will prompt you to put your password and then copy overwriting destination files. It might make it a little more secure.

```

#!/bin/bash
function pause(){
read -s -n 1 -p "Done copying press any key to continue . . ."
echo
}
sudo cp -R -f -v /home/graham/Projects/blog /var/www/blog
pause
```

---

