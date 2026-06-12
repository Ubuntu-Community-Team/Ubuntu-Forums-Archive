---
title: "Purge, remove, delete?"
date: 2009-03-05
forum: New to Ubuntu
---

### Post by beanco on 2009-03-05
OK, n00b alert:

I just got some help on the general forum when asking how to delete from the command line.... Have you tried.

I got this:

```

Code:

sudo apt-get --purge -remove deluge



Code:

sudo apt-get remove deluge-torrent 
sudo apt-get remove deluge


```

what is the difference between purge, remove and delete and what does -- and/or - mean before the purge and the remove above.

now, if this has been posted please do not kill me, just point me to the thread, or some site or whatever, with the info... I really did not find the asnwers yet on my searches... 

thanks

robi

---

### Post by kanikilu on 2009-03-05
```
man apt-get
``` All the options are described in the manual page.

---

### Post by issih on 2009-03-05
Basically remove takes the binaries and purge takes the config files too..

[http://ubuntuforums.org/showthread.php?t=790141](http://ubuntuforums.org/showthread.php?t=790141)

Hope that helps

---

### Post by chamber on 2009-03-05
Remove just removes the binaries whereas purge also removes config files

EDIT

Just to late, issih beat me

---

### Post by beanco on 2009-03-05
> **kanikilu said:**
> ```
man apt-get
``` All the options are described in the manual page.

the things a n00b can learn her.e.. thanks!

still not sure what - and -- mean, ok, I can use them, but not sure wht they do....

robi

---

### Post by beanco on 2009-03-05
chamer, issih, thanks!

robi

---

### Post by beanco on 2009-03-05
hey, sg just occured to me folks.

I used remove to get rid of deluge....since I was having problems with that prgm.... but I suppose I should have purged.

so how do I purge the config files now?

I want to reinstall it and see if it works ....

thanks

robi

---

### Post by kanikilu on 2009-03-05
I'm not sure if this will work, but you may have to reinstall it, purge it, and then reinstall it again.

Unless you know where the config files are and just want to manually delete them...

---

### Post by redseventyseven on 2009-03-05
The hyphens and double-hyphens are used to specify options or arguments when running a command. Often, options prefixed with a double hyphen are full words, for which some have single-letter "shortcut" equivalents, which are prefixed with a single hyphen.

This standard, however, is not rigidly adhered to.

Have a look at the man page for the ls command for an example of what I mean.

```
man ls
```

---

### Post by mcduck on 2009-03-05
> **beanco said:**
> the things a n00b can learn her.e.. thanks!

still not sure what - and -- mean, ok, I can use them, but not sure wht they do....

robi

The standard way is that short format options are marked with a single dash ("ls -a") and long format options with double dash ("ls --all").

The command given to you was a bit funny, as "remove" doesn't need a dash, and there really is no need to "--purge remove", you can just "purge" instead. Both these commands do the same thing:
```

sudo apt-get purge package
sudo apt-get --purge remove package
```

edit: If you have removed a package you can still purge it. The package will also still show in Synaptic, if you use the filter "Status"->"Not Installed (Residual config)" so you can purge them there as well (right-click -> "Mark for Complete Removal").

By the way, purging a package will not remove it's per-user configurations, in other words all configuration files in user home directories will still stay. They belong to the user, not the system, and it's up to users to decide if they want to keep their old configurations or remove them. Purging a package will just remove it's system-wide configurations.

---

### Post by redseventyseven on 2009-03-05
> **beanco said:**
> hey, sg just occured to me folks.

I used remove to get rid of deluge....since I was having problems with that prgm.... but I suppose I should have purged.

so how do I purge the config files now?

I want to reinstall it and see if it works ....

thanks

robi

The config files will probably be in your home folder. Go to your home folder, press Ctrl-H to reveal the hidden files and folders (these are your config files). There should be one obviously related to deluge (called ".deluge" or ".deluge.conf" or something like that). You can safely delete this.

---

### Post by Ben Crisford on 2009-03-05
Remove = byebye binaries.

Purge = byebye configs.

:) thats basically it.

---

### Post by beanco on 2009-03-05
Oh, this is fun stuff!!!

ok, I do not want to use synaptic.. I want to get proficient at CLI, it is cool.

thanks for the info on the hyphens... 

about seeing the hidden files and deleting them.. ok, easy enough but how do I get to them on this CLI ?

thanks folks, this really is much more fun than making dinner or doing my work.. both of which are waiting for me... but they can wait, I am learning stuff...and having fun!!!

robi

---

### Post by mkvnmtr on 2009-03-05
I know it is not command line but when I wish to delete configuration files from home I usually just put them in the trash. I do it quite often to replace them with files from another computer.

---

### Post by oldos2er on 2009-03-05
To show hidden files:
```
ls -a | more
```

 To delete them:
```
rm -rf .foo
```

---

### Post by issih on 2009-03-07
with the ls command there are three things I find utterly essential:

-a, -l and -h:

-a is show all files including hidden ones (which start with a ".", thats how linux hides files just so you know)

-l is show in list format, so you get lots of file details

-h is human readable format, which means you get your file sizes in kb and mb not jsut a huge number

typically I just always run ls with:

```
ls -alh
```

as that gets all three in one go, you can quite often concatenate the options like that..

Hopr taht helps

---

