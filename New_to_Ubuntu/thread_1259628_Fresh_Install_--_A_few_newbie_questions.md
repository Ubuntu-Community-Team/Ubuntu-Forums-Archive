---
title: "Fresh Install -- A few newbie questions"
date: 2009-09-06
forum: New to Ubuntu
---

### Post by mattsilv on 2009-09-06
1.  Firefox

The pre-installed version of Firefox is 3.0.13.  I have tried multiple methods to install the latest version of Firefox, including using the help doc posted on UbuntuForums.org, but I still have not been able to change it.  One of the steps I followed from the help seemed to download and install Firefox 3.5, but I cannot find the application anywhere on the computer.  Any time I open up Firefox is still says version 3.0.13!

2.  Web server stuff

I followed [these instructions ]("http://www.howtogeek.com/howto/ubuntu/installing-php5-and-apache-on-ubuntu/")to install PHP/Apache on my new linux box, but when I try to save files in /var/www it gives me a permission error.  This is probably a very simple fix, but for a Linux newbie, it's kind of confusing

3.  Text editor for coding

Does anyone have recommendions for a text editor to use for coding?  Preferably one that color codes the tags, but i'm flexible.  I have experiemented with the command line editors like Nano, which actually works really well, if only it had some form of color coding.  

I apologize if these are realy silly questions, but any help would be greatly appreciated.  Thanks!

---

### Post by NoaHall on 2009-09-06
You need to download the firefox 3.5 .deb file, it's either under /home/USERNAME or /home/USERNAME/Desktop or /home/USERNAME/Downloads

To save files like that, you need to open the editor using "sudo" or "gksudo" if it's outside of the terminal.

I use Geany for programming.

---

### Post by jrothwell97 on 2009-09-06
You need to start Firefox 3.5 differently - it'll appear on your menu under the name "Shiretoko".

Anything saved outside your home directory is not writable, by default. You have to become the system administrator, or "root", to copy files into /var/www - put simply, you open a terminal and run
```
gksudo nautilus
```

Be aware that you should only do this in cases where you *need* to edit/copy/manipulate files outside your home folder, as running a program as root is very dangerous. So quit the file manager once you're done.

For coding, you're spoiled for choice. gedit or Scribes make good vanilla text editors with syntax highlighting.

---

### Post by falconindy on 2009-09-06
> **jrothwell97 said:**
> For coding, you're spoiled for choice. gedit or Scribes make good vanilla text editors with syntax highlighting.
gedit is actually fantastic, but to really make it shine, you'll want to install the gedit-plugins package. I used scribes for a few weeks and got fed up with it. I appreciate what the author is trying to do, but he's too full of himself and there's some functionality that I couldn't put up with.

---

### Post by Sealbhach on 2009-09-06
How about [Bluefish]("http://bluefish.openoffice.nl/") for your coding?

.

---

### Post by earthpigg on 2009-09-06
the next question you will likely have will be 'wtf is the deal with this shiretoko stuff? i want firefox!'

firefox, though Free and Open Source Software, does not use the GPL & has the name 'firefox' trademarked.

this combination results in some legal mumbo jumbo that results in ff 3.5 needing to be renamed *for now*. it still functions identically, and indeed *is* firefox 3.5

---

### Post by twright on 2009-09-06
> **mattsilv said:**
> 
Does anyone have recommendions for a text editor to use for coding?  Preferably one that color codes the tags, but i'm flexible.  I have experiemented with the command line editors like Nano, which actually works really well, if only it had some form of color coding.  

This will be controversial but I recommend VIM.

It is an awesome command line editor which after a few hours (or more) of learning you will be able to edit with faster than anything you have used before.

Or you could just go the easy route and use gedit.

> the next question you will likely have will be 'wtf is the deal with this shiretoko stuff? i want firefox!'

firefox, though Free and Open Source Software, does not use the GPL & has the name 'firefox' trademarked.

this combination results in some legal mumbo jumbo that results in ff 3.5 needing to be renamed *for now*. it still functions identically, and indeed *is* firefox 3.5Actually this is nothing to do with legal stuff - they just did not want 2 things branded firefox in the repos (it has always been that way with new/dev versions in Ubuntu).
> Anything saved outside your home directory is not writable, by default.
If you want to change this dir's permissions (not a good idea if it is a production server) then just pop open a terminal and type:
```
sudo chmod 777 /var/www/
```

---

### Post by Sealbhach on 2009-09-06
[Swiftweasel]("http://swiftweasel.tuxfamily.org/about.php") is good, I'm finding it faster and more stable than Shiretoko.

.

---

### Post by mattsilv on 2009-09-06
> **jrothwell97 said:**
> You need to start Firefox 3.5 differently - it'll appear on your menu under the name "Shiretoko".


Sure enough, under the Applications > Internet > folder there was an nondescript application called Shiretoko.  It is completely beyond me why this is, but I will just accept it for now.

> **jrothwell97 said:**
> Anything saved outside your home directory is not writable, by default. You have to become the system administrator, or "root", to copy files into /var/www - put simply, you open a terminal and run
```
gksudo nautilus
```Be aware that you should only do this in cases where you *need* to edit/copy/manipulate files outside your home folder, as running a program as root is very dangerous. So quit the file manager once you're done.

This worked in allowing me to use the file browser to go to the /var/html folder, and I right-clicked, selected Properties, then set the Owner as "matt" (my username).  How can I set the owner of the file using Terminal?  I'd prefer to learn the shell way.. :)

> **jrothwell97 said:**
> For coding, you're spoiled for choice. gedit or Scribes make good vanilla text editors with syntax highlighting.

I will check into those.  Thanks!

---

### Post by mattsilv on 2009-09-06
> **twright said:**
> This will be controversial but I recommend VIM.

It is an awesome command line editor which after a few hours (or more) of learning you will be able to edit with faster than anything you have used before.

Or you could just go the easy route and use gedit.


I was recommend VIM by a friend as well; can you recommend any beginner VIM tutorials, including preferably.. How do I start using it with Ubuntu? (Literally.. is it installed already.. open via console.. etc?)

As a side-note, I am really blown away by the quick, thorough, and amazingly helpful responses on my first day at the UbuntuForums.  Thanks everyone!

---

### Post by NoaHall on 2009-09-06
I would not set the folder as yours! You can create major problems through doing that.

---

### Post by twright on 2009-09-06
> **mattsilv said:**
> 
This worked in allowing me to use the file browser to go to the /var/html folder, and I right-clicked, selected Properties, then set the Owner as "matt" (my username).  How can I set the owner of the file using Terminal?  I'd prefer to learn the shell way.. :)

sudo chown -R matt /var/www/

If you want a full-on command line file browser you could try mc

It is better to change the permissions (as I posted before) though.

---

### Post by jrothwell97 on 2009-09-06
> **mattsilv said:**
> Sure enough, under the Applications > Internet > folder there was an nondescript application called Shiretoko.  It is completely beyond me why this is, but I will just accept it for now.
I believe Shiretoko was Firefox 3.5's codename.


> **mattsilv said:**
> This worked in allowing me to use the file browser to go to the /var/html folder, and I right-clicked, selected Properties, then set the Owner as "matt" (my username).  How can I set the owner of the file using Terminal?  I'd prefer to learn the shell way.. :)

Navigate to the correct directory (in this case /var) and then use *chown*. The syntax is

```
chown *<username>* file1 file2...
```

so you'd want

```
chown matt html
```

However, if you want to change the contents of a folder as well as the folder itself, you need to run

```
chown -R matt html
```

(the -R switch stands for 'recursive'.)

If you want to know more about chown (or any other terminal command) you can get help with it by running

```
man *command*
```

To get back to the terminal, just hit Q.

---

### Post by twright on 2009-09-06
> **jrothwell97 said:**
> I believe Shiretoko was Firefox 3.5's codename.




Navigate to the correct directory (in this case /var) and then use *chown*. The syntax is

```
chown *<username>* file1 file2...
```so you'd want

```
chown matt html
```If you want to know more about chown (or any other terminal command) you can get help with it by running

```
man *command*
```To get back to the terminal, just hit Q.
You will want to use chown -R if you want to change the owner of the folders contents as well

---

### Post by mattsilv on 2009-09-06
> **NoaHall said:**
> I would not set the folder as yours! You can create major problems through doing that.

Hrmm.. what do I set is as then in order to be able to have read/write access, if I do not set it to my own username?

---

### Post by NoaHall on 2009-09-06
Use it as root, but use sudo/gksudo to edit the files when you need to. You should also be using gksudo instead of sudo to open nautilus.

---

### Post by twright on 2009-09-06
If you are using the server mostly for testing then apache's userdir is the best way to have a web folder you can edit as your user account:
[http://selinap.com/2009/04/enable-ubuntu-public_html-user-directory-for-apache/](http://selinap.com/2009/04/enable-ubuntu-public_html-user-directory-for-apache/)
You should also consider installing the suexec module for apache to make permissions in php work properly - [link]("apt:apache2-suexec").

---

