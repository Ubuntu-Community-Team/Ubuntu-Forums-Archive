---
title: "[SOLVED] Samba error 255"
date: 2008-12-31
forum: New to Ubuntu
---

### Post by marcgh on 2008-12-31
After installing samba, I wanted to share with other computers on the LAN and all in 'WORKGROUP' one file.

This is the error I got after right-clicking the file and allow access and Guest access:

'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error Permission denied
You do not have permission to create a usershare. Ask your administrator to grant you permissions to create a share.

What am I doing wrong? (I'm sure it's me!)
Thanks in advance for any advice.

---

### Post by albinootje on 2008-12-31
> **marcgh said:**
>  'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error Permission denied
You do not have permission to create a usershare. Ask your administrator to grant you permissions to create a share.


Can you post your /etc/samba/smb.conf ?

---

### Post by marcgh on 2008-12-31
> **albinootje said:**
> Can you post your /etc/samba/smb.conf ?
Thanks albinootje for your concern.
I have found my solution in this link and my shares are now visible on my XP laptop.

[http://linuxowns.wordpress.com/2008/10/28/share-ubuntu-folders-with-windows-samba/](http://linuxowns.wordpress.com/2008/10/28/share-ubuntu-folders-with-windows-samba/)

Bedankt!

---

### Post by albinootje on 2008-12-31
> **marcgh said:**
> Thanks albinootje for your concern.
I have found my solution in this link and my shares are now visible on my XP laptop.

[http://linuxowns.wordpress.com/2008/10/28/share-ubuntu-folders-with-windows-samba/](http://linuxowns.wordpress.com/2008/10/28/share-ubuntu-folders-with-windows-samba/)
Okay, cool!

Bedankt!

Geen probleem :)

---

### Post by AMD XL on 2009-04-05
The file manager that I am tiring to share is **** up.

See this 

'net usershare' returned error 255: net usershare add: cannot convert name "Everyone" to a SID. Invalid parameter.

How to

---

### Post by jtpoole99 on 2009-04-22
> **AMD XL said:**
> The file manager that I am tiring to share is **** up.

See this 

'net usershare' returned error 255: net usershare add: cannot convert name "Everyone" to a SID. Invalid parameter.



I'm using nautilus and I'm having the same problem with sharing folders.  This post says solved, but I don't see a solution anywhere...

---

### Post by marcgh on 2009-04-22
Hi,
Try this link : [http://linuxowns.wordpress.com/2008/10/28/share-ubuntu-folders-with-windows-samba/](http://linuxowns.wordpress.com/2008/10/28/share-ubuntu-folders-with-windows-samba/)

It solved the problem for me. Good luck.

---

### Post by ojobson on 2010-05-15
The suggestion of opening nautilus using sudo command to have higher permissions when enabling shares does not work for the error:

"'net usershare' returned error 255: net usershare add: cannot convert name "Everyone" to a SID. The connection was refused. Maybe smbd is not running"

It is running because I can access the shares over smb.

anyone have a clue? Just upgraded to 10.04 and haven't a clue what's going on. All the commands for using samba seem to now not work. brilliant.

---

### Post by johnyuan2000 on 2010-07-19
Hi, everybody !

 The same here! it said [SOLVED] but the solution :

  > [http://linuxowns.wordpress.com/2008/...windows-samba/]("http://linuxowns.wordpress.com/2008/10/28/share-ubuntu-folders-with-windows-samba/")did not work for me.

 All I did was upgrade to 10.4 from 9 and all samba share dead and I kept getting Error message :

> net usershare add: cannot convert name "Everyone" to a SID. Invalid parameter.Did anyone work around other than "nautilus root access" ???

any help would be appliciated !

John

---

### Post by timfinley on 2010-08-23
> **johnyuan2000 said:**
> Hi, everybody !

 The same here! it said [SOLVED] but the solution :

  did not work for me.

 All I did was upgrade to 10.4 from 9 and all samba share dead and I kept getting Error message :

Did anyone work around other than "nautilus root access" ???

any help would be appliciated !

John

Bump

Same for me

---

### Post by luvshines on 2010-09-28
I think these are 2 different errors we are talking about:

1. 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error Permission denied

2. net usershare add: cannot convert name "Everyone" to a SID. Invalid parameter.

For the first one, the fix is simple. Add the user to group 'sambashare'

sudo usermod -a -G sambashare <username>

This is because of this:
```

ls -ld /var/lib/samba/usershares/
drwxrwx--T 2 root sambashare 4096 2010-09-28 13:41 /var/lib/samba/usershares/

```

For the second one, can anyone tell me how to recreate it ??

---

### Post by luvshines on 2010-09-28
Yeah, one more thing. The additional group might not become active unless you logout and then login again

---

### Post by HumanAnarchist on 2011-06-06
I can still not solve this problem. Maybe it could be that the folder I am trying to share is on a NTFS partition, that is not auto mounted when the computer starts only when I access it through nautilus.

---

### Post by HumanAnarchist on 2011-06-06
this helped me [https://bugs.launchpad.net/ubuntu/+source/samba/+bug/513427](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/513427) ...
i think, not tried to access it from a win xp computer yet, but hopefully it will work :)

---

### Post by masterlocdown on 2011-11-22
I have tried this but kept getting the errors to repeat so this was what I ended up doing.

I opened up terminal and ran these commands:
sudo apt-get remove samba samba-common
sudo apt-get remove system-config-samba

I then restarted the computer and went ahead and installed the above again to make sure everything is working ok.

sudo apt-get install samba samba-common
sudo apt-get install system-config-samba

and then follow the rest from here:
[http://www.n00bsonubuntu.net/content/install-samba-and-share-folders-ubuntu-10-10-maverick-meerkat/]("http://www.n00bsonubuntu.net/content/install-samba-and-share-folders-ubuntu-10-10-maverick-meerkat/")

---

