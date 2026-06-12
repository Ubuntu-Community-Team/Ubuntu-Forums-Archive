---
title: "Permission Denied Error Message creating new folder on Desktop"
date: 2010-12-29
forum: New to Ubuntu
---

### Post by ozark_hillbilly on 2010-12-29
Evidently the Permissions aspect of Linux is my achilles heel. I still don't understand it.

I just tried to create a new folder on my Desktop and was denied.
Error creating directory: permission denied.

I can't even save a screenshot of the error message. Permission denied.

Do I have to go into Terminal mode and change something around to give me full admin privileges again?  :confused:

A Dazed & Still Confused Old Hillbilly,  :lolflag:  

Ed

---

### Post by Foxheadz on 2010-12-29
in System>administrator>users and groups their is an option to edit the permissions of certain users. Youll probably find something useful there.

---

### Post by Idefix82 on 2010-12-29
There is something wrong with your permissions. You should always be able to save things on your desktop. Can you open the terminal, type in
```

ls -l ~
```
and copy the line that contains the entry Desktop? If there is no sensitive private data displayed, you may as well copy the whole output, since the permissions on the rest of your home folder might also be screwed up.

---

### Post by matt_symes on 2010-12-29
Hi

> **Idefix82 said:**
> There is something wrong with your permissions. You should always be able to save things on your desktop. Can you open the terminal, type in
```

ls -l ~
```and copy the line that contains the entry Desktop? If there is no sensitive private data displayed, you may as well copy the whole output, since the permissions on the rest of your home folder might also be screwed up.

+1 to this.

Also, at the terminal, type

```
whoami
```and post back results so we know who you are.

I assume you can sudo to create a directory on your desktop?

```
sudo mkdir ~/Desktop/test_dir
```

Does this succeed?

Kind regards

---

### Post by ozark_hillbilly on 2010-12-29
whoami = ed

i can't print out the listing since permissions is hanging me up....

it looks like the files are controlled by root....

how do i change this stuff to remove root as owner?

OK, I think I might know what has happened. In trying to get my data files transferred to my release 10.04 install i must of went in and changed permissions somehow so it would let me copy the files to the new install. This is something i did a week or so ago. In the interim i decided to purchase a USB zipdrive (which is still in shipping) and copy my data files to it and then to the new Lucid Lynx install from the zipdrive. Someone else here on the forums recommended this to avoid ownership and permission problems during the file transfers. I wish there was a way i could remove or just override permissions as I don't need or use that security aspect on this computer.

---

### Post by Idefix82 on 2010-12-29
Why don't you just copy and paste? The curvy thing is called tilde, but since I don't know your keyboard I can't tell you where to find it.

If you get "permission denied" when executing the command, prepend sudo to it.

---

### Post by baadford on 2010-12-29
the whoami command isnt asking who you are personally, its asking who you are logged into the computer as
if you go to system > administration > users and groups you should be able to edit your account type to administrator.

also, specifically, you dont want to change root as owner, but change yourself to have root permissions.

but im a noob still myself, so im sure there are better ways to go about this.

---

### Post by SuaSwe on 2010-12-29
I don't have my Ubuntu box in front of me but I do believe that if your home folder has been changed to being owned by root, you should be able to change that back to your username using 'chown'. 

E.g. if you do:

```

ls -l /home/

```

and get something like this by your home folder:

```

// output omitted
drwx------   3 root root     512 Apr 12  2010 ed
// output omitted

```

... it would suggest that your own home dir is owned by root instead of by you. If this is the case, I expect that the following should solve it (though for all I know this could cause problems, and I expect would also take ages with all those files - hopefully someone else can confirm/deny?):

```

sudo chown -R ed /home/ed/
sudo chmod 700 /home/ed    <== edit: ignore this one!

```

This would set you as owner to /home/ed and all its contents [edit: ignore the following bit!] as well as give you permissions to read, write and execute its files.

---

### Post by Idefix82 on 2010-12-29
> **baadford said:**
> 
also, specifically, you dont want to change root as owner, but change yourself to have root permissions.

but im a noob still myself, so im sure there are better ways to go about this.

This is completely wrong. Do **not** follow this advice.

---

### Post by SuaSwe on 2010-12-29
Actually, reading from here: [http://ubuntuforums.org/showthread.php?t=857847](http://ubuntuforums.org/showthread.php?t=857847)

Don't do the chmod one I suggested, looks like that really can cause problems!

Is your home folder owned by root though?

---

### Post by matt_symes on 2010-12-29
Hi

> **ozark_hillbilly said:**
> I wish there was a way i could remove or just override permissions as I don't need or use that security aspect on this computer.

Permissions are in integral part of Linux and Unix and have been since the start. They are an integral part of security model and it is far better to spend the time to earn them. These will help...

[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)
[http://www.linuxforums.org/articles/file-permissions_94.html](http://www.linuxforums.org/articles/file-permissions_94.html)
[http://catcode.com/teachmod/](http://catcode.com/teachmod/)
[http://www.elated.com/articles/under...g-permissions/]("http://www.elated.com/articles/understanding-permissions/")

And if you have questions on permissions post them here (after reading up first)

Kind regards

---

### Post by matt_symes on 2010-12-29
Hi

 > you dont want to change root as owner, but change yourself to have root permissions.Telling someone how to start a gnome session as root will get you kicked off this forum. If that is what is being suggested and not a temporary elevation of privileges using gksudo then this is the daftest advice i have heard in a long time.

Although i am sure the poster was espousing the use of gksudo.

Kind regards

---

