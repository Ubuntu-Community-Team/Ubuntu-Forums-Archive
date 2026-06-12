---
title: "Long time Win user, choosing a distro?"
date: 2010-09-04
forum: New to Ubuntu
---

### Post by _Fordy on 2010-09-04
Ok, so my desktop runs W7 x64, and my netbook Ubuntu (The desktop edition atm, but about to try out the "netbook remix").

I've used Ubuntu before on my desktop, but then gradually stopped.

However, I'll need to keep W7 for games, but other than that I want to convert to Linux.

Despite using it before I'm still pretty new, have no idea how half the stuff works and can only just get my head around things being mounted instead of.. well.. just there. And GNOME DE.

I also have no idea, for most of them, the differences ad benefits between distros. Obviously some are meant for HTPC's or other specialist applications - other than that, not a clue.

So for video encoding, web use, shifting files around my network etc. Ubuntu, Xubuntu, Kubuntu - or something else?


PS 
What's tty? And how do you say it - I've always read it as t*tty! ;)

---

### Post by scorp123 on 2010-09-04
> **_Fordy said:**
>  What's tty?  A historical artifact that has survived. The first computers were invented long before any usable and affordable CRT --let alone LCD!!-- screens were available. So instead of displaying their output on a screen --which were simply not available yet-- IT engineers would rig **electric typing machines** to the serial interface of their monstrous gigantic computers, and the computer would spit out its results on that. You can still see such scenes in 1960's science-fiction movies, or in the original "Star Trek" TV show, where computers will always print their analysis on paper ...

And because those typing machines were usually remotely connected, they earned the addition "***tele***". (You know the word 'tele' already from a different context: Telephone = 'distant voice' in ancient Greek.)

Tadddddaaa: The **tele typer** was born = distant/remote typing machine.

In those ancient times typing something on a computer could take awful ages. Nowadays you hit a key and whatever you typed instantly appears on your screen. Not so in the early days. Whatever you typed could take minutes to show up. Hence why everything was shortened. The less you have to type the less likely you're going to mistype and the less you are going to have to wait.

And thus the **[COLOR="Red"]t[/COLOR]**ele[COLOR="Red"]**ty**[/COLOR]per became the "**_[COLOR="Red"]tty[/COLOR]_**".  (tee tee eye).

Yes, when your OS prints a message on "**tty2**" ... then technically it still thinks it's printing that message on a remote type printer. The internal mechanisms are still the same, and it is indeed still possible to have a serial printer connected to the RS-232 port and have the OS print its messages on that. 

Or hook up a VT100 terminal ... some really really big Unix systems from Sun/Oracle, IBM, HP, Fujitsu and others have no graphics cards whatsoever (why should they have one?? Nobody is ever going to sit in front of that extremely loud system!!) and you still only have the serial port to perform a local login on such a machine: a tty.

So that's where "tty" comes from.

Ancient IBM S/360 with a "tty" terminal next to it:
[IMG]http://www-03.ibm.com/ibm/history/exhibits/mainframe/images/2423PH2040.jpg[/IMG]


System administrator checking a "tty's" output:
[IMG]http://i.i.com.com/cnwk.1d/i/ne/p/2004/040604_ibm360.jpg[/IMG]

---

### Post by Jazzy_Jeff on 2010-09-04
> **_Fordy said:**
> Ok, so my desktop runs W7 x64, and my netbook Ubuntu (The desktop edition atm, but about to try out the "netbook remix").

I've used Ubuntu before on my desktop, but then gradually stopped.

However, I'll need to keep W7 for games, but other than that I want to convert to Linux.

Despite using it before I'm still pretty new, have no idea how half the stuff works and can only just get my head around things being mounted instead of.. well.. just there. And GNOME DE.

I also have no idea, for most of them, the differences ad benefits between distros. Obviously some are meant for HTPC's or other specialist applications - other than that, not a clue.

So for video encoding, web use, shifting files around my network etc. Ubuntu, Xubuntu, Kubuntu - or something else?


PS 
What's tty? And how do you say it - I've always read it as t*tty! ;)

Any of the distros you have listed will do what you want. They pretty much just have different GUI's and programs that work best for that environment. It pretty much comes down to what you prefer. I prefer using the Gnome desktop so I use the regular Ubuntu. If you prefer the KDE desktop than you might want to use Kubuntu.

---

### Post by _Fordy on 2010-09-05
> **Jazzy_Jeff said:**
> Any of the distros you have listed will do what you want. They pretty much just have different GUI's and programs that work best for that environment. It pretty much comes down to what you prefer. I prefer using the Gnome desktop so I use the regular Ubuntu. If you prefer the KDE desktop than you might want to use Kubuntu.

That's pretty much what I feared..


Seems extraordinary to me, coming from a Win (and not light usage) background..

What I really struggle with is that a new "Desktop Environment" really requires a whole separate ISO, and dev team? Seems extravagant for what seems to be no more than a skin with a twist.

And thanks for that scorp :)
But if that's the case, why have I seen it crop up in so many threads? I presumed it was some kind of terminal function.


One other forum-related question that really doesn't deserve it's own thread..
I can't seem to work out how to auto-subscribe to threads that I post in? Is that not possible on ubuntuforums? I like to use it because if I'm not getting email alerts, I never think to check back! Being fairly regular on so many forums.. they just get forgotten if I'm not being mailed.

-- No worries, found it. You can expect me to be more regular ;)

---

### Post by kelvin spratt on 2010-09-05
Go to quick links click on edit options you can then scrol down to Default Thread Subscription Mode and change to instant E-mail notification.

---

### Post by fslezak on 2010-09-05
I notice WIN(the forbidden ending) uses more of a KDE environment. Try using Kubuntu.

---

### Post by scorp123 on 2010-09-08
> **_Fordy said:**
>  What I really struggle with is that a new "Desktop Environment" really requires a whole separate ISO It doesn't per se ... But then the ISO image gets bigger and bigger to the point where you need 2 x DVD's or one Double-Layer DVD if you really want it all. Here at Ubuntu they wanted the image that people have to download as small as possible, i.e. not bigger than 1 x CD-R. Hence the necessity to create a KDE-focused fork: Kubuntu.

Other distros until recently didn't care if you can download their ISO's or not, they packed everything + the kitchen sink onto their ISO. SUSE's (before they became 'openSUSE') commercial distro was legendary for that: with each package you'd get like 8 x CD's plus 2 x DVD's, containing both the 32-bit "i386" and the 64-bit "AMD64" editions.

Try downloading that over a phone line ... 

Only recently they too have begun to produce "GNOME-only" or "KDE-only" images, bringing the download sizes down to CD-R size. They openly admit imitating Ubuntu there.

> **_Fordy said:**
>  I presumed it was some kind of terminal function. A **tty** is a terminal, i.e. the device node for it. Remember: On Unix-like OS such as Linux ***everything*** is ultimately a device. When you open a terminal your Linux will still see you as being *"connected to tty-something"* ... So it still sees you as sitting at one of those wired typing machines. When you login via the GUI it sees you as using a *"pts-something"* (e.g. **pts/0**) ... **[COLOR="Red"]P[/COLOR]seudo [COLOR="Red"]T[/COLOR]erminal [COLOR="Red"]S[/COLOR]lave.** 

So even if one day in the future there would be telepathic input methods (you think it -- the computer already executes it!) to Linux this would still be a 1950's era **t**ele**ty**per device. :D


BTW ... for choosing a distro: Did you take the quiz? I'd highly recommend doing that. Maybe Ubuntu isn't even the right choice for you, so this quiz will help you find the right distro.

[http://www.zegeniestudios.net/ldc/](http://www.zegeniestudios.net/ldc/)

---

### Post by techningeer on 2010-09-08
I recomend Ubuntu. Xubuntu doesn't work very well.

---

### Post by Calash on 2010-09-08
You can never go wrong with using the liveCD to test the different distributions before installing.  It gives you a good feel for the OS and will give you warning if there will be any driver issues beforehand.

---

### Post by _Fordy on 2010-09-08
> **scorp123 said:**
> It doesn't per se ... But then the ISO image gets bigger and bigger to the point where you need 2 x DVD's or one Double-Layer DVD if you really want it all. Here at Ubuntu they wanted the image that people have to download as small as possible, i.e. not bigger than 1 x CD-R. Hence the necessity to create a KDE-focused fork: Kubuntu.

Other distros until recently didn't care if you can download their ISO's or not, they packed everything + the kitchen sink onto their ISO. SUSE's (before they became 'openSUSE') commercial distro was legendary for that: with each package you'd get like 8 x CD's plus 2 x DVD's, containing both the 32-bit "i386" and the 64-bit "AMD64" editions.

Try downloading that over a phone line ... 

Only recently they too have begun to produce "GNOME-only" or "KDE-only" images, bringing the download sizes down to CD-R size. They openly admit imitating Ubuntu there.

 A **tty** is a terminal, i.e. the device node for it. Remember: On Unix-like OS such as Linux ***everything*** is ultimately a device. When you open a terminal your Linux will still see you as being *"connected to tty-something"* ... So it still sees you as sitting at one of those wired typing machines. When you login via the GUI it sees you as using a *"pts-something"* (e.g. **pts/0**) ... **[COLOR="Red"]P[/COLOR]seudo [COLOR="Red"]T[/COLOR]erminal [COLOR="Red"]S[/COLOR]lave.** 

So even if one day in the future there would be telepathic input methods (you think it -- the computer already executes it!) to Linux this would still be a 1950's era **t**ele**ty**per device. :D


BTW ... for choosing a distro: Did you take the quiz? I'd highly recommend doing that. Maybe Ubuntu isn't even the right choice for you, so this quiz will help you find the right distro.

[http://www.zegeniestudios.net/ldc/](http://www.zegeniestudios.net/ldc/)

Thanks for everything there.

I did the test just now -

100%:
Kubuntu
OpenSuSE
Linux Mint
Ubuntu

95%:
Mandriva - GUI installer
Debian - requires expert linux knowledge
Fedora - " "

---

### Post by bodhi.zazen on 2010-09-08
> **techningeer said:**
> I recomend Ubuntu. Xubuntu doesn't work very well.

Please do not spread FUD re: Xubuntu.

You may not have had a good experience, but I have been using Xubuntu for years and prefer it to Ubuntu. Xubuntu works fine.

---

### Post by bodhi.zazen on 2010-09-08
> **_Fordy said:**
> Ok, so my desktop runs W7 x64, and my netbook Ubuntu (The desktop edition atm, but about to try out the "netbook remix").

I've used Ubuntu before on my desktop, but then gradually stopped.

However, I'll need to keep W7 for games, but other than that I want to convert to Linux.

Despite using it before I'm still pretty new, have no idea how half the stuff works and can only just get my head around things being mounted instead of.. well.. just there. And GNOME DE.

I also have no idea, for most of them, the differences ad benefits between distros. Obviously some are meant for HTPC's or other specialist applications - other than that, not a clue.

So for video encoding, web use, shifting files around my network etc. Ubuntu, Xubuntu, Kubuntu - or something else?


PS 
What's tty? And how do you say it - I've always read it as t*tty! ;)

I advise you start with the major OS. Some distros are more new user friendly then others.

I would run Ubuntu, SUSE, and Fedora in a virtual machine on Virtual box and go with what seems best to you.

Arch, Debian, Slackware, and Gentoo will take more time to learn and install.

---

### Post by halitech on 2010-09-08
As someone that started with Ubuntu, moved to Xubuntu and then to Debian w/XFCE, I would slightly disagree with you bodhi on debian taking more time to learn and install. Personally, if a person can install Ubuntu, then they can install debian and use it. True, debian doesn't have the ubuntu-restricted-extras package to get all the "goodies" with one command but it's not all that much more work to follow the info on debian-multimedia.org to be able to get them.

Personally, I found some of the "handholding" to actually be holding me back on learning how the system actually works until I changed over to debian. But, the good thing about *nix is the fact that we are free to choose what works best for each of us.

---

