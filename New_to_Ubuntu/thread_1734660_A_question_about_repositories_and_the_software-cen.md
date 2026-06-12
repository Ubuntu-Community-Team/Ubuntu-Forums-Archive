---
title: "A question about repositories and the software-center."
date: 2011-04-20
forum: New to Ubuntu
---

### Post by StarZtorm on 2011-04-20
So im thinking about this thing that has me a little bit frustrated. Ofcourse this is due to the fact that i am new to the operating system but anyhow, let me get on with this. 

The software center is a great tool for me. To find programs and games and just install with a click is fantastic for me. Problem is that when games (like widelands and openttd) are released in newer versions, the new versions dont appear in the software center.

For me, the dream would be to install a game, and whenever a new build was released it would show up in the update manager. This is not how it works ofcourse, but it would be lovely if it did. 

But anyway, Installing the new release of Widelands forexample, seems like a bit more complicated process.. Ive been at their site, and its like i have to install some extra contents and stuff, by running codes in the terminal and so on.. 

All im saying is.. wouldnt it be great if it worked like this:

The devs releasing a new build of a game sends a mail to Canonical, and tells them theres a new version of the game. Canonical includes it in the software manager, replaces the old build with the new one, and then when you launch the software manager on your comp, it would have a message saying "hey, theres a new version of blablabla available". 

So i asked the guys over at widelands irc channel "hey, why doesnt the new build appear in Ubuntu's software manager?" The answer i got had something to do with a feature freeze. 

So now im asking you guys: Why isnt new builds appearing in the software manager?


(Oh, and thanks for reading :)

---

### Post by mikewhatever on 2011-04-20
Let's be realistic here, Canonical is a relatively small company, and doesn't have the man power to test and package every single game and program there is. That's exactly where the community steps in.

PS: I don't know what's up with the PPA for Widelands, it looks like every single package there failed to build. Perhaps you should learn how to package and help the maintainer.:P

---

### Post by GWBouge on 2011-04-20
One great thing about the software center is that you can add repositories instead of just relying on Ubuntu's main repo's.  For widelands:

[https://launchpad.net/~timo-wingender/+archive/ppa]("https://launchpad.net/~timo-wingender/+archive/ppa") (Edit: which according to the person above me, doesn't work, sry)

There is also [PlayDeb.net]("http://www.playdeb.net/welcome/"), who houses quite a few games, and more recent versions of games that are already in Ubuntu's repo's, and it looks like widelands is in there.  Dunno which version, though.

As far as the games in Ubuntu's repos being a bit out of date ... I really don't mind, especially since you can often just add the ppa from the game developers themselves, but I'd rather see the Ubuntu dev's and maintainers working on Ubuntu than continuously checking random 3rd party software packages to put in their repositories.  =o)

---

### Post by StarZtorm on 2011-04-20
> **GWBouge said:**
> One great thing about the software center is that you can add repositories instead of just relying on Ubuntu's main repo's.  For widelands:

[https://launchpad.net/~timo-wingender/+archive/ppa]("https://launchpad.net/~timo-wingender/+archive/ppa") (Edit: which according to the person above me, doesn't work, sry)

There is also [PlayDeb.net]("http://www.playdeb.net/welcome/"), who houses quite a few games, and more recent versions of games that are already in Ubuntu's repo's, and it looks like widelands is in there.  Dunno which version, though.

As far as the games in Ubuntu's repos being a bit out of date ... I really don't mind, especially since you can often just add the ppa from the game developers themselves, but I'd rather see the Ubuntu dev's and maintainers working on Ubuntu than continuously checking random 3rd party software packages to put in their repositories.  =o)

Cool thanks, im gonna have to look more into that. I dont know how to add a repository, i dont even know what a PPA is. whoa man, i got some reading to do. But this was a good answer, thanks.

---

### Post by madmax75 on 2011-04-20
Basically PPA's are additional software repositories for Ubuntu. With them you can add programs that are not in the default software repositories, and they usually contain newer versions of the programs that are in the default repos.

Here's how to add them:

Lucid Lynx 10.04 LTS

[https://help.ubuntu.com/10.04/add-applications/C/adding-repos.html#adding-ppa](https://help.ubuntu.com/10.04/add-applications/C/adding-repos.html#adding-ppa)

Maverick Meerkat 10.10

[https://help.ubuntu.com/10.10/add-applications/C/adding-repos.html#adding-ppa](https://help.ubuntu.com/10.10/add-applications/C/adding-repos.html#adding-ppa)
[]("https://help.ubuntu.com/9.10/add-applications/C/adding-repos.html")
Also, check out the Ubuntu Tweak program. With that you can easily add some useful repositories (Medibuntu, LibreOffice, Mozilla Firefox Stable etc.).

[http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)

---

### Post by perspectoff on 2011-04-20
I personally like to add repositories with the command (from a command-line terminal):

 sudo add-apt-repository ppa:user/ppa-name

That's two steps (one step is opening the command-line terminal).

To add repositories through a package manager takes 4-5 steps.

Besides, then I can just install a package with a single additional command (which takes 2 more steps in a package manager).

But that's just me. I like efficiency. (It's partly what computers are all about.)

---

### Post by mikewhatever on 2011-04-20
There is a version of Wideland for Ubuntu 10.04 on playdeb.
[http://www.playdeb.net/updates/ubuntu/10.04/?q=wideland](http://www.playdeb.net/updates/ubuntu/10.04/?q=wideland)

---

