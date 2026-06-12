---
title: "Changing Permission for many files"
date: 2011-07-28
forum: New to Ubuntu
---

### Post by Ed_Ziffel on 2011-07-28
Been getting by with just slopping around to change file permissions.

System froze up a day after install so rather than play guess a problem just backed up coding work, or so I thought, to my thumb drive and reinstalled.  Long to short.  Only copied the Directory, no files to thumb drive.  Lost a ton of work.  So now making an effort to do all the proper way.  

After installing lamp I need to have full access as user or log in as root so that I don't have to jerk around with persmissions about how I can't save this or that.  Was using Ctrl_F2 -> gksudo nautilus to change permission which apparently doesn't work.  Have tried to apply folder permissions settings, on say my web root /var/www, for default user to create delete, read/write (which always disappears when you hit the add permissions to enclosed files).  Now cant change permissions for my thumb drive and so can't copy and paste my web files to it.  

Could use some help with this.  Using 10.04 LTS.  How do I set the proper permissions so that I don't have to spend 3 minutes every time I want to change a conf file or change permission on my thumb drive in a reliable fashion?

---

### Post by Paqman on 2011-07-28
> **Ed_Ziffel said:**
> After installing lamp I need to have full access as user or log in as root so that I don't have to jerk around with persmissions

On Ubuntu you don't need to log in as root. The first user has admin rights, which means when you need to you can elevate your privileges to that of the root user.

In short: prefix any command with sudo, enter your password and you're effectively root for that command.

Getting the permissions right on a web-facing server is crucially important. Don't be tempted just to set them as permissive as possible in order to make life easier for yourself. It also makes life very, very easy for an attacker.

> 
Was using Ctrl_F2 -> gksudo nautilus to change permission which apparently doesn't work.

You can do it that way, but the command line is probably quicker and easier in this case.

The two key commands are chmod and chown. Lots of general info [here]("https://help.ubuntu.com/community/FilePermissions"), or if you let us know exactly what you're struggling with we can give more specific advice.

---

### Post by Ed_Ziffel on 2011-07-28
Thanks,

I use bluefish a lot.  I want to be able to change all config files for php5, MySQL and Apache with bluefish, as well as all the files for my frame work, Code Igniter, and separately, all my thumb drive files,.  

To start with, The file that I though I backed up to my thumb drive is an empty directory which even though the permissions show create delete it will not let me move it to the trash.  Permissions say my login user is the owner with create and delete files, --- for file access, but with my login user selected as Group it will not allow me to change permissions.  Did a sudo 777 chmod PATRIOT (my thumb dirve).  Now the PATRIOT file when clicking on the icon has my login user as owner folder access = Create and delete files but will not let me delete the back up file.

It may be important that I have windows machines that I use with the thumb drive and it is formated NTSf.  Have a couple of other Ubuntu boxes am not have a problem with it, then again as stated I BSed by way through it and really want to have things right this time.

---

### Post by Wim Sturkenboom on 2011-07-28
I don't know how to do this in Ubuntu (I will probably edit a config file) as I use Slackware based LAMP servers.

All my (intranet) websites are placed in directories in my home directory and I have told Apache to use those directories as the document roots instead of /var/www (or a subdirectory in there). Only permission issue one has to deal with is if one wants to allow apache to write in the document root.

Maybe somebody with experience with Ubuntu based servers can indicate how to do it; I heard something about a usermodule, but not sure.

---

### Post by stmiller on 2011-07-28
You should never chmod 777 anything, at anytime for any reason.


Having web (apache owned) files in your home directory is going to be problematic as well. :/

Basically, most web software is going to want the entire path to be owned by apache (www-data).

So, put all of your web stuff in:

/var/www/

Then chown it to apache:
```

sudo chown -R www-data:www-data /var/www/

```

If those other users are on Windows or OS X (or Linux) you can setup samba in Linux so they can mount and edit files in that /var/www/ directory.


And yeah you should never ever log in as root, or even use root for any reason as well. 

:)

---

### Post by fdrake on 2011-07-28
well if you just want to change your conf files just use
```

sudo bluefish file.config
```

i would NOT change the ownership of the config file in a webserver(like apche or PHP).


for the website /var/www you can use:
```
chmod -R 755 /var/www
```
for development purposes of course. this way you can move edit and add your website files with no restriction.

---

### Post by Wim Sturkenboom on 2011-07-29
> **Wim Sturkenboom said:**
> 
Maybe somebody with experience with Ubuntu based servers can indicate how to do it; I heard something about a usermodule, but not sure.Found something in [http://ubuntuforums.org/showthread.php?t=1813983](http://ubuntuforums.org/showthread.php?t=1813983)

> **volkswagner said:**
> You also have the option to move your web directory to your home directory and edit the /etc/apache2/sites-available/hostfilename to point to that location.  


---

