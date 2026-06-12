---
title: "[SOLVED] logging in as root from main screen (8.10)"
date: 2009-01-05
forum: New to Ubuntu
---

### Post by theacerguy on 2009-01-05
im a relativity experienced linux user but brand new to ubuntu i tried to log in as root from the main screen but it said super user canot log in at this screen how do i log in as root???:confused::confused::confused:

---

### Post by halitech on 2009-01-05
you can't because of the security model that Ubuntu uses. You log in as  your user and then use sudo to do admin work on the system.

---

### Post by theacerguy on 2009-01-05
im a relativity experienced linux user but brand new to ubuntu i tried to log in as root from the main screen but it said super user canot log in at this screen how do i log in as root???:confused::confused::confused:

---

### Post by arpanaut on 2009-01-05
you don't...

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by halovivek on 2009-01-05
> **theacerguy said:**
> im a relativity experienced linux user but brand new to ubuntu i tried to log in as root from the main screen but it said super user canot log in at this screen how do i log in as root???:confused::confused::confused:

it is not always wise to log in as root user from the main screen. because of security. log in as normal user then go to terminal and login there as root to install or update the software.

---

### Post by jiangshi on 2009-01-05
Ubuntu's default is to not enable root logins. Even the server version has the root login disabled. The recommended procedure is to use sudo in a terminal window. For the desktop, you can easily gui edit and save system config files.

sudo gedit <filename>

Enabling the root logon for Ubuntu is a very sore subject for some of the admins on these Ubuntu forums. This is one area where the Ubuntu credo and philosophy does not seem to apply. The powers that be are very determined to save us from ourselves, and if anyone posts on an Ubuntu forum how to log on as root, they go to some sort of "jail."

I believe that linuxquestions.org does not have any of these prohibitions.

~jiangshi

---

### Post by theacerguy on 2009-01-05
ok im used to logging in as root when needed sorry about double post of topic firefox is playing up is it possible with hacks?

---

### Post by theacerguy on 2009-01-05
thanks everyone when i used opensuse i always logged in as root for most things it saved me typing my password every time can i do it in a hack or something?

---

### Post by stchman on 2009-01-05
> **theacerguy said:**
> im a relativity experienced linux user but brand new to ubuntu i tried to log in as root from the main screen but it said super user canot log in at this screen how do i log in as root???:confused::confused::confused:

There is NEVER a need to log in as root.

The sudo command in a terminal is all you need.  If you need to run a graphical program as root use gksudo.  If you log in as root you bypass all of the security Linux has.

Also NEVER run Firefox as sudo, NEVER.

---

### Post by jken146 on 2009-01-05
It is possible to log in as root, and not difficult to enable, once you know how.  It's not recommended though, as sudo pretty much covers everything you (probably) need.  To get a 'root' prompt: ```
sudo -i
```

---

### Post by stchman on 2009-01-05
> **theacerguy said:**
> im a relativity experienced linux user but brand new to ubuntu i tried to log in as root from the main screen but it said super user canot log in at this screen how do i log in as root???:confused::confused::confused:

There is NEVER a need to log in as root.

The sudo command in a terminal is all you need.  If you need to run a graphical program as root use gksudo.  If you log in as root you bypass all of the security Linux has.

Also NEVER run Firefox as sudo, NEVER.

---

### Post by theacerguy on 2009-01-05
ok the only reason was i needed to create another user but it kept rejecting my root password so i tried logging in as root i found if you use kde user manager it works just a question why never run firefox sudo??

i find it easier to use root if installing software

---

### Post by halitech on 2009-01-05
yes

---

### Post by halitech on 2009-01-05
running firefox as root opens your system up to all the nasties that are on the internet as you browse. If you do that you might as well have a root account with no password with a big red flag saying "fark my system up for me please"

---

### Post by scorp123 on 2009-01-05
> **theacerguy said:**
> when i used opensuse i always logged in as root for most things  Congratulations on you having been lucky so far ... **[COLOR="Red"]one accidental "drag & drop" in the wrong places and your system will be hosed! [/COLOR]**Been there + done that, when I was a noob (I should have listened .... ).

Also .... I assume you surfed the web when you were "root"?? And therefore giving all the stupid malware you might have encountered full "root" priviledges so they can do actual system-wide damage? (something that could not happen if you were a normal user ... ) :D

What I am trying to tell you:
**[COLOR="Red"]You are not supposed to login to "root" unless you have system-admin tasks to do. [/COLOR]** If you do way too many things have way too much power. It's easy to hose your system in an instant. As I said: been there + done that back when I was a noob .... 

You should read this:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by wizard10000 on 2009-01-05
> **jiangshi said:**
> ...Enabling the root logon for Ubuntu is a very sore subject for some of the admins on these Ubuntu forums. This is one area where the Ubuntu credo and philosophy does not seem to apply. The powers that be are very determined to save us from ourselves, and if anyone posts on an Ubuntu forum how to log on as root, they go to some sort of "jail."

And here's the policy.

[http://ubuntuforums.org/showthread.php?t=765414](http://ubuntuforums.org/showthread.php?t=765414)

---

### Post by scorp123 on 2009-01-05
> **theacerguy said:**
> im a relativity experienced linux user but brand new to ubuntu i tried to log in as root from the main screen but it said super user canot log in at this screen how do i log in as root???:confused::confused::confused: Nice job at opening redundant threads! (= same thread twice!) :(

[http://ubuntuforums.org/showpost.php?p=6499143&postcount=6](http://ubuntuforums.org/showpost.php?p=6499143&postcount=6)

---

### Post by wizard10000 on 2009-01-05
All respect to OP but if "a relativity *[sic]* experienced linux user" doesn't know how to enable root logins he probably has no business logging on as root.

I've gotta admit I agree with the forum staff on this one.  I can do just as much damage with sudo but at least that takes an extra step  ;)

---

### Post by halitech on 2009-01-05
> **wizard10000 said:**
> All respect to OP but if "a relativity *[sic]* experienced linux user" doesn't know how to enable root logins he probably has no business logging on as root.

+1

> I've gotta admit I agree with the forum staff on this one.  I can do just as much damage with sudo but at least that takes an extra step  ;)

I agree but hopefully with it asking for the root password it will at least make you stop to think for a moment before executing a command that requires root rights.

---

### Post by jken146 on 2009-01-05
> **theacerguy said:**
> ok the only reason was i needed to create another user but it kept rejecting my root password so

You don't have a root password (to begin with at least) and you should use the password of your first user (the one created at installation) or any user in the *admin* group (by default sudo rights are restricted to this group).

It's a different security model from some other distros, but once you get used to it it's not a problem.

---

### Post by scorp123 on 2009-01-05
> **wizard10000 said:**
> all respect to op but if "a relativity *[sic]* experienced linux user" doesn't know how to enable root logins he probably has no business logging on as root. +2!

---

### Post by lswb on 2009-01-05
> **stchman said:**
> There is NEVER a need to log in as root.

The sudo command in a terminal is all you need.  If you need to run a graphical program as root use gksudo.  If you log in as root you bypass all of the security Linux has.

Also NEVER run Firefox as sudo, NEVER.

I agree fully with the use of sudo as implemented in ubuntu (if anything, it is a little too lax in its timeout policy) but to say that logging in as root will "bypass all of the security that Linux has" is really an overstatement. It just bypasses that one small security enhancement that sudo provides. Lots of other distros allow a root login and we aren't hearing any horror stories about them.

There are lots of things "there is NEVER a need" for but that doesn't mean we should prohibited from doing them when, after due consideration, we decide it is the most efficient course of action.

If you need to have an extended session with root priveledges, as others have noted, using sudo -i is for all practical purposes the same as logging in as root. 

OTOH using gksudo, IMHO presents some real security concerns though they would not be an issue on the typical single user machine.

---

### Post by stchman on 2009-01-05
> **theacerguy said:**
> ok the only reason was i needed to create another user but it kept rejecting my root password so i tried logging in as root i found if you use kde user manager it works just a question why never run firefox sudo??

i find it easier to use root if installing software

Ubuntu has a graphical user manager that will prompt you for your admin password upon launch.  On Ubuntu it is System--->Administration--->Users

Once there you can create users and edit users permissions.

I have been using Ubuntu for nearly two years and never had a need or desire to log in as root.  The sudo or gksudo command does everything I need.  I gather there are ways to enable Ubuntu root login but I do not know or have ever had a desire to do this.

You never want to give an application that has direct access to the internet administrator rights.  This bypasses Ubuntu's security.

If anyone tells you that you need to login as root IGNORE them.

---

### Post by stchman on 2009-01-05
> **lswb said:**
> I agree fully with the use of sudo as implemented in ubuntu (if anything, it is a little too lax in its timeout policy) but to say that logging in as root will "bypass all of the security that Linux has" is really an overstatement. It just bypasses that one small security enhancement that sudo provides. Lots of other distros allow a root login and we aren't hearing any horror stories about them.

There are lots of things "there is NEVER a need" for but that doesn't mean we should prohibited from doing them when, after due consideration, we decide it is the most efficient course of action.

If you need to have an extended session with root priveledges, as others have noted, using sudo -i is for all practical purposes the same as logging in as root. 

OTOH using gksudo, IMHO presents some real security concerns though they would not be an issue on the typical single user machine.

I perfer to err on the side of caution.

The OP can do with their Ubuntu installation as they see fit.  I am just making it crystal clear that they could have security issues if they do so.

---

### Post by mkvnmtr on 2009-01-05
Well I did it just because I realized how. I found it to be with out value. I have more access with sudo.

---

### Post by bodhi.zazen on 2009-01-05
> **stchman said:**
> There is NEVER a need to log in as root.

Just a point of clarification ...

There are (rare) times when it is necessary to enable a root password and/or log in as root (for example recovery mode). In this event setting a root password and/or logging in as root is supported on these forums.

Such an event is quite rare, however, and we strongly discourage indiscriminate use of the root account in an attempt to circumvent learning how to admin a new OS and/or learn things such as sudo and permissions.

---

### Post by theacerguy on 2009-01-07
> **wizard10000 said:**
> All respect to OP but if "a relativity *[sic]* experienced linux user" doesn't know how to enable root logins he probably has no business logging on as root.

I've gotta admit I agree with the forum staff on this one.  I can do just as much damage with sudo but at least that takes an extra step  ;)

im a experienced linux user but i am just a 10 year old i just find root login usefull if doing system changes

---

### Post by overdrank on 2009-01-07
Threads merged.

---

### Post by Joppeb on 2009-01-07
How can I tell Gedit I am the root and want to save a file that I adjusted?
You dont want me to use terminal in a graphic system to change a file?
for why a graphical OS and not using the possibilities?
In my Mac I can adjust every file in a editor. How to do such in Ubuntu? 
JppeB

---

### Post by bodhi.zazen on 2009-01-07
> **Joppeb said:**
> How can I tell Gedit I am the root and want to save a file that I adjusted?
You dont want me to use terminal in a graphic system to change a file?
for why a graphical OS and not using the possibilities?
In my Mac I can adjust every file in a editor. How to do such in Ubuntu? 
JppeB

```
gksu gedit
```

Or

```
gksu gedit /path/to/file/to/edit.txt
```

If you wish to avoid a terminal create a custom launcher.

---

### Post by oldos2er on 2009-01-07
> **Joppeb said:**
> How can I tell Gedit I am the root and want to save a file that I adjusted?
You dont want me to use terminal in a graphic system to change a file?
for why a graphical OS and not using the possibilities?
In my Mac I can adjust every file in a editor. How to do such in Ubuntu? 
JppeB

 One way is to install the package nautilus-gksu, restart X, then you can right-click on a file and choose 'Open as administator.'

---

### Post by bodhi.zazen on 2009-01-07
Thanks, nautilus-gksu is a new one on me :twisted:

---

### Post by halitech on 2009-01-07
*falls over in shock* you mean *YOU* didn't know something bodhi? OMG, my faith has just been shaken to the core in you  :shock:


just kidding bodhi, you've probably forgotten more then alot of us know combined and its great to have you here as a helper.

---

### Post by bodhi.zazen on 2009-01-07
> **halitech said:**
> *falls over in shock* you mean *YOU* didn't know something bodhi? OMG, my faith has just been shaken to the core in you  :shock:


just kidding bodhi, you've probably forgotten more then alot of us know combined and its great to have you here as a helper.

:lolflag:

Thank you for your kind words :redface:

---

### Post by oldos2er on 2009-01-07
> **bodhi.zazen said:**
> Thanks, nautilus-gksu is a new one on me :twisted:

 That and nautilus-open-terminal are the usually the first packages I install on Ubuntu. Can't live without 'em.

---

### Post by halitech on 2009-01-07
> **bodhi.zazen said:**
> :lolflag:

Thank you for your kind words :redface:

very welcome and just stating what alot of us probably feel but have never said. I know I've looked at threads where I was thinking about an answer only to see you come along and give good advice to help the poster out that was faster and easier then anything I would have thought of. 

so, on behalf of everyone here on the forum

[SIZE="7"][COLOR="Red"]Thank You![/COLOR][/SIZE]

---

### Post by theacerguy on 2009-01-10
it is done go into system administration then login window click security then allow local admin login it works

---

