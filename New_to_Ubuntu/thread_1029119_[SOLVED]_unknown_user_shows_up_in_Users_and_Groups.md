---
title: "[SOLVED] unknown user shows up in Users and Groups."
date: 2009-01-03
forum: New to Ubuntu
---

### Post by egalvan on 2009-01-03
While searching for solutions to another problem,
(an error with permissions, stating "user's $HOME/.dmrc is being ignored"),
 I went to the following:

```
System->Administration->User and Groups
```

this showed the regular two users that have been on my machine since I installed Ubuntu back in April

[I]root
ernest[/I]

but imagine my surprise when I saw a third one:

***sabayon-admin***


with no User Privileges,

and with a home directory of:

**/var/run/sabayon-admin**


No, I have NOT tried to install Sabayon Linux on this machine!
I don't even have a Sabayon CD!
And I am the ONLY user on this machine. 

So where could this have come from?

Any thoughts?

ErnestG

---

### Post by Michael.Godawski on 2009-01-03
Sabayon is a user profile editor. A admin can pre configure user accounts.
 [http://www.gnome.org/projects/sabayon/](http://www.gnome.org/projects/sabayon/)
 I think you installed Sabayon by mistake, you can uninstall that package.


taken from:
[https://answers.launchpad.net/ubuntu/+question/20768](https://answers.launchpad.net/ubuntu/+question/20768)


Does it help?

---

### Post by egalvan on 2009-01-03
OK, I checked Synaptic, and sure enough, there was Sabayon.

I did not know what this software did, and I do not remember installing it.

Is it possible it was installed by another package, as a dependency?

And is it possible to find the date and time it was installed?

And is it supposed to become a user on my system?

Many thanks for the help.

ErnestG

---

### Post by meborc on 2009-01-03
> **egalvan said:**
> OK, I checked Synaptic, and sure enough, there was Sabayon.

I did not know what this software did, and I do not remember installing it.

Is it possible it was installed by another package, as a dependency?

And is it possible to find the date and time it was installed?

And is it supposed to become a user on my system?

Many thanks for the help.

ErnestG

if you try to uninstall it, synaptic should tell you what is dependent on it (if any) and that these programs have to be uninstalled too

---

### Post by egalvan on 2009-01-03
> **meborc said:**
> if you try to uninstall it, synaptic should tell you what is dependent on it (if any) and that these programs have to be uninstalled too

Well, I want to study this a little further.
I KNOW I did not install Sabayon... 
I went to the web-site, and nothing sounds familiar.

But before I uninstall it, is it possible to do a "fake" uninstall?
One that just goes through the motions, but does not really get rid of anything?

Thanks

---

### Post by mcduck on 2009-01-03
> **egalvan said:**
> OK, I checked Synaptic, and sure enough, there was Sabayon.

I did not know what this software did, and I do not remember installing it.

Is it possible it was installed by another package, as a dependency?

And is it possible to find the date and time it was installed?

And is it supposed to become a user on my system?

Many thanks for the help.

ErnestG

Yes, it's possible it might have been installed as a dependency. For something related to user management, most likely, as Sabayon is the tool used to configure the desktop settings for different users/groups.

You might be able to see the installation date in Synaptic's logs.

Yes, Sabayon is supposed to create it's own user. This is because it needs to be able to edit all user groups' profiles, but at the same time shouldn't have any other privileges in the system. Using users and groups for this kind of purposes is normal in Unix/Linux.

Most likely it got installed with something else you were installing, or because you have accidentally selected it to be installed. You really shouldn't worry about it, it definitely is nothing dangerous, the worst thing anybody could do to you with Sabayon is to re-arrange your desktop. Definitely not a likely tool of choice for cracking into somebody's computer. ;)

edit: no, making a "fake uninstall" isn't possible. The programs don't install/uninstall themselves like in Windows, instead the package manager handles all installing & uninstalling. To "fake" the uninstall you'd need to change the package management itself, a bit harder thing to do than messing around with some self-installing .exe file.. Besides, which ever way the package got installed into your system, it's still coming from Ubuntu's repositories so you can be sure nobody has had any change to change the package in any way.

---

### Post by jerome1232 on 2009-01-03
> **egalvan said:**
> Well, I want to study this a little further.
I KNOW I did not install Sabayon... 
I went to the web-site, and nothing sounds familiar.

But before I uninstall it, is it possible to do a "fake" uninstall?
One that just goes through the motions, but does not really get rid of anything?

Thanks

Yes you can do a "fake" uninstall, it's called a dry run or simulation run. You just add the -s option

```
sudo apt-get -s remove *packagename*
```

Also to see more info about a package

```
apt-cache show *packagename*
```

You may want to check the man pages for apt-get and apt-cache for more info

```
man apt-get
man apt-cache
```

---

### Post by egalvan on 2009-01-06
> **jerome1232 said:**
> Yes you can do a "fake" uninstall, it's called a dry run or simulation run. You just add the -s option

```
sudo apt-get -s remove *packagename*
```

Also to see more info about a package

```
apt-cache show *packagename*
```

You may want to check the man pages for apt-get and apt-cache for more info

```
man apt-get
man apt-cache
```

Belated THANKS for this information...

(busy holidays, and all that...)


I guess I can mark this as "SOLVED"


ErnestG

---

