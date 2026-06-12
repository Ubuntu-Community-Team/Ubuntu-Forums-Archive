---
title: "deb install for sunbird"
date: 2010-07-10
forum: New to Ubuntu
---

### Post by rburkartjo on 2010-07-10
does anyone know where i can get a deb install for the final version of sunbird. the only link i can find is this 

[http://www.mozilla.org/projects/calendar/sunbird/download.html](http://www.mozilla.org/projects/calendar/sunbird/download.html)

i have been using linux for about 4 years and still have problems with installing .tar.bz2 files if i cant find a .deb file just dont install/tks

---

### Post by rburkartjo on 2010-07-10
or if someone wants to give an old man instructions on how to install this. that would work

---

### Post by sandyd on 2010-07-10
> **rburkartjo said:**
> or if someone wants to give an old man instructions on how to install this. that would work
[https://launchpad.net/~davidf/+archive](https://launchpad.net/~davidf/+archive)

---

### Post by rburkartjo on 2010-07-11
carlee tks but is sunbird 1.0 beta1 that i want to install

---

### Post by sandyd on 2010-07-11
> **rburkartjo said:**
> carlee tks but is sunbird 1.0 beta1 that i want to install

use the mozilla daily builds ppa then.

---

### Post by rburkartjo on 2010-07-11
tks carlee will mark thread as solved when i get the update

---

### Post by gandaran on 2010-07-11
installing sunbird is easy! sunbird is already compiled, just download that tar package, right click » extract here, the resulting extracted sunbird folder you can put it anywhere you like, your home folder or root directory, to run sunbird cd terminal to sunbird folder and type ./sunbird or even better make your own launcher, the launch command is just the full path to the sunbird file in the sunbird folder, couldn't be easier.

---

### Post by skyjacker on 2010-07-11
> **gandaran said:**
> installing sunbird is easy! sunbird is already compiled, just download that tar package, right click » extract here, the resulting extracted sunbird folder you can put it anywhere you like, your home folder or root directory, to run sunbird cd terminal to sunbird folder and type ./sunbird or even better make your own launcher, the launch command is just the full path to the sunbird file in the sunbird folder, couldn't be easier.

I to would like to have Sunbird", but I tried your solution and it didn't work for me. I just got a message that said sunbird was not installed...

---

### Post by rburkartjo on 2010-07-11
gan i installed sunbird in my home folder but still cant get it to run the newest version that is 1.0

ray@ray-desktop:~$ cd /home/ray/sunbird
ray@ray-desktop:~/sunbird$ 

any ideas this is no big thing it is just these tar installs are a p.i.a/tks

---

### Post by gandaran on 2010-07-11
> **skyjacker said:**
> I to would like to have Sunbird", but I tried your solution and it didn't work for me. I just got a message that said sunbird was not installed...
can you provide some details, where did you put the extract sunbird folder and what launcher command did you run.

---

### Post by gandaran on 2010-07-11
> **rburkartjo said:**
> gan i installed sunbird in my home folder but still cant get it to run the newest version that is 1.0

ray@ray-desktop:~$ cd /home/ray/sunbird
ray@ray-desktop:~/sunbird$ 

any ideas this is no big thing it is just these tar installs are a p.i.a/tks
you tried this?
ray@ray-desktop:~/sunbird$ ./sunbird 
like I said it's better to make your launcher with the full path.

the launcher command for you would be » /home/ray/sunbird/sunbird
try it, it will work if the sunbird folder is still in home directory

---

### Post by rburkartjo on 2010-07-11
gan must be problem with the app itself


ray@ray-desktop:~$  /home/ray/sunbird/sunbird
/home/ray/sunbird/sunbird-bin: 10: &#65533;&#65533;@8: not found
/home/ray/sunbird/sunbird-bin: 10: @@@@@@00pp@p@@@&#65533;&#65533;&#65533;&#65533;: not found
/home/ray/sunbird/sunbird-bin: 10: &#928;: not found
/home/ray/sunbird/sunbird-bin: 10: .&#65533;: not found
/home/ray/sunbird/sunbird-bin: 10: .&#65533;&#65533;@&#65533;@: not found
/home/ray/sunbird/sunbird-bin: 10: : not found
/home/ray/sunbird/sunbird-bin: 10: Q&#65533;tdR&#65533;td: not found
/home/ray/sunbird/sunbird-bin: 10: &#65533;7&#65533;: not found
/home/ray/sunbird/sunbird-bin: 10: &#65533;e&#65533;&#65533;
                                            &#65533;&#65533;P: not found
/home/ray/sunbird/sunbird-bin: 10: ELF: not found
/home/ray/sunbird/sunbird-bin: 11: 0: not found
/home/ray/sunbird/sunbird-bin: 12: &#65533;&#65533;&#65533;&#65533;&#65533;&#65533;: not found
/home/ray/sunbird/sunbird-bin: 12: w: not found
/home/ray/sunbird/sunbird-bin: 13: $: not found
/home/ray/sunbird/sunbird-bin: 14: Syntax error: ")" unexpected
ray@ray-desktop:~$

---

### Post by gandaran on 2010-07-11
> **rburkartjo said:**
> gan must be problem with the app itself


ray@ray-desktop:~$  /home/ray/sunbird/sunbird
/home/ray/sunbird/sunbird-bin: 10: &#65533;&#65533;@8: not found
/home/ray/sunbird/sunbird-bin: 10: @@@@@@00pp@p@@@&#65533;&#65533;&#65533;&#65533;: not found
/home/ray/sunbird/sunbird-bin: 10: &#928;: not found
/home/ray/sunbird/sunbird-bin: 10: .&#65533;: not found
/home/ray/sunbird/sunbird-bin: 10: .&#65533;&#65533;@&#65533;@: not found
/home/ray/sunbird/sunbird-bin: 10: : not found
/home/ray/sunbird/sunbird-bin: 10: Q&#65533;tdR&#65533;td: not found
/home/ray/sunbird/sunbird-bin: 10: &#65533;7&#65533;: not found
/home/ray/sunbird/sunbird-bin: 10: &#65533;e&#65533;&#65533;
                                            &#65533;&#65533;P: not found
/home/ray/sunbird/sunbird-bin: 10: ELF: not found
/home/ray/sunbird/sunbird-bin: 11: 0: not found
/home/ray/sunbird/sunbird-bin: 12: &#65533;&#65533;&#65533;&#65533;&#65533;&#65533;: not found
/home/ray/sunbird/sunbird-bin: 12: w: not found
/home/ray/sunbird/sunbird-bin: 13: $: not found
/home/ray/sunbird/sunbird-bin: 14: Syntax error: ")" unexpected
ray@ray-desktop:~$
you still got it wrong, this command '/home/ray/sunbird/sunbird' is for the desktop or main menu launcher, you don't run it in terminal.
for the terminal you cd to the sunbird folder, hit enter then type ./sunbird and hit enter

---

### Post by gandaran on 2010-07-11
this is how I have mine installed, I renamed the sunbird folder to .sunbird (the extra dot makes the folder hidden in your home directory), then go to system»preferences»main menu, select the office or any other option of you choice, click the add button, fill in launcher name and the start command (/home/ray/.sunbird/sunbird » *dont forget the dot if you want to hide the folder*) then find a nice icon to go with, thats all, now you can start sunbird from the applications menu.

---

### Post by rburkartjo on 2010-07-11
gan tks for your help but still cant get it to work no big deal. just that this will be the last release of sunbird and would like to upgrade. also checked and there is not a ppa

---

### Post by gandaran on 2010-07-11
> **rburkartjo said:**
> gan tks for your help but still cant get it to work no big deal. just that this will be the last release of sunbird and would like to upgrade. also checked and there is not a ppa
which version did you download? sunbird 1.0 beta1 ?
this [one]("http://download.mozilla.org/?product=sunbird-1.0b1&os=linux&lang=en-US")? this is the one I an running, well I cant figure out why it doesn't work for you then, as you can see from my instructions it's easy.

---

### Post by ankspo71 on 2010-07-11
Hi, 
Here are download and install instructions for Songbird_1.8.0b3.
[http://www.webupd8.org/2010/07/how-to-run-songbird-18-beta-in-ubuntu.html](http://www.webupd8.org/2010/07/how-to-run-songbird-18-beta-in-ubuntu.html)
It also includes the gstreamer plugin workaround (which is just removing the gstreamer plugins from the sunbird folder).

After you do this, songbird should be installed in your home directory ;)

OOPS. Disregard my post. I missed the part where you said:
> carlee tks but is sunbird 1.0 beta1 that i want to install
I think I'll leave my response for other people to see though.

---

### Post by rburkartjo on 2010-07-11
gan should i uninstall sunbird 9.0 before i try again what you suggested. if it worked for you i am just doing something dumb

---

### Post by gandaran on 2010-07-11
> **rburkartjo said:**
> gan should i uninstall sunbird 9.0 before i try again what you suggested. if it worked for you i am just doing something dumb
no, you don't have to remove it, it cant interfere in any way, the older version is installed in root file system and you can run any other versions as long they are installed somewhere else even the root file system as long they are separated and have deferent start commands.

did you try the launcher? or have you only tried running it from the terminal?
try this, right click on the desktop area, choose from the menu to make launcher, type Sunbird in the name field and enter the full path to the sunbird file (not just the sunbird folder, must be the full path to the file) in the command field, close it, now you have a desktop launcher which will work if you have the correct path.
just one question, you did extract the tar package and have a sunbird folder in your home user directory?

---

### Post by rburkartjo on 2010-07-11
gan tks for you help but still cant get it to work.note i download the tar of the x86-64 i have a 64 dual system. that could be the problem. i have learned that if i go to the directory i have created and click on the bin file the program should launch. cant get it to to this. again tks for everything

---

### Post by gandaran on 2010-07-12
> **rburkartjo said:**
> gan tks for you help but still cant get it to work.note i download the tar of the x86-64 i have a 64 dual system. that could be the problem. i have learned that if i go to the directory i have created and click on the bin file the program should launch. cant get it to to this. again tks for everything
how about one last try ;)
maybe I was wrong about removing the older version, I forgot about the sunbird user profile, maybe the older and newer are not compatible and they share the same user profile, so try this, don't unisntall the older version yet, just don't use it, go to the hidden home folder, find and open the .mozilla folder, there should be a sunbird folder inside, don't delete it just rename it to something else like 'sunbird_0' so you can restore it later if needed.
now click on the new version launcher, if this time it works it will make a new sunbird profile in /home/user/.mozilla/sunbird, I hope this time it works. 
and about clicking the sunbird bin file, it doesn't work! I even tried a launcher for the bin file and it doesn't work too, only launching the sunbird file works here.

---

### Post by rburkartjo on 2010-07-14
gan tks will give that a try this weekend. and again tks for the extra effort you put into helping me

---

### Post by rburkartjo on 2010-07-23
gan just wanted you to know that i finally got it to work just as you said. i have been working too many hours and just had to get a clear head

---

