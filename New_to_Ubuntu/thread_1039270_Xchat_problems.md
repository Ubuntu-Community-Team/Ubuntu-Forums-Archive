---
title: "Xchat problems"
date: 2009-01-14
forum: New to Ubuntu
---

### Post by Dravenm4 on 2009-01-14
Hey guys I am trying to install xchat irc client to ubuntu and am having some problems with libglib2.0 and gtk an error comes up and says cant find path? i am unsure i have searched google to see if i can find some answers but none were of any use. Let me know what you need from me and I'll get it, (if there is a command i can use to find this info please include it in your reply) also is there a better irc client than this that is easier?

Thanks 

Draven,

Ubuntu 8.10
Toshiba Satellite a135
2gb mem
80gb hdd
ati radeon mobile

---

### Post by Titan8990 on 2009-01-14
What method are you using to install xchat? Source code? .deb? Synaptic Package Manager?

---

### Post by Dravenm4 on 2009-01-14
i dl it from sourceforge and ran ./configure then make and make install

---

### Post by kostkon on 2009-01-14
Install it from *Add/Remove* (*Applications &#8594; Add/Remove*) or *Synaptic* (*System &#8594; Administration &#8594; Synaptic Package Manager*).

You could check [this very good how-to]("http://www.psychocats.net/ubuntu/installingsoftware") on how to install software in *Ubuntu*, if you want.

---

### Post by Titan8990 on 2009-01-14
> i dl it from sourceforge and ran ./configure then make and make install


You will very rarely have to do this. Follow the instructions from the poster above. Synaptic makes program installation easier than it is in windows.

---

### Post by Dravenm4 on 2009-01-14
thanks guys but not everything I am interested in is available through the app manager. Plus I switched to linux to learn not to be so dependent on 100% automation. Either way can anyone let me know how to uninstall the stuff i just installed and i will start fresh? :o

---

### Post by mjheagle8 on 2009-01-14
delete the files you downloaded. i believe. then go open a terminal and type [code]sudo apt-get install xchat[/xchat]

---

### Post by Dravenm4 on 2009-01-14
Thanks Im sorry if I sounded rude that was not my intention but I still want to learn how to use the command line and terminal box before I get real comfortable with having it all done for me. Does that make sense?

---

### Post by Titan8990 on 2009-01-14
Yes, from the command line to install xchat:


sudo apt-get install xchat-gnome


If you were specifically trying to learn how to compile with makefiles, I recommend something smaller such as: [http://www.openwall.com/john/](http://www.openwall.com/john/)


I always recommend john for learning to compile via make files because it does not require odd libraries that many programs do.

In order to compile programs from source, you need the build-essential package:

sudo apt-get install build-essential

---

### Post by mcduck on 2009-01-14
It's not a question of "all being done for you", installing through the package manager is the best and cleanest way, provides you with updates for your programs, and easy ways to list, manage and remove installed programs. It's not just some automated way for dummies to installl stuff, it's the standard way of installing packages in all Debian-based Linux distributions.

Compiling from source is very different way of installing programs, and gives you none of the benefits of using the package manager.

If you wish to learn to use command line, then use "apt-get" to install instead of the graphical applications. I can promise you'll get plenty of practice in compiling if, like you said, many of the programs you want aren't available in repositories. ;)

edit: by the way, most likely you'll want the "xchat"-package instead of the simplified "xchat-gnome". Both are for Gnome, but the xchat-gnome removes most of the program's features to make the UI simpler.

---

### Post by Titan8990 on 2009-01-14
Also, there are other distros that "force feed" you source compilation....

---

### Post by Dravenm4 on 2009-01-14
Thanks guys it is up and running now. :KS

---

### Post by Titan8990 on 2009-01-14
Good to hear.

---

### Post by Armag3ddon on 2009-02-10
well i got a problem with XChat guys, i installed it through Add/Remove..., and it used to work just fine, it crashed once for no reason and with no error, and it never opened since, iv tried to uninstall it and install it back again though Add/Remove... Same problem... Any ideas?

---

### Post by Armag3ddon on 2009-02-10
Well problem solved, i installed it using terminal :) thanks anyway guys...

---

