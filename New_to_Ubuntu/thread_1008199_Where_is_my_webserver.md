---
title: "Where is my webserver?"
date: 2008-12-11
forum: New to Ubuntu
---

### Post by Roger Allott on 2008-12-11
I've installed Apache, MySQL and PHP. All seems to be fine so far with Apache, because when I go to [http://localhost](http://localhost), I get the message "It works!".

What I want to do now is to do a bog-standard test of PHP by creating a simple phpinfo() page, but I can't work out where it should go in the folder/directory structure that Apache creates in Linux, as it seems to be completely different to the structure created by Apache under Windows.

I guess it must be somewhere in the /etc directory, but could anyone help me with finding out exactly where php files should be stored?

Furthermore, I've located the httpd.conf file, but it seems to be locked. I don't even seem to have permission to read it! Is there an Apache configuration tool out there I could use to do what's necessary?

---

### Post by binbash on 2008-12-11
it should be at /var/www

for howto : 

[http://joeabiraad.com/linuxunix/installing-lamp-on-ubuntu-710-linuxapachemysqlphp/100](http://joeabiraad.com/linuxunix/installing-lamp-on-ubuntu-710-linuxapachemysqlphp/100)

edit the config with sudo

---

### Post by albinootje on 2008-12-11
Between apache 1.x and apache 2.x there's a difference between de structure of the logfiles. If you're using a recent Ubuntu release, then you will be using apache 2.x where the main config lives at /etc/apache2/sites-enabled/000-default
There's also a difference between the "it works" standaard redirect message.
With newer apache2 installations it's a html-file in /var/www but before it was a rewrite rule in the apache2 config, which you should remove to get rid of that message.

---

### Post by Roger Allott on 2008-12-11
Thanks for that guys. I've now managed to create and save an index.php phpinfo file, and I can see on it my PHP setup nicely.

My next problem though is one of simplicity of use. I seem unable to just save a file to /var/www/, which means that the sites I want to copy across won't save there.

Is there any way I can make the /var/www/ directory open access (i.e. not necessitating a sudo command via Terminal)?

Also, does anyone have a recommendation for a php editor? I've got gPHPEdit, but that looks rather basic. I'm used to using Dreamweaver on Windows. Is there anything similar for Linux/Ubuntu?

BTW, my version of Apache is 2.2.9.

---

### Post by Kareeser on 2008-12-11
Basic should be all you need.... heh heh. I personally like a touch of colour, and that's it, so I used Notepad2 in Windows. GEdit fills that niche quite nicely.

As for opening permissions of /var/www, you'll need to modify permissions using the "chmod" command, with the switch "o+w", to give "others" the ability to "write". This is because you don't "own" the directory (for me, "root" owns /var/www), so you're considered a third-party user accessing /var/www.

```

cd /var/www
sudo chmod -R o+w ./*

```

P.S. For bonus points, can anyone fill me in on what might happen if one chown'd /var/www to something else? Would Apache break?

---

### Post by binbash on 2008-12-11
playonlinux has a script for installing dreamweaver 8, also dreamweaver cs3 works with wine : [http://appdb.winehq.org/objectManager.php?sClass=version&iId=7694](http://appdb.winehq.org/objectManager.php?sClass=version&iId=7694)

---

### Post by Roger Allott on 2008-12-12
> **binbash said:**
> playonlinux has a script for installing dreamweaver 8, also dreamweaver cs3 works with wine : [http://appdb.winehq.org/objectManager.php?sClass=version&iId=7694](http://appdb.winehq.org/objectManager.php?sClass=version&iId=7694)

Thanks, but unfortunately my copy of Dreamweaver is very old v6.

What I'm really looking for is something that gives me syntax colour highlighting and having multiple php pages open simultaneously as a project. I certainly don't want the Dreamweaver HTML design nonsense!

---

### Post by Roger Allott on 2008-12-20
> **Kareeser said:**
> Basic should be all you need.... heh heh. I 
As for opening permissions of /var/www, you'll need to modify permissions using the "chmod" command, with the switch "o+w", to give "others" the ability to "write". This is because you don't "own" the directory (for me, "root" owns /var/www), so you're considered a third-party user accessing /var/www.

```

cd /var/www
sudo chmod -R o+w ./*

```

P.S. For bonus points, can anyone fill me in on what might happen if one chown'd /var/www to something else? Would Apache break?

That code is very useful but it seems to last only as long as one's session. Upon reboot, the original permissions settings are re-set.

To avoid having to re-enter that code every time I try to do anything with my local php files etc., is there a command that I can run that will permanently change the permissions for that directory?

---

### Post by louieb on 2008-12-20
Change permissions of the folder itself. ```
sudo chmod 777 /var/www
```

I changed my apache configuration to use a directory in my home folder. 

good stuff here [ApacheMySQLPHP - Community Ubuntu Documentation]("https://help.ubuntu.com/community/ApacheMySQLPHP")

---

### Post by Roger Allott on 2008-12-20
> **louieb said:**
> Change permissions of the folder itself. ```
sudo chmod 777 /var/www
```

Thanks for that. It works fine now. Hopefully it will do when I reboot too!

> **louieb said:**
> I changed my apache configuration to use a directory in my home folder. 

That's very sensible. Oh well, the files are now in var/www, but if I hit any more permissions probs I'll try that approach.

---

### Post by Iowan on 2008-12-20
Another option is to move the document root somewhere else - such as /home/<yourusername>/www. (the directory will need to exist, first) 
More details [here]("https://help.ubuntu.com/community/ApacheMySQLPHP").

---

