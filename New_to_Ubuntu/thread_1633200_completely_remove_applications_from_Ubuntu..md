---
title: "completely remove applications from Ubuntu."
date: 2010-11-29
forum: New to Ubuntu
---

### Post by babloo75 on 2010-11-29
I had installed few applications in Ubuntu and want to remove them completely. Following the thread : 
[http://ubuntuforums.org/showthread.php?t=943773&highlight=completely+remove+applications](http://ubuntuforums.org/showthread.php?t=943773&highlight=completely+remove+applications)

It seems all is well.

I had supposedly done this till I happened to see them again in my computer while trying to configure Docky.

I pressed ALT+F2 and typed gconf-editor. In the apps drop down list I can still see avant-window-navigator, Banshee player, etc... which i uninstalled long time back.

Please help me in completely removing these.
Thanks in advance.

---

### Post by camaron1 on 2010-11-29
> **babloo75 said:**
> I had installed few applications in Ubuntu and want to remove them completely. Following the thread : 
[http://ubuntuforums.org/showthread.php?t=943773&highlight=completely+remove+applications](http://ubuntuforums.org/showthread.php?t=943773&highlight=completely+remove+applications)

It seems all is well.

I had supposedly done this till I happened to see them again in my computer while trying to configure Docky.

I pressed ALT+F2 and typed gconf-editor. In the apps drop down list I can still see avant-window-navigator, Banshee player, etc... which i uninstalled long time back.

Please help me in completely removing these.
Thanks in advance.

with synaptic use *completely remove* as oppose to just *remove*

With *apt-get* use *purge*: [I]sudo apt-get purge ....
[/I]
This gets rid of configuration files which otherwise are left behind. 

But you still need to get rid of the user configuration files for the apps. 

In your home folder click CTR+h to show hidden folders. Look for the folders named after the software you want to remove and also in *.conf* folder. 

Delete any related folder

---

### Post by wojox on 2010-11-29
You need [GNOME Gconf Registry Cleaner - Gconf Cleaner]("http://linuxpoison.blogspot.com/2010/11/gnome-gconf-registry-cleaner-gconf.html")

---

### Post by aytech on 2010-11-29
Not sure if I understand the issue fully, but try typing ```
alacarte
``` in terminal, if that's what you're looking for
[B][FONT=Helv][SIZE=2][FONT=Helv][SIZE=2] 
[/B][/SIZE][/FONT][/SIZE][/FONT]

---

### Post by amjjawad on 2010-11-29
Have you tried this:

> **aysiu said:**
> ```
sudo apt-get autoremove
``` is pretty  good, but if you ever want to try out a program and want to make sure  it's completely gone when you remove it, keep track of the packages that  get installed along with *packagename* when you ```
sudo apt-get install *packagename*
``` and then paste them into a text document you can use later to ```
sudo apt-get remove *packagename1* *packagename2* *packagename3andsoon*
```

It's mentioned in the first [link]("http://ubuntuforums.org/showthread.php?t=943773&highlight=completely+remove+applications") you posted.

---

### Post by babloo75 on 2010-11-29
> **camaron1 said:**
> with synaptic use *completely remove* as oppose to just *remove*

With *apt-get* use *purge*: [I]sudo apt-get purge ....
[/I]
This gets rid of configuration files which otherwise are left behind. 

But you still need to get rid of the user configuration files for the apps. 

In your home folder click CTR+h to show hidden folders. Look for the folders named after the software you want to remove and also in *.conf* folder. 

Delete any related folder

Thanks. I did exactly as you have explained. The terminal command with "purge" didn't help. But after the hidden files were made visible, they were easy to look for and delete.
Thanks once again.

Yes wojox, this might be a good option to clean gconf registry with Gconf Cleaner, but as mentioned on the web page: 
"...Some applications puts the GConf keys without schemas. in such case, your applications might be damaged after cleaning up. It's recommend to save an registry in GConf Cleaner before actually cleaning up and if you see any weird behavior in your applications, restore your lost keys using following command gconftool --load < saved filename >.."
I am scared to lose my work. (I am not an expert of Ubuntu)...
I will carry on with this much only.... Thanks anyway.

Thanks aytech, for another way of opening the same box.

Dear amjjawad, the commands you mentioned, didn't work.

Thanks to all of you.

---

### Post by beew on 2010-11-30
Use Ubuntu tweak to clean your configuration files. I don't know any gconf registry cleaner, this seems kind of odd as Linux has no registry, why use such misleading terminology just to sound more Windows like? That already makes me feel uneasy. :)

I don't know why, but configuration files do get left behind even if I use the completely remove option in Synaptic. If they are not removed they would show up in Ubuntu Tweak's screen and you can remove them there.
[https://launchpad.net/~tualatrix/+archive/ppa]("https://launchpad.net/%7Etualatrix/+archive/ppa")

I don't think entries in gconf-editor matters. I may be wrong but I don't think those dead entries would do anything. gconf is not a registry in the sense of Windows registry.

---

### Post by HermanAB on 2010-11-30
Howdy,

Removing applications is somewhat like trying to unscramble an egg.  The best approach is not to install things in the first place.  

In my experience, a simple way to create a minimal system is to start with a server install and then add only what I really want.  On Red Hat like systems (Red Hat, Suse and Mandriva), it is easy to automate an installation and create a customized list of packages to install.  On Ubuntu it is harder to do.

---

### Post by amjjawad on 2010-12-01
> **babloo75 said:**
> Dear amjjawad, the commands you mentioned, didn't work.

The steps I posted were taken from [here]("http://ubuntuforums.org/showthread.php?t=943773&highlight=completely+remove+applications") which is the same link you provided in your first post. I thought it might be help or perhaps you didn't read it carefully but apparently you tried that and it did not work for you.

I'm also suffering from the same issue. 
I'm not going to say in Windows we used to do this and that because Linux is not Windows but all what I wish is a REAL un-install process in Ubuntu that could remove ALL the files. It's the 21st century and if we won't use the latest technologies to serve our needs, when exactly we shall use them?

I understand NO OS IS PERFECT but it just doesn't make sense to do it manually. I guess you agree with me :)

---

### Post by amjjawad on 2010-12-01
> **beew said:**
> I don't know why, but configuration files do get left behind even if I use the completely remove option in Synaptic. 

Same here :)


> If they are not removed they would show up in Ubuntu Tweak's screen and you can remove them there.
[https://launchpad.net/~tualatrix/+archive/ppa]("https://launchpad.net/%7Etualatrix/+archive/ppa")

I might be wrong but I guess this is the most basic feature that any OS must have. I mean why would I install or find another tool just to remove something I installed?
Yeah, I know, nothing is perfect ;)

---

### Post by amjjawad on 2010-12-01
> **HermanAB said:**
> In my experience, a simple way to create a minimal system is to start with a server install and then add only what I really want.

Great idea, I might try that :)
I feel there are so much stuff I don't really want.

With Red hat like systems you mentioned, is it easier to un-install any applications? do I still have to remove some files manually just like Ubuntu?

---

