---
title: "Create Desktop Launcher and include sudo password?"
date: 2010-08-23
forum: New to Ubuntu
---

### Post by MaxVK on 2010-08-23
Hi. I'm using Xampp for some development work and I have two launchers on my desktop, one to start Xampp and one to stop it.

Xampp needs to be started with sudo, so I have: "*sudo /opt/lampp/lampp start*" as the command in one of the launchers. However, its a pain to keep typing the password, so is there a way to include the password for sudo inside the launcher (so I can just click it and go)?

Cheers

Max

---

### Post by MaxVK on 2010-08-24
Just a 'lil old bump!

---

### Post by tom.swartz07 on 2010-08-24
The only way I could think of getting the same result you're looking for is to create a launcher script, and give it root permissions.

open gedit (or any other plain-text editor)
and type the following:

```
#!/bin/bash
/opt/lampp/lampp start

```

Save it to your desktop, then right click the icon. Properties>Permissions. 

Select 'execute'

and you should be good from there!

Repeat the process with the 'stop', you simply have to edit the 2nd line in the script, natch. 

Hope this helps!

---

### Post by MaxVK on 2010-08-24
Thanks Tom, but it doesn't seem to work. When I click on the file it asks how it should be run (in terminal etc) but whichever way I try to run it there is a very quick flash on the screen and thats it. Xampp however, is not running.

Its not a real biggie, but its one of those little niggles that Id really like to get sorted out.

Any other ideas anyone?

Cheers

Max

---

### Post by inameiname on 2010-08-24
I had a similar question a few days back, and I was able to figure out a solution. Check it out:

[http://ubuntuforums.org/showthread.php?t=1556333](http://ubuntuforums.org/showthread.php?t=1556333)

---

### Post by tom.swartz07 on 2010-08-24
> **inameiname said:**
> I had a similar question a few days back, and I was able to figure out a solution. Check it out:

[http://ubuntuforums.org/showthread.php?t=1556333](http://ubuntuforums.org/showthread.php?t=1556333)

Ah! a cron job! I knew I forgot something.

Yeah, follow the method that inameiname used, that will get it to work, the only thing is, it could only easily be run on a schedule, not upon command.

---

### Post by x1a4 on 2010-08-24
Configure your system to open lampp without asking for authentication.  Be sure you know exactly why you want to do this.  Convenience is not a good reason.  Anyway, just edit the file /etc/sudoers.  Do it using 'visudo'
```
sudo visudo
```
and append 
```
%usergroup LOCAL=NOPASSWD:/opt/lampp/lampp
```
to the file.

Where %usergroup is the group name of the user(s) who will use lampp without asking for password. 

Look in the manual for sudoers(5) and visudo(8).

---

### Post by MaxVK on 2010-08-25
Thanks guys Ill look into that later on.

> Convenience is not a good reason.

x1a4: Your modified method looks like its the one that will be the best, but why do you say this? The whole point is convenience and I'm the only one with access to the machine. Would this produce any serious kind of security risk? (and if so is it possible to keep the convenient method of starting and stopping Xampp while negating the security risk?)

Cheers all

Max

---

### Post by gandaran on 2010-08-25
you can also start lampp with gksu in your launcher
```
gksu /opt/lampp/lampp start
```
this way you just click the start launcher and type the the password in the gksu dialog box

---

### Post by inameiname on 2010-08-25
To [tom.swartz07]("http://ubuntuforums.org/member.php?u=831692"), that method I figured out works just fine for me, both on a schedule (have it run at startup through Startup Applications), AND on command, whenever I feel like clicking the desktop launcher. I even have an alias for it in my .bashrc file for whenevever I feel like running it while using the terminal. So if you're having trouble with not being able to run it on command, I'm not sure why. Just remember you have to insert your own username, (not 'me'), in it, which I forgot to put on my post.

---

### Post by x1a4 on 2010-08-25
> **MaxVK said:**
> 
x1a4: Your modified method looks like its the one that will be the best, but why do you say this? The whole point is convenience and I'm the only one with access to the machine. Would this produce any serious kind of security risk? (and if so is it possible to keep the convenient method of starting and stopping Xampp while negating the security risk?)


I suppose there isn't that big of a security threat as long as you configure xampp, apache, mysql correctly and ensure that you have only allow local users to run it without a password (The LOCAL alias).  

BTW I forgot to mention that you probably need to create the host alias.  I don't remember if it's created by default.  If not add this line 
```
Host_Alias LOCAL = localhost, *compname*
```
in the Host alias block of the file (under the '# Host alias specification' comment)
Where *compname* is the name of your computer.

Remember that you still have to run lampp using sudo/gksudo which (without specifying a user) will run as root and if you have NOPASSWD set it will not ask for a password.

---

### Post by MaxVK on 2010-08-25
Well Xampp is set up nicely so I doubt that Ill have a problem in that respect. Ill be getting on this once I'm back at home!

Cheers

Max

---

