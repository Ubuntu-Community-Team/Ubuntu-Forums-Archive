---
title: "ubuntu/kubuntu/xubuntu - I feel so stupid!"
date: 2009-11-04
forum: New to Ubuntu
---

### Post by anewguy on 2009-11-04
Well, I've read many posts here with some mentioning the specific benefits of one version (not release) over another depending on circumstances.  I'm familiar enough with the "default" Ubuntu - getting the Gnome desktop, and I've also install kubuntu in the past but then decided to just add the kde desktop to my "default" Ubuntu so I could decide what session I wanted.  I've seen mention of xubuntu, but never really paid much attention.  Having just moved from an extremely small town to a large city this summer, this week I discovered a huge computer store much like the ones I was used to in the very early days of home computing - all kinds of OEM parts, etc., plus all the regulars.  They also had a CD of xubuntu for a couple of bucks so I got it just to see what it was like.  Well, I booted the livecd and now I'm a little confused - perhaps I'm not the only one?

Could someone explain just exactly what the differences really are between ubuntu, kubuntu, xubuntu, edubuntu, the media center edition, etc.?  i'm sure there must be a post somewhere that details all of this and suggests where each might be the better choice (perhaps hardware differences,etc.), but I haven't found it yet.

I'm not a dumb guy, but suddenly I feel really stupid!

Thanks in advance!
Dave :)

---

### Post by The Funkbomb on 2009-11-04
The difference between Ubuntu, Kubuntu and Xubuntu is the desktop environment.  Ubuntu uses GNOME, Kubuntu uses KDE and Xubuntu uses XFCE.

This is a very easy to use table to see what's going on with your DE.

[http://en.wikipedia.org/wiki/Comparison_of_X_Window_System_desktop_environments](http://en.wikipedia.org/wiki/Comparison_of_X_Window_System_desktop_environments)

---

### Post by LunaticHiatus on 2009-11-04
It will probably be best to explain how you build ubuntu from the ground up.

Ok, if you install Ubuntu Minimal. You will get to command line and thats it. You then will need a windowing system. So you would apt-get the X window system. This is basically a command line in a window. No taskbar, no walpaper, nothing. Just a window with command line so you could lunch something like a browser that needs a window.

You then could install the Gnome desktop and you would get a regular ubuntu install (actually, ubuntu minimal has a lot of technical setting not turned on by default. But it would be very close to a regular ubuntu install). Gnome is a bunch of programs that offer everything from a text editor (gedit) to a windows decorator and the Gnome taskbar. Most of these programs use the GTK toolkit. The gtk toolkit which makes running and managing these programs easier.

The Gnome project focuses on ease of use.

You could have also installed the kde desktop and it would essentially be Kubuntu. Which also has a bunch of programs (most of which begin with K) and uses the QT toolkit which is considered a little bloated but very fancy looking. KDE suffered a bad reputation with its latest update since it crashed a lot and was very buggy out of beta. I heard its a bit better now.

Or you could install the XFCE desktop and essentially have Xubuntu. XFCE is also based on the GTK toolkit and from what I have seen, uses about the same amount of memory however the default programs tend to less memory then Gnome's (like XFCE uses Mousepad text editor, as opposed to the memory using gedit text editor)

there is also LXDE which is very small desktop. Moreso then XFCE but has a dumb logo. (well, it does) (some guys are making a lubuntu I heard)

You can also install things like Fluxbox which is just a windows manager (to make the windows prettier then just flat, unmovable X) and a taskbar. You access everything from right clicking. (fluxbuntu is fluxbox with something to keep in track of the wallpaper, desktop icons, and default programs)

Or Openbox (which is fluxbox without the taskbar basically to make it even lighter) Crunchbang (which is a ubuntu based distro) uses openbox with its own taskbar, etc. etc. etc.


or enlightenment (I never really understood what enlightenment really is supposed to be exactly. Weird I guess.)

Edubuntu is Ubuntu with a focus on schools and education. Media center ubuntu I assume is for installing on a media center so you can play movies and such on your tv with it.

---

### Post by undecim on 2009-11-04
Each variant of ubuntu is nothing more that the ubuntu base system with certain packages installed by default. The main visual difference is the Desktop Environment; That is, the interface that you use.

With Ubuntu, you have GNOME, with Kubuntu, you have KDE, and with Xubuntu, you have Xfce.

Each of these works exactly the same under the hood, but look entirely different and come with different applications. For example, Kubuntu has k3b preinstalled for burning CDs, whereas Ubuntu has Brasero, because each one works best with its respective desktop environment.

Most people recommend Xubuntu for older systems, because Xfce is lightweight, and uses less resources.

Each of these are the same system, just with a different mask on. In fact, if you were to delete all the packages of the default Ubuntu and install all the packages for of the default Kubuntu install, you would have the exact same setup as if you installed from a Kubuntu CD.

The same rules apply for flavors like Ubuntu Studio and Edubuntu, except rather than different desktop environments, they have certain other packages preinstalled. Again, you can just take an Ubuntu install and install the same packages as one of those two and get the same setup.

---

### Post by stderr on 2009-11-04
Essentially they're all identical with different packages installed by default. Canonical could release a new version called "Allbuntu" with Gnome, KDE and XFCE packages :)

You may find this helpful: [https://help.ubuntu.com/community/MetaPackages]("https://help.ubuntu.com/community/MetaPackages")

---

### Post by mivo on 2009-11-04
> **LunaticHiatus said:**
> XFCE is also based on the GTK toolkit and from what I have seen, uses about the same amount of memory 

Is what you have seen Xubuntu? Xubuntu is bloated and nearly as heavy as the regular Ubuntu. If you install Xfce4 using a minimal Ubuntu CD or in Arch, it uses about a quarter to a third of the RAM that Gnome wants.

In Arch, a fresh Xfce4 install with Midori, Mousepad, htop and wicd (a network manager) running uses around 70 MB of RAM. Gnome's usage, under similar conditions, is closer to 300 MB. I imagine that setting up Xfce4 after a minimal Ubuntu install will yield comparable results.

Xubuntu however is a poor example to measure Xfce4 by. It's riddled with Gnome stuff.

---

### Post by LunaticHiatus on 2009-11-04
> **mivo said:**
> Is what you have seen Xubuntu? Xubuntu is bloated and nearly as heavy as the regular Ubuntu. If you install Xfce4 using a minimal Ubuntu CD or in Arch, it uses about a quarter to a third of the RAM that Gnome wants.

In Arch, a fresh Xfce4 install with Midori, Mousepad, htop and wicd (a network manager) running uses around 70 MB of RAM. Gnome's usage, under similar conditions, is closer to 300 MB. I imagine that setting up Xfce4 after a minimal Ubuntu install will yield comparable results.

Xubuntu however is a poor example to measure Xfce4 by. It's riddled with Gnome stuff.

Wat? I am running gnome now with firefox (three tabs and addons) and compiz on KK and it uses 243 mb. without compiz running on first boot, it idles around 130. XFCE idles round 130 for me as well (or at least the last time I used it). I can get 80mb with ubuntu minimal + lxde + wicd. (it doesnt matter what minimal browser you install when you first login. Its not like it has a module or is cached on first boot)

---

### Post by mivo on 2009-11-04
Then perhaps Ubuntu is the problem. :) In Arch, the aforementioned xfce4 installation used exactly 69 MB RAM according to htop. It's the default xfce4 package with wicd. I didn't think it would be necessary to take a screenshot, but you can verify this in a VM session, I guess.

---

### Post by LunaticHiatus on 2009-11-04
eh, I choose slackware over arch for a minimal distro. don't care for that rolling (broken) release stuff. Actually, that might have something to do with it.

---

### Post by mivo on 2009-11-04
I prefer rolling release distros, and I don't have trouble with them. Slack's still alive? I recall reading recently that the hostile community drove off the returning founder. But anyway, it's off topic here. :) I only wanted to point out that Xubuntu doesn't give an accurate idea of how light Xfce4 is.

---

### Post by Padsz on 2009-11-04
ubuntu uses gnome kubuntu uses KDE and xubuntu uses XFCE

---

### Post by praveesh on 2009-11-04
> **LunaticHiatus said:**
> It will probably be best to explain how you build ubuntu from the ground up.

Ok, if you install Ubuntu Minimal. You will get to command line and thats it. You then will need a windowing system. So you would apt-get the X window system. This is basically a command line in a window. No taskbar, no walpaper, nothing. Just a window with command line so you could lunch something like a browser that needs a window.

You then could install the Gnome desktop and you would get a regular ubuntu install (actually, ubuntu minimal has a lot of technical setting not turned on by default. But it would be very close to a regular ubuntu install). Gnome is a bunch of programs that offer everything from a text editor (gedit) to a windows decorator and the Gnome taskbar. Most of these programs use the GTK toolkit. The gtk toolkit which makes running and managing these programs easier.

The Gnome project focuses on ease of use.

You could have also installed the kde desktop and it would essentially be Kubuntu. Which also has a bunch of programs (most of which begin with K) and uses the QT toolkit which is considered a little bloated but very fancy looking. KDE suffered a bad reputation with its latest update since it crashed a lot and was very buggy out of beta. I heard its a bit better now.

Or you could install the XFCE desktop and essentially have Xubuntu. XFCE is also based on the GTK toolkit and from what I have seen, uses about the same amount of memory however the default programs tend to less memory then Gnome's (like XFCE uses Mousepad text editor, as opposed to the memory using gedit text editor)

there is also LXDE which is very small desktop. Moreso then XFCE but has a dumb logo. (well, it does) (some guys are making a lubuntu I heard)

You can also install things like Fluxbox which is just a windows manager (to make the windows prettier then just flat, unmovable X) and a taskbar. You access everything from right clicking. (fluxbuntu is fluxbox with something to keep in track of the wallpaper, desktop icons, and default programs)

Or Openbox (which is fluxbox without the taskbar basically to make it even lighter) Crunchbang (which is a ubuntu based distro) uses openbox with its own taskbar, etc. etc. etc.


or enlightenment (I never really understood what enlightenment really is supposed to be exactly. Weird I guess.)

Edubuntu is Ubuntu with a focus on schools and education. Media center ubuntu I assume is for installing on a media center so you can play movies and such on your tv with it.

Kde may be bloated . But no one say qt bloated .

---

### Post by anewguy on 2009-11-04
Well, most of this stuff I already knew, and I know that the base is all the same, but I was thinking more along the lines of if there is any advantages to one over the other for a beginner who scans the forum and sees the various types.  As far as gnome and KDE go, that's pretty straight forward, but as mentioned in this thread, I was under the impression that xubuntu was lighter, and therefore more suited for older, less robust hardware.  I have always had one question though concerning the term lighter - is it just that certain things, like the window manager, are easier on memory, etc., or does the package itself come with fewer of the extras, things like office, etc.?  Way back in my day, lighter leaned more toward fewer packages, etc., because everyone then was concerned with memory.  

I know it was sort of a open-for-interpretation type of question, but for the beginner coming on board, a brief explanation of the benefits, if any, of one particular type over the other, especially when it comes to the hardware and the expected use of the machine are concerned.

Slackware?  Messed with that about 1994 or 1995 - back when I was still working as a systems programmer and systems admin.  Was fun then - but now in my old age I just like something to "work" - and I give Ubuntu credit for the strides made.  I haven't looked at Slackware in years, but it always used to be more of the old-fashioned type of hacker distribution, you know, us old guys who used to like digging around inside of stuff to make it work.  Is it still that way or has it gone to a more "mature" marketing angle as well?



Thanks for the input!

Dave :)

---

### Post by LunaticHiatus on 2009-11-04
slackware really has no corporate marketing, its still a bit of a hacker distro but its a lot easier to install then people think. I found slackware easier to install then arch even.

but yeah, XFCE is supossed to be "lighter" because it uses less memory but xubuntu is not all that much lighter on memory. Idling around the same usage as gnome. (although one dude implied that its just a xubuntu thing, not an xfce thing)

either way, LXDE, Openbox, flubox, blackbox, icewm, FVWM are all lighter alternatives to xfce.

---

### Post by running_rabbit07 on 2009-11-04
> **mivo said:**
> Then perhaps Ubuntu is the problem. :) In Arch, the aforementioned xfce4 installation used exactly 69 MB RAM according to htop. It's the default xfce4 package with wicd. I didn't think it would be necessary to take a screenshot, but you can verify this in a VM session, I guess.

Ya just gotta get it to install first. Ubuntu is best for a reason. Maybe Debian's XFCE version would be suitable.

---

