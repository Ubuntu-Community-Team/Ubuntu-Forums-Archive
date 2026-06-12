---
title: "64 bit adobe... how do i install a tar?/"
date: 2009-08-23
forum: New to Ubuntu
---

### Post by R3fr4cti0n on 2009-08-23
i can download it from here [http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)

but how do i install it ?

---

### Post by perce on 2009-08-23
A tar.gz is a compressed archive, not an installer. You should download it and uncompress it (right click on the file, and choose something like "extract"). Then it will create a subdirectory which will contain the actual installation program and some instruction file (usually called README). The instructions will tell you how to install.

---

### Post by SunnyRabbiera on 2009-08-23
For newcommers I personal;ly suggest the ubuntu-restricted-extras package as opposed to relying on the .tar
You will get the 32bit version of flash yes but some have had luck with it.
You can use some 32bit apps under 64bit

---

### Post by loomsen on 2009-08-23
```

wget http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz -O- | tar xzf -
 
```

Then for firefox:
```

mv libflashplayer.so ~/.mozilla/plugins/

```

for opera:
```

sudo mv libflashplayer.so /usr/lib/opera/plugins

```

*done*

---

### Post by R3fr4cti0n on 2009-08-23
> **loomsen said:**
> ```

wget http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz -O- | tar xzf -
 
```Then for firefox:
```

mv libflashplayer.so ~/.mozilla/plugins/

```for opera:
```

sudo mv libflashplayer.so /usr/lib/opera/plugins

```*done*



Did this...  julian@Abriella:~$ mv libflashplayer.so ~/.mozilla/plugins/

got this... mv: cannot move `libflashplayer.so' to `/home/julian/.mozilla/plugins/': Not a directory

---

### Post by celthunder on 2009-08-23
does /hom/julian/.mozilla/plugins/ exist?

---

### Post by loomsen on 2009-08-23
> **R3fr4cti0n said:**
> Did this...  julian@Abriella:~$ mv libflashplayer.so ~/.mozilla/plugins/

got this... mv: cannot move `libflashplayer.so' to `/home/julian/.mozilla/plugins/': Not a directory

```

mkdir -p /home/julian/.mozilla/plugins/ && mv ibflashplayer.so ~/.mozilla/plugins/

```

---

### Post by R3fr4cti0n on 2009-08-23
neither of them exists "no such file or directory for both..

---

### Post by Thelasko on 2009-08-23
go to places>home folder
then press control+h
look for the .mozilla folder and double click on it.
double click on plugins and then paste (ctrl+v) the plugin (libflashplayer.so) there.
Then right click on it and go to properties.
Click on the permissions tab, and make sure the box that says "Allow executing file as a program" is marked.

---

### Post by SunnyRabbiera on 2009-08-23
> **R3fr4cti0n said:**
> neither of them exists "no such file or directory for both..

Just ignore the command line stuff for now, just use the ubuntu restricted extras package.
[http://packages.ubuntu.com/jaunty/ubuntu-restricted-extras](http://packages.ubuntu.com/jaunty/ubuntu-restricted-extras)

---

### Post by R3fr4cti0n on 2009-08-23
> **SunnyRabbiera said:**
> Just ignore the command line stuff for now, just use the ubuntu restricted extras package.
[http://packages.ubuntu.com/jaunty/ubuntu-restricted-extras](http://packages.ubuntu.com/jaunty/ubuntu-restricted-extras)
   

i went to it clicked on  [flashplugin-nonfree]("http://packages.ubuntu.com/jaunty/flashplugin-nonfree") 	          [amd64]Adobe Flash Player plugin installer (transitional package)	  
also a virtual package provided by 	   	     [flashplugin-installer]("http://packages.ubuntu.com/jaunty/flashplugin-installer")
that took me to 

this [flashplugin-installer]("http://packages.ubuntu.com/jaunty/flashplugin-installer") 	         Adobe Flash Player plugin installer         and the linc took me to a page with nothing about flash on it


and does /hom/julian/.mozilla/plugins/  does not exist... man i suck at this ubuntu thing.                                   [B]
[/B]

---

### Post by oldos2er on 2009-08-23
There's a script in the stickies of the x86_64 forum: [http://ubuntuforums.org/attachment.php?attachmentid=125745&d=1250873141](http://ubuntuforums.org/attachment.php?attachmentid=125745&d=1250873141)

---

### Post by R3fr4cti0n on 2009-08-23
mkdir: cannot create directory `/tmp/pluginstall': File exists ...ugg

starting to hate this os it just will not work on my tx2z!

---

### Post by oldos2er on 2009-08-23
> **R3fr4cti0n said:**
> mkdir: cannot create directory `/tmp/pluginstall': File exists ...ugg

starting to hate this os it just will not work on my tx2z!

 Knowing exactly what you're doing when the error popped up would help. You only need to run the script once, then restart Firefox.

---

### Post by R3fr4cti0n on 2009-08-23
can't even run it: 

/tmp/Get64bitFlash.tar-2.gz could not be opened, because the associated helper application does not exist. Change the association in your preferences.

no option to open with firefox just archive manager

---

### Post by loomsen on 2009-08-23
Still?

OK, here you are a script:

[http://yep.it/w42ko8](http://yep.it/w42ko8)

download it, open a terminal, change into the directory you saved it to
(or simply save it to ~/ as this is the default dir you'll be dropped to when opening a terminal)

OK, again, save the script as 
```
getflash-for-r3fr4ction.sh
```

open a terminal, and run
```
sh getflash-for-r3fr4ction.sh
```

When done you're ready and should have flash working (the script will check for the proper directory and create it if non-existent, so nothing else to do than this 1 command above)

---

### Post by perce on 2009-08-24
> **R3fr4cti0n said:**
> can't even run it: 

/tmp/Get64bitFlash.tar-2.gz could not be opened, because the associated helper application does not exist. Change the association in your preferences.

no option to open with firefox just archive manager

It is an archive, no wonder you must open it with an archive manager

---

### Post by SunnyRabbiera on 2009-08-24
> **R3fr4cti0n said:**
> i went to it clicked on  [flashplugin-nonfree]("http://packages.ubuntu.com/jaunty/flashplugin-nonfree") 	          [amd64]Adobe Flash Player plugin installer (transitional package)	  
also a virtual package provided by 	   	     [flashplugin-installer]("http://packages.ubuntu.com/jaunty/flashplugin-installer")
that took me to 

this [flashplugin-installer]("http://packages.ubuntu.com/jaunty/flashplugin-installer") 	         Adobe Flash Player plugin installer         and the linc took me to a page with nothing about flash on it


and does /hom/julian/.mozilla/plugins/  does not exist... man i suck at this ubuntu thing.                                   [B]
[/B]

You should just be able to download the version for 64bit, save it and install it like a windows .exe
I wonder why its causing you trouble, the ubuntu restricted extras package usually works even on 64bit

---

### Post by 3rdalbum on 2009-08-24
> **SunnyRabbiera said:**
> You should just be able to download the version for 64bit, save it and install it like a windows .exe
I wonder why its causing you trouble, the ubuntu restricted extras package usually works even on 64bit

*sigh*  Anyone here actually installed Flash Player on 64-bit or been a newbie?

Firstly, if you have the "flashplugin-nonfree" package, get rid of it. It doesn't work very well on 64-bit.

Secondly, decompress the 64-bit alpha tar.gz from the Adobe site. Inside is a file called "libflashplayer.so".

Now open up a file browser window as root, by pressing Alt-F2 and typing:

```
gksudo nautilus
```

Navigate this new root window to the "/usr/lib/mozilla/plugins" folder, and drag the libflashplayer.so file into the folder. Restart Firefox. That's all.

---

### Post by miklcct on 2009-08-24
I have a 64-bit flash player .deb available but I can't find the download link.

---

### Post by R3fr4cti0n on 2009-08-24
> **3rdalbum said:**
> *sigh*  Anyone here actually installed Flash Player on 64-bit or been a newbie?

Firstly, if you have the "flashplugin-nonfree" package, get rid of it. It doesn't work very well on 64-bit.

Secondly, decompress the 64-bit alpha tar.gz from the Adobe site. Inside is a file called "libflashplayer.so".

Now open up a file browser window as root, by pressing Alt-F2 and typing:

```
gksudo nautilus
```Navigate this new root window to the "/usr/lib/mozilla/plugins" folder, and drag the libflashplayer.so file into the folder. Restart Firefox. That's all.



i canrt seem to locate the usr folder..

---

### Post by gn2 on 2009-08-24
It's a pity that people have been wasting your time with terminal commands.
Installing it can be done very easily without ever opening a terminal.

Here's how: [http://news.softpedia.com/news/How-to-Install-Adobe-Flash-Player-64-bit-on-Ubuntu-8-10-98076.shtml](http://news.softpedia.com/news/How-to-Install-Adobe-Flash-Player-64-bit-on-Ubuntu-8-10-98076.shtml)

---

### Post by loomsen on 2009-08-24
> **gn2 said:**
> It's a pity that people have been wasting your time with terminal commands.
Installing it can be done very easily without ever opening a terminal.

Here's how: [http://news.softpedia.com/news/How-to-Install-Adobe-Flash-Player-64-bit-on-Ubuntu-8-10-98076.shtml](http://news.softpedia.com/news/How-to-Install-Adobe-Flash-Player-64-bit-on-Ubuntu-8-10-98076.shtml)

Do you really think this will save time? 
Compared to a 1-liner (well, dependency brain usage >= 0.9 enabled) from a terminal?

Never.

---

### Post by 3rdalbum on 2009-08-24
> **R3fr4cti0n said:**
> i canrt seem to locate the usr folder..

Click "File System" in the left pane. It's in there.

---

### Post by gn2 on 2009-08-24
> **loomsen said:**
> Do you really think this will save time?

For the OP, yes.
Fourteen hours have elapsed between his/her first and last posts in the thread and the problem is yet to be fixed.

---

### Post by loomsen on 2009-08-24
> **gn2 said:**
> For the OP, yes.
Fourteen hours have elapsed between his/her first and last posts in the thread and the problem is yet to be fixed.

I already fixed it twice... The problem isn't the difficulty of this task but the lack of effort the threadstarter is willing to put it 
( --- yes, even copy n pasting two commands one after another seems to be to hard. Thats why I wrote this quick n dirty script, still 2 hard...)

No excuses in this case imo.

---

### Post by 73ckn797 on 2009-08-24
The restricted-extras flash from synaptic works perfectly in 9.04 64 bit for me.

---

### Post by gn2 on 2009-08-24
> **loomsen said:**
> I already fixed it twice.

No you didn't, because the commands you quoted were incorrect.

Then there was your script.
The instructions accomanying your script assume knowledge which it's extremely unlikely the OP will have and it should have been very easy for you to see that.
Worse, your script is not guaranteed to work.

Terminal is great, but works well *only* if you speak the language.
The OP doesn't (yet)

For the OP and other inexperienced users of Linux, the GUI option I linked to is far simpler for this task.

---

### Post by R3fr4cti0n on 2009-08-24
[3rdalbum]("http://ubuntuforums.org/member.php?u=61044"), i got an error message when i tried to place the file in the pugins folder, it said Extraction not performed

"You don't have the right permissions to extract archives in the folder "file:///usr/lib/mozilla/plugins" thankyou for the help tho.

[gn2]("http://ubuntuforums.org/member.php?u=142809"), your instructions worked! idw they seemed to be basicly the same as 3rdalbum's

[loomsen]("http://ubuntuforums.org/member.php?u=638338"), I'll have you know that i have been trying to program this Tablet Pc with ubuntu for about a week at about 4 hours a day. yes i suck at it but i am sure that at some point you were a noob aswell and i am sure that you understand that the community is one of the best features of this OS. Infact i would venture to bet that, Like me, you use ubuntu because of its stability and freedom along with the various schools of thought that have been put into this Os built with efficity and beauty. I feel that it is a work of art. This is the Os that the top Programers at Microsoft and Apple go home to play with, this is the Os of Passion not just Paychecks i would hope that you pay the users and the OS the respect  they undoubtly deserve it is a beautiful cycle of communism. Served by noobs like me and Vets like yourself that make this system work. without us, there is no you, and no ubuntu. Lets spread the love not insults.

---

### Post by SunnyRabbiera on 2009-08-24
Uhh Open source is not really communism

---

### Post by gn2 on 2009-08-24
> **R3fr4cti0n said:**
> gn2, your instructions worked! idw they seemed to be basicly the same as 3rdalbum's

The major difference between the method I linked to and 3rdAlbum's are that with his/hers, the .so file is copied to the /usr directory instead of /home.

With the one I linked to, on a multi-user set-up, you would have to do the procedure for each user, 3rdAlbum's way it would automatically be done for every user.

---

### Post by loomsen on 2009-08-24
> No you didn't, because the commands you quoted were incorrect.

No, they weren't. The OP was only missing a directory I assumed would exist ( - I don't use FF myself)

> loomsen, I'll have you know that i have been trying to program this Tablet Pc with ubuntu for about a week at about 4 hours a day. yes i suck at it but i am sure that at some point you were a noob aswell and i am sure that you understand that the community is one of the best features of this OS. Infact i would venture to bet that, Like me, you use ubuntu because of its stability and freedom along with the various schools of thought that have been put into this Os built with efficity and beauty. I feel that it is a work of art. This is the Os that the top Programers at Microsoft and Apple go home to play with, this is the Os of Passion not just Paychecks i would hope that you pay the users and the OS the respect they undoubtly deserve it is a beautiful cycle of communism. Served by noobs like me and Vets like yourself that make this system work. without us, there is no you, and no ubuntu. Lets spread the love not insults.

I don't use ubuntu. However, well said, didn't mean to offend you and I apologize if it sounded like.

So long.

---

### Post by gn2 on 2009-08-24
> **loomsen said:**
> No, they weren't. The OP was only missing a directory I assumed would exist ( - I don't use FF myself)

So a command that doesn't work is correct and the default Ubuntu file structure is wrong.
Good, glad that's cleared up. :rolleyes:

---

### Post by tuxxy on 2009-08-24
> **SunnyRabbiera said:**
> For newcommers I personal;ly suggest the ubuntu-restricted-extras package as opposed to relying on the .tar
You will get the 32bit version of flash yes but some have had luck with it.
You can use some 32bit apps under 64bit

ubuntu-restricted-extras will install 32-bit Flash, the OP asked for 64-bit.  32-bit Flash is really poor on 64-bit and really does affect performance for web browsing and dont get me started on npviewer.

To install 64-bit flash which is much better than the 32-bit simply download this file [http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html) and extract it to /usr/lib/share/mozilla/plugins

To finish it off don't forget to remove flashplugin-nonfree that came with ubuntu-restricted-extras, you can do this in synaptic or use this command

```
sudo apt-get remove flashplugin-nonfree
```

---

### Post by R3fr4cti0n on 2009-08-24
come on loomsen use ubuntu and firefox all the cool kids r doing it. :)

ty all for your help

---

### Post by 73ckn797 on 2009-08-24
> **tuxxy said:**
> 
To install 64-bit flash which is much better than the 32-bit simply download this file [http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html) and extract it to /usr/lib/share/mozilla/plugins


I use the restricted-extra flash plugin and want to install the 64 bit.

The directory you suggest (/usr/lib/share/mozilla/plugins) does not exist. Should I create it? I do find this "/usr/lib/mozilla/plugins".

---

### Post by R3fr4cti0n on 2009-08-24
> **gn2 said:**
> It's a pity that people have been wasting your time with terminal commands.
Installing it can be done very easily without ever opening a terminal.

Here's how: [http://news.softpedia.com/news/How-to-Install-Adobe-Flash-Player-64-bit-on-Ubuntu-8-10-98076.shtml](http://news.softpedia.com/news/How-to-Install-Adobe-Flash-Player-64-bit-on-Ubuntu-8-10-98076.shtml)

73ckn779, this is the easyest way for 64bit that i found

---

### Post by miklcct on 2009-08-25
You can try this .deb:

[ftp://miklcct.no-ip.org/adobe-flashplugin_10.0.d20_amd64.deb](ftp://miklcct.no-ip.org/adobe-flashplugin_10.0.d20_amd64.deb)

This .deb is the best version I found ever.

---

### Post by 3rdalbum on 2009-08-25
> **R3fr4cti0n said:**
> [3rdalbum]("http://ubuntuforums.org/member.php?u=61044"), i got an error message when i tried to place the file in the pugins folder, it said Extraction not performed

"You don't have the right permissions to extract archives in the folder "file:///usr/lib/mozilla/plugins" thankyou for the help tho.

I said to extract it and then open a file browser as root and copy the extracted file to /usr/lib/mozilla/plugins. You opened the archive in File Roller (as your normal user) and then tried to extract it to that location. That doesn't work.

In order to write to anything outside your home directory, the program that is doing the copying needs to be run as root.

The other poster's instructions worked for you because they worked on a per-user basis, and only installed the file into your home directory (didn't need root access). If you decide to make a user account for someone else, they won't be able to use Flash until you install it per-user for them.

If you're going to be successful on Linux you must be able to ditch the Windows mindset of "My user account can do anything" and get into the Linux mindframe of "If it's modifying anything outside my home directory, it needs to be run as root". More accurately, if it's something that can affect the other users on the computer, then it needs to be run as root.

---

