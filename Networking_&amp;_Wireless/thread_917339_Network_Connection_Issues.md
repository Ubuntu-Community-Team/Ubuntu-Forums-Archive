---
title: "Network Connection Issues"
date: 2008-09-10
forum: Networking &amp; Wireless
---

### Post by mackay12 on 2008-09-10
Ok I now have a USB Wireless Lan, I need to know if it will work and what I have to do to get it to. Also the WINE program doesn't work. I downloaded the .dep to my computer and it gets an error. i got all the versions but I got the same thing. Please Help. 

The adapter is the *BUFFALO WLI-US-KG54-AL Wireless LAN Adapter*

---

### Post by Panzor on 2008-09-10
Umm, for wine, I would suggest just doing "sudo aptitude install wine" and see the errors (if there are some) when you type "wine" at a terminal prompt. 

Have you tried the wireless adapter yet? The majority of things work. I would just test it and see. Sorry if you've already tried it, it didn't sound like you had.

---

### Post by lilmale1 on 2008-09-10
uname -m

try that and it will tell u If the output is 'i686' (or possibly 'i586' or 'i486' on older machines), you have a 32-bit kernel; if it's 'x86_64,' you're using 64-bit. If the output is anything else, you don't have an x86-compatible processor and you can't use ndiswrapper (because Windows doesn't support platforms other than x86)

this will tell you what kind of machine you got

from there we will install wine

and then ur usb from wine, wine can also come in diffent system types
so just get the system type and i will find you the deb for wine

---

### Post by mackay12 on 2008-09-11
Ill try the things. but ill say something. My USB one is a Grey for supported in the thing for finding out if it is or not, ill look up the wireless network card now.

It says its Yellow, so Im not sure if its supported or not.

---

### Post by mackay12 on 2008-09-11
Ok my computer is a i686. But the Wine archives only have the i3 something, what now.

---

### Post by mackay12 on 2008-09-11
Come on guys dont ignore me.

You guys are ignarent, stop being an *** and help me. (sorry to say that but its been like ages. I have seem threads newer than mine and they get help straight away)

---

### Post by mackay12 on 2008-09-11
please help.

---

### Post by mackay12 on 2008-09-11
Ok I just need someone to give me the dep archive of wine for a i6xx system. I require this for to install my network card drivers. Please help.

---

### Post by mackay12 on 2008-09-12
Ok I'll post one more time and if I get no help again, this proves that this forum support sucks. I have posted 3 times, past 2 have gotten no replies. and to make it worse, I reply saying please help soon. But then threads made straight away get help. You are all shocking for ignoring a person who needs help.

**Issue:**
I need help, I need to know how to get it to work. I have a Belkin Wireless g54 Network Adapter. Aparently it should work, it has yellow for supported drivers. I also need the dep package of Wine for a i6xx computer. 

Now please for the last time, dont be selfish and ignore me. I need Ubuntu to work. Windows Sucks Balls!

---

### Post by adewale on 2008-09-12
To get wine package why not go to packages.ubuntu.com or wine HQ. 
I don't use wireless so i don't know much about it ;but i guess you could try restricted manager and if that doesn't work then what you need is ndsiwrapper .
There could be several reasons why no one responded to any of your threads(for instance am just seeing it now), but falsely accusing people isn't good. 
Am yet to come across 'selfish' people on this forum. I've met people here who are very selfless. Why would someone develop a software just so others can use it freely? is that being selfish? That selflessness. That's what ubuntu is about. 

Take care.

---

### Post by stone@bruti on 2008-09-12
seeing the quality of the replys here, i find that this forum is far from "shocking"... it somtimes takes time for people to understand the requests or the questions are a bit hard for some (i know that many questions have got me googling for ages ...)

for a quick deb for wine (or any prog), i tend to look at getdeb.net

[http://www.getdeb.net/app/Wine]("http://www.getdeb.net/app/Wine")

or as adewale said, try the official site, if you can't get a deb then they probably give instructions on how to install.
if not an "apt-get install wine" or Synaptic will probably get you wine a lot quicker.

for your belink, not so easy since I tend to stick with atheros based chipsets. I would bet on NDISwrapper to get it working.
A few links that a lucky google search got me :

[http://ubuntuforums.org/showthread.php?t=187004]("http://ubuntuforums.org/showthread.php?t=187004") (Hmm that shocking forum again ......)

[http://www.gidforums.com/t-4390.html]("http://www.gidforums.com/t-4390.html")

[http://ndiswrapper.sourceforge.net/joomla/]("http://ndiswrapper.sourceforge.net/joomla/")

good luck and don't forget to post a bit of info if you manage to get it working, Free software is all about sharing after all !

Stone

---

### Post by mackay12 on 2008-09-12
Thanks, but as I said I need the i6xx they only suply the i3xx version. So I cannnot get this. And what I need now is the drivers for my card. they only come in a exe so thats why I need Wine.

---

### Post by Lizard_King on 2008-09-12
I think the reason Noobs like you and I are having so much trouble getting help is because members who *can* help don't visit the "Noob" section.

I've had to reinstall Ubuntu twice in the past three days because a member thought it would be cute to give me bad advice.

---

### Post by Therion on 2008-09-12
> **mackay12 said:**
> Now please for the last time, dont be selfish and ignore me. I need Ubuntu to work. Windows Sucks Balls!
One search on Google took me to a [solution](http://www.gidforums.com/t-4390.html).

---

### Post by KOld Iron on 2008-09-12
> **mackay12 said:**
> Thanks, but as I said I need the i6xx they only suply the i3xx version. So I cannnot get this. ...

Well, if you would have followed the link by
> **stone@bruti said:**
>  ...for a quick deb for wine (or any prog), i tend to look at getdeb.net

[http://www.getdeb.net/app/Wine]("http://www.getdeb.net/app/Wine")
then you would have found that there is also a link for the Ubuntu Hardy 64 bits version!

---

### Post by mackay12 on 2008-09-12
I did it, didn't work. Every wine deb package i get no matter which version, has an error in the deb, something to do with the version or something.

And this aint the noob area.

---

### Post by mackay12 on 2008-09-12
I will just say this, can anyone sugest a network card that is in ubuntu by default without need to install anything. And Ubuntu should come with Wine in future releases, dunno why they havent yet.

---

### Post by rustybronco on 2008-09-12
> **mackay12 said:**
> Ok I'll post one more time and if I get no help again, **this proves that this forum support sucks**. I have posted 3 times, past 2 have gotten no replies. and to make it worse, I reply saying please help soon. But then threads made straight away get help. You are all shocking for ignoring a person who needs help.


> **mackay12 said:**
> Ok I have an Orange Livebox, but how do I use it with Ubuntu. It on windows uses and install or it wont work, but Ubuntu wont start any exe's. Please Help. and if i cant use it then **yous arent as good as i thought**, and I thought Ubuntu was the best.

it may help to be polite.

**is your wireless card a usb stick or a pcmcia card or an internal card? **

this post should help you get started finding the chipset of your device.
[http://ubuntuforums.org/showthread.php?t=596797](http://ubuntuforums.org/showthread.php?t=596797)

---

### Post by TSupra88 on 2008-09-12
mackay do you prefer italian or mexican food? I like italian because of the pastas and sauces used, but I also like mexican because it tends to be spicy and I'm a fan of spicy foods.

---

### Post by issih on 2008-09-12
.debs being broken is not something the users here can necessarily help with. Wine should not be included by default, it is a package that is installable quite happily as a seperate download, and believe it or not, some people don't want to run windows apps..just because you want it doesn't make it necessary.

For future advice about i686 debs as you put it, I suggest you post in the 64 bit forum, those guys will be more likely to know what is working and what isn't, this is assuming you are sure you are running the 64 bit version, both 64 bit and 32 bit will run on basically all processors these days, so you need to be sure.

You do not need wine to solve your problem, the link already posted looks very hopeful. and can solve the issue quite happily without any need for windows.

This page is also probably very useful:

[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

Finally, calm down, this isn't paid support, it isn't anybodies job to help you out, and there is no guarantee that people who know how to solve your exact problem are online to see and help at the right moment...this forum is NOT a support helpdesk, and acting as if you deserve something is frankly very rude.

Everyone here is just a user, and any help you get is kindness, it is not selfishness if you don't get help immediately, people are busy and have their own problems, be reasonable

---

### Post by stone@bruti on 2008-09-12
Right lets try to get things cleared up a bit here

> **mackay12 said:**
> I will just say this, can anyone sugest a network card that is in ubuntu by default without need to install anything. And Ubuntu should come with Wine in future releases, dunno why they havent yet.

I tend to stick with atheros based cards and my personal favorate is the PCMCIA D-Link DWL-G650. works out of the box and has easy to configure drivers (madwifi and the new ath5k) which enables wifi security testing.
to install wine, open a terminal and type :
"sudo apt-get install wine"

pesonaly I'd rather type a line and wait 30 seconds download if i need it than having somthing that loads my system with junk that I won't use (one of the reasons I abandond windows 3 years ago)

> **mackay12 said:**
> I did it, didn't work. Every wine deb package i get no matter which version, has an error in the deb, something to do with the version or something.

And this aint the noob area.

Stange, could be that you have dependancy problems, the apt-get install should take care of that.

> **mackay12 said:**
> Thanks, but as I said I need the i6xx they only suply the i3xx version. So I cannnot get this. And what I need now is the drivers for my card. they only come in a exe so thats why I need Wine.

Umm lets not go too fast here, are you confusing i386, i686 and a 64 bit processor (x86_64)

[http://ubuntuforums.org/archive/index.php/t-711289.html]("http://ubuntuforums.org/archive/index.php/t-711289.html")

to stay simple then there is no difference between i386 and i686 for the soft you install since they are both 32 bit architecturs (Hmm getting a bit late, my spellings a bit dodgy, sorry !!)

google and wikipedia will be able to explain the difference between i386 i686 32 bit an 64 bit processors better than me !


go back to this post
[http://ubuntuforums.org/showthread.php?t=187004]("http://ubuntuforums.org/showthread.php?t=187004")

at the end of the post, you have a tar file (like a zip file but for linux) with the drivers to compile in ndiswrapper.

good luck

Stone

---

### Post by mackay12 on 2008-09-12
Got some good news. I got a USB card that as soon as I plugged in got suported. YEPI!!! But It detects my Livebox, but when I click on it and put in the key it usaly does nothing, or mostly my entire Linux freezes. I can't even open or close my cdrom.

I need to get linux on the internet soon, Windows has 20 days till it expires.

---

### Post by mackay12 on 2008-09-12
> **TSupra88 said:**
> mackay do you prefer italian or mexican food? I like italian because of the pastas and sauces used, but I also like mexican because it tends to be spicy and I'm a fan of spicy foods.

What has that got to do with anything. But I would say Mexican, all the way. Spicy Foods RULE!

---

### Post by mackay12 on 2008-09-12
> **rustybronco said:**
> **is your wireless card a usb stick or a pcmcia card or an internal card? **
I have two, one in the computer is a PCI and the one that I got working is a USB, so lets go with the USB. Its made by LM Technologies.

---

### Post by stone@bruti on 2008-09-12
> **mackay12 said:**
> Got some good news. I got a USB card that as soon as I plugged in got suported. YEPI!!! But It detects my Livebox, but when I click on it and put in the key it usaly does nothing, or mostly my entire Linux freezes. I can't even open or close my cdrom.

I need to get linux on the internet soon, Windows has 20 days till it expires.

pleased to hear that you had a suported USB dongle, a lot easer that fussing around with the drivers (witch you can do once you're used to using linux).

try changing your wifi from wpa to wep and getting rid of mac filtering to start with (I know that our liveboxes in france have the mac filtering on, not sure with the box in UK). once that's done try connecting. wpa has problems sometimes and mac filtering is a pain with no real extra security since it is easy for a pirate to change his mac adress to match yours

if ok, reactivate wpa and then try to reconnect and see what happens.


> **mackay12 said:**
> What has that got to do with anything. But I would say Mexican, all the way. Spicy Foods RULE!

No Indian any day for me !! :p  HOT HOT HOT (and an extra popadom on the side with a pint of larger)

---

### Post by mackay12 on 2008-09-12
ok could you explain how to change it to WEP, I know it is a WEP key it uses, some how I got it randomly. It connected and I dont know what I did. But I cant seem to get it again. And when It connected Computer Froze. And I am wondering why its doing that. I dont think its supposed to. Maybe its broken. And I don't want to reinstall it all.

---

### Post by mackay12 on 2008-09-12
> **stone@bruti said:**
> No Indian any day for me !! :p  HOT HOT HOT (and an extra popadom on the side with a pint of larger)

But popadoms are Indian. not italian. Wait nvm just got you said indian, :P

---

### Post by stone@bruti on 2008-09-12
> **mackay12 said:**
> ok could you explain how to change it to WEP, I know it is a WEP key it uses, some how I got it randomly. It connected and I dont know what I did. But I cant seem to get it again. And when It connected Computer Froze. And I am wondering why its doing that. I dont think its supposed to. Maybe its broken. And I don't want to reinstall it all.

um this could be a bit hard since I haven't got a livebox and only a french version of intrepid alpha 5 ubuntu and my translation is a bit dodgy after a few beers :s

normaly you can access your livebox by going to 192.168.0.1 in an internet browser. be careful and don't change anything you aren't sure about.

to access your wifi, you need to use network manager (top right next to the hour), for wep you should have 3 choices :
wep parphrase (just normal text)
wep hexadecimal : numbers and a to h lettres
web ascii

you should need the parphrase or the hexadecimal.

once connected, you should have 4 bars indicating the signal strength.

and no it shouldn't have frozen. if it does, try ctrl + alt + del to reboot ou ctrl+alt+backspace to go back to the login.

good luck

Stone

---

### Post by mackay12 on 2008-09-12
Ill say a few things. Its not my livebox I need to access. I think its in my Ubuntu. When you click on the network thing you can slect the network which gives you only wpa but then there connect to other network. here you can enter your network name e.g Livebox-4570, and your choice of key WPA,WEP, and a few other. Will this work as well?

Oh and Ctrl+Alt+Del do nothing. The computer its self freezes, even the hardware. The Disc Drives dont open when I click the button. And nothing works.

---

### Post by mackay12 on 2008-09-12
OK now im worried, It crashes at times when it shouldn't, I logged in waited about 5 mins everything was loaded. Then I moved my curser over the Applications button and it frooze. This is not normal. I thought Linux didn't crash. Well not like this. This is like a Entire Computer Freeze, lights are on but no ones home. cdroms dont open or close things dont do anything.

---

### Post by stone@bruti on 2008-09-12
> **mackay12 said:**
> Ill say a few things. Its not my livebox I need to access. I think its in my Ubuntu. When you click on the network thing you can slect the network which gives you only wpa but then there connect to other network. here you can enter your network name e.g Livebox-4570, and your choice of key WPA,WEP, and a few other. Will this work as well?

it only gives you WPA because that is the kind of protection your livebox is using at the moment.
the button "other network" is to connect to hidden networks so no it won't enable you to connect to your livebox using wep.

normaly your WPA key is written under the livebox and you have to press one of the 2 buttons to disable the mac filtering while you connect, not sure which one though, probably Number 1.
if the compuer freezes then reboot and try again, if it still freezes then you have a problem somewere. that's where you'll need to go into your livebox and change the wpa to wep and retest the connection. if you can connect with wep then your wpasupplicant might need a reinstall or a reconfiguration (a prog in linux which takes care of wpa).

good luck

Stone

---

### Post by mackay12 on 2008-09-12
Ok well, It is set to WEP or WPA in the livebox. So it should work. And Im not sure wat the two buttons do. 1 is to enable Paring mode but maybe I need to do this. You do in Windows. But i don't think I should try button 2 it might do something to it. It could be a Livebox reset, and I have info on my livebox, like portforwarded stuff.

---

### Post by stone@bruti on 2008-09-12
> **mackay12 said:**
> OK now im worried, It crashes at times when it shouldn't, I logged in waited about 5 mins everything was loaded. Then I moved my curser over the Applications button and it frooze. This is not normal. I thought Linux didn't crash. Well not like this. This is like a Entire Computer Freeze, lights are on but no ones home. cdroms dont open or close things dont do anything.

Linux on its own doesn't crash (the command line version) but the graphics part does, especialy with compiz (that's the thing that gives you all the flashy eye candy like 3d box).

you might have corrupted somthing trying to get your belink card working (happend to me often when I started using linux). a reinstall would clear that matter. lukaly a reinstall is a lot quicker with linux than with windows.

or maby you've hot a hardware problem. try testing your memory with the memtest that is with most linux live CDs or checking the temperature (most recent bios give you the temp of processor and motherboard)

---

### Post by stone@bruti on 2008-09-12
> **mackay12 said:**
> Ok well, It is set to WEP or WPA in the livebox. So it should work. And Im not sure wat the two buttons do. 1 is to enable Paring mode but maybe I need to do this. You do in Windows. But i don't think I should try button 2 it might do something to it. It could be a Livebox reset, and I have info on my livebox, like portforwarded stuff.

yep paring mode is the one you want, that enables you to connect other wifi material.

---

### Post by rustybronco on 2008-09-13
> **mackay12 said:**
> I have two, one in the computer is a PCI and the one that I got working is a USB, so lets go with the USB. Its made by LM Technologies.To get one working please REMOVE the other (no need to fight that issue).  I would suggest you first try to get the pci card working.

I would suggest you also start a thread for each problem... wine, wireless, ect. 
and edit your post's by adding adding additional information if needed not a complete edit of the post, it makes it hard to follow what has been done so far.

what problem are you trying to solve in this thread?

---

### Post by mackay12 on 2008-09-13
No need, the PCI one aint detected so I don't need to remove it. And the USB one works. Just need to get the correct settings and stuff.

And I think my Livebox is broken, the 1 and 2 buttons dont work. 1 is for paring mode. Normaly the light flashes slowly when its on, but now it dont do anything. And I could try the No Security in the Livebox Settings.. Would that work.

---

### Post by mackay12 on 2008-09-13
Ok guys got it working, im on my Ubuntu now. Execpt I have a major problem. I cant use the Add/Remove thing, I get an error when trying to install things.

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

I run dpkg --configure -a but it says I need to be a superuser, and I need to get this to work.

---

### Post by mackay12 on 2008-09-13
It has gotten worse, update manager does no longer work either. wats going on here.

---

### Post by mackay12 on 2008-09-13
Now the Package Installer has problems. It says please close one of the others, but none are open, synapsis isn't aptitude isn't so whats going on. without it im having to use windows version of things in Wine. This is anoying me.

---

### Post by stone@bruti on 2008-09-13
> **mackay12 said:**
> Ok guys got it working, im on my Ubuntu now. Execpt I have a major problem. I cant use the Add/Remove thing, I get an error when trying to install things.

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

I run dpkg --configure -a but it says I need to be a superuser, and I need to get this to work.

Hi,

glad you finaly got it working. to become a superuser add sudo in front of your command, eg:
sudo dpkg --configure -a

you will be asked for your password.

since your problem concerning the wifi is solved, it would be better to start a new post.

---

### Post by stone@bruti on 2008-09-13
> **mackay12 said:**
> Now the Package Installer has problems. It says please close one of the others, but none are open, synapsis isn't aptitude isn't so whats going on. without it im having to use windows version of things in Wine. This is anoying me.

sounds like synaptic or aptitude is still running, try :
ps -e|grep synaptic


If you get an output then it is still running (even though you cant see it graphicly). normaly it would look like this

7490 ?        00:00:01 synaptic

the most important is the number at the front. it's the ID of you processus on the computer.

to end the processus, you need to use the kill command eg:

kill -9 7490  
(notice my number is the same as the ID of synaptic) this will kill my session of synaptic

Hope that helps.

---

### Post by mackay12 on 2008-09-13
hmm nothing shows with ps -e|grep synaptic

nvm nothing showd because sudo dpkg --configure -a workd, I think its closed now. The things working. Thanks guys I now have a Fully working Ubuntu. Thanks for all the Help. And I wanna say Ill take part in this forum, and try to help others.

---

### Post by stone@bruti on 2008-09-13
> **mackay12 said:**
> hmm nothing shows with ps -e|grep synaptic

nvm nothing showd because sudo dpkg --configure -a workd, I think its closed now. The things working. Thanks guys I now have a Fully working Ubuntu. Thanks for all the Help. And I wanna say Ill take part in this forum, and try to help others.

glad we managed to help, have fun with your new system.

a quick word of advice, keep the ps -e | grep "prog" and the kill -9 "number" written down, always handy when somthong crashes and easy to use.

Stone

PS don't forget to do an "apt-get moo" every day  :p

---

### Post by mackay12 on 2008-09-14
> **stone@bruti said:**
> glad we managed to help, have fun with your new system.

a quick word of advice, keep the ps -e | grep "prog" and the kill -9 "number" written down, always handy when somthong crashes and easy to use.

Stone

PS don't forget to do an "apt-get moo" every day  :p

Thanks I will, gonna make a txt file with it RIGHT IN MIDDLE OF DESKTOP!

---

### Post by truico on 2009-01-18
[QUOTE=stone@bruti;5777956]it only gives you WPA because that is the kind of protection your livebox is using at the moment.
the button "other network" is to connect to hidden networks so no it won't enable you to connect to your livebox using wep.

Stone@bruti, here is to you from the bottom of my OS: button I did the job! For the first time in 12 months, since we got adsl (Orange Livebox) here in France I too can use wireless (Ahtec laptop). The M$-users in my family already could (@#&*!!!) Can you imagine what I had to go thru? Like: *still using Ubuntu? Not very modern, right?* Whereas I kept insisting it was the Livebox (in Holland I use a SpeedTouch without any problems).
Soooo, thanks a million!:guitar:

---

