---
title: "Unistalling and Removing Stuff"
date: 2011-04-07
forum: New to Ubuntu
---

### Post by maembe on 2011-04-07
I have kind of a general question about removing stuff in kubuntu 10.10.  As I understand it, in order to completely remove something you installed via the command terminal, you essentially just rm the thing you installed.  For example, I'm going to remove rubyripper before I try to install it again because it wasn't working properly.  Do I type:

sudo apt-get rm rubyripper
sudo apt-get rm rubyrippergtk

Here are the commands used for install:

[LEFT]sudo add-apt-repository ppa:aheck/ppa

sudo apt-get update

sudo apt-get install rubyripper
sudo apt-get install rubyripper-gtk[/LEFT]

Do I need to do anything about the repository?



If I installed with the command below and then downloaded and extracted a deb package, how would this change the removal process?

sudo apt-get install cd-discid cdparanoia flac lame mp3gain normalize-audio ruby-gnome2 ruby vorbisgain

Would I just delete the folder it extract to and do sudo apt-get rm (everything in the above line)?

Is there a better method I should be using to get rid of stuff?

Thanks for the help!

---

### Post by jerome1232 on 2011-04-07
Your understanding is incorrect on this.

When using apt-get to completly remove a program which was installed by apt-get you'd use the purge option.


```
sudo apt-get purge packagename
```

If you wanted to remove it but leave it's configuration file behind

```
sudo apt-get remove packagename
```

If you wanted to remove the extra packages that apt-get thinks you no longer need (usually things that were pulled in as dependenceies)
```
sudo apt-get autoremove
```


When working with a command line program you are unfamiliar with, always look at it's man page for help.

If you wanted to look at apt-get man page

```
man apt-get
```

I hope that helps, if you need further clarification just ask.

---

### Post by maembe on 2011-04-07
> **jerome1232 said:**
> Your understanding is incorrect on this.

When using apt-get to completly remove a program which was installed by apt-get you'd use the purge option.


```
sudo apt-get purge packagename
```If you wanted to remove it but leave it's configuration file behind

```
sudo apt-get remove packagename
```If you wanted to remove the extra packages that apt-get thinks you no longer need (usually things that were pulled in as dependenceies)
```
sudo apt-get autoremove
```When working with a command line program you are unfamiliar with, always look at it's man page for help.

If you wanted to look at apt-get man page

```
man apt-get
```I hope that helps, if you need further clarification just ask.

I thought purge only removed outdated versions of the program.

So in my case, is autoremove the best option or purge?
What about --purge remove?
I'm just not quite sure what commands I should use.

---

### Post by jerome1232 on 2011-04-07
I would do this. It would remove the listed packages AND any dependencies they pulled in that you did not explicitly install yourself.

```
sudo apt-get autoremove --purge cd-discid cdparanoia flac lame mp3gain normalize-audio ruby-gnome2 ruby vorbisgain
```

---

### Post by maembe on 2011-04-07
> **jerome1232 said:**
> I would do this. It would remove the listed packages AND any dependencies they pulled in that you did not explicitly install yourself.

```
sudo apt-get autoremove --purge cd-discid cdparanoia flac lame mp3gain normalize-audio ruby-gnome2 ruby vorbisgain
```

Will this take care of the repository as well?

---

### Post by jerome1232 on 2011-04-07
No to remove the repo and it's gpg key (syntax is silly here they should really write two separate scripts but...)

```
sudo apt-add-repository -remove ppa:aheck/ppa
```

---

### Post by maembe on 2011-04-07
> **jerome1232 said:**
> No to remove the repo and it's gpg key (syntax is silly here they should really write two separate scripts but...)

```
sudo apt-add-repository -remove ppa:aheck/ppa
```

Great, thanks for your help.

---

