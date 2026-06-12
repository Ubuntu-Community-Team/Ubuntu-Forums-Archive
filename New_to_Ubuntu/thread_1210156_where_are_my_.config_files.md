---
title: "where are my .config files?"
date: 2009-07-11
forum: New to Ubuntu
---

### Post by Duke Togo on 2009-07-11
hi
I was using dosbox on my other machine and edited the .config folder to up the virtual memory
however after installing on this machine there doesn`t seem to be a dosbox .config file (I tried crtl H)
where is it?
can I "force" it to appear?
thanks

---

### Post by Duke Togo on 2009-07-11
btw I also recently installed seamonkey and that doesn`t have a .config folder either??:confused:

---

### Post by carml on 2009-07-11
Look if they are under /usr/bin.

---

### Post by CatKiller on 2009-07-11
They won't have a file called .config. They'll often have a directory called .programname in your Home folder that will contain configuration files for that program.

---

### Post by Duke Togo on 2009-08-02
to answer all responses:

1,
they do have a .program name folder , except in this case there aren`t any for these programs?!

2,
under /usr/bin you can open the application but not alter the config files

confused?

---

### Post by OutOfReach on 2009-08-02
Hmm, what exactly are you trying to accomplish?
There are a lot of config files so we would need to know what you want to edit.

---

### Post by Duke Togo on 2009-08-02
I wish to edit the .config file associated with dosbox so I can increase the virtual memory

---

### Post by CatKiller on 2009-08-02
> **Duke Togo said:**
> I wish to edit the .config file associated with dosbox so I can increase the virtual memory

You create your own, so that you can have a different one for each application you wish to run with DOSBox.

There is a template to use at /usr/share/doc/dosbox/dosbox.conf.example.gz.

You choose which config file you wish to use with the -conf option, for example 

```
dosbox -conf ~/dosboxSyndWars.conf
``` loads the configuration file that I've optimised for Syndicate Wars.

The default file if you don't specify one is ~/.dosboxrc. Next it will look for a file called dosbox.conf in the current directory.

**man dosbox** will tell you more.

---

### Post by Duke Togo on 2009-08-02
ok thanks
I get this in the terminal

richard@richard-laptop:~$ dosbox -conf ~/dosboxcm9798.conf
DOSBox version 0.72
Copyright 2002-2007 DOSBox Team, published under GNU GPL.
---
CONFIG: Using default settings. Create a configfile to change them
ALSA:Can't subscribe to MIDI port (65:0) nor (17:0)
MIDI:Opened device:oss

and 3000 CPU cycles in the dosbox but how do I get the game to run there?

---

### Post by CatKiller on 2009-08-02
What have you put in dosboxcm9798.conf?

There is some information on what the dosbox.conf entries do [here]("http://dosbox.com/wiki/Dosbox.conf"). You can also find some information on DOSBox and particular applications [here]("http://www.dosbox.com/").

EDIT: actually, the first link I gave you suggest that rather than initially making the file yourself, you should do this instead:> **Linux**

 If you are using Linux, you first have to issue the command *CONFIG -writeconf dosbox.conf* inside of DOSBox. Afterwards, the **dosbox.conf** file will be written to your home directory). If an error message pops up telling you that the file cannot be created, you may want to run *touch dosbox.conf* in your home directory to first create an empty file. 


---

### Post by Duke Togo on 2009-08-02
I am not really sure what you mean by  		What have you put in dosboxcm9798.conf?
guess I have some reading to do
thanks

---

### Post by llamabr on 2009-08-02
I don't know anything about dosbox

But most applications have system wide, and user specific configuration files, which are usually called rc files, not .config.

For example, my nano (text editor) rc file is in /etc/nanorc .  I override it in my own case with my ~/.nanorc file, which has calls that only apply to me.

Bigger programs will have their own directory in your home.  Firefox's, for example, live in ~/.mozilla/firefox/

---

### Post by Duke Togo on 2009-08-02
thanks
that helped a lot

---

### Post by CatKiller on 2009-08-02
> **Duke Togo said:**
> I am not really sure what you mean by          What have you put in dosboxcm9798.conf?

I mean, what have you put in there? :)

That would be a specific configuration file that you're loading because you want to over-ride the defaults in some way, or have something automatically run when DOSBox has loaded. So you would need to configure that file to do what you want.

---

