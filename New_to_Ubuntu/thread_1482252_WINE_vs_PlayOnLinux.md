---
title: "WINE vs PlayOnLinux"
date: 2010-05-13
forum: New to Ubuntu
---

### Post by flyfishingphil on 2010-05-13
Hope I can get answers this time. I seem to ask questions that there are no answers to, or nobody knows.

Looked at WINE and PlayOnLinux. Get the impression that POL is maybe a different/easier to use version of WINE. 

Previous questions, unanswered:

1. Do you have to install a Windough$ version (XP, Vista, 7) before you can install programs in WINE?

2. Is WINE good for anything other than games and a couple of other programs?

Regarding POL: 

1. Do you have to have any Windough$ installed to use POL?

2. Is it more versatile than WINE? (I.E. Can I use it to install/work my magellan gps & map send programs?)

Does anybody know where I can find user instructions, other than the quick glance style I've found on the site, for POL and WINE?

Are there any suggestions on other possible ways to "adapt" some of the programs I use in Vista to use them in 10.04 without having to do the VBox?

---

### Post by aloprot on 2010-05-13
Hello, I'm not an advanced gnu/linux user but I will try to help you as much as I can.
"Do you have to install a Windough$ version (XP, Vista, 7) before you can  install programs in WINE?"

No! You only need a linux distro and a wine version in oder to install your programs. Wine is not really a full emulator but a compatibility layer  providing alternative implementations of the dll that Windows programs call, and a  process to substitute for the Windows NT KERNEL.

"Is WINE good for anything other than games and a couple of other  programs?"
That was why Wine was created, to allow computer programs written for Microsoft Windows to run on Unix Like operating systems.[]("http://en.wikipedia.org/wiki/Microsoft_Windows") You can check [http://appdb.winehq.org/](http://appdb.winehq.org/) to see which applications are supported. What else do you want to do with Wine? This is its function. You can read more here: [http://en.wikipedia.org/wiki/Wine_%28software%29](http://en.wikipedia.org/wiki/Wine_%28software%29)

Regarding POL:
 "Do you have to have any Windough$ installed to use POL?"
No, pol  is an application to ease the installation of Windows applications  (primarily games) using Wine. That's all.

" Is it more versatile than WINE? (I.E. Can I use it to install/work my  magellan gps & map send programs?)"

Pol is more helpful  and I think was created to ease the users effort when installing applications using wine.  I don't know if you can install your magellan gps and map send programs. Maybe this link can help you : [http://tuxmobil.org/linux_gps_navigation_applications.html](http://tuxmobil.org/linux_gps_navigation_applications.html)


Good luck !

---

### Post by Jerry N on 2010-05-13
I don't know what a Windough$ is - did you mean Windows?  If so, no you don't have to install Windows because Wine contains the necessary components to make _some_ Windows programs work.  I don't know about POL.  The last few versions of Wine that I have tried (Ubuntu 9.04, 9.10, 10.04) installed Office 97 but Excel 97 did not work.  I have found that Codeweavers Crossover (costs a few dollars) works**much** better than Wine and that Office 97 running under Crossover performs a lot better than Openoffice.org.

Jerry

---

### Post by lykwydchykyn on 2010-05-13
Play On Linux is what we call a "front end" for Wine.  "front end" programs are just interfaces that make it simpler to control and use other programs.

In other words, POL doesn't do anything WINE can't do, it just simplifies the process for mere mortals.

Games make up a huge portion of the WINE development effort, probably because unlike utilities or productivity applications, games are not really "replaceable".  But even so, many popular productivity applications get attention from wine developers, and sometimes the collateral effect of development makes other programs work even if they aren't the focus of development.

---

### Post by jfreak_ on 2010-05-13
POL CANNOT run anything that WINE can't. It only simplifies the procedure of installing some games by autofetching libraries , etc, etc( I think). It has the added advantage of letting us choose which version of Wine we want to use a particular software with. This is because sometimes some softwares work better in an older version of Wine that a newer one.

---

### Post by flyfishingphil on 2010-05-13
> **aloprot said:**
> Hello, I'm not an advanced gnu/linux user but I will try to help you as much as I can.
"Do you have to install a Windough$ version (XP, Vista, 7) before you can  install programs in WINE?"

No! You only need a linux distro and a wine version in oder to install your programs. Wine is not really a full emulator but a compatibility layer  providing alternative implementations of the dll that Windows programs call, and a  process to substitute for the Windows NT KERNEL.

"Is WINE good for anything other than games and a couple of other  programs?"
That was why Wine was created, to allow computer programs written for Microsoft Windows to run on Unix Like operating systems.[]("http://en.wikipedia.org/wiki/Microsoft_Windows") You can check [http://appdb.winehq.org/](http://appdb.winehq.org/) to see which applications are supported. What else do you want to do with Wine? This is its function. You can read more here: [http://en.wikipedia.org/wiki/Wine_%28software%29](http://en.wikipedia.org/wiki/Wine_%28software%29)

Regarding POL:
 "Do you have to have any Windough$ installed to use POL?"
No, pol  is an application to ease the installation of Windows applications  (primarily games) using Wine. That's all.

" Is it more versatile than WINE? (I.E. Can I use it to install/work my  magellan gps & map send programs?)"

Pol is more helpful  and I think was created to ease the users effort when installing applications using wine.  I don't know if you can install your magellan gps and map send programs. Maybe this link can help you : [http://tuxmobil.org/linux_gps_navigation_applications.html](http://tuxmobil.org/linux_gps_navigation_applications.html)


Good luck !
Thanks all first. Aloprot, went back in and checked the WINE site and finally found the listing for other than the Gold, Platinum and Silver rated. Looks like that will take some time to go voer and see what all is offered and if anything is close to what I'm looking for.

Now, more questions:

When I click Applications > Wine > a "programs" box pops up, (somehow I got Serif Photo plus in there??? It may have happened when I was checking out VBox.) but I see nothing about installing programs to WINE. Is there something missing? Are there other installs needed to bring it up to full operation? How do you install anything using WINE? I may have missed them somewhere but I can't find a "users manual" on the how to's. Anybody know where that is?

There will probably be lots more questions. Hope nobody gets bored or gives up.

Thanks again

Edit note: Stopped by the Tuxmobile site and clicked on the Magellan part and I think I got an Error 404 notification. I'm not real sure because what I saw was all in Russian. Very interstink!

I went back in and did a reinstall on WINE. Now, when I click  Applications > Wine> it offers Programs, Browse C Drive, Configure Wine and uninstall Wine software. What else do I need?

---

### Post by 3rdalbum on 2010-05-14
Open a terminal and type 'wine' followed by a space, and then drag in the installer for the program you want to install:

```
wine <drag file into terminal>
```

---

### Post by Paqman on 2010-05-14
Even easier than that, just double-click on the .exe installer and Wine will do the rest. Your system is smart enough to know that it has to use Wine to open a .exe. 

For PlayonLinux you can launch the app and browse a list of software to install. It'll either download the app for you, or ask for the install disks.

---

### Post by sxmaxchine on 2010-05-14
POL uses wine
1. you dont need to install windows
2. Wine is perfect for some programs but as other programs were not made for linux systems there is only so much wine can do without making your computer windows.
regarding POL
1. You dont need windows installed but you need to have wine installed
2. I dont know what you mean by versatile, because POL is basically a GUI for wine you select the program from a list of supported programs and POL will install it and required winetricks (fonts and stuff)
 
dont know were you can find good tutorials
 
wine and POL are probably the best you will be able to get windows programs to wok on linux without virtualizing windows.
 
hope this answers your questions
 
and i assumed Windough$ meant windows

---

### Post by Dayofswords on 2010-05-14
> 1. Do you have to have any Windough$ installed to use POL?
thats it,
i'm making a list of everyway i see microsft and windows is spelt on here

---

### Post by flyfishingphil on 2010-05-14
Thanks again for the help. It's looking better all the time as far as using Wine to open some of the programs I want to use but can't figure out how. I'm still studyng the listing of what all is available in Ubuntu but have to do some "figuring out", when it comes to some of the info listed on the programs, just what does what I want to do.

Daysofwords: I started doing that years ago when I realized how much is being done by Microsoft to set everything up so you can only use their products if you use the Windough$ program. (If you pay attention to the news it wasn't very long ago there was a major court decision on that very matter.) The only real reason I continued to use it was I hadn't found any good info, aimed at those that don't tinker with the programming, regarding Linux or I would have been a user years ago.

Thanks again for the assists. I'll tinker around a bit and, if it appears to be doing what it should, I'll be back immediately to mark this as solved.

---

### Post by Nick_Jinn on 2010-05-14
Play on linux is automatic settings for wine. It uses wine but its only about 1000x better and easier than trying to manually set up wine yourself.


Play on Linux is the way to go. Whoever made that program increased Ubuntus support.

---

### Post by mom2twinzz on 2010-05-14
I use both.  For some older games (like Pharaoh) the games played on older versions of wine, but fail to work on newer versions.  POL allows older wine versions to be run parallel to the current version.  Although I would love for two of my must have programs to work on either (The Sims 2 and Legacy Family Tree) but at the moment I have a virtual box version of Windows XP Pro running just for them. :)

---

### Post by Calash on 2010-05-14
> **Dayofswords said:**
> thats it,
i'm making a list of everyway i see microsft and windows is spelt on here

LOL

Personally I think that type of misspelling makes otherwise intelligent posts look very childish.  About 1 step from crying to Linus about how Bill Gates stole your lunch money and kicked your cat.

On topic, I really like how POL creates separate wine prefixes for your applications.  I have had instances where libraries installed by one app cause issues on another.  Installed in a separate prefix this prevents this type of problem.

---

### Post by Jerry N on 2010-05-14
> **Calash said:**
> LOL

Personally I think that type of misspelling makes otherwise intelligent posts look very childish.  About 1 step from crying to Linus about how Bill Gates stole your lunch money and kicked your cat. 

[SIZE="4"]Complete agreement here!  [/SIZE]  Some of those spelling variations were cute the first time, maybe even the 2nd time, but become really annoying after the 100th or 200th time.  If people want to hate Microsoft, that's their business (I don't hate anyone!) but folks should remember that Microsoft is a major "cash cow" for a lot of states and several countries.  Taxes would go up if it weren't for the huge settlements extorted from Microsoft.  BTW, my favorite used to be "Microsquish" but I quit using that well before my first experimental Ubuntu installation.


Jerry

---

### Post by flyfishingphil on 2010-05-14
> **Calash said:**
> LOL

Personally I think that type of misspelling makes otherwise intelligent posts look very childish.  About 1 step from crying to Linus about how Bill Gates stole your lunch money and kicked your cat.

On topic, I really like how POL creates separate wine prefixes for your applications.  I have had instances where libraries installed by one app cause issues on another.  Installed in a separate prefix this prevents this type of problem.
(Misspellings also prevent "copyright" infringements)

OK. I have Wine installed and have tried to do a couple of entries but have run in to problems so, for those willing to put up with, here are some more questions:

1. Do a lot of stuff with my Magellan Explorist (save/share location info on great fishing spots) The Magellan installed in wine with no problem but can't do the MapSend Topo 3d USA installation. Reaches about 8% and up pops "Can't install drivers. Error 2". I tried installing the maps using both Autorun.exe and Startup.exe. (All I could find for info on the data) is it is Navteq Data)
   Any suggestions on how I may be able to find/get around this problem, or do I just need to give up and do "hand entries" with the POI locations?

2. Tried to install my Sony Ericsson Walkman Suite using Wine. In trying to open the readme file nothing happens and, when trying to do anything with the phone, I get the notice "Unable to mount device". Anything here anybody knows about that will make this workable? Do I need to get something like Wammu and GMobileMedia to work this properly?

3. If I can't get this stuff to work right how do I get it out of Wine Listings? Looked all over the place and find nothing regarding remove/uninstall.

I'll go get POL now and try the same installs there to see if that makes any difference. (I've notice that Ubuntu, like many other areas, fits real well with the old line: The more I learn I realize the less I know.)

**[COLOR="Red"]UPDATE[/COLOR]**OK, went in and tried downloading POL. Gave up on that. Took about 5 tries to get it to download. Went in to "first use" window and it went after updates. Just gave up and uninstalled it after setting there for about 25 minutes waiting for it to do the download updates. Appeared to be hung up about midstream similar to the way it installed. Checked internet connection everything fine there.

Using 10.04 so wondering if there's a conflict there.

---

### Post by QIII on 2010-05-14
Windows, like any other OS (including Linux distros), has its quirks, kinks and problems.

Windows is useful for those who want or need it, as is Linux for those who want or need it.  Choice is the thing.

My personal beef is with the hegemony, monopoly and strangle hold the purveyor of Windows has on the entire industry.

OEMs are forced to write drivers that work with Windows to remain alive.  When 98% of an industry is controlled by one entity, everyone else dances to their pipe.

I'm all for making money.  I'm all for good business practice.

But, like Teddy Roosevelt (a Republican, by the way), I'm death on monopoly.  It throttles innovation and forces everyone else to fall in line.

It's a little silly to greet that sort of thing by hurling childish taunts like Microshaft, Micro$oft, Windoze, Window$, Windough$ ...

The fact is that Windows is incredibly useful for some people and they certainly have the right to choose to use it.  They shouldn't, however, be forced to use it by virtue of the fact that it monopolizes the industry.

Rather than childishly peeing in the wind, we would do much better to let those around us know there are alternatives.  I'm not saying we should "evangelize" for Linux or any distro.  We can talk about Ubuntu, Gentoo or Fedora.  We can talk about OpenSolaris as a Unix distro.

Our effort would be much better spent doing that than joking among ourselves in the choir.

---

### Post by flyfishingphil on 2010-05-14
Guess I expect too much from programs. Installed Wammu and GMobileMedia and tried to communicate with my SonyEricsson W760i but to no avail. Finally contacted support at SE and was told "We don't support Linux". That's all I got when I asked if there was a forum where I might find more info. 

Tried every option available in both the Wammu and GMobile and got nowhere. Neither one would locate the phone plugged in to the usb port.

Guess I'll go ahead and enter this set of questions as solved because I can't get any of it to work.

Also, noted that when I tried to use the VBox that I got the statement that the XP was an uncertified copy, despite that it was from Micro. Really don't want to have to bounce between Vista and Ubuntu using dual boot but it looks like there isn't much choice on most of what I do.

---

### Post by Dayofswords on 2010-05-15
> **flyfishingphil said:**
> 

Daysofwords: I started doing that years ago when I realized how much is being done by Microsoft to set everything up so you can only use their products if you use the Windough$ program. (If you pay attention to the news it wasn't very long ago there was a major court decision on that very matter.) The only real reason I continued to use it was I hadn't found any good info, aimed at those that don't tinker with the programming, regarding Linux or I would have been a user years ago.



its fine that you use and and the reason behind it, when i had posted that it was the fourth variant i had seen in the last five minutes =p

> Misspellings also prevent "copyright" infringements
mear mention is fair use

---

### Post by Nick_Jinn on 2010-05-15
> **QIII said:**
> Windows, like any other OS (including Linux distros), has its quirks, kinks and problems.

Windows is useful for those who want or need it, as is Linux for those who want or need it.  Choice is the thing.

This is a very true statement.

Still, not you necessarily, but some people use this perspective to express a 'take it or leave it' response to criticisms concerning the difficulty of Ubuntu. In my opinion however, if Ubuntu's philosophy is to be the OS for 'everyone'.....people with third world education levels who dont speak english, youngsters starting out, old people who didnt grow up using electronics....when somebody tells you what would make something a lot easier you should appreciate the incite....you might not be able to relate to what a novice is going through so it helps to listen....this is assuming of course that you actually care what a novice is going through because you really do what to make Ubuntu the most user friendly system for non-geeks ever....and do it without sacrificing functionality or customization for power users.

> **QIII said:**
>  My personal beef is with the hegemony, monopoly and strangle hold the purveyor of Windows has on the entire industry.

OEMs are forced to write drivers that work with Windows to remain alive. When 98% of an industry is controlled by one entity, everyone else dances to their pipe.

I'm all for making money.  I'm all for good business practice.

But, like Teddy Roosevelt (a Republican, by the way), I'm death on monopoly. It throttles innovation and forces everyone else to fall in line.


Excellent! I agree entirely. Its horrible how they have deliberately cornered the market by making things purposefully incompatible....Its profitable but its highly unethical. 

Ans lets not forget that Microsoft is a lot friendlier to data mining for corporations and governments, develops media players that basically turn you in to the police if you play a downloaded song....even one that was from a CD that you bought in the 90s that got scratched. 

Also, while the system itself is fairly stable..fairly...Windows is based on a pre-internet security model. They have consistently been the WORST in regard to protecting you from viruses....oh, unless you GIVE THEM MORE MONEY to protect your computer with built in spyware....but if you dont shell out another 200 bucks on top of as much that you just spent on the OS, then your families computer network is going to be running like its a pentium-2 or 3.

> **QIII said:**
>   The fact is that Windows is incredibly useful for some people and they certainly have the right to choose to use it. They shouldn't, however, be forced to use it by virtue of the fact that it monopolizes the industry.
 

Absolutely.

> **QIII said:**
>  we would do much better to let those around us know there are alternatives. I'm not saying we should "evangelize" for Linux or any distro. We can talk about Ubuntu, Gentoo or Fedora. We can talk about OpenSolaris as a Unix distro.
  
  Our effort would be much better spent doing that than joking among ourselves in the choir.

I again agree totally.

I support Linux for ideological and ethical reasons....but I am not too much of a geek. Maybe I am more of a 'geek' than before I started using Ubuntu. I have gotten pretty good at adding repositories, and customizing my system in a matter of hours. I am even using the command line now.....but still....as wonderful as it is that the system has forced me to learn, I think we could deal a major blow to hegemony more effectively if just the absolute most basic features that any novice would want on the first day...if JUST that stuff worked with NO tweaking or use of the command line, I think people would be linning up to trash their old computers rather than upgrade to vista.


And to be fair, 7 is a major step up from vista or XP. Ubuntu is ready for intermediate and power users, but it wasnt really ready for novices when Vista came out....if it was, I think Linux would have claimed its place next to Windows and Mac by now. 






Back on topic. Play On Linux is awesome. I even got fallout 3 to run, though I have not figured out how to use mods. Ubuntu meets all of my needs as a user who is somewhere between a novice and intermediate. I still wish that it was as easy for the rest of my family to use.

---

