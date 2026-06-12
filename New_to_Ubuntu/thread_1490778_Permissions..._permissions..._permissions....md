---
title: "Permissions... permissions... permissions..."
date: 2010-05-22
forum: New to Ubuntu
---

### Post by Abera on 2010-05-22
[SIZE=2]It seems alot of what I try to do it says You don't have the [/SIZE]permissions.  Where might I go to change full permissions to me? I set up LAMP with my desktop. When I try to move anything in to the www dir it tells me [SIZE=2]You don't have the [/SIZE]permissions to make changes. 
Thanks

---

### Post by tankjer on 2010-05-22
Try to use that command:
*sudo chown yourusername /dirname -R*

For example if www dir is /www and your username is abera then:
*sudo chown abera /www -R*
Chown command changes the owner of a file or a folder. When used with -R parameter it works recursive, that is it changes the ownership of files and folders under that folder too.

---

### Post by Abera on 2010-05-22
> **tankjer said:**
> Try to use that command:
*sudo chown yourusername /dirname -R*

For example if www dir is /www and your username is abera then:
*sudo chown abera /www -R*
Chown command changes the owner of a file or a folder. When used with -R parameter it works recursive, that is it changes the ownership of files and folders under that folder too.
Alright... That did it and thank you!

---

### Post by Nythain on 2010-05-22
oh please, dont chown your /www dir
just

sudo mv <files> /www/where/you/need/them

most web servers will run scripts and the such as either root or http or web-server or whatever... if you chown your /www, you will have to give "other" write access at times, and that is the last thing you want to do for a web server (and thats just one of many reasons you probably shouldnt chown your web directory)

---

### Post by Abera on 2010-05-22
tankjers way  seemed to be the only way I could move my dirs and files to the www dir and work on them.  It's just a local test site only for my live site.
Thanks

---

### Post by 3rdalbum on 2010-05-22
> **Abera said:**
> tankjers way  seemed to be the only way I could move my dirs and files to the www dir and work on them.  It's just a local test site only for my live site.
Thanks

tankjers method is okay for a local test site, but it's not actually the best security practice which is what Nythain was trying to say.

On Ubuntu, your ordinary user account can only modify files inside its home directory. Everything else is restricted to the administrator (root), to prevent attack by local users, local programs, viruses, and crackers.

This includes the /var/www directory.

Tankjer's code makes /var/www writable by anybody on the system, which is a **loosening** of security policy. If this was a production server, a remote attacker who gains access to your user account would now be able to deface your website with impunity; whereas before, they would also have to guess your password.

What Nythain advocated was that you simply elevate your privileges to root temporarily, for one operation (the copy or move operation). That's what the 'sudo mv' and 'sudo cp' commands are for - the 'sudo' bit says "Run this as root). Nythain's approach **preserves** security policy on the system; no attacker can modify the /var/www directory without guessing your password, which is the status quo.

Most Ubuntu users will advise the same as Nythain and I, especially when you get into situations where you're copying files into places more important than /var/www. For some places on your system, changing the permissions can stop the system from working.

So remember: If you run a command and get "permission denied", then run it again with the 'sudo' command before it. So, if your command was "cp file.html /var/www/file.html", then make it "sudo cp file.html /var/www/file.html".

If you are running a desktop on your machine, you can use this method to run a file browser window as root, where you can make whatever modifications or copies you want:

```
gksudo nautilus
```

('gksudo' is for graphical programs).

---

### Post by Abera on 2010-05-22
Tankjer's code makes /var/www writable by anybody on the system, which  is a **loosening** of security policy.
If you mean anyone using my system then I am the only one. This is a local test site that I will use to test the modifications and then upload to my live site at my host, so am I open to the net, or is the server truly offline? I know with WAMP (one Windows app for a local server) can be on, or offline. There are 1047 files and 10 dirs and working with alot of them all of the time.  if I'm offline then I'd be ok wouldn't I?
Thanks

---

### Post by dubhear on 2010-05-23
> **Abera said:**
> [SIZE=2]When I try to move anything in to the www dir it tells me [SIZE=2]You don't have the [/SIZE]permissions to make changes. 
Thanks

> **tankjer said:**
> Try to use that command:
*sudo chown yourusername /dirname -R*

For example if www dir is /www and your username is abera then:
*sudo chown abera /www -R*
Chown command changes the owner of a file or a folder. When used with -R parameter it works recursive, that is it changes the ownership of files and folders under that folder too.

I think command sudo chown WITH -R is not necessary. A bit like shooting a fly with a cannon. 


Next time go with the Nythain way. think about 1,446 beans vs. 5 tankjer beans. no offense but that's just the way it is. don't shoot the messenger :)
> **Nythain said:**
> oh please, dont chown your /www dir
just

sudo mv <files> /www/where/you/need/them

most web servers will run scripts and the such as either root or http or web-server or whatever... if you chown your /www, you will have to give "other" write access at times, and that is the last thing you want to do for a web server (and thats just one of many reasons you probably shouldnt chown your web directory)

> **Abera said:**
> if I'm offline then I'd be ok wouldn't I?
Thanks more or less so. "if it ain't broken why fix it?"

either way mark the thread solved, thanks, peace.

---

### Post by Abera on 2010-05-23
Next time go with the Nythain way. think about 1,446 beans vs. 5 tankjer beans. no offense but that's just the way it is. don't shoot the messenger 

and you dubhear with 57? Look at 3rdalbum 8,029. Not a word from him. He shows class. You? Not here to argue. Here to find the answer to my question from users like 3rdalbum.  

This is a local test site that I will use to test the modifications and then upload to my live site at my host, so am I open to the net, or is the server truly offline? I know with WAMP (one Windows app for a local server) can be on, or offline. There are 1047 files and 10 dirs and working with alot of them all of the time. If I'm offline then I'd be ok wouldn't I?
Thanks

---

### Post by theozzlives on 2010-05-23
> **Abera said:**
> Next time go with the Nythain way. think about 1,446 beans vs. 5 tankjer beans. no offense but that's just the way it is. don't shoot the messenger 

and you dubhear with 57? Look at 3rdalbum 8,029. Not a word from him. He shows class. You? Not here to argue. Here to find the answer to my question from users like 3rdalbum.  

This is a local test site that I will use to test the modifications and then upload to my live site at my host, so am I open to the net, or is the server truly offline? I know with WAMP (one Windows app for a local server) can be on, or offline. There are 1047 files and 10 dirs and working with alot of them all of the time. If I'm offline then I'd be ok wouldn't I?
Thanks

If you're behind a router (and don't have port 80 forwarded), or have a dynamic IP you should be okay. Just because you have more "beans" doesn't mean you have more knowledge.

---

### Post by BoneKracker on 2010-05-23
Another way to handle such things is to create a group to which the web server administrators belong (which is apparently just you at this point), and then, in the relevant directories, assign that group identifier and enable selective permissions without altering ownership or other permissions.

---

### Post by Abera on 2010-05-23
> **theozzlives said:**
> If you're behind a router (and don't have port 80 forwarded), or have a dynamic IP you should be okay. Just because you have more "beans" doesn't mean you have more knowledge.
Thank you sir. That's all I wanted to know and how true that is on the knowledge.

---

### Post by dubhear on 2010-05-24
All I wanted to do is to guide you and any other who find this thread by searching a solution to their problems (we don't do this just for you... you know). 

If that doesn't "show class" then I don't know what does!?!

You got your solution? yes? try marking this thread as "solved" for further convenience. please.

ps. i didn't mean to hurt anyone, just wanted to say that we users are all real persons like you, we make mistakes, we forget things and so on...

pps. i hope no feelings were hurt in progress of this thread. if so. i'm sorry. please forgive me.

---

### Post by Abera on 2010-05-24
Just want to thank all of you for your help. I did get the permissions set and I can see and work the test site. I have never been to a vBulletin forum and If I could figure out how to mark it solved dubhear I would. No hare feeling here.;)
Thanks again

---

### Post by dubhear on 2010-05-24
[http://ubuntuforums.org/showthread.php?t=524404&highlight=mark+as+solved](http://ubuntuforums.org/showthread.php?t=524404&highlight=mark+as+solved)

---

