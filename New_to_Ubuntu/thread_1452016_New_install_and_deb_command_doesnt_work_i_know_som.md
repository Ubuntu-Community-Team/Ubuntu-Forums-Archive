---
title: "New install and deb command doesnt work? i know something is missing"
date: 2010-04-11
forum: New to Ubuntu
---

### Post by BeatnikBandit on 2010-04-11
Before posting this I searched the forums and it seams no one else has this problem so i must be more than an absolute beginner I must be an absolute(squared) Beginner (I don't know how to type it like with winblows alt codes for squared in linux)

Well recently I decided to format (pretty stupid in retrospect but hey hindsight is 20/20) because I wanted to install 9.10 fresh as previously I was running 9.10 but it was upgraded from 9.04 and my system was acting up. Well now it is MUCH more stable although now that I am in the process of setting up all the apps and repositories, etc...

So here after that bit of background of where I am coming from. Here is the meat of the issue. I don't know why because I have never encountered this problem and its been a while since I did this and I know know I am Rusty. Firstly the only thing i have encountered yet is that i do not have the dependencies to run the deb command, to me this is odd.

(I am trying to keep it short but this is the command I tried to use and the results i got in the terminal)
The command:
```
deb http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt all main
```What i got after entering it:
```
No command 'deb' found, did you mean:
 Command 'debc' from package 'devscripts' (main)
 Command 'derb' from package 'libicu-dev' (main)
 Command 'dab' from package 'bsdgames' (universe)
 Command 'debi' from package 'devscripts' (main)
```(this was from [this page]("http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page") to install firefox)

(most likely un-needed I installed all thoes packages just in casde although i know it wont fix it and of course it didnt but whatever I did it anyway. Should I Remove any of them? I REALLY doubt i would ever need "bsdgames" LOL but they might be fun)


So what do I need to install to get deb working??
Also to get it out of the way what else should I get while i am at it to get my system ready to do what I want?

So far using synaptic I have added Build as I know ill need that later. 

Importantly  what else do i need to get back into working order? Like all packages needed on an average system like build, deb and anything else I don't have anymore that will be useful. I thought i had a hang of this but the last full install i did was when I received my 9.04 cd in the post. Frankly I cant remember anything.

I thank you for reading this and i hope i provided enough information (most likely I added more than needed as what I need is basically a list of either terminal commands to add everything I need or a list of packages to be installed with synaptic so i can get going.)

---

### Post by sisco311 on 2010-04-11
That's not a command. You have to add the t line to your sources:
```
gksu gedit /etc/apt/sources.list.d/ubuntuzilla.list
```
paste the line in the file, then run:
```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com C1289A29
sudo apt-get update
```

---

### Post by BeatnikBandit on 2010-04-11
**Sisco311**, Thank you SOO Much you always answer my questions and you do it fast I wonder why the site said it was a command? weird cuz you know everything on the internet in true right? LOL So far you have prevented me from burying a new printer because of your advanced knowledge and now you set me straight on this.

I was able to do it a different way by adding it to the repositories in the synaptic gui and it seamed to work but I still did what you said to do because you have never steered me in the wrong direction. I wish i could do more than say thank you but sadly you being in Romania I cant even shake your hand so Just know i appreciate your help immensely.

I wonder what was up with the guy/girl that posted that command:confused:  "People are strange when you're a stranger"

Anyway since I kinda have your attention are there anything i might want to install basides Build (which i have already installed) so whn i come acrost things that need to be done Via Terminal Ill be fine and wont run into things like this when the commands are correct, LOL if not ill mark this as solved. I thank you VERY MUCH

---

### Post by sisco311 on 2010-04-11
You are welcome!

The phrasing of the tutorial may be confusing, but it's technically correct. It says "add manually to the sources.list" which means that you have to append the sources.list file with the mentioned line.

You can sing up at sourceforge.net to contribute to the project(s) & improve the quality of the tutorials / wiki pages.

---

