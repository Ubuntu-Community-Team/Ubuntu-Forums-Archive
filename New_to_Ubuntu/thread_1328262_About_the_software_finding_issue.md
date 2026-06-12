---
title: "About the software finding issue"
date: 2009-11-16
forum: New to Ubuntu
---

### Post by ivica_tajto on 2009-11-16
This is my first post here and i have one question - i installed my jaunty perfectly for now everything is ok - and i love ubuntu - but the only place where i find software for now its synaptic. So i was searching trough internet mainly google to find some sites for software - but there is so few of them. So if you are kind to help me find some software sites - i mainly look an ubuntu deb packages but as i have wine installed i now can run with wine tar.bz2 files to( i found those on softpedia ).  I was and i am addicted to software - so i would apreciate any kind of help - thanks in advance.

---

### Post by nitstorm on 2009-11-16
Go to Applications--> Add/Remove programs
There at the option show is a drop down menu, choose all available applications.
u'll find tons of stuff there :)  adding a screenshot jus in case ...  cheers!

---

### Post by KIAaze on 2009-11-16
> **ivica_tajto said:**
> but as i have wine installed i now can run with wine tar.bz2 files to( i found those on softpedia ).

.tar.bz2 files should not be run with Wine.

".tar.bz2" files are similar to ".zip" and ".rar" files on Windows: They are compressed archives.
To extract their contents, just right-click them and select extract.

You can also extract them by command-line with:
```
tar -xjvf file.tar.bz2
```
(this command is for ".tar.bz2" files only)

Wine should only be used to run Windows executables, i.e. files like ".exe" or ".msi".

Please read this for more info on installing software in Ubuntu:
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)
[https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)

P.S.: While I have never had any problems with software downloaded from softopedia (and have never heard of them hosting spyware/malware), I would always try getting software first from the official repositories and then from the original source instead.

This is safer and if you have problems with the software, you will know who to turn too.
Most software under GNU/Linux is open-source and so most of it is available directly from its developers on code hosting sites like sourceforge, launchpad, google code, Savannah.gnu.org, github, etc.

I usually only use softopedia if I was unable to find the software somewhere else on the net.

---

### Post by wmcbrine on 2009-11-16
> **ivica_tajto said:**
> the only place where i find software for now its synaptic.This is a bit like having an iPhone, and complaining that the only place you can find software for it is the App Store. Seriously, have you seen how deep the repositories go? I quote my Synaptic: "28897 packages listed, 1983 installed".

Make sure you enable Universe and Multiverse if you haven't, though.

I actually see this as a big advantage of Ubuntu over, say, Windows -- having this huge collection of software that you can feel pretty good about, instead of having to pick things up from random sources.

Of course the repos *aren't* the only place you can get software, but I'd certainly always look there first. What you'll find outside of the repos are generally individual packages hosted individually*, not the huge collections like download.com that you see for Windows. There just isn't a need for those. But there's always freshmeat.net.

* Even on sites like SourceForge, each project's hosting is managed largely independently. However, there are sometimes features to let you browse through lists of hosted projects.

---

### Post by ivica_tajto on 2009-11-16
Well i am beginer but not that much :) - i am joking - i saw the add/remove section and i installed pretty big amount of software from there - and for the thing about tar.bz2 i just extraxted it and when i open later it shows that it opens it trough wine - however it suits fine to me - just to open it :). And for the repositories i added the universe and multiverse - thanks a lot to that one - and the only thing that i will ask for now - and not to bother you guys is - i cannot run adobe photoshop cs4 trough wine - and i need the exact program - not other that are simular - so can anyone say can i make it to work or just download it from somewhere. 
 
And another thing - can you say to me is there any warez site like there is for windows application - but just for linux - no matter is it an deb package or tar.gz or tar.bz2 file - cuz i think i can manage them to.

Once again thanks to the guy who point me in the right direction about the repositories.

---

### Post by KIAaze on 2009-11-16
> **ivica_tajto said:**
> And another thing - can you say to me is there any warez site like there is for windows application - but just for linux

No, not that I know of, and even if I knew of one, I wouldn't tell you. :P

Why would you need to pirated software if most of it is already available free of charge?
Not only is most of it free of charge, but it is also [Free as in freedom]("http://www.gnu.org/philosophy/free-sw.html"): [http://www.fsf.org/about/what-is-free-software](http://www.fsf.org/about/what-is-free-software)

Ok, now of course, there is also some software you have to pay for like games and perhaps some complex science/engineering software.
But you will be able to find free alternatives most of the time.

Here's a list of a few sites listing GNU/Linux equivalents of Windows software:
[http://www.linuxalt.com/](http://www.linuxalt.com/)
[http://wiki.linuxquestions.org/wiki/Linux_software_equivalent_to_Windows_software](http://wiki.linuxquestions.org/wiki/Linux_software_equivalent_to_Windows_software)
[http://linuxappfinder.com/alternatives](http://linuxappfinder.com/alternatives)
[http://www.libervis.com/wiki/index.php?title=Table_of_Equivalent_Software](http://www.libervis.com/wiki/index.php?title=Table_of_Equivalent_Software)

Note: Pirating GNU/Linux ports of games will discourage developers/publishers from porting more games to GNU/Linux. Do you want that?

---

### Post by scorp123 on 2009-11-16
> **ivica_tajto said:**
>  but the only place where i find software for now its synaptic. There are like ~30'000 packages in Synaptic. Not enough for you???

> **ivica_tajto said:**
>  So if you are kind to help me find some software sites  Not really recommended. Installing software from outside the official repositories is a potential way to get yourself hacked. Please read that again: "potential way". 

You might want to try out these sites:

[http://appnr.com/](http://appnr.com/)
[http://www.allmyapps.com](http://www.allmyapps.com)
[http://www.getdeb.net](http://www.getdeb.net)

And if you don't mind experimenting then this search engine will help you find experimental stuff from the personal package archives (= PPA's) from various Ubuntu developers ... some of the stuff is pretty cool, but rather unstable and therefore didn't make it into the official Ubuntu repos ... yet.

[http://ppa-search.appspot.com](http://ppa-search.appspot.com)

---

### Post by ivica_tajto on 2009-11-16
Thanks for the software that are same as in windows - and the links that you provided - i appreciate it - and for the question about the games - first of all i dont even play games at all - thats why i chosed ubuntu - because it offers stability and speed in everything - and as i said - i am not dissapointed - i am happy that i can get rid of windows - cuz of his weakness with viruses and spywares - i just want to be able to switch completely from windows to ubuntu - i personally think that i will manage it - cuz i read alraidy 2 books for ubuntu - and thats why i asked for your help for software - and thanks for the links once again

---

### Post by ivica_tajto on 2009-11-16
> **scorp123 said:**
> There are like ~30'000 packages in Synaptic. Not enough for you???

 Not really recommended. Installing software from outside the official repositories is a potential way to get yourself hacked. Please read that again: "potential way". 

You might want to try out these sites:

[http://appnr.com/](http://appnr.com/)
[http://www.allmyapps.com](http://www.allmyapps.com)
[http://www.getdeb.net](http://www.getdeb.net)



thank you scorp123 for the links - there are great stuffs there especcialy in the appnr - so i am very thankfull - i already like this society - i heard that the people are helping each other - but you guys are very quick and very helpfull - thanks a lot - once again

---

