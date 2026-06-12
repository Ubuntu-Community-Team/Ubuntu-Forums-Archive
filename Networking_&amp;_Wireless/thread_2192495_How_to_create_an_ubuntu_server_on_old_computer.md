---
title: "How to create an ubuntu server on old computer?"
date: 2013-12-08
forum: Networking &amp; Wireless
---

### Post by a_willett on 2013-12-08
[COLOR=#000000][FONT=Helvetica Neue]Im following this project on how to build a Linux Web Server Computer and I'm almost done! But when I try to allow sharing on my www folder ubuntu says that "Sharing service is not installed: You need to install the Windows networks sharing service in order to share you folders". When i select "Install service" It directs me to install something called "samba" but then immediately says "Can not install 'samba' (E:Unable to correct problems, ou have held broken packages.)" How can I fix whatever's going on so I can share this folder and finish this server set up? I'm like right there at the end >.< [/FONT][/COLOR]

[COLOR=#000000][FONT=Helvetica Neue]Link to project: 
[/FONT][/COLOR][http://www.makeuseof.com/tag/build-linux-web-server-computer-part-2/](http://www.makeuseof.com/tag/build-linux-web-server-computer-part-2/)

---

### Post by ian-weisser on 2013-12-08
Which version of Ubuntu (10.10, 12.04, 12.10, 13.04, 13.10) did you install?
Since the instructions included installing Synaptic, open it up and check the 'broken packages' filter. Let us know *exactly *what it says.

---

### Post by a_willett on 2013-12-08
I have Ubuntu 12.04 LTS because I'm a noob and it had more support with it. 

I went to "Synaptic Package Manager" went to the "Missing Recommends" and downloaded all the suggested files again. That solved the problem and I was able to check "Share this folder"  But now went I go to okay the changes with "Create Share" ubunu says:

'net usershare' returned error 255: net usershare add:
cannot share path/var/www as we are restricted to
only sharing directories we own.
Ask the administrator to add the line "usershare
owner only=false"
to the [global] section of the smb.conf to allow
this

and won't let me continue

---

### Post by a_willett on 2013-12-08
i don't feel so bad because i read the post comments and everyone else got stuck here too hehe

---

### Post by ian-weisser on 2013-12-08
> **a_willett said:**
> 'net usershare' returned error 255: net usershare add:
cannot share path/var/www as we are restricted to only sharing directories we own.
Ask the administrator to add the line "usershare owner only=false" to the [global] section of the smb.conf to allow this

The author of the article addressed this in the comments:

> You will have to run [gk]sudo gedit /etc/smb/smb.conf to edit that file as  the root user. It should let you edit it and then change permissions on  that /var/www file as well.

So:

1) Use the command **gksudo gedit /etc/smb/smb.conf** to open the Samba configuration file with the correct permission to edit and save changes.

2) In that file, find the [global] section.

3) In that section add the line *usershare owner only=false*

4) Save the changed file. Close gedit.


Changing the permissions of /var/www is a different issue.




There are lots of ways to share files. Samba is merely one good way.

---

### Post by SeijiSensei on 2013-12-08
And restart samba with "sudo service samba restart" so it will reread the changed configuration file.

---

