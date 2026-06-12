---
title: "Mkdir and unzipping permission failure"
date: 2009-12-11
forum: New to Ubuntu
---

### Post by mathew edison on 2009-12-11
Now I know that a lot of you want to throw a giant RTFM at me but I'm seriously stuck with my php script in apache. I've chmodded the entire www to 777 and some forums instructed me to change the owner of the files to www-data. I did all of this using -R or recursive or whatever it's called and the owner actually is www-data and the whole danged thing is chmodded 777 but I still get a permission error from PHP when I try mkdir and unzipping. It's driving me nuts and I hope someone can provide me with an answer :) Seeing as this is permission matter within Ubuntu I thought I'd better post it here in stead of the php forums :)

Thx a lot in advance
sincerely
 - Mathew

---

### Post by Mornedhel on 2009-12-11
The point of chown-ing to www-data and chmod-ing to 777 is so that your HTTP server can read the files (to serve them on the web). You still need the permissions, as a user, to create files in the /var/www directory.

If you plan to do a lot of manipulations in there, I suggest you do ```
sudo -u www-data -i
``` in your terminal so you can act as the www-data user. Files you create while logged as www-data should then automatically belong to www-data.

---

### Post by mathew edison on 2009-12-12
Thx for the reply Mornedhel. I tried that in the terminal but all I get is a dollar sign in stead of the full user location and then it does nothing. Besides how can it be that I gave my www directory full read and write permisssion and still PHP can't create a directory...

---

### Post by Mornedhel on 2009-12-12
Yes, that would be a dash prompt. Since www-data is not a "real" user, its default shell is a minimalistic one. You can either use that as you would normally any shell, or start a bash shell (by typing bash at the dash prompt). The point is to get you to act as www-data so you don't have to chown every file you create to www-data by hand.

For the permissions part, check that the /var/www directory itself has write access for you. If not, you will have to either do your thing as root (normal sudo) and chown back to www-data later (not really recommended), sudo to www-data, or give write access to www-data to everyone (not really recommended either).

FYI, the permissions on a /var/www that I help maintain on a Debian box with lighttpd are rwxr-xr-x for directories and rw-r--r-- for PHP scripts and other files.

---

