---
title: "Ubuntu: not for grandma"
date: 2008-07-02
forum: Networking &amp; Wireless
---

### Post by rasiel on 2008-07-02
i don't mean to rag on linux. i really want to like this os but i think i might be stating the obvious by saying that troubleshooting this beast can send one into cardiac arrest.

i'm trying to install a wireless adapter. i've gathered from hours of fiddling that i need to use the ndiswrapper tool. i found it online, downloaded, took it over to the ubuntu desktop and untarred it (hey, double clicking does work!)

here comes the pain:

the instructions are deceptively simple. open a terminal, cd to the extracted directory and:

make uninstall
make
sudo make install

there isn't any mention however that as soon as you type the first command you get a screen's worth of error messages to the effect that, no, you cannot do this. permission denied.

more blood, sweat and tears leads me to a reference to a cryptic command that will actually perform this uninstall using:

sudo apt-get remove ndiswrapper-utils

that did something alright (deleted the command?). however, to reinstall the command, if that's what that did, i summoned this bit of geekspell:

sudo apt-get install kernel-headers-'uname -r'

it does some promising steps done... done... aaaand... wooops. package kernel-headers-'uname -r' not found

if i type ndiswrapper as a command the command line is helpful enough to tell me that ndiswrapper can be installed using:

sudo apt-get install ndiswrapper-common

...only to sucker punch me immediately afterwards with a perfectly logical  "E: Couldn't find package ndiswrapper-common"

what the holy hell?? did i lose a bet? is this some kind of initiation into secret rites of passage?

i'm not computer illiterate. i've spent years with pc's, macs, amigas (remember those?) and at one point could even dabble in configuring cisco routers and doing maintenance on as400 workstations. what can be said for joe sixpack who has a hard time mastering the concept of a mouse?

ras

---

### Post by cszikszoy on 2008-07-02
Sorry you've had such a hard time with ndiswrapper.  It can be very intimidating at first.  You might like to know that there is a gtk frontend tool for ndiswrapper called ndisgtk.  I've used it before, and it did a good job of setting up my wireless card.  You should be able to download it from apt-get or synaptic etc.

Also, when you type `uname -r`, the ` is not an apostrophe, it's the key located next to the number 1 on en-us keyboards (I think - not sure, it's located near the bksp key on german keyboards).

---

### Post by jaton on 2008-07-02
Take a look at this post:
[http://ubuntuforums.org/showthread.php?t=31926](http://ubuntuforums.org/showthread.php?t=31926)

---

### Post by CameO73 on 2008-07-02
To be honest: wireless adapters are definitely not for grandma to install. If you're lucky, they can actually be easier to install in Ubuntu than in XP. Otherwise, they can be a real pain.

For your ndiswrapper problem: why not try using the graphical install tool. Your doing everything on the command line, but Ubuntu has a great tool for this: **Synaptic** (System -> Administration -> Synaptic Package Manager). Just search for **ndiswrapper** and it'll show you all the available packages.

Btw, I eventually replaced my wireless with a powerline adapter and NIC. Still the advantage (no extra cables), but none of the hassles.

---

### Post by gwbennett on 2008-07-02
If it helps any it's `uname -r` with back ticks, not apostrophes. The tilde key, to the left of 1.

---

### Post by kevdog on 2008-07-02
There are plenty of guides available if you look.  Here is one:

[http://ubuntuforums.org/showthread.php?t=574501](http://ubuntuforums.org/showthread.php?t=574501)

---

### Post by Bliepo32 on 2008-07-02
Here is what you need. It is quick and easy.
```
sudo apt-get install ndiswrapper-common ndiswrapper-utils-1.9
```

And could you, if this fixes it, mark the thread as being solved please?

---

### Post by rasiel on 2008-07-02
thanks to all the responses above - i really appreciate the help. i wanted real bad to come here and say it was solved but still getting the errors.

first i tried the graphical approach suggested by looking for ndiswrapper under system > administration > synaptic manager but it's not there

less enthusiastically then i tried all the above commands but in each case get something to the effect that the package can't be found. i'm guessing that it's because i'm in the wrong directory and the commands are buried god knows where.

all the same, this just isn't fun anymore. can anyone recommend a wireless adapter that is truly plug and play for ubuntu 8.04?

ras

---

### Post by CameO73 on 2008-07-02
Well ... the [UbuntuHCL](http://www.ubuntuhcl.org/browse/search?keywords=wireless) has a couple of user reviews for wireless cards. Another way would be to google your possible choices before buying (something like **ubuntu wireless <your card>**).

I have personally had good experiences with the Realtek (RT2500) wireless chips. Those are found in all kinds of cheap wireless cards. As you can see from [this thread](http://www.ubuntuhcl.org/browse/search?keywords=wireless) there are various tested solutions (and admittedly also known problems) available for Ubuntu.

As I said before ... my troubles finally all went away (not Ubuntu-related, but wireless signal interference) when I decided to go for Powerline equipment (see [this example](http://www.netgear.com/Products/PowerlineNetworking/PowerlineEthernetAdapters/HDX101.aspx)). It is more expensive, though.

---

### Post by chili555 on 2008-07-02
I'm not sure a fresh install and installing wireless drivers, even from an install CD, is for grandma, either. Mac OS is a different story since, for a high yet affordable price, all the dirty work has been done for you.

Once up and running, Ubuntu is fine for granma, including the one in my house that runs Kubuntu every day without a complaint. No, she's not one of those hillbilly 39-year old granmas, either. She is past 65. She loves her Frozen Bubble, email, Pidgin and Firefox. She worries not about virii, malware, spyware or BSOD.

---

### Post by cszikszoy on 2008-07-03
> **chili555 said:**
> for a high yet affordable price

$80 for an airport card isn't really what I'd call affordable.  More like highway robbery.


rasiel:

It's wierd that you can't find ndiswrapper.  Do you have all of the extra repositories enabled?  Although I though ndiswrapper was just in the default repo...  If you go to synaptic, and search "ndiswrapper", really nothing shows up?  Unless something is wrong with your repositories, that shouldn't happen.  When I search it about 10 things come up.

---

