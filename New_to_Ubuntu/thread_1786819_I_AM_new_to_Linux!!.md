---
title: "I AM new to Linux!!"
date: 2011-06-20
forum: New to Ubuntu
---

### Post by Tilith on 2011-06-20
Hi Ubuntu Forums!

i don't know where to start but the "absolute beginner talk" sounded like the right place to be. I have only run Linux on my computer for a short amount of time and I'm starting the get the feel of how the desktop works for a total newbie.. so what i was hoping in this post is to get some pointers to how i can do some exploring on it. What kind of possibilities do i have?

First of I want say that I'm pretty handy with computers... well.. With Windows at least. Been running windows since W95 and I'm currently dual-booting with Windows 7. I have gotten bored of Windows and went looking for something else to do on my computer. So i found Linux. I also read that Ubuntu was one of the easier for newbies like myself (tried Linux Mint tho but i wasn't happy with the look and feel).

As far as i have figured my "computing-skills" as a Windows-user wont help me out here in Linux... which isn't surprising since its two totally different OS's. Well enough of the chitchat.

I want to know what i can do on Linux\Ubuntu.
1. Find some things to toy around with. For instance i cant even use the "Terminal" yet. What are my possibility? I know the "terminal" is a powerful tool in Linux and people really shouldn't "mess" around in it if they don't know what to do. 
2. Is there anywhere i can find a very good step-by-step walkthrough about how to "make" a program... or other sorts of programming. Nothing fancy but something like and executable file which does a simple task.
3. Where and how do i get widgets (if thats what they are called)?
4. I know how a computer with Windows works. I want to know how a computer with Linux works. So any other usage i can get out of Ubuntu.

I'm a newbie as you know. I want to take my first steps towards becoming a more advanced Linux-user. For info I'm using a fairly powerful computer and running Ubuntu 11.04. Also know i could probably find answers to all of my questions in the forums here but i kind-of also wanted to try to make myself an own thread. I hope that is OK.

PS: Sorry for a big thread. Another thing i want to know is: Why did you change to Linux from Windows or Apple-OS. For me the answer would be. I want to widen my computing experience... and also i got bored of Windows.
PSS: i have also tried out and had some fun with compiz. Making my desktop look like an amusement-park is fun but... I don't really need it

---

### Post by tej1984 on 2011-06-20
Hello -- The *Force is strong* with this one!!

a good place to start is [www.**omgubuntu**]("http://www.%3Cb%3Eomgubuntu%3C/b%3E").co.uk 

it will give you an idea of what you can do in ubuntu and make it your own workspace which im sure you'll love!! but one peace of advice please do back up, because it takes a long time to configure it the way you want it and then if you make a mistake on a config file its ALL OVER!!

---

### Post by Tilith on 2011-06-20
Hi.

Thanks for the fast reply. I will check out the website. I actually have an application on my smart-phone named OMGubuntu. Gives me lots of news etc. really handy. It didn't come to mind that it was an actually website. Btw, any other applications for smart-phone that can help me as an Ubuntu-user? 

> but one peace of advice please do back up, because it takes a long time  to configure it the way you want it and then if you make a mistake on a  config file its ALL OVER!!

This actually sounds interesting. But to back-up a file i just have to copy it and make it safe? or is it an more proper way to do it? Also. If a mess everything up how will i able to restore my original? I have lots of experience with Windows so I am very used to have to reinstall the entire system if something goes bad. I probably wouldn't get sad if i had to do it with Ubuntu. Luckily for me installing Ubuntu takes no time compared to Windows 7 at least.

---

### Post by mastablasta on 2011-06-20
Look in my signature for a guide/manual and then have a look at linuxcommand.org for a free e-book on terminal commands.
 
a cool thing you can do is create a (web)server (dont' forget to put a firewall in place for security) so you can access you computer from anywhere with your phone ;-)
 
> **Tilith said:**
>  
This actually sounds interesting. But to back-up a file i just have to copy it and make it safe? or is it an more proper way to do it? Also. If a mess everything up how will i able to restore my original? I have lots of experience with Windows so I am very used to have to reinstall the entire system if something goes bad. I probably wouldn't get sad if i had to do it with Ubuntu. Luckily for me installing Ubuntu takes no time compared to Windows 7 at least.
 
One way is to create a clone of all system/disk (with a programme Clonezilla for example).
There are also terminal commands.
 
but the simplest way is to use a small tool (that linux Mint uses) called minta backup. it has only 4 buttons. 2 are for backing up and 2 for restoring. really easy and simple to use. 1 backsup applications and the other one your files and configurations in home folder. here is how you get it in Ubuntu:
[http://www.webupd8.org/2010/07/install-mintbackup-linux-mint-backup.html](http://www.webupd8.org/2010/07/install-mintbackup-linux-mint-backup.html)

---

### Post by collisionystm on 2011-06-20
Make sure to install Ubuntu Tweak. Its an awesome addition to Ubuntu.

[http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)

---

### Post by nerdy_kid on 2011-06-20
Well, some things that I would have loved to know:

First off, if you want to use the terminal then know this:

1.  <TAB> is autocomplete.  It will autocomplete file/folder names and command names, it is AWESOME.  If you double-tap <TAB> then you will get a listing of all possible command/filenames depending on what the command is you are trying to do.  Also, these are a few basic commands:

cd moves you into another folder.
pwd prints the folder you are in.
ls lists files and folders in the folder you are in.
rm removes stuff
mkdir makes a folder.
touch makes a file.
nano is a text editor.

You can use the man command (see my next tip) on any of these commands.

2.  the command "man" (without quotes) is the "manual".  type it in front of any other command to get that command's manual, for example, "man rm" would give you the manual for the "rm" command.  Also, you can use the -k flag to search all of the manuals:  "man -k firewall"  would search all the manuals for "firewall".  Very useful -- see "man man" for more :)

3.  One thing I wanted to know is how the filesystem was setup -- which files went where.  Linux uses one big virtual file system -- / (root).  Every file that is read is somehow connected to root.  Under root, there are the /etc, /usr, /var, /home, /dev, and /media folders, among others.  The /etc folder is where all of the core system config files are.  You probably don't want to fiddle too much in here for a while.  The /usr folder is where programs and libraries (.so files -- the Linux version of dlls pretty much) go.  /usr/bin is where most executables go, /usr/lib/ is where most libraries go, /usr/share/ is where most program data goes.  System logs are in /var/logs.  Your personal files and folders reside under /home.  Any cds/dvds/external media that you use gets "mounted" (attached to Linux's virtual filesystem) under /media.  /dev is a really cool folder, all the files in it are "block devices"  basically, they can give you direct access to the hardware.  This can be really useful.


I would backup all your important files, and try your best to bust Ubuntu, and then fix it.  Just think of something awesome that you would love to have Ubuntu do, and then google it.  Usually there is a dangerous way to get what you want, so do it :)

---

### Post by fballem on 2011-06-20
In my signature is a list of programs that I have found useful and how to install them fairly quickly as well as some setup notes on the repositories (and yes, I do have some use of Terminal in those notes).

As for why my switch to Linux, it was because of Windows Vista and Microsoft Office 2007. In the case of Vista, it was terrible and in the case of Microsoft Office 2007, I could never get used to the changes in the interface (I used to be an Office guru).

Once I started on Linux (specifically Ubuntu), I found the Windows interface to be primitive at best.

Regards,

---

### Post by Tilith on 2011-06-20
wow thanks for all the replies. The online-community is really good (as i had heard). 

**mastablasta** Thanks for the tip backup-programs, and terminal-commands. I'm very sure they will come to great help. And i will also try to make a web-server as you suggested. That sounds awesome. 

> 1. <TAB> is autocomplete. It will autocomplete file/folder names and command names, it is AWESOME. If you double-tap <TAB> then you will get a listing of all possible command/filenames depending on what the command is you are trying to do. Also, these are a few basic commands:

cd moves you into another folder.
pwd prints the folder you are in.
ls lists files and folders in the folder you are in.
rm removes stuff
mkdir makes a folder.
touch makes a file.
nano is a text editor.

You can use the man command (see my next tip) on any of these commands.

2. the command "man" (without quotes) is the "manual". type it in front of any other command to get that command's manual, for example, "man rm" would give you the manual for the "rm" command. Also, you can use the -k flag to search all of the manuals: "man -k firewall" would search all the manuals for "firewall". Very useful -- see "man man" for more 
This information is very handy for me as well. I will save them on my computer so i don't forget them. Its nice to have them explained as well i thank you for that. I notice some of the commands is the same as CMD in windows. What i like about the Terminal in linux (atleast how i have understood it) it can be one of the most important tools in Linux. Using the CMD in Windows is totally last resort :p

> 3. One thing I wanted to know is how the filesystem was setup -- which files went where. Linux uses one big virtual file system -- / (root). Every file that is read is somehow connected to root. Under root, there are the /etc, /usr, /var, /home, /dev, and /media folders, among others. The /etc folder is where all of the core system config files are. You probably don't want to fiddle too much in here for a while. The /usr folder is where programs and libraries (.so files -- the Linux version of dlls pretty much) go. /usr/bin is where most executables go, /usr/lib/ is where most libraries go, /usr/share/ is where most program data goes. System logs are in /var/logs. Your personal files and folders reside under /home. Any cds/dvds/external media that you use gets "mounted" (attached to Linux's virtual filesystem) under /media. /dev is a really cool folder, all the files in it are "block devices" basically, they can give you direct access to the hardware. This can be really useful.

I would backup all your important files, and try your best to bust Ubuntu, and then fix it. Just think of something awesome that you would love to have Ubuntu do, and then google it. Usually there is a dangerous way to get what you want, so do it 

This information is interesting. Because i have not had any clue where for example installed programs go. So by "try your best to bust Ubuntu" you mean i should mess around abit just to see how things work and what will happen? 

I also have another question. Ubuntu is open source? That is very new for me. What is open source? I know i can probably just google it but... I want to hear it from you people if you want.

> Make sure to install Ubuntu Tweak. Its an awesome addition to Ubuntu.

[http://ubuntu-tweak.com/](http://ubuntu-tweak.com/) I will make sure to check this out aswell.

And to **fballem**. Ill check you signature. I used Microsoft Office for a while. I dont like the interface on the newest releases of it. For me its messy. I have tried using Libre Office and for me its more than good enough. I think i like it better in some ways... but is it any different from Open Office?

I may have forgotten to reply to some of you I'm sorry about that. But for all the replies. Thanks for the guides, info, commands, pointers etc.

---

### Post by fballem on 2011-06-20
> **Tilith said:**
> 
I also have another question. Ubuntu is open source? That is very new for me. What is open source? I know i can probably just google it but... I want to hear it from you people if you want.

...

And to **fballem**. Ill check you signature. I used Microsoft Office for a while. I dont like the interface on the newest releases of it. For me its messy. I have tried using Libre Office and for me its more than good enough. I think i like it better in some ways... but is it any different from Open Office?


Open Source basically means that the source code is available to anyone for any purpose whatsoever. Depending on the terms of the license, this may include commercial use, although I think the Linux license is pure open source - any modifications to the core have to be contributed back to the community.

Unless you are a hardcore developer, you won't use the actual source code. In practice, there are enough hardcore developers that a lot of good work gets done. Because it is open source and so many people are working with it, it means that it is much harder to introduce viruses and other nasty bits (too many really good eyes). It is also very broadly tested.

There are some closed source bits that are not part of the Linux core (such as the nVidia or AMD video drivers), but there are open source alternatives that work well in many situations. The closed source bits use hooks that are provided by Linux to connect to the core.

LibreOffice is a fork from OpenOffice. As I understand it, it is community maintained, and happened when Oracle bought Sun. It seems to work the same as OpenOffice, and is the default office suite for Ubuntu 11.04 and for Fedora as well (probably some others too).

Glad that this was of some help,

---

### Post by dcsoldschool53 on 2011-06-20
Learning linux, I have serveral places that you can start.

Ubuntu pocket guide
1.) [http://www.ubuntupocketguide.com/index_main.html](http://www.ubuntupocketguide.com/index_main.html)
Linux commands
2.) [http://linuxcommand.org/](http://linuxcommand.org/)
Ubuntu desktop guide
3.) [http://docs.google.com/viewer?a=v&q=cache:ig17yL-nqOsJ:https://help.ubuntu.com/6.06/pdf/ubuntu/C/desktopguide.pdf+learn+ubuntu+linux+pdf&hl=en&gl=us&pid=bl&srcid=ADGEESjePGBmITFVuIPOVgH_wcSgMN0PSyUs2HgGURB5GGZN7FG4uyHXHUTTaPV-YnasyfsjBL5BWASpPlfnOuG7op0H-VyuOeJ8yPJugQNYF7riwqtgmO5INDOxx0l25POvPmqEbTKX&sig=AHIEtbRUOYBkIyiPCLeNOoxOhS0lywV61Q](http://docs.google.com/viewer?a=v&q=cache:ig17yL-nqOsJ:https://help.ubuntu.com/6.06/pdf/ubuntu/C/desktopguide.pdf+learn+ubuntu+linux+pdf&hl=en&gl=us&pid=bl&srcid=ADGEESjePGBmITFVuIPOVgH_wcSgMN0PSyUs2HgGURB5GGZN7FG4uyHXHUTTaPV-YnasyfsjBL5BWASpPlfnOuG7op0H-VyuOeJ8yPJugQNYF7riwqtgmO5INDOxx0l25POvPmqEbTKX&sig=AHIEtbRUOYBkIyiPCLeNOoxOhS0lywV61Q)
Ubuntu forum start here
4.) [http://ubuntuforums.org/showthread.php?t=801404](http://ubuntuforums.org/showthread.php?t=801404)
Gnome Library administrator
5.) [http://library.gnome.org/admin/](http://library.gnome.org/admin/)

---

### Post by Poor Android on 2011-06-20
Hello!

If you are seeking to learn more about the command shell (terminal), then I highly recommend this tutorial:

[http://linuxcommand.org/](http://linuxcommand.org/)

I'm working through it myself and I'm learning a lot! Oh, and just to make your life a little easier, the keyboard shortcut for the terminal window is control + alt + T

I much prefer using that to having to access "Applications" each and every time I need to use the terminal.

One last thing: the latest version of Ubuntu has the Unity desktop interface preinstalled. For me, and especially with respect to when I'm working through a tutorial, the GNOME or Classic Ubuntu is much more suited to my needs, namely because programs currently running are accessible via the bottom bar. (Perhaps I am ignorant, but Unity forced me to scroll over to the side every time I needed to change current programs.) If you would like, you can switch to GNOME by logging out of your current user session, changing the setting at the bottom of the login screen that says "Unity" to "Ubuntu Classic" and logging back in again.

Good luck! :)

Edit: Just noticed your last question. I fully switched to Ubuntu because Windows Vista blew up on me after months of terrible lag, freezing and generally straddling the borderline between functional and not. So, hardware intact, I installed the latest version of Ubuntu and it has been a wonderful learning experience ever since.

---

### Post by nerdy_kid on 2011-06-20
> **Tilith said:**
> 
So by "try your best to bust Ubuntu" you mean i should mess around abit just to see how things work and what will happen? 


exactly!  If you are looking for something to mess around with, then I would check out this:  [http://ubuntuforums.org/showthread.php?t=1772639](http://ubuntuforums.org/showthread.php?t=1772639)  (I can't look at that thread cause then I want to destroy my nice Unity setup)

Some of the screenies in there should make you drip with jealousy, try your hand at making ubuntu look like what you want for a start :)  You'll find yourself editing config files and tweaking the internals of Ubuntu before too long :)

---

### Post by s.fox on 2011-06-20
Hello and welcome.

You may wish to review [this]("http://ubuntuforums.org/showthread.php?t=801404") sticky for new comers. It has many useful reading materials referenced.

-s.fox

---

### Post by FormatSeize on 2011-06-20
> **Tilith said:**
> I have gotten bored of Windows and went looking for something else to do on my computer. As far as i have figured my "computing-skills" as a Windows-user wont help me out here in Linux... which isn't surprising since its two totally different OS's.
Well, kind of. Learning Linux helped me to learn a lot about computers in general. I was pretty good with computers, but toying around with Linux opened my eyes to a lot of things that are possible with computers in general, regardless of the OS. I use Windows at work, although not having administrative rights on my computer prevents me from doing things that I know I could do. 
 
> **Tilith said:**
> I want to know what i can do on Linux\Ubuntu.
1. Find some things to toy around with. For instance i cant even use the "Terminal" yet. What are my possibility? I know the "terminal" is a powerful tool in Linux and people really shouldn't "mess" around in it if they don't know what to do.
No Linux user should go about using his or her computer without using the terminal, in my opinion. Yes, it's true that you can wreak a lot of havoc by doing the wrong things in a terminal, but as a beginner, in all likelihood, you won't know what to do to screw things up (mostly). The terminal was always one of my favorite things about Linux, since to me it felt more integrated, as opposed to the Windows command line which felt like going back in time one hundred years, or the MacOS command line that feels like it's missing something. 
> **Tilith said:**
> 2. Is there anywhere i can find a very good step-by-step walkthrough about how to "make" a program... or other sorts of programming. Nothing fancy but something like and executable file which does a simple task.
It's inside of your computer. Input the following command in a terminal:
```

man bash
```
> **Tilith said:**
> 3. Where and how do i get widgets (if thats what they are called)?
[http://kde.org](http://kde.org)
 
> **Tilith said:**
> I'm a newbie as you know. I want to take my first steps towards becoming a more advanced Linux-user. 
Install VirtuaBox. Install a random Linux distribution in VirtuaBox. Break the system. Try to fix it. If you can fix it, then that means that you know a little, so then you have to break it worse. If you can't fix it, then learn how. 
 
How much you know about Linux is directly proportional to the severity of the damage that you can fix. 
> **Tilith said:**
> PS: Sorry for a big thread. Another thing i want to know is: Why did you change to Linux from Windows or Apple-OS. For me the answer would be. I want to widen my computing experience... and also i got bored of Windows.
I switched to Linux for the same reason I stopped playing Zelda games: there's is way too much baggage that is there for no other reason than The Makers Put It There. 
> **Tilith said:**
> PSS: i have also tried out and had some fun with compiz. Making my desktop look like an amusement-park is fun but... I don't really need it
You're well on your way. Compiz will break. When it does, see if you can figure out why.

---

### Post by Tilith on 2011-06-20
Sorry if my english is a bit messy sometimes. It's not my primary language.

> Open Source basically means that the source code is available to anyone  for any purpose whatsoever. Depending on the terms of the license, this  may include commercial use, although I think the Linux license is pure  open source - any modifications to the core have to be contributed back  to the community.

Unless you are a hardcore developer, you won't use the actual source  code. In practice, there are enough hardcore developers that a lot of  good work gets done. Because it is open source and so many people are  working with it, it means that it is much harder to introduce viruses  and other nasty bits (too many really good eyes). It is also very  broadly tested.

There are some closed source bits that are not part of the Linux core  (such as the nVidia or AMD video drivers), but there are open source  alternatives that work well in many situations. The closed source bits  use hooks that are provided by Linux to connect to the core.

LibreOffice is a fork from OpenOffice. As I understand it, it is  community maintained, and happened when Oracle bought Sun. It seems to  work the same as OpenOffice, and is the default office suite for Ubuntu  11.04 and for Fedora as well (probably some others too).

Glad that this was of some help,     So if i understood correctly Open Source means i can do whatever i want with the product as long as i contribute it to the community? For example make my own "version" of Ubuntu or another Open Source-program right? You mention the source code.. all programs has one right? Open Source-programs means you have access to the source code?, and modifying it means modifying the program? while closed source development (like the video drivers) doesn't give you that possibility... or legally.?


> One last thing:  the latest version of Ubuntu has the Unity desktop interface  preinstalled. For me, and especially with respect to when I'm working  through a tutorial, the GNOME or Classic Ubuntu is much more suited to  my needs, namely because programs currently running are accessible via  the bottom bar. (Perhaps I am ignorant, but Unity forced me to scroll  over to the side every time I needed to change current programs.) If you  would like, you can switch to GNOME by logging out of your current user  session, changing the setting at the bottom of the login screen that  says "Unity" to "Ubuntu Classic" and logging back in again.

Good luck! :smile:

Edit: Just noticed your last question. I fully switched to Ubuntu  because Windows Vista blew up on me after months of terrible lag,  freezing and generally straddling the borderline between functional and  not. So, hardware intact, I installed the latest version of Ubuntu and  it has been a wonderful learning experience ever since.           Yeah i use the Unity Desktop. I have tried the classic look but I want to try the Unity-look some more. The GUI is a bit glitchy at times but nothing serious. Sure its a bit heavier to scroll trough programs but Im used to using Alt+Tab anyways. And i think i read somewhere that they were planning to make it faster and smoother in 11.10 or something. Its easier to navigate trough the classic-look tho in my opinion.

Windows Vista is by far the worst OS i have ever had on my computer. I found it unstable and the OS's itself was so heavy it made my computer slower in lots of ways. Windows 7 is a big upgrade but as for now i only use it to play SCII when i feel like it. I even got Ubuntu 11.04 up and running on my laptop now too. 

> exactly!  If you are looking for something to mess around with, then I would check out this:  [http://ubuntuforums.org/showthread.php?t=1772639](http://ubuntuforums.org/showthread.php?t=1772639)  (I can't look at that thread cause then I want to destroy my nice Unity setup)

Some of the screenies in there should make you drip with jealousy, try  your hand at making ubuntu look like what you want for a start :smile:  You'll find yourself editing config files and tweaking the internals of Ubuntu before too long :smile:I will try to mess around things abit. I will also install Virtualbox as **FormatSeize** said and do it in there i think. Sounds a bit safer as well. Hehe.. i cant help but to feel a bit excited. Some of the screenshots on the thread you posted nerdy_kid looks very tempting. If i will be able to do stuff like that after a while.. i just cant wait to start.

> 
Well, kind of. Learning Linux helped me to learn a lot about computers  in general. I was pretty good with computers, but toying around with  Linux opened my eyes to a lot of things that are possible with computers  in general, regardless of the OS. I use Windows at work, although not  having administrative rights on my computer prevents me from doing  things that I know I could do. 
 
No Linux user should go about using his or her computer without using  the terminal, in my opinion. Yes, it's true that you can wreak a lot of  havoc by doing the wrong things in a terminal, but as a beginner, in all  likelihood, you won't know what to do to screw things up (mostly). The  terminal was always one of my favorite things about Linux, since to me  it felt more integrated, as opposed to the Windows command line which  felt like going back in time one hundred years, or the MacOS command  line that feels like it's missing something. 

I switched to Linux for the same reason I stopped playing Zelda games:  there's is way too much baggage that is there for no other reason than  The Makers Put It There. 
     
I understand what you mean but feeling more integrated with the system using the Terminal. i get the feeling that you are actually using the computer in a more direct way rather than just clicking on alot of shortcuts. Now when I'm trying to install a program or something like that i always try to use the Terminal before dragging myself to the Ubuntu Software Center. Sadly i don't always find the program i want to but mostly because of writing the wrong word. First i tried was sudo apt-get install vlc which made me very happy :D.

I see what you mean about baggage in the OS's but i don't think i will ever stop playing Zelda-games... or the last one on Wii was kind of poor tho. 

Thanks for all the help. Thanks for the links (**dcsoldschool53**) and the sticky.** s.fox** and all the others. btw i just typed in "man bash" in the terminal and.. I'm impressed stuff like this is integrated.

---

### Post by cgroza on 2011-06-20
To make programs check out bash and Python.

The first one is better for automated scripts, the second is more useful for application development and some types of scripts.

---

### Post by Tilith on 2011-06-20
I will check out python aswell. I have python pre-installed on Linux i think. Thanks :) I just have to say how satisfied i am with the replies here at this forum. I expected help but not this much.

---

### Post by nothingspecial on 2011-06-20
> **Tilith said:**
> First i tried was sudo apt-get install vlc which made me very happy :D.

Well in that case, put a video in your Videos directory and then type

```
cvlc ~/Videos/*
```

and feel even happier :p

---

### Post by Tilith on 2011-06-20
> cvlc ~/Videos/*
Yea thats pretty nice. Btw starting a movie now i noticed i have a crackling sound in my speakers. I dont get it when i use headphones. I got USBspeakers by Logitech i think they are called Z-5.. Just bad support for those kind of speakers or is it something i can do about it?

---

### Post by idoitprone on 2011-06-20
> **Tilith said:**
> Sorry if my english is a bit messy sometimes. It's not my primary language.

So if i understood correctly Open Source means i can do whatever i want with the product as long as i contribute it to the community? For example make my own "version" of Ubuntu or another Open Source-program right? You mention the source code.. all programs has one right? Open Source-programs means you have access to the source code?, and modifying it means modifying the program? while closed source development (like the video drivers) doesn't give you that possibility... or legally.?



How the GPL works is simple, you can do anything you want with the source code and not distribute as long as you keep it to yourself.

However, when you are shipping binaries, then you are forced to give source. The other party such as a friends is legally entitled to receive the source if he or she pleases.

I am not sure how charging for the program works. I know that the company can charge for the binaries as long he or she also include the source code, furthermore giving the binaries free, but charging for the source. I am not sure on the legal issues.

I know that red hat does charges for the binaries with their subscription contract and if the subscriber tries to steal their work, they are able to terminate the contract and stop sending updates which means no source code.

---

### Post by rewyllys on 2011-06-20
> **mastablasta said:**
> . . . . a cool thing you can do is create a (web)server (dont' forget to put a firewall in place for security) so you can access you computer from anywhere with your phone ;-)
Mastablasta,

This idea intrigues me.  Could you please elaborate on it a bit?, or perhaps point me to a tutorial that explains how to set up such a server?

Thanks in advance for any comments you care to make.

---

### Post by Tilith on 2011-06-20
>  	Quote:
 	 	 		 			 				 					Originally Posted by **mastablasta** 					[[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=10960236#post10960236") 				
 				*. . . . a cool thing you can do is  create a (web)server (dont' forget to put a firewall in place for  security) so you can access you computer from anywhere with your phone :wink:*
 			 		 	 	 
Mastablasta,

This idea intrigues me.  Could you please elaborate on it a bit?, or  perhaps point me to a tutorial that explains how to set up such a  server?

Thanks in advance for any comments you care to make.

indeed.. I got alittlebit confused.. Where and how do i start? XD Can you give me some pointers on how i can do it?

---

### Post by sjorsv on 2011-06-20
here is a website for some ubuntu downloads but its always better to use the software center [http://linux.softpedia.com/]("http://linux.softpedia.com/")also i am very interested in fixing and improving things but my recommendation for now is to Google everything you wanna change but 
the thing that really helped me was wine a program that allows you to run windows programs on your Linux machine or really any .exe file

---

### Post by Tilith on 2011-06-20
**idoitprone**

Okay i think i understand now. That is actually pretty nice. Could be pretty cool too contribute with something. So if i take a source from an open source-program.. and make something out of it... upgrade it in some way or make it different... I can share it with others? if they want it ofc. Just have to make sure. I said my english may be blurry. That involves reading and understanding it aswell.

if open source means; editing, sharing, creating and repairing stuff really makes me want to spend more time on my computer.

---

### Post by idoitprone on 2011-06-20
> **Tilith said:**
> **idoitprone**

Okay i think i understand now. That is actually pretty nice. Could be pretty cool too contribute with something. So if i take a source from an open source-program.. and make something out of it... upgrade it in some way or make it different... I can share it with others? if they want it ofc. Just have to make sure. I said my english may be blurry. That involves reading and understanding it aswell.

if open source means; editing, sharing, creating and repairing stuff really makes me want to spend more time on my computer.

Not actually, sharing with other people is a natural side effect of distributing the source code. The whole point of GPL is that for every program there is. The source code will be guaranteed with the program. Stallmen's protection from vendor lock in

---

### Post by zealibib slaughter on 2011-06-20
if you want widgets and want to learn at the same time i suggest checking out conky.  Its non interactive but can display just about any info you want and is only limited by what you discover when making the script files for it.  There are a few threads on here that can get you started

---

### Post by Tilith on 2011-06-21
Think im starting to get the hang of it now. Thanks for all the help people... and i will be sure to check out the widgets.. Wine is also installed now..and Virtualbox. Noticed i can do alot of havoc with it. Is there someway i can do a screenshot of my desktop? It is probably nothing good but I just want to show what i have been able to do with my desktop with all your help.

---

### Post by jerome1232 on 2011-06-21
> **fballem said:**
> Open Source basically means that the source code is available to anyone for any purpose whatsoever. Depending on the terms of the license, this may include commercial use, although I think the Linux license is pure open source - any modifications to the core have to be contributed back to the community.


Open Source can be commercial, I think your a bit confused about the nature of open source.


There is software that is only free as in speech. (meaning you can use it however you want, modify it, redistribute it, etc...) A good example would be the Linux Distribution known as Red Hat Enterprise Linux, I think it costs around $100 for a copy.

Then there is software which is free as in beer, and free as in speech. Ubuntu for example, you don't have to pay for it and you are free to use it however you want, modify it, redistribute it, etc...

---

### Post by nothingspecial on 2011-06-21
> **Tilith said:**
> Think im starting to get the hang of it now. Thanks for all the help people... and i will be sure to check out the widgets.. Wine is also installed now..and Virtualbox. Noticed i can do alot of havoc with it. Is there someway i can do a screenshot of my desktop? It is probably nothing good but I just want to show what i have been able to do with my desktop with all your help.

Press PrtSc

---

