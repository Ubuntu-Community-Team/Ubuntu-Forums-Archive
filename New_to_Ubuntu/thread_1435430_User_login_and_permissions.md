---
title: "User login and permissions"
date: 2010-03-21
forum: New to Ubuntu
---

### Post by phroman on 2010-03-21
Hello all, I'm afraid this is going to be an embarrassingly dumb question but I'm stuck and have to ask.  

Just installed 9.10, created one user during the install.  I don't remember if it was designated as an administrator or regular user, but it was the only one I created during the install.  I can login using this account, and if I go to Applications > System > User Settings, I see 2 users, one is root, and the other is the account I created during the install.  I cannot make any changes to either of these accounts, not even the standard one that I'm logged into at that moment.  It says 'Not authorized to make changes' at the bottom of the User Settings window.  

I can't do anything in the system like this, I can't create folders or documents or anything.  So, did I do something wrong at the install, is there something glaringly obvious that I'm missing?  How do I access the ability to change the parameters for this user?  I'm not too command line savvy but I'm not afraid of it either.  ;)  Why can't I enter a password in the graphical front end to allow me to make changes?  Thanks for any help!

---

### Post by oldsoundguy on 2010-03-21
you need to follow some threads about the use of "sudo" in terminal.  NOT needed in most cases, but good to learn about.
Your programs are in the repositories (provided you enabled them) and seldom, as a new user, will you need to vary out of that comfort and safety zone.

Root is NOT the way to operate anymore, although, because of the general purpose of the kernel and the need for root in other builds, it shall remain.

you will be asked for your password every time you attempt to install or change anything.  Why? YOUR PROTECTION.  One of the primary reasons that Linux of any iteration is so much more secure than any other OS.

---

### Post by phroman on 2010-03-21
Hi oldsoundguy, thanks for your reply, I'm familiar with sudo and how it works, but is it normal to be locked out of making changes at the desktop at this initial point after an install?  I should be able to make changes at the desktop level and not be limited to only the command line right?  I don't even have the option of entering and administrator password to make changes to my own account that I'm logged into.  

In Applications > System > Software Sources, it asks me for the administrator password, I enter the one password I have, and it works.  But I don't have that option to enter a password when trying to change my user account to be able to read and write to other directories the way I need to.  At the terminal if I type:
su  it returns with Authentication Failure

So, I'm basically locked out of my own system at the desktop.  If I missed something during the install I'll re-install, but this can't be the way it's supposed to work, right.  Thanks again, cheers.

---

### Post by quadproc on 2010-03-21
I think that perhaps you are looking for the "unlock" capability in Users and Groups.  Under System > Administration choose Users and Groups.  The small window that pops up should have a button which says "Unlock"; press that, and when asked, enter your password.  You can then work with the user data for any usercode.

quadproc

---

### Post by phroman on 2010-03-21
Hey quadproc, in Applications > Sytem > Users and Groups, I do not have the option of unlocking anything.  There is a small square icon of a set of keys at the bottom of that window, but next to it is only says: 'Not authorized to make changes'.  This is the first start up after an install.  Thank you for the reply, hope I can get this figured out...

---

### Post by Directive 4 on 2010-03-21
sudo nautilus

---

### Post by phroman on 2010-03-21
Hi Directive4, I went to Applications > System > Synaptic Packet Manager, installed nautilus and can start it but I don't understand how that pertains to my user/access issues.  I was using mythbuntu about 6 months ago and definitely didn't have anything like this happen, did something change?  Thanks everyone.

---

### Post by Directive 4 on 2010-03-21
mythbuntu is a bit of a mess, tried it but gave up.

did you install mythbuntu, or did you install ubuntu and are now trying to make it a mythbuntu box?

i'm confused with your pathways... 
on my 9.10 to find 

Applications > System > User Settings

what i think this is???
 i go to system>admin>users and groups.

in this place there is a set of keys, click on them to unlock.


what happens if you right click on the desktop. can you create a folder?

if you type in the terminal

sudo nautilus

and go to your home folder

filesystem>home


select your home folder.

go to file>properties>permissions

here you can select the owner and access.

---

### Post by Miljet on 2010-03-21
Personally I think that you are going to regret tinkering with user permissions, but it is your system. You need to go to system -> Administration -> Users and Groups. Click the unlock button, enter your password, and change to your heart's content.

BTW, nautilus isn't something that your have to install, it is the built-in file browser.

---

### Post by phroman on 2010-03-21
Things seem very weird..  

Directive4:  I installed mythbuntu 9.10, From the desktop toolbar at the top, I click on Applications > System > Users and Groups. I don't have any Administration links of any kind.  At the terminal sudo nautilus brings up the Nautilus window.  The properties of my home folder are: 

Owner: it lists my username
Access: read/write

group: again, lists my correct username which I assume it made a group of the same name.
access: read only

others: read only

Miljet:  From Applications > System, I don't have any Administration choice anywhere, just straight to Users and Groups, and I do not have the option to click the Unlock button.  Nautilus was not installed on my system, only Thunar was, I had to install it myself.  

I need to be able to create directories and create and edit files throughout the system to configure all of my mythtv settings which I cannot do right now.  You know, I need normal, full access to my system.  I can't do anything outside of my home folder from my desktop.  Can't create or edit anything at all, and can't find anywhere to change that.  Did mythbuntu install with too 'stripped down' of a version?  Sooo  confuuuuused... 

Thanks guys.

---

### Post by quadproc on 2010-03-21
This is very curious.  You are able to get to the window that shows user accounts but you don't get to make any changes if I read you correctly.

On Ubuntu 9.04, when I try to access the user data as a nonprivileged user, I get stopped right away before the user data window pops up.  On 9.04 as a privileged user, I get a user data window which has an Unlock button at the bottom.

On Ubuntu 9.10 from a Live CD, I get the user data window and it is ready to allow me to change things.

I wonder if there is a bug in the version which you have.  Did you do an integrity check on your installation media such as MD5SUM?

There might be an issue with groups.  You could add your usercode to the other groups and that may have a useful effect, but there can be some risk involved in so doing.  Probably not something that you would wish to do because it probably isn't the problem.

One final thought: it appears that you have a new installation so it might be practical to reinstall the system.  Of course, this means losing any data and setups that you have created so far, but it would give you a fresh start.

quadproc

---

### Post by Directive 4 on 2010-03-21
sudo nautilus

this will let you make new folders anywhere in the system, just navigate to where you want and use the menu


file>create folder 

 with this you can create directories and create and edit files throughout the system

don't know about configure mythtv settings

i set it up and got everything working on my box but had to enter my password to logout plus was unable to get fullscreen so i went back to ubuntu.

good luck with myth. it's very confusing.


...  i would just install ubuntu then try to get the features you require that way.
do you need a fully functions dvr...

or can you get by on just tv and being around to hit record.

---

### Post by Miljet on 2010-03-21
Sorry, I didn't realize that the menus for Mythbuntu were that much different that Ubuntu.

Just remember that any files or folders that you create with sudo, or gksu nautilus, will belong to root. That will cause continuing problems trying to access/change them.

---

### Post by phroman on 2010-03-22
Ok, Directive4, > sudo nautilus, this will let you make new folders anywhere in the system, just navigate to where you want and use the menusI guess I could do that but there really seems to be a bigger problem here that I'm going to try to get to the bottom of.

quadproc, > This is very curious. You are able to get to the window that shows user accounts but you don't get to make any changes if I read you correctly.
 That is correct.  And I forgot to md5sum the download, could definitely be a problem.  I think I'm going to re-download, md5sum this time, and see what happens.  Thanks to all for the help, I'll update with new info after the re-install.  Cheers :D

---

### Post by phroman on 2010-03-22
Well, just re-downloaded mythbuntu 9.10, md5 was good, running the live cd and everything is the same as far as the menus available.  No Administration choices anywhere. Should I even bother re-installing?  I mean, this is definitely not normal, right?  I'm gonna wait for a response before I do anything else.  Thanks a lot everyone.

---

### Post by Frogs Hair on 2010-03-22
Hi Phroman,
 
I understand that you are trying to create a user account with root permissions .
Dierctive4 and miljet have both described the correct path to change user permissions in Ubuntu 9.10 I know little about mythbuntu, but installation does require a root password. 
 
[http://www.mythpvr.com/mythtv/dstri...buntu/mcc.html](http://www.mythpvr.com/mythtv/dstri...buntu/mcc.html)
 
[http://www.mythbuntu.org/9.10/beta](http://www.mythbuntu.org/9.10/beta)

---

### Post by sylaryn on 2010-03-22
Not to deviate from resolving your issue... but have you considered XBMC?

---

### Post by phroman on 2010-03-22
Hey guys, yes Directive4 mentioned sudo nautilus, I can do that to create/edit/adjust permissions for files and folders.  But it seems that in some areas, my system was missing or had different menu options and pathways than other people's, and I was thinking something might have gone wrong with the install.  I can't seem to do things in the same way as others can, like make changes to my own user account, like if I want to add it to another group or something, at least not at the desktop.  For me this is of some concern.  The last time I was experimenting with mythbuntu things definitely did not function like this.  I remember that I could do these things at the deskop, graphically. 

Example from quadproc:
> On Ubuntu 9.10 from a Live CD, I get the user data window and it is ready to allow me to change things.  I wonder if there is a bug in the version which you have.
That's not something I can do, so I was looking deeper to make sure there's not something wrong with my system.  

I don't know how to make changes to user accounts at the terminal, don't get me wrong, I'm going to learn, but something seemed off and I wanted to figure it out I guess...

sylaryn, I wanted the dvr function of mythtv, I actually have xbmc on my mac, it's pretty good stuff, but I've been trying to learn more about linux in general and mythtv is something that's interested me for a while.  Thanks for the suggestion though.  Thanks for the reply's and help everyone, I'm open to any more info, thoughts or ideas.  Cheers  :P

---

