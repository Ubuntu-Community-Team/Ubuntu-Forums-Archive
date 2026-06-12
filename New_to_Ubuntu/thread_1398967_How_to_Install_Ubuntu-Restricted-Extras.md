---
title: "How to Install Ubuntu-Restricted-Extras?"
date: 2010-02-05
forum: New to Ubuntu
---

### Post by Akatsuki26 on 2010-02-05
This is what I enter in terminal: (I want to install flashplayer)

"myname"@ubuntu:~$ sudo aptitude install ubuntu-restricted-extras
[sudo] password for "myname": (I entered my password here)
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Couldn't find any package whose name or description matched "ubuntu-restricted-extras"
Couldn't find any package whose name or description matched "ubuntu-restricted-extras"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done

What am I doing here?

Thanks!

---

### Post by dvlchd3 on 2010-02-05
The ubuntu-restricted-extras package is in the multiverse repository.  Make sure you have that enabled in your sources.list file.

Can you find the package by searching in Synaptic package manager?

---

### Post by Akatsuki26 on 2010-02-05
Where can I find my sources.list file? Thanks.

also, another question. I looked in the Software Center and found Ubuntu Restricted Areas.

When I click on it, it's written "Not available in the current data"!

Can anyone help?

---

### Post by capybara! on 2010-02-05
Your sources.list should be here:
/etc/apt/sources.list

Open it with some editor, for example 
sudo emacs /etc/apt/sources.list

Then add something like

deb [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) hardy multiverse
deb-src [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) hardy-updates multiverse
deb-src [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) hardy-updates multiverse

to the file

and maybe change "hardy" to whatever version you have and change "nl." to "com." or something like that, depending on the country you are in.

Hope this helps...

---

### Post by anaconda on 2010-02-05
/etc/apt/sources.list

YOu can edit it with eg:
gksudo gedit /etc/apt/sources.list

And after editing it
you need to update your apt-data by:
sudo apt-get update

PS. you can also do all of this graphically by using 
System>Administration>Synaptic package manager

---

### Post by crazy_fox on 2010-02-05
sources.list is in /etc/apt/sources.list

You should not try to edit this manually if you are new or not willing to mess you system in order to learn.

Which version of ubuntu are you running?
If you are in 9.10, open Ubuntu Software Centre and search for "restricted".

---

### Post by toogooda on 2010-02-05
Hey Buddy,

You need two things 
first have you selected all the sources for apt that are listed System->software Sources esp restricted on first tab and canonical on second tab. this tells ubuntu where to look,
Second update
```
sudo apt-get update
```then is should find it ok

Cheers AT

---

### Post by Fred2a on 2010-02-05
Go to System -> Administration -> Software Sources (or Sources - I can't remember exactly)

I think the 2nd tab has the repository lists put check marks in the Multiverse repo.

Save/Reload data and you should now be able to install using either Software Centre or  Terminal or Synaptic - whichever is your preference.

---

### Post by audiomick on 2010-02-05
> **crazy_fox said:**
> sources.list is in /etc/apt/sources.list

[COLOR=Red]You should not try to edit this manually if you are new or not willing to mess you system in order to learn.[/COLOR]

Which version of ubuntu are you running?
If you are in 9.10, open Ubuntu Software Centre and search for "restricted".
My thoughts exactly.

Another fairly safe GUI route is the synaptic package manager in system> administration. In that, there is an option under "preferences" for setting up you package sources.

"Fairly safe" is still relative. There is less chance of saving garbage to your package list, or even accidently erasing it entirely, but of course you can still tell the application to remove packages that are existential to the computer.

---

### Post by houseworkshy on 2010-02-05
There is a new and quick way of doing this.  It's called an apt:url.  If you go here [https://help.ubuntu.com/](https://help.ubuntu.com/) and go through the guide for your version of Ubuntu one of the links will do it for you.  It's quite a nice feature for a new comers quick start as at the end of the guide one will not only have a very basic overview but have video/sound/flash etc sorted out too. 
As an aside because you will be asked for your password and will effectively be in an admin mode for a while ( fifteen minuets) don't have the browser open elsewhere.  Whilst this new feature is easy and fast to use nor have I heard of any problems with it (if one can't trust Ubuntu.com who can one trust?) I feel strangely nervous about its' potential.  I think trusted pages only and not browsing elsewhere during the fifteen minuets grace sudo period may become the standard advice in years to come so may as well start with good habits now.

After that this book, the pdf download is free.

[http://www.ubuntupocketguide.com/index_main.html](http://www.ubuntupocketguide.com/index_main.html)

Superb short overview, and IMO deserves a place in anyones documents. Got me started and I still refer to it occasionally.

---

### Post by sisco311 on 2010-02-05
> **dvlchd3 said:**
> The ubuntu-restricted-extras package is in the multiverse repository.  Make sure you have that enabled in your sources.list file.



Yep, it's in the multiverse repo. 

The fastest way to enable the repo & install the package is:
```
sudo software-properties-gtk -e multiverse
sudo apt-get update
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by apochry on 2010-06-30
Just wanted to say THANKS!

---

