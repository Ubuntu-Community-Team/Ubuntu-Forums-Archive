---
title: "Newbie on Ubuntu, wanna know some important things...Plz help!"
date: 2010-06-03
forum: New to Ubuntu
---

### Post by Dzaster on 2010-06-03
Hey guyz...first of all - thanks a million to all the members like y'all who've helped to create such a marvellous OS...Hats off!

Now, please help me figure out the following terms, I am really confused as I am a new migrant and am not much good at using my brains...

--repository
--.deb packages
--/etc(what does this mean and where to use it?)
--/usr

And also I know what is program files, start menu, control panel etc in Windows but don't know what are the following windows terms known as in Ubuntu, plz help :-

--where is program files located in Ubuntu?
--what IS the system of download and installing files in Ubuntu?
--what is the Registry in windows replaced by in Ubuntu?
--anyother useful thing I should know....

Plz, i tried to read stuff on other sites, but with zero understanding- so help me out, I believe in sharing knowledge so maybe I'll be able to help you guys in some way or the other...?!?!

P.S.- Would anyone like to befriend me so I can check them out when I need help?(pullleeeeeeeeezzzzzzz)

Thanks once again!

---

### Post by pk_m on 2010-06-03
[COLOR=Blue]Welcome to Ubuntu family, cool computing, Ubuntu users play with computers....[/COLOR][COLOR=Red]where as windows users, computers play with users[/COLOR]

Even i am searching for these answers but i can help you with couple of questions

what IS the system of download and installing files in Ubuntu?
[COLOR=Blue]if you are mentioning system updates then it will be done automatically.[/COLOR]
[COLOR=Blue]but usually for applications and games its ***.deb** like **[COLOR=Red]*.exe[/COLOR]** in windows[/COLOR]

what is the Registry in windows replaced by in Ubuntu?
[COLOR=Blue]there is no registry.[/COLOR]

anyother useful thing I should know....
[COLOR=Blue]make 2 partitions one /root and other /home to save all your personal documents...[/COLOR]

---

### Post by oldos2er on 2010-06-03
Most of your questions are answered here: [https://help.ubuntu.com/10.04/index.html](https://help.ubuntu.com/10.04/index.html)

A repository is a server containing package files. Ubuntu is a derivative of Debian, hence the name *.deb.

/etc and /usr are system directories. The "/" is the root directory. Your user directory "lives" in /home/user.

---

### Post by nhasian on 2010-06-03
welcome aboard!  i strongly recommend you read the book Ubuntu Unleashed 2010 Edition.  I read the previous version when i first started with Ubuntu 2 years ago and it helped immensely. 

> **Dzaster said:**
> 
--repository
--.deb packages
--/etc(what does this mean and where to use it?)
--/usr

a repository is library of software.  they contain the .deb packages which are programs compatible with debian and ubuntu.  all of your personal files are stored in /home while system wide programs are stored in /usr and settings are in /etc.


> **Dzaster said:**
> And also I know what is program files, start menu, control panel etc in Windows but don't know what are the following windows terms known as in Ubuntu, plz help :-

--where is program files located in Ubuntu?
--what IS the system of download and installing files in Ubuntu?
--what is the Registry in windows replaced by in Ubuntu?
--anyother useful thing I should know....


wow lots of questions :)  I'm sure by now you've probably figured out the "program files" is the Applications menu in the top left corner of the screen.  there is no control panel, but you can adjust system settings from System-> Administration and personal preferences from System-> Preferences.

No registry in linux.  all settings are configurable via text files. 

[Installing Software in Ubuntu]("http://www.psychocats.net/ubuntu/installingsoftware")

---

### Post by Brandel Valico on 2010-06-03
Will try and give what I can of the top of my head.

--repository
This is a collection of programs/files all stored in one spot that you can search and download from. The easy example is the software center. It is full of programs that have been verified as good and safe. (Be careful about adding third party Reps) You can look at what Reps are active by going to System->Admin->Synaptic In the window that opens click settings goto Repositories

The tabs there will show you what you have on. I for example turn on the Reps in the Update Tab. The Other Tab will show 3rd party Tab. Medibuntu is a Favorite most have there.

--.deb packages
Think .exe files. If you add .deb after most searches it will make you looking for the very and I do mean very rare times you need to install something not in the main Reps. alot easier.

--/etc(what does this mean and where to use it?)

It's in the root area of the drive. Its usually discouraged to mess around in there without better info then I can give you.

--/usr

See above for --/etc


--where is program files located in Ubuntu?
You can locate the Config files of most by opening Natulis Click Places-> Home then press CTRL+H this will show the Hidden files. Same thing Hides them again. 

If your talking about the actual physical files they are in the /usr area usually 

--what IS the system of download and installing files in Ubuntu?

 Best method is to go into the Software Center. Click Applications->Ubuntu Software Center (This assumes your using the last couple releases of Ubuntu.)

Pretty much everything there is just a click and install field trip.

You can also open a terminal and use apt-get install (program name) if it's in the Reps it will just install it. (Most Windows programs have an alternative but are called something else and work somewhat differently so don't expect to find them there. Some like skype are though)

You can also install in Synaptic from above. 

Or download .deb files and install them.

Or a few other methods also.

But for now with being new stick to the Software Center. While you do some study of your new playground then branch out.


--what is the Registry in windows replaced by in Ubuntu?
Yep no Registery that abomination is not present here. We use the Dewey Decimal System :guitar: (Joking)

--anyother useful thing I should know....

Contrary to popular belief the CLI (Terminal) is not Satan and is in fact useful and friendly once you get to know it.

---

### Post by Guy Sibley on 2010-06-03
I would like to say that I find the repository does not have at least 30% of the software i install therefore knowing to download a .deb is a very important thing.  The repositories are good, but they aren't perfect.  Therefore you are going to want to learn how to install software without using apt-get (although it is great, i relied to heavily on it at first and it was hard for me to get used to installing software w/o it.  Good luck!

---

