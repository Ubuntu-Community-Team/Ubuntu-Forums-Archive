---
title: "Struggle"
date: 2009-04-08
forum: New to Ubuntu
---

### Post by kenb12 on 2009-04-08
Have been trying to use Ubuntu for several days now, it is causing me an enormous amout of time trying to install programs.
Endless repetitions of the message 'That there is no application for this program'.
A simple attempt to run Google Earth, is met with all sorts of instructions from answers given on this forum.
How does one KNOW which application is necessary for EACH and every program and where/ how does one go about getting it/them. 
In my endless search I came across references to Linux Mint which comes with applications already installed, or so 'they' claim. Is this the case and is it a Distro easier for an 'Absolute Beginner' to use. 
I followed precisely the instructions to obtain Medibuntu, each and every time, Error 404.
Be interested to hear Forum Members comments,have read the Post 'I am not an idiot but Ubuntu makes me feel like one'.
There must be many new users, who just give up, which is a shame.

---

### Post by ivanvajar on 2009-04-08
I find Window's way of installing programs odd. You have Applications/AddRemove Applications for installing. Also, there is System/Administration/Synaptic Package manager. When you select a program module in them, those programs determine all the dependencies you need and install them automaticaly over the internet. Basically, what you see in those installation applications are links to installation packages. You select them, apply them and it's that simple.

---

### Post by billgoldberg on 2009-04-08
> **kenb12 said:**
> Have been trying to use Ubuntu for several days now, it is causing me an enormous amout of time trying to install programs.
Endless repetitions of the message 'That there is no application for this program'.
A simple attempt to run Google Earth, is met with all sorts of instructions from answers given on this forum.
How does one KNOW which application is necessary for EACH and every program and where/ how does one go about getting it/them. 
In my endless search I came across references to Linux Mint which comes with applications already installed, or so 'they' claim. Is this the case and is it a Distro easier for an 'Absolute Beginner' to use. 
I followed precisely the instructions to obtain Medibuntu, each and every time, Error 404.
Be interested to hear Forum Members comments,have read the Post 'I am not an idiot but Ubuntu makes me feel like one'.
There must be many new users, who just give up, which is a shame.

Ubuntu (and most other Linux distributions) use package managers.

The package manager gets it applications from a repository.

Google Earth is in a repository called Medibuntu.

This should be the only extra repository you'll ever need to install.

Then you can install all the programs in "system, administration, synaptic package manager" or "applications, add/remove".

Do you need help installing the Medibuntu repository?

If you installed it, just search for google earth in synaptic, select it and press apply.

---

### Post by Michael.Godawski on 2009-04-08
Hi and welcome kenb12,

before all else, feel free to ask every question be it a very trivial one or not. That is the great advantage of Ubuntu: namely the community which will truly assist you in all your struggles you may encounter.

A good way to get some comprehensive information is to check out the ubuntu community documentation.


[LIST]
[*][https://help.ubuntu.com/community/GoogleEarth](https://help.ubuntu.com/community/GoogleEarth)
[/LIST]
Try to follow the instructions presented there. If something goes wrong or you feel uncertain about some points ask. 

Good luck.

---

### Post by kpkeerthi on 2009-04-08
> **kenb12 said:**
> Have been trying to use Ubuntu for several days now, it is causing me an enormous amout of time trying to install programs.
Endless repetitions of the message 'That there is no application for this program'.
A simple attempt to run Google Earth, is met with all sorts of instructions from answers given on this forum.
How does one KNOW which application is necessary for EACH and every program and where/ how does one go about getting it/them. 
In my endless search I came across references to Linux Mint which comes with applications already installed, or so 'they' claim. Is this the case and is it a Distro easier for an 'Absolute Beginner' to use. 
I followed precisely the instructions to obtain Medibuntu, each and every time, Error 404.
Be interested to hear Forum Members comments,have read the Post 'I am not an idiot but Ubuntu makes me feel like one'.
There must be many new users, who just give up, which is a shame.

You may want to spend some time reading [The Official Ubuntu Documentation]("https://help.ubuntu.com/8.10/index.html") so you know your way around.

---

### Post by kenb12 on 2009-04-08
Have noted all the replies, but it is a big but, the information given in other posts to obtain Medibuntu repository have ALL failed.
sudo wget [http://www.medibuntu.org/sources.list](http://www.medibuntu.org/sources.list) etc, tried a number of them (posts info re Medibuntu). 
There is something radically wrong when the instructions posted here are not correct, this is claimed to be for 'Absolute Beginners'.
In a similar fashion I had a problem with Java.
Done the download and accepted the program, Then at the very end, there is a big OK, what on earth is one supposed to do. By sheer chance I hit the tab key (after hitting just about every key on the keyboard) when the Yes or No was able to be selected.Precise instructions should have indicated when the OK is reached to hit the Tab key.
In my opinion Absolute Beginner is a misnomer.I question whether the Posters actually 'Try' their instructions prior to posting. Looking through some of my old MS Dos 5.0 and MS Dos 6 books, the instructions are precise, so much for repeated criticisms of Windows/Bill Gates.
Purely as a Hobby/Interest I am interested in getting Ubuntu to work, have been through 3.1/95/98/XP/Vista,and Vista 7.Having built two computers I appear to be able to follow accurate instruction.

---

### Post by tarps87 on 2009-04-08
sudo wget [http://www.medibuntu.org/sources.list](http://www.medibuntu.org/sources.list) should be sudo wget [http://www.medibuntu.org/sources.list](http://www.medibuntu.org/sources.list) then the distro version.
Could you please post what version of Ubuntu you are using and also the instructions you are following

Is you are using 8.10 this should sort it
```
sudo wget http://www.medibuntu.org/sources.list.d/intrepid.list --output-document=/etc/apt/sources.list.d/medibuntu.list
```

"How does one KNOW which application is necessary for EACH and every program and where/ how does one go about getting it/them" this doesn't make any sense to me, applications and programs run on the OS if the program/application is not wirten for GNU/Linux it will not work (althought there is wine and others).

Did you succeed in installing google earth?

I try most of the commands I suggest but there a inevitably some which vary, i.e. hard drive names, users ids.

---

### Post by mkvnmtr on 2009-04-08
Try this for to enable the medibuntu repository. Google the word "medibuntu". One of the first three sites is the Ubuntu community docs instrucution for enabling the repository. Follow the instructions. You will need to cut and paste two commands in the terminal. You are done. I have done it exactly this way about ten times and it worked every time on Ubuntu distros from 6.06 up to 9.04.

When I want to install a program or do something I use the search box on the package manager. I review the results and install the programs I think will do what I want. If I am not happy with the results I uninstall and try again.

As an example: when I do an install one of the things I want is the ability to work with zip files. In the search box I type "zip". Then I review all the results and install everything I think might help me work with said files.

Seems like a pretty easy way to me but then I am just an old guy without a lot of experience on computers.

---

### Post by presence1960 on 2009-04-08
> **kenb12 said:**
> Have noted all the replies, but it is a big but, the information given in other posts to obtain Medibuntu repository have ALL failed.
sudo wget [http://www.medibuntu.org/sources.list](http://www.medibuntu.org/sources.list) etc, tried a number of them (posts info re Medibuntu). 
There is something radically wrong when the instructions posted here are not correct, this is claimed to be for 'Absolute Beginners'.
In a similar fashion I had a problem with Java.
Done the download and accepted the program, Then at the very end, there is a big OK, what on earth is one supposed to do. By sheer chance I hit the tab key (after hitting just about every key on the keyboard) when the Yes or No was able to be selected.Precise instructions should have indicated when the OK is reached to hit the Tab key.
In my opinion Absolute Beginner is a misnomer.I question whether the Posters actually 'Try' their instructions prior to posting. Looking through some of my old MS Dos 5.0 and MS Dos 6 books, the instructions are precise, so much for repeated criticisms of Windows/Bill Gates.
Purely as a Hobby/Interest I am interested in getting Ubuntu to work, have been through 3.1/95/98/XP/Vista,and Vista 7.Having built two computers I appear to be able to follow accurate instruction.

kenb12, I understand where you are coming from. My first try at Ubuntu I hated it and then when I removed it I found out I had overwritten my windows install during the Ubuntu installation. I was so mad! So I ran back to windows blaming Ubuntu for my problem. Omce back to windows I was reminded almost daily of why I had wanted to try Ubuntu in the first place. This time I did all the reading I could to familiarize myself with Ubuntu. When I thought I was schooled enough to make another go at Ubuntu i set up a dual boot process successfully because I had did my prep to insure it was successful. I haven't been frustrated since then. I have had issues but because I have continued to learn I can apply the help I find in here to solve my problems.

Linux is not windows. I had to stop holding onto the ways I did things in windows and then complaining about how Linux is different. In my case I say it was an ego thing because I prided myself on how well I knew windows but as far as Ubuntu well that is another story. Instead of feeling like I am stupid I looked at it as an opportunity to learn new things, a chance to better something I want/need to use every day-my computer. It was not that bad of a blow to accept the fact that in spite of all my knowledge of windows I was back to being a beginner with Ubuntu. Once I accepted that learning became easier and actually fun. Another motivation for me to learn new tricks is the fact that my alternative was windows. In spite of how well I knew it the reasons for me wanting to find another OS were still there-windows had not changed because of me. I needed to change or be stuck with something not totally fulfilling for me. If you are looking for a "better version" of windows I can guarantee you that you will be greatly dissatisfied. Linux is not windows. Check out this link : [http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

check out this link : [https://help.ubuntu.com/](https://help.ubuntu.com/)  pick your version then check out the two links Installing Applications and Switching From Windows.

You will only get out of Ubuntu what effort you put into learning. One must learn because it is not like windows. Which is a very good thing indeed. Good Luck!

---

### Post by Lunx on 2009-04-08
Hi Kenb12,

Sorry to hear that you're having troubles, I'm a relative newcomer to Linux and Ubuntu and I admit that sometimes I get annoyed and/or confused by some of the information found and given on the forums and other places 'round the web. One thing I've found is it is best to try and find things that are specific to the version of Ubuntu you are using, as some things change as new releases come to life, for example a Google search of "install Google Earth in Ubuntu Intrepid" will often give better results than simple "install Google Earth in Ubuntu". GE was one of the first apps I tried to install when I first came to Ubuntu about 3 months ago, nothing seemed to work and I got frustrated myself. I decided it wouldn't defeat me, so I did some more searching and found that by trying several ideas I'd found in different threads, I was able to get the medibutu repository up and running and then it was all straight forward to install GE and get it working.

I found a method that worked for me in Intrepid and then came across similar advice which I used to get it working in Jaunty. I have now installed GE in both Intrepid and Jaunty several times. Thanks goes to Philinux, another member, who posted in this thread 

[http://ubuntuforums.org/showthread.php?t=1114219](http://ubuntuforums.org/showthread.php?t=1114219)

And I added a post of my own in that thread which I've included below. I now have the latest version of GE (v5beta) installed and it works pretty well flawlessly now (apart from being able to run the "atmosphere" effect)

Hopefully following this should get it working for you

> Having torn my hair out following all the advice and mis-advice I could findon getting GE to run, I can vouch that the suggestion from Phuilinux in post #2 up there ^ is the best way of getting it installed (medibuntu repository has v5 beta ). Make sure that step one is to follow the advice about enabling the Medibutu repository

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

Then once that is done you can find the package in Synaptic and install as usual.

I have found that every version of GE I've tried runs very buggy (if at all) when first started, but have worked out with advice cobbled together from several sources how I can get it to run. First of all, if it is playing up when you first try it, close GE and then switch from Compiz to Metacity. Restart GE and it should look better but it will probably now run as if half frozen, if this is the case you need to go to View in the GE menu and disable the Atmosphere setting and now hopefully all is good with the worlds again (both your own and Google's).

And remember to switch Compiz back on after, or you'll be wondering what happened to your effects .

Real PITA needing to use work arounds like this, hope Google get their act together and get this Linux version sorted (didn't I hear half of Google staff use Ubuntu? They must staff who don't use GE...)

Good luck and hope you hang in 'coz it really does get easier with experience. I'm no computer expert, very limited in many (most) aspects and actually find I'm learning more/ understand more now that I've switched to Linux.

---

### Post by kenb12 on 2009-04-08
Have read the replies, but unable, because of shortage of time, to follow up the information given.But will try ALL !!!! later.
Regarding Tarps87 post. Yes, Google is installed (somewhere)according to Synaptic Manager, it is installed, the box is coloured.
It shows up on the Desktop,as GoogleEarthLinux.bin.When clicked the message comes up: 'There is no application installed for this file type'.
That is what I posted, regarding the word 'application'.It is a total mystery to me such a message.
Anyway,thank you all for taking the trouble to reply. My words possibly reflect my frustration. But will persevere.

---

### Post by nothingspecial on 2009-04-08
Hey kenb12, imagine how I felt when I got my first ever computer and it had Ubuntu on it. I`d never used one before. That being said in some ways it probably made it easier not being used to anything else.

Are you sure you installed the package called googleearth and not the binary files package?

I`ve just installed it using apt-get and there it is in my menu under Internet.

I suggest you use synaptic to remove what you have installed and do what I have just done seconds ago.

```
sudo apt-get install googleearth
```

Watch out though, if you install it that way you`re going to have to press tab again to accept the licence.

---

### Post by freesitebuilder on 2009-04-08
Lots of good info here on installing:
[http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php)

---

### Post by kenb12 on 2009-04-08
'Are you sure you installed the package called googleearth and not the binary files package?'

This is exactly the problem, round and round we go.
I have not the slightest idea what I have downloaded.
I went to the Google site and SIMPLY downloaded Google Earth for Linux.
How on 'Earth'(excuse the pun) am I to know which is suggested I downloaded. All I know I have GoogleEarthLinux.bin on the Desktop and as stated before it shows up in Synaptic Manager as a coloured block to show it is installed.
In the Applications:Internet it does not SHOW.
Anyway will try the other suggestions as posted when I have the time.
The other posts hinting at being a Window User, suggested as being a problem, is not,in my case. I FOLLOW Explicitly ALL INSTRUCTIONS GIVEN in this 'Absolute Beginners Forum'. From what I have discovered the instruction contents of some Posts are absolute nonsense. How this is allowed by the Moderators is a mystery, or maybe 'They' are too busy to verify posts. There is an expression regarding 'Urine Off' which I am tempted to use to some of the Posters.Possibly they are purely on an EGO trip, if so, better they go and lie down in a dark room until the urge to post such nonsense passes. 
If this criticism of the Forum (Posters)causes dismay so be it.

---

### Post by durand on 2009-04-08
[https://help.ubuntu.com/community/Medibuntu#Adding the Repositories](https://help.ubuntu.com/community/Medibuntu#Adding the Repositories)

You need to copy the relevant bit of code depending on which version of ubuntu you have. For example, if you have 8.10, the latest stable version, open a terminal **(Applications > Accessories > Terminal)** and paste this code into it:

```
sudo wget http://www.medibuntu.org/sources.list.d/intrepid.list --output-document=/etc/apt/sources.list.d/medibuntu.list
```
I got that directly from the link above. **You need to change this according to what version you have!**

You will need to enter your password though it will not show any asterisks or any recognition. Then press enter.

Next, type in: 
```
sudo apt-get update
```
This will update all the "repositories" to get the latest information about packages.

Then you can install google earth.
```
sudo apt-get install googleearth
```

When that's done, you should see it in your menu.

Just remember that ubuntu is _not_ windows and it has it's own methods of installing programs and doing things. In windows, you would get the installer from the program's website and then run that. In ubuntu, it is much easier. We have a repository with most of the applications that you may need. Synaptic and other programs allow you to simply select the program and it will be downloaded and install in one go. It will also update it in the future when a new version is out.

---

### Post by presence1960 on 2009-04-08
> **kenb12 said:**
> 'Are you sure you installed the package called googleearth and not the binary files package?'

This is exactly the problem, round and round we go.
I have not the slightest idea what I have downloaded.
I went to the Google site and SIMPLY downloaded Google Earth for Linux.
How on 'Earth'(excuse the pun) am I to know which is suggested I downloaded. All I know I have GoogleEarthLinux.bin on the Desktop and as stated before it shows up in Synaptic Manager as a coloured block to show it is installed.
In the Applications:Internet it does not SHOW.
Anyway will try the other suggestions as posted when I have the time.
The other posts hinting at being a Window User, suggested as being a problem, is not,in my case. I FOLLOW Explicitly ALL INSTRUCTIONS GIVEN in this 'Absolute Beginners Forum'. From what I have discovered the instruction contents of some Posts are absolute nonsense. How this is allowed by the Moderators is a mystery, or maybe 'They' are too busy to verify posts. There is an expression regarding 'Urine Off' which I am tempted to use to some of the Posters.Possibly they are purely on an EGO trip, if so, better they go and lie down in a dark room until the urge to post such nonsense passes. 
If this criticism of the Forum (Posters)causes dismay so be it.

Kenb12 it is pretty hard to ask someone for help and discredit them at the same time. I understand your frustration, but some things are better left unsaid. I have never used Google Earth on Linux. Tried it in Windows but had no real use for it. Therefore I know nothing about it. I can tell you this- everyone who posts has the intention of helping you. The problem is they are not there on your machine with you to see everything you may or may not have done. By your own admission you have not the slightest idea what you have downloaded! You say you downloaded it from google's site and it is installed in Synaptic. Is there any chance you installed both versions? I know with flash and java sometimes you need to uninstall all other instances before installing a new one.

I can tell you that cooler heads will prevail. This is not tech support that is paid for, everyone here does it on their own time. Paid support techs have to put up with the abuse & BS, volunteers do not. To basically trash those trying to help you is not conducive to either your cause or anyone else's. The posters are trying to help you as best they can. Sometimes it can take a tremendous amount of fiddling to get one thing to work in Linux. On my first install that worked it took me over 3 days to get compiz running correctly and working on bootup. Now because of that experience I can do it right in no time. 

Maybe a break from this particular problem is in order and try tackling it when more refreshed and peaceful. I hope you stay on here and stick it out. My biggest problems in Linux required some work, but the knowledge gained is all worth it. Nothing worthwhile in life is easy.

P.S. on a personal note nothing a newbie says in here really upsets me. My pet peeve is when some older members get arrogant with noobs. But you know that is my stuff that I need to work on. Why does that bother me?

---

### Post by CRIMPS on 2009-04-08
> **presence1960 said:**
> Kenb12 it is pretty hard to ask someone for help and discredit them at the same time. I understand your frustration, but some things are better left unsaid. I have never used Google Earth on Linux. Tried it in Windows but had no real use for it. Therefore I know nothing about it. I can tell you this- everyone who posts has the intention of helping you. The problem is they are not there on your machine with you to see everything you may or may not have done. By your own admission you have not the slightest idea what you have downloaded! You say you downloaded it from google's site and it is installed in Synaptic. Is there any chance you installed both versions? I know with flash and java sometimes you need to uninstall all other instances before installing a new one.

I can tell you that cooler heads will prevail. This is not tech support that is paid for, everyone here does it on their own time. Paid support techs have to put up with the abuse & BS, volunteers do not. To basically trash those trying to help you is not conducive to either your cause or anyone else's. The posters are trying to help you as best they can. Sometimes it can take a tremendous amount of fiddling to get one thing to work in Linux. On my first install that worked it took me over 3 days to get compiz running correctly and working on bootup. Now because of that experience I can do it right in no time. 

Maybe a break from this particular problem is in order and try tackling it when more refreshed and peaceful. I hope you stay on here and stick it out. My biggest problems in Linux required some work, but the knowledge gained is all worth it. Nothing worthwhile in life is easy.

P.S. on a personal note nothing a newbie says in here really upsets me. My pet peeve is when some older members get arrogant with noobs. But you know that is my stuff that I need to work on. Why does that bother me?

I second this ;)  Remember, also, that nobody here has been forced into Linux, that we all use linux because we want to.  the community here is awesome!  Help us help you.  Just take your time and tell us what the problem is.

---

### Post by tarps87 on 2009-04-09
For google earth first try
```
googleearth
```
If this does not work it is not installed correctly so remove it
```
sudo apt-get remove googleearth
```
Now as from what I've read I believe you have already download google earth which is a .bin file. The chances are this file does not have permission to execute, this would explain the error message.
First open the terminal and assuming the file is on your desktop
```
cd ~/Desktop
chmod a+x GoogleEarthLinux.bin
sudo ./GoogleEarthLinux.bin
```
Don't change the default value just click begin install, when finished click exit
Now type```
googleearth
```
There will also be a short cut in the applications menu.
(All commands are case sensitive)
I have just tried this with the latest GNU/Linux installer and it works.
The information is also available in the community documentation
[https://help.ubuntu.com/community/GoogleEarth](https://help.ubuntu.com/community/GoogleEarth)

---

### Post by Michael.Godawski on 2009-04-09
Thank you tarps87 for posting the instructions how to install .bin files.

Installing new software in Linux is different than in Windows or any other operating system, but it is not more complicated. Everything what we have done for a long time becomes a habit, we do it automatically.

But when we are forced to break out of the routine, it gets tricky. Because we have to change our thinking. 

Here some useful guides how to install all sorts of different applications in Ubuntu:

[LIST]
[*][https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)
[*][http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)
[*][http://zenlife.comze.com/2009/04/ubuntu-software-installation-guide/](http://zenlife.comze.com/2009/04/ubuntu-software-installation-guide/)
[/LIST]
Please also try to remain calm. I know Ubuntu may be a beast.

---

### Post by nothingspecial on 2009-04-09
I`m not trying to do anything else but help you. :D

You`ve got to read what people are posting. All the links in this thread are valuable stuff. People make mistakes sometimes but I have rarely found instructions in these forums to be wrong.

It`s no good just blindly copying and pasting.

You have been shown a number of times how to correctly add medibuntu to your sources.

You have also been shown correctly in a number of different ways how to install google earth. I suggest forgetting  everything else and using these instructions from durand


> You need to copy the relevant bit of code depending on which version of ubuntu you have. For example, if you have 8.10, the latest stable version, open a terminal (Applications > Accessories > Terminal) and paste this code into it:

:```


sudo wget http://www.medibuntu.org/sources.list.d/intrepid.list --output-document=/etc/apt/sources.list.d/medibuntu.list
```

I got that directly from the link above. You need to change this according to what version you have!

It might be an idea to do ```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```

> You will need to enter your password though it will not show any asterisks or any recognition. Then press enter.

Next, type in:
```

sudo apt-get update
```

This will update all the "repositories" to get the latest information about packages.

Then you can install google earth```


sudo apt-get install googleearth
```

---

### Post by Mortus Pryde on 2009-04-09
> **nothingspecial said:**
> I`m not trying to do anything else but help you. :D

You`ve got to read what people are posting. All the links in this thread are valuable stuff. People make mistakes sometimes but I have rarely found instructions in these forums to be wrong.

It`s no good just blindly copying and pasting.

You have been shown a number of times how to correctly add medibuntu to your sources.

You have also been shown correctly in a number of different ways how to install google earth. I suggest forgetting  everything else and using these instructions from durand




It might be an idea to do ```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```

That is a great summery of the thread! Will have to look back here when I get home.

kenb12, I greatly suggest you look at the Free Beginners Guide, you may find you understand things a little better. Print it out if you have to, though I suggest if you favor trees and do not have a duplexing (Two Sided Printing) printer at home like I do printing it at work if they have one there as it is 170 pages. As geeky as I am, I still like to ave hard copies especially for computers of things I may need to referance documentation for that is away form a computer. ;) Yes I am a guy who reads manuals. LOL

I myself have been working with Ubuntu for a week, I have read many confusing instructions both here and elsewhere on the internet, namely due to the shear scope of meathods and experiance levels they were written for. Finally I stumbled across what I later discovered is refured to as the Unofficial ATI Wiki and it had a useful step by step guide to installing ATI drivers including the meathod I needed for my tempermental T42 so I could make use of 3D Exceleration.

---

### Post by kenb12 on 2009-04-10
I have not tried all the suggestions posted regarding getting Google Earth to work. Quite frankly I have had such a sickner I don't feel like going down that road again.The time wasted, was incredible trying to make the 'bad' entries (as posted by various contributors)into Terminal.
Will try the advice given in this 'Struggle' thread, for which I thank you.  As far as actually using Google Earth. It is purely to try Ubuntu effectiveness. I have three computers, twelve hard drives, and Google is on most of them through Windows  (every version from 95 up to Win7 Beta)Still have some 7 floppies with Windows 3.1 on them, kept for old times sake!!!!!!!!.
Again, thanks for your time taken in replying to my (rant)posts.
Pushed for time at present but WILL try all suggestions, time allowing.
The Book 'Ubuntu Pocket Guide and reference' arrived from the States yesterday so will have a look at that.
Again, many thanks for your time, I have sort of cooled down, steam has stopped coming out of my ears!!!!!!.
Having bought the above, and also Ubuntu Linux for Dummies, I am serious in trying to use Ubuntu.Cheers.

---

### Post by Mortus Pryde on 2009-04-10
> **kenb12 said:**
> The Book 'Ubuntu Pocket Guide and reference' arrived from the States yesterday so will have a look at that.

Having bought the above, and also Ubuntu Linux for Dummies, I am serious in trying to use Ubuntu.Cheers.

LOL Well I guess that is an advantage to me prefering the "Cheaper than laser" business inkjets, I printed and bindered my own copy. LOL Thats just me though... If I didn't I would have no use for a printer.

Glad to hear you are traying, took me a lot of reading, trying, reading and trying to get a 3D Accelerated driver to install for my Radeon Mobility 9600. About 10 attempts to be exact so I know your pain.

Anyway will try to install GoogleEarth myself and see if I can help you out one newbie to another. ;)

---

### Post by pbpersson on 2009-04-10
> **kenb12 said:**
> 
I went to the Google site and SIMPLY downloaded Google Earth for Linux.
How on 'Earth'(excuse the pun) am I to know which is suggested I downloaded. All I know I have GoogleEarthLinux.bin on the Desktop and as stated before it shows up in Synaptic Manager as a coloured block to show it is installed.

I don't know if anyone has mentioned this in this thread, but there are different ways to install things - the Ubuntu way and the manual way.

When you go into the Synaptic Package Manager you are viewing thousands of applications developed by companies all over the world.  If you ONLY use this method of installing software, you have the following advantages:

1.  You can search on and view all the details for each package
2.  All the dependencies for the package will be automatically installed for you
3.  You will automatically receive regular updates for the package when they are released
4.  All the details of the installation will be handled automatically, including the addition in the menu system

Now, if you manually go to the web site of the company who created the software and get a .BIN file:

1.  You need to follow their installation instructions which is different for each piece of software
2.  You might not have the dependencies installed so the software might not function
3.  It might not add the software into your menu system and you will not know how to run it
4.  You  will not get any updates
5.  You will need to follow their instructions to uninstall it

Therefore, it is generally recommended to NEVER go out to a web site and download software - that is way too much work.  You should only do this if the software is not in the Ubuntu repositories.

Had you gone through with your plans to run the .BIN file you might have installed two competing versions of Google Earth.

---

### Post by candtalan on 2009-04-10
> **kenb12 said:**
> 'Are you sure you installed the package called googleearth and not the binary files package?'

This is exactly the problem, round and round we go.
I have not the slightest idea what I have downloaded.
I went to the Google site and SIMPLY downloaded Google Earth for Linux.

Welcome! and sorry to hear you are having problems.

(please note that I found some bad news see at the end) 

What you did was a natural action after using Windows for a long time. Windows users are downloading exe files from all sorts of places all the time, and Windows is arranged for these to work. It also is pretty easy for stuff you do not want, like malware and viruses.

It is unusual for Ubuntu users to do what you did, download from somewhere outside of Ubuntu. The usual thing is to use either the facility
Applications> Add/Remove
or for more general applications or packages or libraries etc etc use
System>Administration>Synaptic Package Manager

Please note that these list the contents of Ubuntu and other 'Repositories' of software which has either been checked out for Ubuntu or is believed to be suitable in most ways. the Repositories contain information which is specific for your version of Ubuntu.

When first installed, Ubuntu has links to the basic repository. It is easy to add to include the wider ranging repositories (Universe and Multiverse). However, such things as google earth (a completely proprietary item) are conveniently held in a special repository named medibuntu. There are legal reasons why medibuntu is not included in the original Distribution and it means you arrange to use it yourself.

You need to be sure that you know that medibuntu repository is installed, and if it is not, then how to install it.

When it is installed, you will see it available in 
System>Administration>Synaptic Package Manager
I hav ejust done this and I marked it for install, and when applied, I saw three files download and install. I then went to 
Applications>Internet>Google Earth and I would expect it to run.

All good so far? I hope so. 

Bad news:
There is bad news here though. My own trial described above showed that my google earth does not run. A message appears from google that I have an outdated version. This is an example of what can happen with proprietary software unfortunately. It is hard to keep the repositories of closed software up to date I guess.
For reference I am using Ubuntu 8.04.2

Plan 'B' would be to also do as you seem to have done which is to download a binary file direct from Google.com itself. However, this means you will be using linux experience to manage what then needs to be done. In brief, the downloaded binary (.bin) file must be set as being executable, then it can be run using the command
./

hope that helps a bit?

---

### Post by pbpersson on 2009-04-10
It runs fine on Intrepid 8.10

I did not the first time I attempted to run it but it worked the second time

What an awesome program!

It wanted me to upgrade to a newer version but I ignored that prompt

---

### Post by kenb12 on 2009-04-11
Most kind of you all in posting. I really appreciate your efforts.
The overall consensus seems to be to 'Get Hold' of Medibuntu, as a starting point.
Will take the indicated steps (as posted)to obtain it, as soon as possible.
At least, none of you have told me to pick up the dummy that I spat out! for which I thank you.
Will return to this thread and let you all know, how I got on.
Many thanks again.

---

### Post by kenb12 on 2009-04-13
As promised, I managed to download and get GooglEarth working.
Following the instructions given by you all, it worked like a charm. The only 'little' problem was the GPG key, which I had and typed in.
Bravely!!! I did download the Google update and that went in OK.
As a point of interest,in the two books bought 'Ubuntu Linux for Dummies' and 'Ubuntu Pocket guide and Reference', I could not see any reference to 'Medibuntu' so effectively I would still be 'tearing my hair out' without the aid of all your invaluable help.
(The Poster who commented re downloading and printing the above Pocket Guide against buying it, maybe I am a MP and could get it on expenses or at least for my second home!!!!!!!!!!!!!).
A sincere, big thank you all for bearing with me,and giving up your time in posting your helpful advice with such good graces.
Thanks.

---

### Post by 3rdalbum on 2009-04-13
I'm glad you got everything working, and I'm sorta surprised none of the books mention Medibuntu. I know it distributes libraries that are regarded as "possibly illegal" in some parts of the world, but after all you don't need to download those libraries.

---

### Post by Lunx on 2009-04-13
> **kenb12 said:**
> As promised, I managed to download and get GooglEarth working.
Following the instructions given by you all, it worked like a charm. The only 'little' problem was the GPG key, which I had and typed in.
Yay, perseverance leads to success :)

> 
As a point of interest,in the two books bought 'Ubuntu Linux for Dummies' and 'Ubuntu Pocket guide and Reference', I could not see any reference to 'Medibuntu' so effectively I would still be 'tearing my hair out' without the aid of all your invaluable help.

Not sure why they don't make more mention of what's available through Medibuntu, I guess it's cause some stuff like GE isn't exactly Open Source. Seems odd though, since I imagine most users would enable it.

> 
A sincere, big thank you all for bearing with me,and giving up your time in posting your helpful advice with such good graces.
Thanks.

Glad to see you finally got the answers you were after, forum is useful for that :lolflag:

---

### Post by nothingspecial on 2009-04-13
Glad you got it sorted. :guitar:

---

### Post by kenb12 on 2009-04-21
A further, further 'Feed Back' just in case you 'Helpers' return to this thread.
Getting into the swing of things with Ubuntu now, have installed it on three of my HDs and installed Medibuntu also.(so have got Google earth on them) :)
I really don't know how I would have managed without your tremendous help for which I am very, very grateful.
Really enjoying the learning process of Linux after the rather boring (lately) years with Microsoft,must be fair and say,they have produced some marvellous programs.
Thanks again to you all.
kb

---

