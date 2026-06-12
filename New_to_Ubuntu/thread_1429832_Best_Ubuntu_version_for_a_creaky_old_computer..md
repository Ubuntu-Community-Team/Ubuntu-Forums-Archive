---
title: "Best Ubuntu version for a creaky old computer."
date: 2010-03-14
forum: New to Ubuntu
---

### Post by WarrenL on 2010-03-14
Hi folks,

I'm sure this question has been asked in various forms a million times already, so I'll be happy for anybody to point me to an old thread rather than typing out an answer, however:

I'm resurrecting an old PC for my 6 year old son. It is a Duron 800, with 256 Mb of RAM, of which I think 32 Mb are stolen by the onboard graphics. It has a generous 20 Gb hard drive on which to store an Ubuntu installation.

I split the HDD into two 9 Gb partitions (system and home) and left 1 Gb for a swap space. Then I installed Xubuntu 9.10.

However I'm finding the machine is still rather slow, subjectively quite a lot slower than it seemed to run its old XP installation, and certainly slow enough to frustrate my son when he's running Tuxpaint, Tux Math, etc. From what I've read, the machine should be singing along with Xubuntu, but before I rush out and buy more RAM I'd like to know what other options I should try.

Are there tweaks I can make to Xubuntu? Should I install an alternative interface such as Fluxbox?

What's the collective opinion on making an 800 MHz, 256 Mb machine hum?

PS> Now that I've got used to Ubuntu 9.10 on my own desktop there's NO WAY IN HELL I'll ever go back to Windows! Thanks Ubuntu!
[IMG]http://www.qtl.co.il/img/copy.png[/IMG][[IMG]http://www.google.com/favicon.ico[/IMG]]("http://www.google.com/search?q=%0D%0AWhat%20is%20the%20best%20way%20to%20extract%20performance%20from")[IMG]http://www.babylon.com/favicon.ico[/IMG]

---

### Post by J V on 2010-03-14
I have a lappy with half those specs running xubuntu "Relativley snappy", you can't expect much from old machines.

However, if xp sp 3 runs fine (If you add the service packs it gets a lot slower), post us an lshw and a top.

Running ATI?
Background process sucking up resources?

---

### Post by WarrenL on 2010-03-14
The XP installation included SP2, but the machine had been unused for quite some time, so it never received SP3.

Pardon my ignorance; could you please explain "lshw" and "top"?

Obviously I don't expect wonders from an old machine like this, but after everything I've read about Ubuntu/Xubuntu I have a nagging feeling that it should  be running better than it does.

---

### Post by anselm on 2010-03-14
xubuntu isn't much better than gnome.

you might try ubuntu with lxde; 

[http://wiki.lxde.org/en/Ubuntu](http://wiki.lxde.org/en/Ubuntu)

---

### Post by J V on 2010-03-14
Lubuntu is also an option, though I've never tried it...

Open a terminal (accessories) and type in top while running these programs (tux paint etc)

This will show you which apps are using the most CPU power

Then hit Q to stop it and type in "sudo lshw" and paste it here too, that will tell us about your hardware

---

### Post by lemuriaX on 2010-03-14
I'd buy some more RAM for it if that's an option for you.

---

### Post by Trandre on 2010-03-14
> **WarrenL said:**
> Pardon my ignorance; could you please explain "lshw" and "top"?.

You open programs-->accesories-->terminal

Then type in lshw(i think i stands for list hardware) then enter

Type top(sytem recource use) then enter.

Trandre

---

### Post by snowpine on 2010-03-14
Puppy runs well on older hardware and would be cute & fun for a kid. I think there might even be a "puplet" (puppy remix) especially for children. :)

---

### Post by KIAaze on 2010-03-14
Not Ubuntu, but very good and user friendly: [http://puppylinux.org/main/index.php?file=Overview%20and%20Getting%20Started.htm](http://puppylinux.org/main/index.php?file=Overview%20and%20Getting%20Started.htm)

The only thing I don't like about it, is that it makes you run as root by default and there doesn't seem to be an easy way to change it.

But it's definitely very fast and appropriate for old machines.

---

### Post by WarrenL on 2010-03-14
Cheers fellas - I'll do all that at home tonight.

And to be honest anselm, I've had the feeling myself that Xfce isn't that much lighter than Gnome.

---

### Post by Ozitraveller on 2010-03-14
HowTo Achieve "Ubuntu-Desktop-Minimal"
[http://ubuntuforums.org/showthread.php?t=1155961](http://ubuntuforums.org/showthread.php?t=1155961)

---

### Post by WarrenL on 2010-03-14
That's worth looking into, Ozitraveller, but will it really give me a real-world performance benefit or is it simply a cleanup of unnecessary packages?

Please remember that I'm very much a Linux newbie and I'm still just grasping my way around.

---

### Post by Donald1715 on 2010-03-14
I suggest more ram... another 256 mb chip. Chances are you'll need PC100. You should be able to find an old chip on one of the auction sites.

---

### Post by J V on 2010-03-14
Again: I have a 500 mhz 128m ram lappy running xubuntu fine... lubuntu + minimal = fine

---

### Post by michaelzap on 2010-03-14
Contrary to expectations, Xubuntu actually uses more RAM than vanilla Ubuntu:
[http://www.linux-mag.com/cache/7520/1.html](http://www.linux-mag.com/cache/7520/1.html)

Lubuntu is certainly an option, but I'd wait for the final release. Crunchbang is an OpenBox version of Jaunty that works very well on limited systems, but you have to be comfortable with OpenBox (not everyone likes the speed-for-GUI-configuration trade-off). There's an LXDE version of Debian available on teh LXDE website, but I haven't tried that personally.

Your best bet is probably Debian. It runs much better on low-resource systems and you give up very little that you would have in Ubuntu. A stock Gnome installation of Debian will seem almost identical to Ubuntu (with the exception of those funny-sounding FOSS software packages and no sudo account by default).

Eeebuntu is switching from Ubuntu to Debian, and so is Crunchbang. Ubuntu is just not as lean and mean as it could be. Perhaps Lucid will change all that, but we won't really know until April 29th.

---

### Post by WarrenL on 2010-03-14
I've just downloaded the Lubuntu .iso: I'll give it a go. The Xubuntu installation is only fresh, so it won't hurt to blow it away and try Lubuntu.

Reading those links it certainly seems that Xubuntu might have crossed onto the wrong track - shame, 'cause I like the interface.

---

### Post by Ozitraveller on 2010-03-14
> **WarrenL said:**
> That's worth looking into, Ozitraveller, but will it really give me a real-world performance benefit or is it simply a cleanup of unnecessary packages?

Please remember that I'm very much a Linux newbie and I'm still just grasping my way around.

This is basically a bare-bones desktop so it's very lite. I have it on a PII400 with 389mb ram. 

When 10.04 arrives I'll look at Lubuntu and setup a bare-bone version of that.

---

### Post by achase79 on 2010-03-14
I installed on my daughter's computer (almost exactly what you have, 800mhz etc.) and I installed xubuntu on her computer and just added lxde and switched her to it.  She is 5 years old and can do more with her computer than my wife can do with her 3ghz Windows computer.

---

### Post by richs-lxh on 2010-03-14
#! Crunchbang is also a nice lightweight alternative. Ubuntu + OpenBox.
[http://crunchbanglinux.org/](http://crunchbanglinux.org/)

Incidentally, don't judge Xfce by Xubuntu. As of late Xubuntu has become a bit of a hog compared to what it was like a few years ago.

---

### Post by k3lt01 on 2010-03-14
Lubuntu seems to be getting some good reviews, Ranch Hand is testing the 10.04 version and speaks very highly of it. It is also available in the repositories for 9.10 so you could install it and if your machine runs better with it you can remove Ubuntu-Desktop (Gnome).

---

### Post by linux_believer on 2010-03-14
Recently attended a presentation by Akkana Peck at the Southern California Linux Expo.

Puppy is nice but I find it easier to start with a full distro like Ubuntu then strip it down. During her presentation she talked about many services that Ubuntu has that you can turn off, many simply just dont work.


[http://www.socallinuxexpo.org/scale8x/presentations/featherweight-linux-how-turn-netbook-or-older-laptop-ferrari](http://www.socallinuxexpo.org/scale8x/presentations/featherweight-linux-how-turn-netbook-or-older-laptop-ferrari)

---

### Post by michaelzap on 2010-03-14
> **richs-lxh said:**
> #! Crunchbang is also a nice lightweight alternative. Ubuntu + OpenBox.
[http://crunchbanglinux.org/](http://crunchbanglinux.org/)

Incidentally, don't judge Xfce by Xubuntu. As of late Xubuntu has become a bit of a hog compared to what it was like a few years ago.

Absolutely. XFCE is a very nice lightweight DE, but Xubuntu has really let itself go. It's a shame that people will judge XFCE based on Xubuntu.

The next release of Crunchbang will be based on Debian, and it will include an OpenBox/LXDE version and an XFCE version (and I expect it to be amazingly fast).

---

### Post by quantumspiral1919 on 2010-03-15
Maybe an asinine input here but if it's for a 6 y-o you might consider Edubuntu,   I'm not sure, I haven't tried it.

---

### Post by WarrenL on 2010-03-15
Well folks, I didn't get round to running "lshw" and "top" last night, but I did do a few other things.

I downloaded and installed Lubuntu (the Karmic beta version) but found it a bit rough and ready, and unwilling to install once the live CD had booted up. Not so good for a newbie.

So I cleaned out the hard-drive again and reinstalled Xubuntu. And here's what I noticed: it seemed to be running quite well until I allowed it to update. There were 184 updates to download and install, and after they were in place the machine turned into an almost unusable pig. Ta dah!

Perhaps I should try loading the LXDE interface and ditching Xfce?

Perhaps I should wait for the first proper release of Lubuntu?

Perhaps I should simply buy some more RAM for the PC? However it seems to me from everything that I've read that the hardware I currently have will provide a completely adequate system if I get the OS right.

Thanks for all the replies so far: I'm keeping a note of all the links etc and will explore them further as time allows.


[IMG]http://www.qtl.co.il/img/copy.png[/IMG][[IMG]http://www.google.com/favicon.ico[/IMG]]("http://www.google.com/search?q=should")[IMG]http://www.babylon.com/favicon.ico[/IMG]

---

### Post by WarrenL on 2010-03-15
I almost forgot! I have thought of Edubuntu, but figured it would provide me with the same problems that a normal Ubuntu installation would on that hardware. I was originally figuring on Xubuntu with the education packs installed where possible.

And then there's Puppy Linux. I downloaded it and ran my laptop on it from a USB stick. Very impressive for what it is, but I didn't think it suitable for what I'm trying to achieve. And I don't think it's compatible with all the educational stuff that I'd like my son to use. Is that correct?

---

### Post by michaelzap on 2010-03-15
Personally I would try this:
[http://lxde.org/download](http://lxde.org/download)

In the past I've used Dreamlinux on systems like this, but afaik that project is shutting down. It was also a Debian-based XFCE system, and it ran amazingly well on the old machines that I tried it on. In the future I think that Crunchbang and Eeebuntu wil be the ideal options, but neither of those projects has a finished Debian-based release yet.

---

### Post by WarrenL on 2010-03-16
I'm installing LXDE on the Xubuntu machine right now. It'll be interesting to see how it goes.

If it works I'll need to know how to remove Xfce and all its associated baggage.

---

### Post by bodhi.zazen on 2010-03-16
IMO, for the most part, the window manager does not make *that* much difference.

See:

[http://www.phoronix.com/scan.php?page=article&item=650&num=1](http://www.phoronix.com/scan.php?page=article&item=650&num=1)

[http://www.phoronix.com/scan.php?page=article&item=linux_desktop_vitals&num=1](http://www.phoronix.com/scan.php?page=article&item=linux_desktop_vitals&num=1)

If you think about it, this makes sense as much of what is benchmarked is a function of the kernel and not the window manager.

What makes a faster, light weight OS - Minimal services running at start up (for example, if you do not use bluetooth, disable it, etc) and light weight apps.

LXDE does a fantastic job of lightening up, but it may be a bit of a shock if you are looking for the default apps in Ubuntu.

I second the advice to look at Puppy Linux or most any distro based on Slackware (Slax, Wolvix just released a new beta, Zenwalk, Gobln).

[http://www.wolvix.org/article.php?id=30](http://www.wolvix.org/article.php?id=30)

---

### Post by WarrenL on 2010-03-16
I've got LXDE up and running, and there is a noticeable difference in speed when switching between Xfce and LXDE.

Ditching Firefox for Epiphany helps too - a 6yo has pretty basic browsing requirements.

---

### Post by lemuriaX on 2010-03-16
I'd maybe try a minimal install with pure XFCE.

---

### Post by imperius69 on 2010-03-16
hello

why not install Ubuntu normal, updated it then unistall what you dont use/like, install the apps u use the most, stop services that are not used and then do a "sudo aptitude install lxde" and then boot on LXDE.

Might work no?

---

### Post by michaelzap on 2010-03-16
> **imperius69 said:**
> hello

why not install Ubuntu normal, updated it then unistall what you dont use/like, install the apps u use the most, stop services that are not used and then do a "sudo aptitude install lxde" and then boot on LXDE.

Might work no?

That would work, but it takes a lot of effort. It'd probably be easier to just do a minimal Ubuntu installation and then add LXDE and the other apps that you want. Or you could use the Debian LXDE installer that I linked to above and you might be even closer to done as soon as the installation is finished.

---

### Post by dzon65 on 2010-03-16
Installing a full system and then downgrading it will not offer you the same as installing a core and build it up.If you wanna stay in the ubuntu family,install minimal and (in your case)lxde,not lubuntu.However,there's a very annoying bug in the latest lxde and lubuntu.Don't think it's fixed yet,but it's impossible to set default progs.Therefor you might wanna replace pcmanfm with thunar.(or you'll go mad...for sure).I have an old compac lying around with minimal/lxde/gnome panel (which actually isn't THAT much heavier)/thunar/openbox/mplayer/roxterminal....and some more lightweight goodies.The thing takes about 1.6Gb and runs  fast considering the 128mb ram it had initially.Pumped it up to 512mb afterwards.

---

### Post by RJQ on 2010-03-16
In my experience a old computer works better with old software, or a least not cutting edge, forget about updates etc. if this is going to be a kids workstation you don't really need that much, I highly recommend Ubuntu 8.04, (you still have about a year to use the repos) and try from there, there sure are smaller distros like puppy but I don't think they are friendly for a little one (yes is super friendly for us) some times graphic drivers are the ones that slow things up, wrong xorg configuration etc. but 8.04 was in my opinion one of the fastest, working out of the box distros.

---

### Post by WarrenL on 2010-03-16
So far LXDE seems to run quite well on top of Xubuntu, but it is still a bit compromised at this stage of its development. It demonstrates potential though - I will look forward to the official release of Lubuntu.

Meanwhile how would I achieve a minimal Ubuntu install to which I could add an unbloated Xfce?

---

### Post by undecim on 2010-03-16
I would definitely install LXDE if I were you. It's much faster than XFCE (the desktop that comes with Xubuntu)

Just open a terminal and type "sudo aptitude install lxde", and then log out and select lxde as your session before you log in.

---

### Post by WarrenL on 2010-03-16
That's what I've done, Undecim. It works really well, although I think LXDE requires a little more work before it could be considered polished. A promising start though.

---

### Post by phillw on 2010-03-16
As the lxde variant of ubuntu (lubuntu) is still in alpha3 for 10.04, it still has a few 'rough edges'. I've been running it for a few days solid as my 'main' OS and it certainly hasn't crashed on me. As with all the *buntu family, there is a beta due out of them on Thursday 18th March.

Lubuntu is certainly 'light' on resources, and certainly worth a looking at for your computer --> [https://wiki.ubuntu.com/Lubuntu](https://wiki.ubuntu.com/Lubuntu)

Regards,

Phill.

---

### Post by imperius69 on 2010-03-16
> **WarrenL said:**
> Meanwhile how would I achieve a minimal Ubuntu install to which I could add an unbloated Xfce?

You wil have to do some reading as i am doing right now, since im also interested on this topic, and im total penguin n00b :popcorn:. 

Get the minimal CD here

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

then u have several tut's:

(very useful topic)

[http://ubuntuforums.org/showthread.php?t=1155961](http://ubuntuforums.org/showthread.php?t=1155961)

(i did this one to try out first)

[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

(this ones had also lots of info on stuff to install)

[http://distrowatch.com/weekly.php?issue=20081215#feature](http://distrowatch.com/weekly.php?issue=20081215#feature)

[http://distrowatch.com/weekly.php?issue=20090504#feature](http://distrowatch.com/weekly.php?issue=20090504#feature)

Been all afternoon doing experiments on virtualbox 

What i can say so far is, 

Full Ubuntu install after boot up takes 160Mb ram
Full Ubuntu install with LXDE after boot takes 97 Mb ram
Minimal Ubuntu install, after boot, 80 Mb ram

```

This is the stuff i have installed on my minimal so far, and im shure there is stuff here i dont need :P :

xorg menu gnome-core gdm xinit gnome-utils gnome-system-tools x11-xserver-utils epiphany-browser epiphany-extensions synaptic
startupmanager gnome-volume-manager
gcalctool htop tsclient jockey-gtk
nautilus-sendto nautilus-share nautilus-cd-burner
network-manager-gnome network-manager-pptp pptp-linux
human-theme humanity-icon-theme gnome-themes-ubuntu ubuntu-artwork xcursor-themes gnome-screensaver tangerine-icon-theme
xsplash ubuntu-xsplash-artwork
indicator-applet-session
software-center 

```

---

### Post by WarrenL on 2010-03-16
Just for laughs I'm going to try the Minimal CD.

---

### Post by k3lt01 on 2010-03-16
> **imperius69 said:**
> Get the minimal CD here

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

(i did this one to try out first)

[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal) +1. This is how I always do it now on my own machines. The benefit her is you get only what you want (plus dependencies but there are even ways around that).

---

### Post by WarrenL on 2010-03-17
Right guys, I've run the Ubuntu Minimal installation, and apt-got Xfce. Now I can log in and start Xfce with a startx command. And I have one very swift-running old box. But how do I set things up to boot straight to the desktop environment?

---

### Post by robert shearer on 2010-03-17
> **WarrenL said:**
> Right guys, I've run the Ubuntu Minimal installation, and apt-got Xfce. Now I can log in and start Xfce with a startx command. And I have one very swift-running old box. But how do I set things up to boot straight to the desktop environment?

You need a display manager. I see several posts have recommended using gdm and I have used xdm for low spec installs.

[http://tldp.org/HOWTO/XDM-Xterm/index.html](http://tldp.org/HOWTO/XDM-Xterm/index.html)

You can install it from the terminal using
```
sudo apt-get install xdm
```

Any other votes for either gdm or xdm ??

---

### Post by k3lt01 on 2010-03-17
> **WarrenL said:**
> Right guys, I've run the Ubuntu Minimal installation, and apt-got Xfce. Now I can log in and start Xfce with a startx command. And I have one very swift-running old box. But how do I set things up to boot straight to the desktop environment?
Check out the psychocats link that was posted it has all that info and more.

---

### Post by dzon65 on 2010-03-17
> **k3lt01 said:**
> Check out the psychocats link that was posted it has all that info and more.
+1.Check out the links that were posted.Everything you'll need is there.The psychocats tutorial is with all the screenshots you'll encounter.

---

### Post by derrick81787 on 2010-03-17
My personal vote would be to install a command line system using the Ubuntu minimal CD and then install xfce4 and gdm/xdm, like I believe some people have already mentioned.

I've actually been wanting to set up a system like this just for fun, but I loaned my only spare computer (which also has low specs) to someone, and my others are working fine with default installations, and I don't really want to change them right now.  I bet you can get a pretty snappy system this way, though.

- Derrick

---

### Post by WarrenL on 2010-03-17
Thanks everyone.

I understand the concept of a display manager now. GDM looks nice but I want to keep it simple and I don't really want Firefox installing on this machine.

How can I do a simple GDM installation that adds only the minimum possible stuff to the machine?

---

### Post by imperius69 on 2010-03-17
> **WarrenL said:**
> Thanks everyone.

I understand the concept of a display manager now. GDM looks nice but I want to keep it simple and I don't really want Firefox installing on this machine.

How can I do a simple GDM installation that adds only the minimum possible stuff to the machine?

Im using xfce4, couse it seams to be your choice before.
```

sudo apt-get update && sudo apt-get upgrade

sudo apt-get install xorg menu xterm xinit gdm xfce4 xfce4-goodies x11-xserver-utils synaptic

sudo /etc/init.d/gdm start

after boot u may open terminal:

sudo apt-get install htop jockey-gtk epiphany-browser epiphany-extensions


others via synaptics:

software-center
update-manager
gdebi
gdebi-core

after this, is up to you!

```

I personally used wdm, its lighter, from what i read is a derivative of xdm. Both xdm and wdm dont allow automatic log in, while gdm allows it.
I also use gnome simply couse xfce4 dont have a menu editot GUI (im a gui whore :P )

---

### Post by WarrenL on 2010-03-17
GDM is my choice, because I want auto-login. But I gather that a browser of some kind is one of the pre-requisites for GDM (hence the rather forbidding apt-get installation string)?

---

### Post by imperius69 on 2010-03-17
> **WarrenL said:**
> GDM is my choice, because I want auto-login. But I gather that a browser of some kind is one of the pre-requisites for GDM (hence the rather forbidding apt-get installation string)?

o no, u dont need to install the browser on the first string.
i used the epiphany browser, couse its lighter then firefox,and only so u can have access from the start to the internet.

You can install that after boot using synaptic or the terminal.
If you dont want to install a browser right away, remove epiphany-browser from the string.

ps - removed the epiphany from the string

---

### Post by WarrenL on 2010-03-17
Cheers for that!

As a Linux newbie (I only touched it for the first time in January) the command line is still very daunting but I'm starting to feel a little more comfortable poking about in there.

I'll try all this out when I get home tonight.

---

### Post by derrick81787 on 2010-03-17
> **WarrenL said:**
> GDM is my choice, because I want auto-login. But I gather that a browser of some kind is one of the pre-requisites for GDM (hence the rather forbidding apt-get installation string)?

To install GDM, just do:
```
sudo apt-get install gdm
```
That will give you the new GDM that is part of Karmic.  To get the older GDM that is part of all the Ubuntu releases before Karmic, do:
```
sudo apt-get install gdm-2.20
```

That long apt-get string just lists programs that the author thinks you will want.  They don't really have any dependencies on each other (and if they did, apt-get would handle that automatically.)

- Derrick

---

### Post by WarrenL on 2010-03-17
Oh yes! Looking at it again I understand now.

I already have all of that stuff that I want - Xfce, Synaptic, etc. I'm simply missing the login screen!

---

### Post by imperius69 on 2010-03-17
> **WarrenL said:**
> Oh yes! Looking at it again I understand now.

I already have all of that stuff that I want - Xfce, Synaptic, etc. I'm simply missing the login screen!

what you mean you missing the login screen?? your PC boots to text mode ??? (did u install xorg? )

---

### Post by imperius69 on 2010-03-17
> **WarrenL said:**
> Cheers for that!

As a Linux newbie (I only touched it for the first time in January) the command line is still very daunting but I'm starting to feel a little more comfortable poking about in there.

I'll try all this out when I get home tonight.

hehe

im a newb too, i might have touched it before January, but i never did do the switch, i just like to try out the new versions and play a bit with them. I have to say, 9.10 for was the first that got me thinking on making the switch, really good.

---

### Post by robert shearer on 2010-03-17
> **imperius69 said:**
> what you mean you missing the login screen?? your PC boots to text mode ??? (did u install xorg? )

Well, if the op can get a **desktop** by doing
```
startx
```

then xorg **must** be installed.
All that is needed is a disply manager of choice.

---

### Post by imperius69 on 2010-03-17
and to start it

```


sudo /etc/init.d/gdm start


```

---

### Post by WarrenL on 2010-03-17
Yep, the desktop starts by typing *startx*, so I assume xorg is in there somewhere. I just want the display manager to give me the graphical login, and be able to configure it for auto-login.

To be perfectly honest, I tried Linux a handful of years ago but it was still too arcane for me. Karmic is the release that persuaded me to try again. I'm really enjoying Linux this time, especially as I'm venturing into all this system mix-n-match to get what I want.

---

### Post by imperius69 on 2010-03-17
instead os startx try

```


sudo /etc/init.d/gdm start


```

---

### Post by ConDsenXieN on 2010-03-17
A bit late, but anything Xfce-based(as most have said) will work fine here.

My desktop is also ancient, but I run Linux Mint 6 Felicia Xfce on that, runs quite well.

Good to hear the old machine found some new use. :D

---

### Post by imperius69 on 2010-03-17
* off topic *
any one here knows how to get qingy to work on a minimal xcfe4?

---

### Post by lemuriaX on 2010-03-18
For a lighter weight browser than Firefox, you might try Seamonkey. It's not the fastest but significantly lighter than Firefox, and is also from Mozilla.

---

### Post by WarrenL on 2010-03-18
Well folks, I'm up and running with an auto-login. Just now I armed myself with a stopwatch and discovered the following:

**Son's PC:**
AMD Duron 800
256 Mb PC133 RAM
IDE HDD 5400rpm 20Gb
Ubuntu Minimal Install
Xfce desktop - basic installation.
GDM with auto-login configured.
Boot time (push power button to desktop completely loaded, all hard drive activity ceased): **52.5 seconds**.

**My PC:**
AMD Athlon XP 2600+
2 Gb DDR400 RAM
SATA hard drive
Ubuntu Karmic standard installation.
Auto-login configured.
Boot time (as above): **58.5 seconds**.

---

### Post by dzon65 on 2010-03-18
> **WarrenL said:**
> Yep, the desktop starts by typing *startx*, so I assume xorg is in there somewhere. I just want the display manager to give me the graphical login, and be able to configure it for auto-login..
WarrenL.If you did install gdm or whatever,USE this command (mentioned before.....)
sudo /etc/init.d/gdm(or whatever you installed) start .If there's no login-screen you did something wrong.

---

### Post by dzon65 on 2010-03-18
Okay,you're up and running.I do quite a few minimal installs.In fact,don't use anything else anymore.They're faster,no matter what.Your boot time's a bit high though.If you want to work faster,I suggest you install lightweight stuff.Two things I always install,no matter if it's xfce-core,gnome-core,are thunar file-manager (which you'll have in xfce) and openbox.Mind you though,using openbox as WM will not allow fancy compiz stuff to run.(in minimal that is,works in arch as far as I know).

---

### Post by robert shearer on 2010-03-18
> **WarrenL said:**
> Well folks, I'm up and running with an auto-login.

Congratulations, well done and welcome.
The hard stuff is done and now it is all fun.

Like the 'boot races' you're having :) cool.

---

### Post by WarrenL on 2010-03-18
Thanks folks, your help was absolutely critical in getting me this far, and I've had a great Linux education along the way. I might even have a go at rebuilding my own desktop with a minimum installation now that I've seen what it's done for my boy's creaky old collection of parts.

With regard to the boot times, I must point out that in both instances the time involved includes the BIOS doing its thing, memory checks etc - about 12-15 seconds for each. Both machines are running Albatron motherboards - a KX600S Pro in the case of mine. I don't know if Albatrons are particularly slow, but I feel they take longer than other machines I know.

Considering that XP took more than 2 minutes to complete the same task on my machine, I reckon 58.5 seconds is pretty damn good!

Thanks again, folks.

---

### Post by t1nm@n on 2010-03-18
Dude there isa distro called Austrumi based on slax it works out of the box ....
[http://distrowatch.com/table.php?distribution=Austrumi](http://distrowatch.com/table.php?distribution=Austrumi)

also try out SliTaz only 25mb containing all the software u need.

[http://distrowatch.com/table.php?distribution=slitaz](http://distrowatch.com/table.php?distribution=slitaz)

goodluck.

---

### Post by imperius69 on 2010-03-18
> **WarrenL said:**
> Thanks folks, your help was absolutely critical in getting me this far, and I've had a great Linux education along the way. I might even have a go at rebuilding my own desktop with a minimum installation now that I've seen what it's done for my boy's creaky old collection of parts.

With regard to the boot times, I must point out that in both instances the time involved includes the BIOS doing its thing, memory checks etc - about 12-15 seconds for each. Both machines are running Albatron motherboards - a KX600S Pro in the case of mine. I don't know if Albatrons are particularly slow, but I feel they take longer than other machines I know.

Considering that XP took more than 2 minutes to complete the same task on my machine, I reckon 58.5 seconds is pretty damn good!

Thanks again, folks.

nice one :) congrats

btw, as a web browser u can try this one that i found

[http://kazehakase.sourceforge.jp/](http://kazehakase.sourceforge.jp/)

look in synaptic for kazehakase, seems very cool and light on ressies

and if you need a fast and simple image viewer try this mirage

[http://mirageiv.berlios.de/index.html](http://mirageiv.berlios.de/index.html)

also on synaptic.

---

### Post by dzon65 on 2010-03-18
Mirage takes only 1% more than gpicview,but,it has slideshow.

---

### Post by imperius69 on 2010-03-18
> **dzon65 said:**
> Mirage takes only 1% more than gpicview,but,it has slideshow.

hahahah

You read the same page as i did :p

---

### Post by dzon65 on 2010-03-18
LOL.Yeah,don't do anything but lightweight installs.I use gpic and mirage on all of them.Okay,scrolling gpic's window does the job as well,but the wife likes this slideshow stuff mirage does.Besides,it's a nice looking thing.Can't really remember that site.Was it the guy who changed his sister's pc?If so,could you post a link?If I recall,there was something that caught my attention on there.

---

### Post by imperius69 on 2010-03-18
here it is

[http://www.linux.com/archive/feature/128940](http://www.linux.com/archive/feature/128940)

---

### Post by dzon65 on 2010-03-18
Ah,thanks.
Kind regards,J.

---

### Post by javyn999 on 2010-03-18
I intend to do a Ubuntu minimal install and put lxde on top of that when 10.04 comes out on my older laptop.

I installed lxde to play around with in Karmic, and discovered the bug that prevents the file manager from remembering file associations.

After digging around a bit, I found the fix.  Apparently, the current "shared mime info" file in the Ubuntu repository is buggy. 

Do a google search and download shared-mime-info_0.60-1_i386.deb

Then do:

sudo dpkg -i shared-mime-info_0.60-1_i386.deb

Log out, log back in, problem solved.  Hope I helped.

edit:  Also, as far as browsers go, I can't recommend Chrome enough.  Firefox is HORRID, Opera is better and faster, but still has trouble playing flash video, but Chrome has been perfect all around.  First time in my year of using Ubuntu that I've been able to watch fullscreen youtube videos without lagging out my system.

---

### Post by bodhi.zazen on 2010-03-18
> **t1nm@n said:**
> Dude there isa distro called Austrumi based on slax it works out of the box ....
[http://distrowatch.com/table.php?distribution=Austrumi](http://distrowatch.com/table.php?distribution=Austrumi)

also try out SliTaz only 25mb containing all the software u need.

[http://distrowatch.com/table.php?distribution=slitaz](http://distrowatch.com/table.php?distribution=slitaz)

goodluck.

+1 to both those distros.

---

### Post by WarrenL on 2010-03-18
> **javyn999 said:**
> ...as far as browsers go, I can't recommend Chrome enough.

Please correct me if I'm wrong, but I thought Google Chrome for Linux was still at some half-formed alpha phase of development.

[IMG]http://www.qtl.co.il/img/copy.png[/IMG][[IMG]http://www.google.com/favicon.ico[/IMG]]("http://www.google.com/search?q=I%20intend%20to%20do%20a%20Ubuntu%20minimal%20install%20and%20put%20lxde%20on%20top%20of%20that%20when%2010.04%20comes%20out%20on%20my%20older%20laptop.%0D%0A%0D%0AI%20installed%20lxde%20to%20play%20around%20with%20in%20Karmic,%20and%20discovered%20the%20bug%20that%20prevents%20the%20file%20manager%20from%20remembering%20file%20associations.%0D%0A%0D%0AAfter%20digging%20around%20a%20bit,%20I%20found%20the%20fix.%20Apparently,%20the%20current%20%22shared%20mime%20info%22%20file%20in%20the%20Ubuntu%20repository%20is%20buggy.%0D%0A%0D%0ADo%20a%20google%20search%20and%20download%20shared-mime-info_0.60-1_i386.deb%0D%0A%0D%0AThen%20do:%0D%0A%0D%0Asudo%20dpkg%20-i%20shared-mime-info_0.60-1_i386.deb%0D%0A%0D%0ALog%20out,%20log%20back%20in,%20problem%20solved.%20Hope%20I%20helped.%0D%0A%0D%0Aedit:%20")[IMG]http://www.babylon.com/favicon.ico[/IMG]

---

### Post by javyn999 on 2010-03-18
I'm running 5.03 Beta.  

Great stuff so far.  The minimalistic layout took getting used to, but I really don't miss the buttons anymore.  Typing everything into the address bar is actually nice and efficient.

As I said before, it runs Flash video GREAT.  I don't understand how...or why.  I know Flash and Linux do not play well together, but I assumed this was due to the Flash plugin rather than the browser.  I have no idea how Google managed to make it as smooth as Windows, even in full screen.  

Also, Chrome seems to be compatible with more sites than Opera, as much as I hate to say it.

---

### Post by imperius69 on 2010-03-18
i tried Chrome, didn't work that well for me. Also tried SeaMonkey, now that worked very well on my old box.

---

### Post by javyn999 on 2010-03-18
On something that old, yeah.

---

### Post by imperius69 on 2010-03-18
> **javyn999 said:**
> On something that old, yeah.

we are trying to install on old machines yes!!!

---

### Post by javyn999 on 2010-03-18
Although I've never tried it, I hear Midori can't be beat for computers that old...

---

### Post by dzon65 on 2010-03-19
> **javyn999 said:**
> I intend to do a Ubuntu minimal install and put lxde on top of that when 10.04 comes out on my older laptop.

I installed lxde to play around with in Karmic, and discovered the bug that prevents the file manager from remembering file associations.

After digging around a bit, I found the fix.  Apparently, the current "shared mime info" file in the Ubuntu repository is buggy. 

Do a google search and download shared-mime-info_0.60-1_i386.deb

Then do:

sudo dpkg -i shared-mime-info_0.60-1_i386.deb

Log out, log back in, problem solved.  Hope I helped.

edit:  Also, as far as browsers go, I can't recommend Chrome enough.  Firefox is HORRID, Opera is better and faster, but still has trouble playing flash video, but Chrome has been perfect all around.  First time in my year of using Ubuntu that I've been able to watch fullscreen youtube videos without lagging out my system.

+1 Great!Thanks.

---

### Post by dzon65 on 2010-03-19
> **bodhi.zazen said:**
> +1 to both those distros.


+1 Yes.Tried slitaz on a veeery low spec and worked nicely.No language support (so far) however.

---

### Post by WarrenL on 2010-03-19
I've just been trying Midori and Google Chrome on the box of old bits the kicked this thread off, and I have to report that Midori aces Chrome for perceived speed at least, on an old machine like that. I'm a long time Firefox user, so I really don't know how either of those two stack up in terms of features, etc, but Midori definitely felt a lot faster.

---

### Post by imperius69 on 2010-03-19
> **WarrenL said:**
> I've just been trying Midori and Google Chrome on the box of old bits the kicked this thread off, and I have to report that Midori aces Chrome for perceived speed at least, on an old machine like that. I'm a long time Firefox user, so I really don't know how either of those two stack up in terms of features, etc, but Midori definitely felt a lot faster.

try seamonkey from the repos

---

### Post by bodhi.zazen on 2010-03-19
> **dzon65 said:**
> +1 Yes.Tried slitaz on a veeery low spec and worked nicely.No language support (so far) however.

What language do you need ?

It has English support.

Form : [http://www.slitaz.org/en/doc/releases/2.0/relnotes.en.html](http://www.slitaz.org/en/doc/releases/2.0/relnotes.en.html)

> The distribution is available in English, German, French and Portuguese - in all 26 keymappings are available. The project website and  documentation are also available in different languages and **other language packs  (locale) can be installed via the package manager**.Emphasis added my me.

---

### Post by dzon65 on 2010-03-19
> **bodhi.zazen said:**
> What language do you need ?

It has English support.

I'm ok with English (native language's Dutch).Slitaz comes in English and French.(unless that's changed)Might be a bit difficult for some.But,like I said,good distro.In fact,it's one of the few that really ran well on very low spec pc.Nice job for such a low footprint.
Edit:just took alook.German and Spanish are also available.

---

### Post by imperius69 on 2010-03-19
Just tried out midori, was very good
but on the repos is a very old version so i went to lok for a new one.

go to these pages and do what they say, adding key and new repo and then go to synaptic and the new version of midori will be there to install.

[https://launchpad.net/~midori/+archive/ppa](https://launchpad.net/~midori/+archive/ppa)
[https://launchpad.net/~webkit-team/+archive/ppa](https://launchpad.net/~webkit-team/+archive/ppa)


bye

imp.L

---

### Post by WarrenL on 2010-03-19
Thanks for that imperius. It turns out I was running an old version - I've just upgraded thanks to your links.

---

### Post by imperius69 on 2010-03-20
just found out by accident that google maps dont work with midori.

!hehehe! 8-[

ps - but yahoo maps works, stange thing!!
ps2 - hahaha, if u change midori identification to safari, now google maps work!!

---

### Post by haddog on 2010-03-20
I would try Puppy Linux. it runs great on old pc's

---

### Post by WarrenL on 2010-03-21
I gave Puppy Linux a go, and you're right, it runs great. But I felt it just didn't have the right look and feel: I wanted something for my son that kept within the familiar Gnome/Xfce framework, with good Ubuntu/Debian compatibility.

The Minimal Ubuntu/Xfce combination seems to be just perfect so far.

---

### Post by WarrenL on 2010-03-23
I should probably put this in a new thread, but I thought you guys who've helped me so much already might spot it first if it was here.

The creaky box of bits (Ubuntu Minimal and Xfce) has a Via 8235 sound chipset in it, and now that it has its own speakers plugged in I've discovered it's not working. I've already googled up a bit of gobbledygook about AlsaMixer but it's all a bit difficult to understand at my level.

What do I need to get the sounds cranking?

---

### Post by KIAaze on 2010-03-23
cf [http://ubuntuforums.org/showthread.php?t=1425815](http://ubuntuforums.org/showthread.php?t=1425815)

It seems the minimum required packages are:
```
alsa-base
alsa-utils
alsa-oss
gstreamer0.10-alsa
libasound2
libasound2-plugins

```

---

### Post by WarrenL on 2010-03-24
Duh! I had another go at it and found that hiking up the PCM volume solved the problem. It was working the whole time!

There is a small problem though. Upon startup the volume controls are all muted. Every time a coconut. Any suggestions?

I'm going to keep track of that list of packages though KIAaze - it might just come in handy in future.

Anyhow, a certain 6-year-old boy is thrilled to bits with the SuperComputer and has been busy playing Widelands (perfectly happily with only 224 Mb of RAM) for at least the last 24 hours solid I think.

---

### Post by k3lt01 on 2010-03-24
> **WarrenL said:**
> Anyhow, a certain 6-year-old boy is thrilled to bits with the SuperComputer and has been busy playing Widelands (perfectly happily with only 224 Mb of RAM) for at least the last 24 hours solid I think.And that is the important thing. Glad it has all worked out for you even if the sound does mute on reboot.

---

### Post by haddog on 2010-04-02
> **WarrenL said:**
>  Anyhow, a certain 6-year-old boy is thrilled to bits with the SuperComputer and has been busy playing Widelands (perfectly happily with only 224 Mb of RAM) for at least the last 24 hours solid I think.

Glad it you found a solution that works. Have not come across that volume muting issue.

---

### Post by warfacegod on 2010-04-02
If no one's mentioned it yet, try SliTaz. It is hands down the fastest and smallest OS I've ever seen. Full graphical interface with a 30 MB (yes Megs) .iso. I run it off of a 4 GB USB jump drive.

---

### Post by javyn999 on 2010-04-03
My parents have been using Ubuntu since I put it on their computer, and like it, but often complain it's very slow.

They have a Pentium p4 1 ghz, 512 ram.  I was considering puppy for them, but it seems a little too complicated to just install to the hard drive rather than running off a cdrom or flash drive, which I don't want them to have to do.

---

### Post by hahnemann on 2010-04-03
Definitely I will buy more Ram and install Xubuntu in the PC.

Greets!

---

### Post by empty_spaces on 2010-04-03
I haven't read all the suggestions in this thread but you might also want to consider Linux Mint 8 LXDE. I just tried out the livecd, and it looked pretty good.

Here's the link:
[http://www.linuxmint.com/rel_helena_lxde.php](http://www.linuxmint.com/rel_helena_lxde.php)

---

### Post by warfacegod on 2010-04-03
> **empty_spaces said:**
> I haven't read all the suggestions in this thread but you might also want to consider Linux Mint 8 LXDE. I just tried out the livecd, and it looked pretty good.

Here's the link:
[http://www.linuxmint.com/rel_helena_lxde.php](http://www.linuxmint.com/rel_helena_lxde.php)

You can get the same result by installing the LXDE desktop from Synaptic. I stopped using Mint when I found out that their updates do not include Kernel upgrades which is a bad idea. LXDE can be pretty swift too.

---

### Post by javyn999 on 2010-04-03
Is Linux Mint updated when Ubuntu is?  Or is it a deal when 10.04 comes out, Mint will just be getting up to 9.10?

---

### Post by empty_spaces on 2010-04-03
Since Mint is based off Ubuntu, it tends to come out 2-3 months after Ubuntu. Mint Gnome is usually released first, followed by the KDE version.
In fact, the Fluxbox and LXDE versions of Mint were just released 4 days ago, about 5 months after Ubuntu.

---

### Post by bodhi.zazen on 2010-04-04
> **javyn999 said:**
> Is Linux Mint updated when Ubuntu is?  Or is it a deal when 10.04 comes out, Mint will just be getting up to 9.10?

Speaking from personal experience, on of the "problems" with basing a distro on Ubuntu (Mint or otherwise) is that the Ubuntu Alpha - Beta is not really "stable" . There are problems in working with those versions and the more complex your customization the harder it is.

What I mean by stable, almost all the packages are updated several times during the development cycle and there may be a time when updates cause breakage.

Now if you are doing a light weight respin, such as Crunchbang, it may not affect you as much. But if you are doing something as complex as Mint, you need to wait for the release, wait for the major bug fixes, then start your customizations. Thus there will be a delay between the release of Ubuntu and your respin.

Unless of course you wish to do all the bug fixes yourself, which would more then likely break compatibility with Ubuntu ...

In my case, with Zenix, we are going with a 1 month delay, Zenix 10.05 rather then 10.04.

---

### Post by JoeNZ on 2010-04-06
I have been using Crunchbang 9.04 for several weeks now. On my old machine (P4 1.5ghz - 1gb ram) it works really well.

---

