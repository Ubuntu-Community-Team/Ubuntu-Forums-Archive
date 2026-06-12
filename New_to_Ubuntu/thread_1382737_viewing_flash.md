---
title: "viewing flash"
date: 2010-01-16
forum: New to Ubuntu
---

### Post by hatridge on 2010-01-16
you tube videos are jerky. Also, if a website has an embedded video....only sound plays with no video. I have an issue with scrolling as well, being slow to react. I believe all my drivers are in order. I've tried all .sfw players including abode. Scroll bar is ok except when i come across a large website, even after page is fully loaded, my scroll sucks. Now using sfwdec to play flash files.

---

### Post by viper474 on 2010-01-16
I'd go into Synaptic and uninstall all of the flash video players you have installed.  Then I'd close Synaptic then use this command in the terminal:
```
sudo apt-get install ubuntu-restricted-extras
```

After doing that, I'd make sure you disabled Compiz if it is enabled.  It has caused weird things to happen for me in the past.  Best of luck!

Note:  You can search Synaptic for ubuntu-restricted-extras for a description.  Know what you're installing before doing so. ;)

---

### Post by hatridge on 2010-01-16
opened synaptic and searched adobe. Do I check off all search results? Total beginner here

---

### Post by Paqman on 2010-01-16
You want to make sure all your browsers are closed and uninstall swfdec and gnash, then install the restricted extras package above.

---

### Post by viper474 on 2010-01-16
Search for flash, then for those things that are marked green: right click and mark for removal.  You can find ubuntu-restricted-extras under within that search as well (hopefully).  Right click and mark for installation.  Once that is complete, apply changes.

---

### Post by hatridge on 2010-01-16
when I right click on the green, I have only two options highlighted ....unmark and properties

---

### Post by viper474 on 2010-01-16
> **hatridge said:**
> when I right click on the green, I have only two options highlighted ....unmark and properties

That means you have marked that item for installation.  Just click the Apply Checkmark on the toolbar at the top to apply changes.  Hopefully this is where you are anyway.

---

### Post by hatridge on 2010-01-16
ok done...however when entering code in terminal, I am getting a pop up about  note of removing flashybrid . That I must disable it and reboot. How please?

&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508; Configuring flashybrid &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
 &#9474;                                                                           &#9474; 
 &#9474; Note about removal of flashybrid package                                  &#8593; 
 &#9474;                                                                           &#9646; 
 &#9474; Please be warned, this package  changes the way your system behaves in a  &#9618; 
 &#9474; really intrusive way. This package is not enabled by default so it        &#9618; 
 &#9474; should not make any problems by just installing it. If you want to        &#9618; 
 &#9474; enable it, please read the documentation.                                 &#9618; 
 &#9474;                                                                           &#9618; 
 &#9474; If you want to remove this package, you should first disable it, boot     &#9618; 
 &#9474; the machine, and ONLY WHEN THE MACHINE HAS BEEN REBOOTED WITHOUT          &#9618; 
 &#9474; FLASHYBRID RUNNING YOU CAN REMOVE THE PACKAGE ITSELF. If you do not to    &#9618; 
 &#9474; do it this way, you can potentially lose data (things like configuration  &#9618; 
 &#9474; files in /etc/ will not get synced to the real drive, stay only in the    &#9618; 
 &#9474; tmpfs and lost on reboot).

---

### Post by viper474 on 2010-01-16
Uh oh...Okay, well I wasn't expecting you to be using a flash disk as a root filesystem.  I'm not too familiar with this, but you should go back into Synaptic and search for this flashybrid.  #1 Cancel its removal somehow OR #2 mark it for (re)installation.  That's my best guess.  Maybe someone else will know more about it.

---

### Post by blueridgedog on 2010-01-16
Flash performance may also be improved by turning off desktop effects.  System, Preferences, Appearance, Visual Effects then none.

---

### Post by Paqman on 2010-01-16
From that dialogue:
> This package is not enabled by default so it should not make any problems by just installing it

So unless you specifically enabled this (very obscure) package then you can remove it without any problems. I'm guessing you installed it without really understanding what it is, because it's something you'd normally have on a desktop system.

---

### Post by hatridge on 2010-01-16
it won't let me into synaptic now
Unable to get exclusive lock

This usually means that another package management application (like apt-get or aptitude) is already running. Please close that application first.


I'm lost ...nothing is open!

---

### Post by viper474 on 2010-01-16
> **hatridge said:**
> This usually means that another package management application (like **apt-get** or aptitude) is already running. Please close that application first.

The terminal command must still be trying to work.  Is your Linux installation on a Hard disk drive?  I'm just a little worried about why this package was installed in the first place.  I'd say just continue to remove it if you know you have linux installed to a HDD.

---

### Post by hatridge on 2010-01-16
yes I have a dual boot install...very new to Linux


Now I have rebooted and when trying to access synaptic I get this message

E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
it then closes

---

### Post by hatridge on 2010-01-16
ok I am progressing and have got to this message again

 Note about removal of flashybrid package                                                                                               &#9474; 
 &#9474;                                                                                                                                        &#9474; 
 &#9474; Please be warned, this package  changes the way your system behaves in a really intrusive way. This package is not enabled by default  &#9474; 
 &#9474; so it should not make any problems by just installing it. If you want to enable it, please read the documentation.                     &#9474; 
 &#9474;                                                                                                                                        &#9474; 
 &#9474; If you want to remove this package, you should first disable it, boot the machine, and ONLY WHEN THE MACHINE HAS BEEN REBOOTED         &#9474; 
 &#9474; WITHOUT FLASHYBRID RUNNING YOU CAN REMOVE THE PACKAGE ITSELF. If you do not to do it this way, you can potentially lose data (things   &#9474; 
 &#9474; like configuration files in /etc/ will not get synced to the real drive, stay only in the tmpfs and lost on reboot).                   &#9474; 
 &#9474;                                                                                                                                        &#9474; 
        

My question is...I'm not worried about removing it but how?

---

### Post by viper474 on 2010-01-16
Before we go any further, do the websites such as Youtube work correctly now?

---

### Post by hatridge on 2010-01-16
no they don't .....here is the message from you tube when trying to play video

Hello, you either have JavaScript turned off or an old version of Adobe's Flash Player. [Get the latest Flash player]("http://www.adobe.com/go/getflashplayer/").

Java is enabled....

---

### Post by viper474 on 2010-01-16
Can you open up synaptic at this point?  Search for ubuntu-restricted-extras if you can.  See if it has a green box beside it indicating that it has been installed.

---

### Post by hatridge on 2010-01-16
no i get this message
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

again... when i run this command in terminal to correct the problem i get this window in the terminal


Note about removal of flashybrid package &#9474; 
 &#9474; &#9474; 
&#9474; Please be warned, this package changes the way your system behaves in a really intrusive way. This package is not enabled by default &#9474; 
&#9474; so it should not make any problems by just installing it. If you want to enable it, please read the documentation. &#9474; 
&#9474; &#9474; 
&#9474; If you want to remove this package, you should first disable it, boot the machine, and ONLY WHEN THE MACHINE HAS BEEN REBOOTED &#9474; 
&#9474; WITHOUT FLASHYBRID RUNNING YOU CAN REMOVE THE PACKAGE ITSELF. If you do not to do it this way, you can potentially lose data (things &#9474; 
&#9474; like configuration files in /etc/ will not get synced to the real drive, stay only in the tmpfs and lost on reboot). &#9474; 
&#9474; &#9474; 
        
? now what?

---

### Post by viper474 on 2010-01-16
Does the prompt come back?  Such as:

you@yourcomputer:~$

Or does it ask you to type something to continue or neither or these?

---

### Post by arnab_das on 2010-01-16
first up install ubuntu restricted extras. next go to the adobe website and check if u can see the flash stuff on their site.

that should work, however there is definitely a problem with flash for linux. there is a solution fortunately. see this link: [http://exploreubuntu.wordpress.com/2010/01/14/the-ultimate-flash-fix-for-ubuntu/](http://exploreubuntu.wordpress.com/2010/01/14/the-ultimate-flash-fix-for-ubuntu/)

hope it helps.

---

### Post by hatridge on 2010-01-16
no i must close terminal and reopen it to get to a promt, but I do get a pop up saying that I have a process running... do i want to cancel or quit terminal

---

### Post by arnab_das on 2010-01-16
> **hatridge said:**
> no i must close terminal and reopen it to get to a promt, but I do get a pop up saying that I have a process running... do i want to cancel or quit terminal

close ur browser, type that code in the terminal. save it. and then reopen/restart ur browser.

---

### Post by hatridge on 2010-01-16
Being so new to Linux, the system that "just works"I have no important data on Linux,,Would you recommend doing a reinstall. And if I do, after updating should I not install compiz? And what about the video driver it recommends for my card. Would any of this resolve my problems.

---

### Post by arnab_das on 2010-01-16
> **hatridge said:**
> Being so new to Linux, the system that "just works"I have no important data on Linux,,Would you recommend doing a reinstall. And if I do, after updating should I not install compiz? And what about the video driver it recommends for my card. Would any of this resolve my problems.

havent u installed the video driver yet? well then u should. linux in itself is very stable. its not like windows where a minor screw up tends to call for reinstallation. so if u want, first of all install ur video driver, next install compiz (necessarily in that order, the link i gave u has loads of posts on compiz configurations) and next follow the link in the previous post and fix ur flash. i dont think there's any need for reinstallation.

btw go to System >Administration >Hardware drivers from the menu and install ut graphics/video drivers. they should be listed there. pretty easy to install.

---

### Post by hatridge on 2010-01-16
yes all drivers installed. I thought maybe I should not have.....


ok square one

closed browser
 
opened terminal

typed       
sudo apt-get install ubuntu-restricted-extras  hit enter
entered password

get the following message in terminal

E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

---

### Post by arnab_das on 2010-01-16
okay u need to close ubuntu software center/synaptic. this message is shown when there's another program installing something on ur pc.

it must be either ubuntu software center or synaptic. close it and type that again in the terminal.

---

### Post by hatridge on 2010-01-16
thats just it...there is _**nothing** _installing or open, except teminal....software center is closed when I attempt terminal

---

### Post by arnab_das on 2010-01-16
well there must be some program running in the background which is busy.

anyway 2 ways to solve it.

1. try installing ubuntu restricted extras from the synaptic

menu > system >administration >synaptic package manager > type ubuntu-restricted-extras in the search bar and install it.

2. or you can just log out and log in and type the code in the terminal. that way ur sure that all programs running in the background are closed.

---

### Post by hatridge on 2010-01-16
tried logging out ....booting up and all that good stuff


again...I'm not sure you understand what I'm trying to tell you

after login
 synaptic will not open... i get this message

Error

E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

then it_ automatically_ closes

I then proceed to termial and run the above command to "correct the problem"

I run 'sudo dpkg --configure -a

it does some stuff....working ....working.....then this message

Note about removal of flashybrid package &#9474; 
 &#9474; &#9474; 
&#9474; Please be warned, this package changes the way your system behaves in a really intrusive way. This package is not enabled by default &#9474; 
&#9474; so it should not make any problems by just installing it. If you want to enable it, please read the documentation. &#9474; 
&#9474; &#9474; 
&#9474; If you want to remove this package, you should first disable it, boot the machine, and ONLY WHEN THE MACHINE HAS BEEN REBOOTED &#9474; 
&#9474; WITHOUT FLASHYBRID RUNNING YOU CAN REMOVE THE PACKAGE ITSELF. If you do not to do it this way, you can potentially lose data (things &#9474; 
&#9474; like configuration files in /etc/ will not get synced to the real drive, stay only in the tmpfs and lost on reboot). &#9474; 
&#9474; &#9474; 
        
 No option and must exit terminal.


Nothing is open or running or installing...nothing..........    compiz is off

So again I will ask....how do I disable this flashybrid so I can remove this package

---

### Post by arnab_das on 2010-01-16
oh! now thats a problem.

okay, first make sure u have all the updates.

sudo apt-get update

are u facing this problem after u installed ur graphics drivers or were u facing it beforehand?

also, type 

gksudo synaptic

from the terminal and see if any error messages come up.

---

### Post by hatridge on 2010-01-16
same message in terminal for both commands....can not unlock...I did not have this issue before or after the driver....the issue came after I followed the introductions from this post.

I think I'll just reinstall. This is crazy. I just wanted to watch one you tube video......4 hours later.....

Question ...are all Linux operating systems this difficult? I don't understand with all the hype I have heard about Ubuntu and stability, which maybe so....but I don't understand if it is designed by all the users of the world, then why is it so difficult to use? It should be close to perfect, no?

---

### Post by arnab_das on 2010-01-16
> **hatridge said:**
> same message in terminal for both commands....can not unlock...I did not have this issue before or after the driver....the issue came after I followed the introductions from this post.

I think I'll just reinstall. This is crazy. I just wanted to watch one you tube video......4 hours later.....

Question ...are all Linux operating systems this difficult? I don't understand with all the hype I have heard about Ubuntu and stability, which maybe so....but I don't understand if it is designed by all the users of the world, then why is it so difficult to use? It should be close to perfect, no?

well first up, i think when u were following the instructions as the others gave u, at that time u must have uninstalled some vital package. that is causing the problems.

next, since nothing is working, a reinstallation is necessary. it is a fact that ubuntu is very secure, and far more stable than windows. however u cant blame the OS if you have (as is evident) accidentally removed some vital component of it (compare it to removing some vital .dll file from a windows setup).

i didnt know of the fact that you had removed flash components. as i didnt go through all the posts.

all u should have done was kept things as it is, and simply typed

sudo apt-get install ubuntu-restricted-extras

thats all. next time do just that. nothing else is needed. ubuntu is not complicated, and u shouldnt do complicated things with it if ur not sure.

---

### Post by arnab_das on 2010-01-16
the next time u install, follow these instructions:

[http://exploreubuntu.wordpress.com/2009/11/17/install-ubuntu/](http://exploreubuntu.wordpress.com/2009/11/17/install-ubuntu/)

and

[http://exploreubuntu.wordpress.com/2009/11/14/install-restricted-extras-for-ubuntu/](http://exploreubuntu.wordpress.com/2009/11/14/install-restricted-extras-for-ubuntu/)

do NOTHING else, your ubuntu will work like a breeze.

---

### Post by hatridge on 2010-01-16
No, I don't know what I'm doing, and that is why I posted in the _Absolute beginners_ forum. I expected to be treated like one. When being told to remove flash components, I didn't think twice about it because I assumed the ones giveing advice might know what they were talking about. Now I know for next time not to trust anyone? Until I have a second opinion? Or third? I am a cook. Would you like some advice on brain surgery from me? Why are people giving advice in a computer forum that don't know what they are doing? No disrepect to you at all and I thank you for your time. Question....is it advisable not to trust someone with limited beans to their credit? Say at lease 1000 beans would make someone trust worthy?

---

### Post by arnab_das on 2010-01-16
> **hatridge said:**
> No, I don't know what I'm doing, and that is why I posted in the _Absolute beginners_ forum. I expected to be treated like one. When being told to remove flash components, I didn't think twice about it because I assumed the ones giveing advice might know what they were talking about. Now I know for next time not to trust anyone? Until I have a second opinion? Or third? I am a cook. Would you like some advice on brain surgery from me? Why are people giving advice in a computer forum that don't know what they are doing? No disrepect to you at all and I thank you for your time. Question....is it advisable not to trust someone with limited beans to their credit? Say at lease 1000 beans would make someone trust worthy?

not at all. there are many experts who have joined ubuntuforums but dont really come here often. so obviously their beans would be less. also, u see ubuntu is a community driven OS. u have to trust at least someone in the community. now that something is messed up with ur OS doesnt necessarily mean ubuntuforums or the ubuntu community is useless.  since other users have a different experience.

its no problem being a beginner. i was a beginner when i started out a few years back as well! but anyway, do follow the link i gave you. it has images, screenshots. so that u know beforehand what you are expecting. now, read them and if u feel comfortable with those suggestions, go for it.

one final thing: ubuntu does take a bit of time/reinstallations to setup (i'm totally being impartial here), but believe me once its setup running it is a pleasure. there is one key thing about ubuntu, its an easy  OS provided u know what ur doing. in future simply dont do something until and unless ur sure of it.

---

### Post by arnab_das on 2010-01-16
do keep us posted about how the reinstallation went.

---

### Post by florus on 2010-01-16
Sometimes newbies feel that their problems are being ignored if they do not get an immediate reply. Unfortunately,the real experts are in limited supply and give such time as they can spare out of the goodness of their hearts, leaving it to lesser mortals to do what they can. Don't despair - reinstall from scratch. Ubuntu really does work and is well worth the learning curve. I never did come to terms with Vista, and now I am very glad.

---

### Post by viper474 on 2010-01-16
> **hatridge said:**
> When being told to remove flash components, I didn't think twice about it because I assumed the ones giveing advice might know what they were talking about.

Hey, sorry that I didn't estimate that there would be things such as this "flashybrid" already installed.  I just thought it would be better to remove other .swf players before installing, since I have had issues in the past.  With Ubuntu, there are community interactions that keep everything flowing.  Sometimes there are mistakes made.  Don't let this issue turn you off from Ubuntu and Linux.  I believe many of us go through steep learning curves if linux isn't our native background (I'm one of those, and I'm always learning).  Really sorry for the confusion, but please update us on how it turns out.

---

### Post by hatridge on 2010-01-16
Hi thanks everyone and hey, I am not discoraged at all. Not with Linux...Windows is another story. After years of Billshit , I've honestly had enough.
 When I installed Linux I was impressed. I find it somewhat easy. The only issue was that with flash. The flickering on embedded video sites was enoying and the slow scroll was equaly so.
 I will reinstall OS now, after I took a breath and ):Pmy happy medicine..... 
 
Finaly after I install Ubuntu updates and drivers you are saying ***_not_*** to install any flash plugins right?
Only enter the code provided in the previous thread?  And no compiz manager to be installed? Just stick with default metacity? Forget the desktop cube and all the bells and whistles? And Youtube will work?
Is all that correct?
 
One more thing .....may I reply to this post for further instructions or, should I make a new post?
 
Thanks again ...I'll be back!

---

### Post by hatridge on 2010-01-16
Reinstalled Ubuntu and I gotta tell ya......to call yourselves mere mortals is totally unrealistic. I bow now and thank you. I apologize for anything that may have come out wrong. I think it maybe a bit of the o Windows frustration that needs to be dusted off.
I installed that code in the terminal and it worked like a charm. Next I need the sea parted please....Monday..

---

### Post by arnab_das on 2010-01-17
good to see that it worked. well actually the ubuntu restricted package is a group of packages (as u might have noticed it downloads quite a large no of files) which contains loads of things, among them, the flash plugin.

now since everything is working fine, you can safely install compiz. a suggestion though, install it from the software center.

if you're not sure how to do it, go through this: [http://exploreubuntu.wordpress.com/2009/11/14/getting-compiz-to-work-on-ubuntu/](http://exploreubuntu.wordpress.com/2009/11/14/getting-compiz-to-work-on-ubuntu/)

it has screenshots, so you know what to expect.

---

### Post by Paqman on 2010-01-17
> **hatridge said:**
> 
I installed that code in the terminal and it worked like a charm. 

It might be handy to give a bit of background here so you can understand what's happened.

Ubuntu-restricted-extras is what we call a meta-package. It contains a lot of useful bits and pieces such as Flash and multimedia codecs that make your system a lot more usable. Ubuntu isn't able to include them by default due to licensing issues, but it's always a good idea to install them right after installing the system.

What might have scuppered your previous install was that Flashybird thing (although this is a guess). Certainly something messed up your system, and that ones does come with dire warnings that it messes with some pretty fundamental parts of the system.

Hope you enjoy your fixed system, and feel free to ask here if you need any more help.

---

### Post by hatridge on 2010-01-17
I`m trying to install java now 
When I download [Linux (self-extracting file)]("http://javadl.sun.com/webapps/download/AutoDL?BundleId=35675")  filesize:  19.9 MB from yahoo
It is asking which application I want to open it with....please help.

---

### Post by arnab_das on 2010-01-17
java is already installed if u have installed restricted extras. no need to install java separately.

click here to check if you have java:

[http://java.com/en/download/installed.jsp?detect=jre&try=1](http://java.com/en/download/installed.jsp?detect=jre&try=1)

btw, dont worry if they tell u that ur java version is old, actually the ubuntu repositories (softwares basically) are updated only when the released codecs have been tried and tested by developers, that means some of ur softwares may not be the updated/latest version, but what ur using is the 'safest' version for Ubuntu.

---

### Post by hatridge on 2010-01-17
I'll try to resolve java later but back to flash....it is working when I play a video on Youtube, the trouble comes if I go full screen, and then, Youtube player controls become slow as well as video itself seems to be jerky. When I return to normal screen from website, everything returns to normal. Also if I play a Youtube video from a non- Youtube website that has a video embedded (different size than original) I get flickering and a slow scroll on my browser. Is this something that I have missed? Perhaps tweaking my Firefox somehow? 

*note...I have not installed anything after Linux exept video driver and all updates, and finally 
sudo apt-get install ubuntu-restricted-extras

---

### Post by hatridge on 2010-01-17
I'll quote this flash fix I got from someone

  	 	 	 	 	 	  "We all know how crappy the Linux version of flash is. And the worst part is, sometimes it becomes impossible to click on flash enabled menus and options.
 Anyway, here’s the **working** fix for this bug.
 1. Open the terminal.
 2. Type:
 [INDENT]gksudo gedit /usr/lib/nspluginwrapper/i386/linux/npviewer[/INDENT] 3. Add the following line **before** the line of the last text:
 [INDENT]export GDK_NATIVE_WINDOWS=1[/INDENT] 4. Save the file and restart your browser or flash app.
 Thats it! Say goodbye to Flash woes!"
 [SIZE=3]Ok I have nooooo problem getting to step 2.[/SIZE]
Could someone please explain step 3 and 4.
I must be getting a laugh that I wouldn't already know this, but here goes
step 3  where is before the line of the last text?
And step 4
Where do I save it to?

---

### Post by arnab_das on 2010-01-18
> **hatridge said:**
> I'll quote this flash fix I got from someone

  	 	 	 	 	 	  "We all know how crappy the Linux version of flash is. And the worst part is, sometimes it becomes impossible to click on flash enabled menus and options.
 Anyway, here&#8217;s the **working** fix for this bug.
 1. Open the terminal.
 2. Type:
 [INDENT]gksudo gedit /usr/lib/nspluginwrapper/i386/linux/npviewer[/INDENT] 3. Add the following line **before** the line of the last text:
 [INDENT]export GDK_NATIVE_WINDOWS=1[/INDENT] 4. Save the file and restart your browser or flash app.
 Thats it! Say goodbye to Flash woes!"
 [SIZE=3]Ok I have nooooo problem getting to step 2.[/SIZE]
Could someone please explain step 3 and 4.
I must be getting a laugh that I wouldn't already know this, but here goes
step 3  where is before the line of the last text?
And step 4
Where do I save it to?

say there is are 3 lines of text

[b]ABCD
EFGH
IJKL[/B]

now before the last line of text means the line between EFGH and IJKL. so basically insert this line between the two.

now your output should look like

[B]ABCD
EFGH
your new text
IJKL[/B]

got it?

this is a solution for non-responsiveness of flash objects. if you havent noticed (or if you have) its quite a big problem. youtube videos get non responsive. gets difficult to pause etc. this is a fix for that.

anyway, you should implement this coz its necessary and will change your flash experience.

but the jerkiness though is really adobe's fault who dont really seem interested in developing a flawless flash for linux.

what you could do is go to [https://bugs.adobe.com/jira/browse/FP-1692](https://bugs.adobe.com/jira/browse/FP-1692) page (its from the official adobe site) and vote for this jerkiness bug, so that adobe feels the need to rectify it.

---

### Post by arnab_das on 2010-01-18
after editing the file it should more or less look like this:

#!/bin/sh
TARGET_OS=linux
TARGET_ARCH=i386
[B]export GDK_NATIVE_WINDOWS=1
[/B]. /usr/lib/nspluginwrapper/noarch/npviewer

---

### Post by hatridge on 2010-01-18
got it?.....I'm afraid not
ok, I opened terminal
I have_ one line_.....the cursor
i type
gksudo gedit /usr/lib/nspluginwrapper/i386/linux/npviewer
which still gives me one line
so i hit enter....hoping.... no...praying.... for more lines...
No more lines
I did get a pop up though, titled     npviewer (usr/lib/nspluginwrapper/i386/linux) - gedit
But nothing in it. No lines. You make it sound simple and again I apologise if its me that is sounding "simple"
But ????
Thanks for your time

---

### Post by arnab_das on 2010-01-18
well then i guess you should leave this thing aside. its not a recommended update, just that it was figured out that doing this substantially reduces flash screen freezes.

since its not working for u, i suggest you wait for a better answer here, or leave it aside.

you do have everything installed and more importantly working. so no need of doing other things if they are not working for u.

---

### Post by hatridge on 2010-01-18
thanks for all your input.
we tried

---

### Post by TBABill on 2010-01-18
If you are willing to try it, give Opera 10.1 a try. You can download it from Opera.com for Linux (deb). For me it's better with flash than both Firefox and Google, but I just downloaded an hour ago. Much less "glitchy" and scrolling is better too.

---

### Post by -kg- on 2010-01-18
> **hatridge said:**
> got it?.....I'm afraid not
ok, I opened terminal
I have_ one line_.....the cursor
i type
gksudo gedit /usr/lib/nspluginwrapper/i386/linux/npviewer
which still gives me one line
so i hit enter....hoping.... no...praying.... for more lines...
No more lines
I did get a pop up though, titled     npviewer (usr/lib/nspluginwrapper/i386/linux) - gedit
But nothing in it. No lines. You make it sound simple and again I apologise if its me that is sounding "simple"
But ????
Thanks for your time

This doesn't make sense.  The command "gksudo gedit /usr/lib/nspluginwrapper/i386/linux/npviewer", when you hit enter afterward, should give you a line that says: "Password:".  You then should type in your password (the one that you log in to Ubuntu with) and hit enter again.  BTW, if you actually have this line, don't worry that you see nothing when you type in your password.  Just type in your password and hit enter.

This *should* launch Gedit (which is a text editor under Gnome) with the file that you specified (in this case, npviewer, which is located in the subdirectory "/usr/lib/nspluginwrapper/i386/linux".  For clarity, this is the same as a sub-folder in Windows Explorer.  To find this file in Windows Explorer, you would open the folder "usr", then inside that folder open the folder "lib", etc.

The point is, you need to launch Gedit, but with root permissions, in order to edit that file.  If you're not being asked for a password on the next line down, then something is wrong.

Are you using Ubuntu (as in the Gnome Desktop GUI) or are you using Kubuntu (as in the KDE desktop)?  I read through the thread and didn't notice whether you mentioned this or not.  If you happen to be using Kubuntu, the commands would be different, and that might be the reason you can't launch the text editor with root permissions.

That's the only thing I can think of for a reason that you can't access Gedit through that terminal command.

---

