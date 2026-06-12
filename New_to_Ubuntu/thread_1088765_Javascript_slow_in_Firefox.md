---
title: "Javascript slow in Firefox"
date: 2009-03-06
forum: New to Ubuntu
---

### Post by damonjablons on 2009-03-06
Hey!

I think it may have something to do with my Nvidia drivers because firefox seems to hook into them, but whenever I run a page that has any javascript at all, things can get painfully slow.

For instance, on gmail, to scroll a page length can take a full 30 seconds.

I tried installing (and using) epiphany using webkit, but it crashes constantly, and I love my firefox plugins <3

Is there any way I can speed up the javascript engine in FF, or is there a Free Software alternative that won't crash?

I like opera (free as in beer), but I don't think it has my beloved Firebug, and I'm a web developer.

Any help is **greatly** appreciated.  Thanks!

-dj:KS

---

### Post by binbash on 2009-03-06
firefox 3.1b has 3x js speed than 3.0.x, however some plugins do not work

---

### Post by damonjablons on 2009-03-06
> **binbash said:**
> firefox 3.1b has 3x js speed than 3.0.x, however some plugins do not work

how can I upgrade to 3.1?

---

### Post by avtolle on 2009-03-06
That's in beta form, if this is important to you. Not having looked into this, I think you would need to go to the Firefox site and download the source code (unless there is a .deb package out there somewhere) and then compile and install it. Someone who has more knowledge/experience can certainly correct me and give you better instructions.

---

### Post by avtolle on 2009-03-06
Here's a link: [http://www.mozilla.com/en-US/firefox/all-beta.html](http://www.mozilla.com/en-US/firefox/all-beta.html)

---

### Post by SamNSane on 2009-03-06
If you've decided to go for the Firefox 3.1 beta you might want to use this repository instead. If you follow the instructions at the link below, you'll be adding the repository and key for the Ubuntu Mozilla Daily Build Team. Might be a easier and better-supported (with continuing updates) way to do it.

You might also consider the possibility that the slowness of your current browser may be due to conflicts among various extension installed in the browser.

That being said, I think that you intuition that your nVidia drivers may play some part in problems with the browser (or, maybe, vice versa) could be accurate. There are lots of people who see serious performance issues of various kinds with JREs / Flash in Firefox under Ubuntu on systems that have nVidia display subsystems.

I have a system that overheats and goes into thermal shutdown if I'm not careful about what I'm doing with the browser. I've tried to help others who have the same problem, and we've come to more or less the same conclusions.

---

### Post by damonjablons on 2009-03-06
> **SamNSane said:**
> If you've decided to go for the Firefox 3.1 beta you might want to use this repository instead. If you follow the instructions at the link below, you'll be adding the repository and key for the Ubuntu Mozilla Daily Build Team. Might be a easier and better-supported (with continuing updates) way to do it.

which repository?  i think you forgot the link!

---

### Post by zika on 2009-03-06
> **damonjablons said:**
> how can I upgrade to 3.1?
go to [http://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-mozilla-1.9.1/](http://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-mozilla-1.9.1/) and pick up and download archive You want (32, 64). make a direcory ~/firefox. do from ~ in terminal ```
sudo tar -xvf firefox-3.1b4pre.en-US.linux-x86_64.tar.bz2
```(note that name is for 64 bit archive) and change the line in ~/firefox/firefox to read: moz_libdir=~/firefox.
start it with Alt-F2 ~/firefox/firefox. enjoy!

if You want to try FF 3.2 then go to [http://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-mozilla-central/](http://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-mozilla-central/) and do the same as written above with appropriate name ... ;)

You can change directory to Your convenience ...

I forgot to say: if You install it this way You can use this version of FF on a daily basis, You can make it default browser (System->Preferences->Preffered Applications->Browser->~/firefox/firefox) and everything You do with "incorporated" FF but You always have a backup: updated "official" version of FF. they share settings and plugins and all. I do update on a sort-of daily basis from these nightly directories.  You can go back and forth from 3.1 to 3.2 with just unpacking required archive. You can even make automated update with some sort of cron. yes, I like to try everything new but I like my Ubuntu to stay as much as it can be close to "initial" state ... this way it does. I did not uninstall NetworkManager. I disabled it. 

3.1 and 3.1 are different lines of development of FF, 3.1 is a branch that has its end and mozilla-central is a line that will, eventually, give a branch for 3.2 and go further ...

sorry if I sound like advertisement, that was not my intention. I just like 3.2 ... ;) it's just like JJ at this moment, KK in future and so on. (no, I did not try JJ)

---

### Post by SamNSane on 2009-03-06
> **damonjablons said:**
> which repository?  i think you forgot the link!

It could be that I am a moron. Here it is.

[https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa](https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa)

Sorry about that.

It's a really good way to go, because the builds are created by people in the Ubuntu dev community.

---

### Post by damonjablons on 2009-03-06
> **SamNSane said:**
> It could be that I am a moron. Here it is.

[https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa](https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa)


gracias!  i'm pretty sure i could've just done a google search and found that (doh!), so maybe i'm the moron.

thanks again!

---

### Post by SamNSane on 2009-03-06
Whatever you do, please let us know how it goes. Stories -- both happy and dire -- are grist for the mill around here!

;)

---

