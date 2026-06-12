---
title: "Using symbolic links with NAS"
date: 2009-06-05
forum: New to Ubuntu
---

### Post by ceabaird on 2009-06-05
Hello, Absolute beginner here...

I have a dell optiplex running ubuntu server 8.04.2 set up as a LAMP. I have a drupal installation that I am trying to configure as a web-based file server/file management system. The drupal installation is working well, but I want to create a symbolic link from the /sites/default/files on the dell to a 2 TB NAS.

Because of the vast amount of documents, presentations, photos, pdfs, etc., I want to take advantage of the NAS storage capability.

However, I'm not sure about the direction the link should point.

I know the conf is:

> sudo ln -s /path/to/real/file /path/to/non-existant/file

so would that mean: 

> sudo ln -s /var/www/website/sites/default/files /NAS/files

I tried a test version, but I'm not sure what the result meant, it seemed that things came out backwards.

Thanks for any advice.

---

### Post by sazan on 2009-06-05
What you are creating is a soft link for "/var/www/website/sites/default/files" to "/NAS/files" 

You can confirm it with 'ls -l' command , you will see an attribute 'l' infront of the permissions which means link and last column will show the link information 

I hope this is what you are looking for ..

Thanks

---

### Post by ceabaird on 2009-06-12
Thanks for the advice... now I tried the symbolic link listed above, but nothing happened. The directory set-up looks like this:

> sudo ln -s /path/to/real/file /path/to/non-existant/file

where: 

> /var/www/website/sites/default/files 

is part of a drupal testsite I have set up, and the "files" directory still has all the original files in it (images, languages, photos, etc.) when I tried to run the above symbolic link command, nothing seemed to change; the drupal files directory is now

> drwxr-xr-x 9 www-data www-data 4096 2009-04-10 02:55 files

while the files in the NAS are

> drwxrwxrwx 9 99 99 0 2009-06-12 13:33 files

As you can see, neither of them is seen as a symbolic link (lrwxrwx...) but as directories (drwxrwx...). Do I need to set the symbolic link on a new, empty directory to work?

Any advice would be appreciated.

Cheers,

S

---

