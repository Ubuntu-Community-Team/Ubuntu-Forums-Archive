---
title: "Live Magic -  wrong release name"
date: 2011-03-21
forum: New to Ubuntu
---

### Post by Jay_E on 2011-03-21
Greetings to all.

I'm not sure if I know what I'm doing - or this is a bug.

I have installed Ubuntu 10.10 and have been updating.
I used Ubuntu Software center to download the package "live-magic"

Executive summary:
It failed looking for "Squeeze" in a URL that had The ubuntu names -
natty, maverick...

Details.

[LIST=1]
[*]  installed Live-magic out of Ubuntu Software Center
[*]Ran Applications -> Accessories -> LiveMagic ; Observed normal "Debian Live Magic" startup
[*]Chose "Standard Debian Gnu/Linux image
[*]At "What distribution of Debian would you like to build?", I chose Testing(squeeze)
[*]Chose ISO image for a CD or DVD as media type for target
[*]Chose default as mirror - [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/)
[*]Chose "Yes, integrate the Debian Installer"  [COLOR=DarkGreen]This may be where I strayed from the path...[/COLOR]
[*][COLOR=DarkGreen][COLOR=Black]Chose Locale and Keyboard layout.[/COLOR][/COLOR]
[*][COLOR=DarkGreen][COLOR=Black]Chose default build folder (my home)[/COLOR][/COLOR]
[*][COLOR=DarkGreen][COLOR=Black]Kicked it off and selected to view the details.[/COLOR][/COLOR]
[*][COLOR=DarkGreen][COLOR=Black]See this message "E: Failed getting release file [/COLOR][/COLOR][http://us.archive.ubuntu.com/ubuntu/dists/squeeze/Release](http://us.archive.ubuntu.com/ubuntu/dists/squeeze/Release)
[/LIST]
OK. I took a look at [http://us.archive.ubuntu.com/ubuntu/dists](http://us.archive.ubuntu.com/ubuntu/dists)
It had directories for dapper, hardy, jaunty, karmic, lucid, maverick and natty.

Is this a bug? Or should I not be using a Debian tool for Ubuntu dists??

Thanks in advance,
Jay
:)

---

### Post by jocko on 2011-03-21
> **Jay_E said:**
> Greetings to all.

I'm not sure if I know what I'm doing - or this is a bug.

I have installed Ubuntu 10.10 and have been updating.
I used Ubuntu Software center to download the package "live-magic"

Executive summary:
It failed looking for "Squeeze" in a URL that had The ubuntu names -
natty, maverick...

Details.

[LIST=1]
[*]  installed Live-magic out of Ubuntu Software Center
[*]Ran Applications -> Accessories -> LiveMagic ; Observed normal "Debian Live Magic" startup
[*]Chose "Standard Debian Gnu/Linux image
[*][COLOR=Red]At "What distribution of Debian would you like to build?", I chose Testing(squeeze)[/COLOR]
[*]Chose ISO image for a CD or DVD as media type for target
[*]Chose default as mirror - [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/)
[*]Chose "Yes, integrate the Debian Installer"  [COLOR=DarkGreen]This may be where I strayed from the path...[/COLOR]
[*][COLOR=DarkGreen][COLOR=Black]Chose Locale and Keyboard layout.[/COLOR][/COLOR]
[*][COLOR=DarkGreen][COLOR=Black]Chose default build folder (my home)[/COLOR][/COLOR]
[*][COLOR=DarkGreen][COLOR=Black]Kicked it off and selected to view the details.[/COLOR][/COLOR]
[*][COLOR=DarkGreen][COLOR=Black]See this message "E: Failed getting release file [/COLOR][/COLOR][http://us.archive.ubuntu.com/ubuntu/dists/squeeze/Release](http://us.archive.ubuntu.com/ubuntu/dists/squeeze/Release)
[/LIST]
OK. I took a look at [http://us.archive.ubuntu.com/ubuntu/dists](http://us.archive.ubuntu.com/ubuntu/dists)
It had directories for dapper, hardy, jaunty, karmic, lucid, maverick and natty.

Is this a bug? Or should I not be using a Debian tool for Ubuntu dists??

Thanks in advance,
Jay
:)

My guess is that live-magic does exactly what it say it does. It tries to build a debian live cd, and it needs to download packages from the debian repos to do so.
If that's what you want to do, you need to add the debian repos to your /etc/apt/sources.list. But that will very likely mess things up seriously in your ubuntu install, so I would not do it if I were you...

---

### Post by Jay_E on 2011-03-21
Thanks, Jocko,

But I do not think that is the problem.

The failure *appears* to be that the code of this version of live magic is asking for squeeze (Debian), not a Ubuntu release.

FYI, I also tried "no" to the question of integrating the Debian installer.
Same error occurred
Jay

---

