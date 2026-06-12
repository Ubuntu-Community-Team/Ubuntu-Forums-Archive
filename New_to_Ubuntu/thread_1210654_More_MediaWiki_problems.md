---
title: "More MediaWiki problems"
date: 2009-07-11
forum: New to Ubuntu
---

### Post by geek_of_doom on 2009-07-11
After setting chmod 755 on the images/ directory within the wiki, I receive the following error whenever uploading an image:

The upload directory (public) is not writable by the webserver.

The only way to get it working is by giving Write access for Other, and that's certainly unsafe. So...any solutions, or extra information I need to give you?

---

### Post by bernied on 2009-07-11
chmod 755 will give write access to the user owner only, not to the group owner. Are you sure you don't want 775?

Use 'ls -l' to find ownership of the directory
Use 'ps -ef | grep apache' to find out the user name for the webserver (if your webserver is apache, else use whatever it is instead of apache)
Use 'groups www-data' to find out which groups the user www-data is a member of.

Hope this helps,
Bernie

---

### Post by geek_of_doom on 2009-07-12
> **bernied said:**
> chmod 755 will give write access to the user owner only, not to the group owner. Are you sure you don't want 775?

Use 'ls -l' to find ownership of the directory
Use 'ps -ef | grep apache' to find out the user name for the webserver (if your webserver is apache, else use whatever it is instead of apache)
Use 'groups www-data' to find out which groups the user www-data is a member of.

Hope this helps,
Bernie
Okay, sudo chmod 775 images/ worked about as well as 755 did. The images/ directory is owned by root, but interestingly enough, all the other files and directories in the wiki/ folder are *not*. Do I need to chown everything in wiki/ to root?

As I said above, images/ is owned by root, while all other files in the wiki/ directory are not. apache itself is owned by root.

groups www-data returned nothing more than "www-data."

---

### Post by bernied on 2009-07-13
I can't tell from here what user your webserver runs under. It would help if you could post your detailed findings on the forums. Else I'm just guessing the details.

I'm also not familiar with mediawiki software, and I was only guessing that it runs on apache. Can you confirm that?

In general, changing ownership to root, and running everything as root, is not good security policy. You are basically subverting the whole permissions system, so making the system insecure. If there was a fault in the webserver software for example (or more likely in the configuration files), and it was running as root, then someone outside the system could have write access to the whole system.

The fact that you have a www-data user suggests that apache has been installed using that user, but you say that:
> apache itself is owned by rootDo you mean the apache executable is owned by root (which is normal) or the process (as found using the 'ps' command) is owned by root (which is not the best)? Again, posting the results of those commands would help.

I suggest that you -
1. change group ownership in directories that need to be written by apache to www-data, like this:
```
sudo chown -R :www-data /path/to/directory
```
and
2. make sure that the webserver (is it apache?) is running as the www-data user, not as root. This is done in the server configuration, then you'd need to restart it.

Doing only one of these things will not help.

I'm not going to advise you to change ownership of everything to root, because then you'll only be able to edit stuff as root. And using permissions 777 is too insecure. Better to use permissions 775, group ownership, and make sure any users (including the webserver) that need to edit the directory are members of the group in question.

You can also make group ownership of directories sticky, so that any new files written there have the same group ownership.
```
sudo chmod g+s /path/to/directory
```

Google stuff that is unfamiliar. You are running a webserver, you should really know how it works, or you're asking for trouble.

---

### Post by geek_of_doom on 2009-07-13
Sorry, this is why I've posted in the Absolute Beginner talk.

I know for certain that MediaWiki runs on Apache 2.

I'm not sure which, the executable or the process, is owned by root. Here are the results from ps -ef | grep apache:

root      5402     1  0 08:34 ?        00:00:00 /usr/sbin/apache2 -k start
www-data  5499  5402  0 08:34 ?        00:00:00 /usr/sbin/apache2 -k start
www-data  5500  5402  0 08:34 ?        00:00:00 /usr/sbin/apache2 -k start
www-data  5501  5402  0 08:34 ?        00:00:00 /usr/sbin/apache2 -k start
www-data  5502  5402  0 08:34 ?        00:00:00 /usr/sbin/apache2 -k start
www-data  5503  5402  0 08:34 ?        00:00:00 /usr/sbin/apache2 -k start
my_user_name    7703  7686  0 12:07 pts/1    00:00:00 grep apache

Running sudo chown -R :www-data /var/www/ caused all files within the /var/www/ directory to be owned by www-data, which, judging by the man page, seems to be the intent. Re-running ps -ef | grep apache once again returns nearly identical results:

root      5402     1  0 08:34 ?        00:00:00 /usr/sbin/apache2 -k start
www-data  5499  5402  0 08:34 ?        00:00:00 /usr/sbin/apache2 -k start
www-data  5500  5402  0 08:34 ?        00:00:00 /usr/sbin/apache2 -k start
www-data  5501  5402  0 08:34 ?        00:00:00 /usr/sbin/apache2 -k start
www-data  5502  5402  0 08:34 ?        00:00:00 /usr/sbin/apache2 -k start
www-data  5503  5402  0 08:34 ?        00:00:00 /usr/sbin/apache2 -k start
my_user_name    7726  7686  0 12:13 pts/1    00:00:00 grep apache

---

### Post by bernied on 2009-07-13
Brilliant - your apache is running the same way as mine. It starts as root, but new processes are owned by www-data. So there's no need to restart apache.

> Running sudo chown -R :www-data /var/www/ caused all files within the /var/www/ directory to be owned by www-data, which, judging by the man page, seems to be the intent.Are you sure that's what you're seeing? The colon before the www-data in that command refers to group ownership. when you do 'ls -l', the first name on each line is the user, the second is the group. Hopefully it was the group ownership we changed with that command.

Has this fixed the problem?

Googling linux permissions will find stuff like this:
[http://www.linuxclues.com/articles/16.htm](http://www.linuxclues.com/articles/16.htm)
(as well as lots of less useful stuff)

And I still think you should use the set group ID bit (the last chmod command I suggested in my last post) on the folder, if multiple users are going to be accessing it. If only apache is going to use it, then this is not necessary. 

And add yourself (and other users that need to write to the directory) to the www-data group:
```
sudo adduser www-data your_user_name
```

Some more stuff:
[http://www.codecoffee.com/tipsforlinux/articles/028.html](http://www.codecoffee.com/tipsforlinux/articles/028.html)

And I'm sorry I didn't notice the post was in the beginners forum. I don't think of webservers as a beginners topic.

---

