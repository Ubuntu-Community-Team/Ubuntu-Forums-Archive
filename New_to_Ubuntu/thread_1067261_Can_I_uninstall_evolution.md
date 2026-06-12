---
title: "Can I uninstall evolution?"
date: 2009-02-11
forum: New to Ubuntu
---

### Post by joegra on 2009-02-11
I have installed Thunderbird as my email solution, I use it on my Windows machines and like it. I would like to uninstall Evolution, if possible. Can anyone help? Thank you.

---

### Post by lazyart on 2009-02-11
Yeah, you can... but it breaks the ubuntu-desktop package.  Ubuntu will still run, but come update time you'll miss stuff because ubuntu-desktop is no longer "installed".

I prefer and use Thunderbird as well.  I just ignore Evolution.

---

### Post by joegra on 2009-02-11
> **lazyart said:**
> Yeah, you can... but it breaks the ubuntu-desktop package.  Ubuntu will still run, but come update time you'll miss stuff because ubuntu-desktop is no longer "installed".

I prefer and use Thunderbird as well.  I just ignore Evolution.

Thank you I will ignore it aswell

---

### Post by anjilslaire on 2009-02-11
I uninstall the top 2 (forget the names atm) evolution files on every install I have of ubuntu. Just open synaptic, search evolution, and check them for removal. Nothing else breaks, and you save a few MBs space and Evolution is no longer in your menu. 

There may be traces of it in the system somewhere, but for all intents and purposes its uninstalled. I update everything else just fine, all the time.

---

### Post by bgs100 on 2009-02-11
I uninstalled evolution without touching the ubuntu-desktop package. Got prism-google-mail and thunderbird

---

### Post by Gramps on 2009-02-11
I use TB also, one day I decided that I didn't use evolution so I would delete it> So I deleted all packages that had the word evolution in them, that should get rid of it right. Everything was fine the rest of the day. The next morning when I fired up the computer and logged in all I had was the main Ubuntu screen which is mainly the wallpaper. Both menu bars were gone. It took me a little to remember that I had deleted evolution the day before. Reinstalled the evolution-desktop stuff and all was well. So now I just leave it alone, guess it really isn't hurting anything.

Now my question would be why does the desktop need an email program to run?

---

### Post by Ciwan on 2009-02-20
> **Gramps said:**
> Now my question would be why does the desktop need an email program to run?

Good question, I would like to know the answer too ! ... please.

Thank you.

---

### Post by s.fox on 2009-02-20
> **Ciwan said:**
> Good question, I would like to know the answer too ! ... please.

Thank you.

You have sparked my interest.  I shall do a little research...

---

### Post by mc4100 on 2009-02-20
You need the Evolution 'email client' to run a desktop because it comes with more than just a client. Specifically e-d-s which is populates the calender in the clock applet with appointments. Also, ever used the "About Me" dialog...

---

### Post by Ciwan on 2009-02-20
Thanks MC4100

I now know a little bit more .. but still why put them other things along with evolution ?

Why not have a separate package (i'm not sure if that is the right word) that has all them "other things" ... so that people who don't like evolution (I'm one of them, I like Thunderbird more) can uninstall it without problems to their beautiful Ubuntu !!

Thank You.

---

### Post by jlimon on 2009-04-06
> **mc4100 said:**
> You need the Evolution 'email client' to run a desktop because it comes with more than just a client. Specifically e-d-s which is populates the calender in the clock applet with appointments. Also, ever used the "About Me" dialog...

That seems like a cause for a bug report in itself.. why should such small tasks be given to such a big (and largely useless) program?

I know a lot of GNOME developers will huff and puff about it being their super cool "default" client, but Ubuntu has already rejected their defaults two times that I know. 1) Firefox instead of Epiphany and 2) Pidgin instead of Telephany.

I think those were great decisions and it would be awesome if they made #3 getting rid of Evolution from the base install.

---

### Post by diskotek on 2009-04-06
> **jlimon said:**
> That seems like a cause for a bug report in itself.. why should such small tasks be given to such a big (and largely useless) program?

I know a lot of GNOME developers will huff and puff about it being their super cool "default" client, but Ubuntu has already rejected their defaults two times that I know. 1) Firefox instead of Epiphany and 2) Pidgin instead of Telephany.

I think those were great decisions and it would be awesome if they made #3 getting rid of Evolution from the base install.

what is Telephany? can you a link?

well evolution is sort of all in one solution. it's nice but claws-mail is just enough for me. but there are many people who uses it. i think it's nice for office users. may be not for us ):P

---

### Post by jlimon on 2009-04-10
> **diskotek said:**
> what is Telephany? can you a link?

well evolution is sort of all in one solution. it's nice but claws-mail is just enough for me. but there are many people who uses it. i think it's nice for office users. may be not for us ):P

Wow, I was way off with the name.. it's EMPATHY. [http://live.gnome.org/Empathy](http://live.gnome.org/Empathy)

I have since switched to Mutt and think Evolution is a broken piece of crufty crap. :)

---

### Post by ubudog on 2009-04-10
Sure just open a terminal and type sudo apt-get remove evolution.

---

### Post by jlimon on 2009-04-10
> **ubudog said:**
> Sure just open a terminal and type sudo apt-get remove evolution.

That "solution" is getting a little tired. Having to lose ubuntu-desktop because of Evolution is a bit lame.

---

### Post by Xamiga on 2009-04-10
Perhaps there is a (Evolution==Internet Explorer) hiccup.....):P
Seriously, Linux should never have a problem like this.

---

### Post by jlimon on 2009-04-10
No kidding. Nobody I know personally uses Evolution. Everyone who isn't serious about Email uses Webmail and everyone who IS serious about email doesn't LIKE Evolution.

Someone said above that the main selling point of Evolution is that it's the upstream's default.

Well, so is Epiphany and Empathy - we use Firefox and Pidgin.

Honestly, I think Ubuntu would be better off including a Firefox shortcut to GMail by default because that's what most people use.

---

### Post by joey-elijah on 2009-04-10
I always tried to like evolution, but it really never works very well for myself without googling, tweaking and having to put up with duplicate e-mails. Thunderbird is flawless straight from the get-go. 

I usually 'remove' it by deleting its menu entry.

---

### Post by jrothwell97 on 2009-04-10
Well, speaking as someone who uses Evolution and likes it, there are ways to remove it without breaking too much of the system. As long as you simply remove the evolution metapackage without touching the Evolution Data Server, you should be OK.

---

### Post by jlimon on 2009-04-10
> **joey-elijah said:**
> 

I usually 'remove' it by deleting its menu entry.

Yeah, that's my current "solution" - I just smile and pretend it ain't there.

It's really the only application that Ubuntu ships with that I just really outright dislike. I mean, I use flickr and rarely use F-Spot, but I think F-Spot is a great piece of software and am glad its included. Same with Rhythmbox even though I use Banshee.

---

### Post by jlimon on 2009-04-10
Yeah, but that's just the thing.. it'd be trickier to "Deveolve" Ubuntu than to "Devolve" desktop installs. And that's the biggest thing.

People typically want to be able to remove applications they don't like and don't want to have their system less supported as a result.

> **jrothwell97 said:**
> Well, speaking as someone who uses Evolution and likes it, there are ways to remove it without breaking too much of the system. As long as you simply remove the evolution metapackage without touching the Evolution Data Server, you should be OK.

---

### Post by ibuclaw on 2009-04-10
> **jlimon said:**
> No kidding. Nobody I know personally uses Evolution. Everyone who isn't serious about Email uses Webmail and everyone who IS serious about email doesn't LIKE Evolution.

Someone said above that the main selling point of Evolution is that it's the upstream's default.

Well, so is Epiphany and Empathy - we use Firefox and Pidgin.

Honestly, I think Ubuntu would be better off including a Firefox shortcut to GMail by default because that's what most people use.

Have you heard of **prism**?
```
sudo apt-get install prism-google-mail
```
And then add it to your gnome-panel, osx-style dock, desktop, or whatever you use ;)

Also, sidenote ... if Ubuntu were to make a shortcut the default... what about people who don't use GMail???

I use GMX, myself, I personally don't want to see Google anywhere on my desktop. :)

Regards
Iain

---

### Post by jlimon on 2009-04-10
I don't personally use or even like GMail, I'm just going with a majority here.

(I love mutt :) )

> **tinivole said:**
> 

I use GMX, myself, I personally don't want to see Google anywhere on my desktop. :)

Regards
Iain

Really? I've heard some pretty nasty/awful things about GMX. I considered using them but bought a fastmail account after reading their reviews.

EDIT: Oh, and also.. a simple firefox shortcut is a LOT simpler to remove than having to risk ditching the ubuntu-desktop metapackage and potentially break crucial parts of GNOME, dontchathink?

---

### Post by rivenathos on 2009-04-10
I also give a +1 for GMX email.  I have not had any problems with their web interface, and it works great with Thunderbird (as well as Evolution).  GMX also has a good XMPP/Jabber server which runs fine with Pidgin.  My experiences have been positive.

As for removing Evolution, I have no problem with it sitting on the computer.  I can either use it, not use it, or hide it in the menu.  Yes, it can be removed, but you have to break the meta-package and then manually reinstall the parts that are necessary for other functionality.  It can be fun and educational if you are thusly inclined.

---

### Post by mikewhatever on 2009-04-10
> **jlimon said:**
> That "solution" is getting a little tired. Having to lose ubuntu-desktop because of Evolution is a bit lame.

I don't have ubuntu-desktop installed and keep getting regular updates. What's all the fuss about?
ubutnu-desktop package doesn't men anything unless one is planning to upgrade (not update) the system today. As for removing evolution, it's safe to remove evolution and evolution-data packages.

> **jlimon said:**
> No kidding. Nobody I know personally uses Evolution. Everyone who isn't serious about Email uses Webmail and everyone who IS serious about email doesn't LIKE Evolution.

Someone said above that the main selling point of Evolution is that it's the upstream's default.

Well, so is Epiphany and Empathy - we use Firefox and Pidgin.

Honestly, I think Ubuntu would be better off including a Firefox shortcut to GMail by default because that's what most people use.

Sounds like pure and pointless bashing. You don't want evolution, the solution is simple, don't use it.

---

### Post by meho_r on 2009-04-10
Although I personally like Evolution and use it on daily basis, it would be nice to have a possibility to uninstall it easily. Integration with desktop is OK, but integration to that level that desktop doesn't function properly without a singe app isn't, no matter what app that is. 

On the other side, don't forget Ubuntu's philosophy &#8212; Linux for human beings. Following that philosophy implies many "guesses" (don't forget that Ubuntu isn't Arch or Gentoo where you make almost all decisions yourself). It is expected that people need a PIM for their daily work, and if you take a look at what apps are there for the purpose, you'll end up with Evolution. It's simply natural choice. Like OpenOffice and other apps. If there were a better one, devs would probably have it included instead.


> **jlimon said:**
> 
No kidding. Nobody I know personally uses Evolution. Everyone who isn't serious about Email uses Webmail and everyone who IS serious about email doesn't LIKE Evolution.

Give me a break :roll:

---

### Post by trlkly on 2009-04-10
You see, I find Evolution so bad that I installed KDE-PIM for my PIM needs.

But I find that the average person uses a cell phone or PDA for their PIM needs. And since syncing is a pain-in-the-neck on Linux...

I really think the average person sees Evolution as an email client with PIM extras that they never use.

My personal problem with Evolution? Any time I add contacts, I have to wait as if the computer is adding a 1 MB file for each contact. And if you add too many, the program crashes. 

I think Evolution fails at trying to do too many things at once. It's mail system is merely adequate, and I've already told how bad the PIM features are. We don't need an Outlook clone.

---

### Post by Stupendoussteve on 2009-04-10
I am on Jaunty and have removed Evolution, yet still have the ubuntu-desktop package. It was not difficult. Maybe they fixed the dependancies of the ubuntu-desktop metapackage, I don't know.

The only thing that tried to remove ubuntu-desktop and others was evolution-data-server, evolution-documentation-en, and evolution-webcal.

---

### Post by jlimon on 2009-04-10
> **Stupendoussteve said:**
> I am on Jaunty and have removed Evolution, yet still have the ubuntu-desktop package. It was not difficult. Maybe they fixed the dependancies of the ubuntu-desktop metapackage, I don't know.

The only thing that tried to remove ubuntu-desktop and others was evolution-data-server, evolution-documentation-en, and evolution-webcal.

```
$ sudo apt-get remove evolution
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  evolution evolution-exchange evolution-indicator evolution-plugins
0 upgraded, 0 newly installed, 4 to remove and 189 not upgraded.
After this operation, 10.8MB disk space will be freed.
Do you want to continue [Y/n]?
```

Weird, you're right.

Maybe they're already making Evolution optional.. I just never heard about it before. Score!

EDIT: I was able to remove rdesktop for the first time.. I've never been able to do that without taking ubuntu-desktop with it!

---

### Post by jlimon on 2009-04-10
> **trlkly said:**
> You see, I find Evolution so bad that I installed KDE-PIM for my PIM needs.

But I find that the average person uses a cell phone or PDA for their PIM needs. And since syncing is a pain-in-the-neck on Linux...

I really think the average person sees Evolution as an email client with PIM extras that they never use.

My personal problem with Evolution? Any time I add contacts, I have to wait as if the computer is adding a 1 MB file for each contact. And if you add too many, the program crashes. 

I think Evolution fails at trying to do too many things at once. It's mail system is merely adequate, and I've already told how bad the PIM features are. We don't need an Outlook clone.

Evolution has gotten progressively worse since Ximian dissolved into Novell.

---

### Post by meho_r on 2009-04-10
> **trlkly said:**
> You see, I find Evolution so bad that I installed KDE-PIM for my PIM needs.

But I find that the average person uses a cell phone or PDA for their PIM needs. And since syncing is a pain-in-the-neck on Linux...

I really think the average person sees Evolution as an email client with PIM extras that they never use.

My personal problem with Evolution? Any time I add contacts, I have to wait as if the computer is adding a 1 MB file for each contact. And if you add too many, the program crashes. 

I think Evolution fails at trying to do too many things at once. It's mail system is merely adequate, and I've already told how bad the PIM features are. We don't need an Outlook clone.

Kontact on KDE is very good app indeed. Still, Evolution does meet some average needs in an average office. I like integration with Gnome and support for Google calendars, just to mention these two feats. POP3 and IMAP works flawlessly, I have access to all my mails in one place, search function is very good... it has all features one PIM needs... I've been using it for about 2 years now and haven't had any problems at all. MS Outlook is a little bit clumsy app, but it isn't that bad;) But, at the end, it IS preference thing.

And so this thread went off-topic :D Question was about uninstalling Evolution and at the end it "evolved" to "I like it", "I like it not"...

---

### Post by jlimon on 2009-04-10
I must also add, when I removed evolution and ran autoremove to clean up packages, it did NOT catch "evolution-common" which contains its .desktop files and as a result, its menu entries.

So be sure to remove it also!

---

### Post by k3lt01 on 2009-04-10
> **jlimon said:**
> Honestly, I think Ubuntu would be better off including a Firefox shortcut to GMail by default because that's what most people use.Who said most people use Gmail? I would seriously doubt that and would think it is a Google marketing ploy to suggest such a thing.

> **jrothwell97 said:**
> As long as you simply remove the evolution metapackage without touching the Evolution Data Server, you should be OK.Thats what I do.

---

### Post by diskotek on 2009-04-21
> **jlimon said:**
> Wow, I was way off with the name.. it's EMPATHY. [http://live.gnome.org/Empathy](http://live.gnome.org/Empathy)

I have since switched to Mutt and think Evolution is a broken piece of crufty crap. :)

thank you for the link :)

i'm cool with claws-mail :)

---

### Post by andrew.46 on 2009-04-22
Hi tinivole,

> **tinivole said:**
> 
I use GMX, myself, I personally don't want to see Google anywhere on my desktop. :)

It is possible to use [gmail as nothing more than a relay]("http://ubuntuforums.org/showthread.php?t=1021746") while using such excellent software as mutt. This way you will not actually *see* Google :-). Mind you I believe that GMX offers POP3 and IMAP access as well?

Andrew

---

### Post by barney385 on 2009-04-22
> **jlimon said:**
> That seems like a cause for a bug report in itself.. why should such small tasks be given to such a big (and largely useless) program?

I know a lot of GNOME developers will huff and puff about it being their super cool "default" client, but Ubuntu has already rejected their defaults two times that I know. 1) Firefox instead of Epiphany and 2) Pidgin instead of Telephany.

I think those were great decisions and it would be awesome if they made #3 getting rid of Evolution from the base install.

Yes, this has been discussed in the past and I find this joined at the hip e-mail client to be very windowsesque...

As far as I'm concerned this goes against the open-source philosophy IMO.

---

### Post by stimpyaw on 2010-03-09
> **jlimon said:**
> ```
$ sudo apt-get remove evolution
 Reading package lists... Done
 Building dependency tree       
 Reading state information... Done
 The following packages will be REMOVED:
   evolution evolution-exchange evolution-indicator evolution-plugins
 0 upgraded, 0 newly installed, 4 to remove and 189 not upgraded.
 After this operation, 10.8MB disk space will be freed.
 Do you want to continue [Y/n]?
```Weird, you're right.
 
 Maybe they're already making Evolution optional.. I just never heard about it before. Score!
 
EDIT: I was able to remove rdesktop for the first time.. I've never been able to do that without taking ubuntu-desktop with it![FONT=Verdana, sans-serif][SIZE=1]
[/SIZE][/FONT]
> **jlimon said:**
> I must also add, when I removed evolution and ran autoremove to clean up packages, it did NOT catch "evolution-common" which contains its .desktop files and as a result, its menu entries.

So be sure to remove it also!

[FONT=Verdana, sans-serif][SIZE=2]I have had the same problem in a older version of Ubuntu. When I attempted to remove Evolution it would "break" my system. meaning that the system would boot and be able to login. I was only left with the wall paper, I had panels or menu items. That was Ubuntu version 6.06, I'm currently using 8.10 now and I did these steps 'jlimon' outlined and it worked like a charm!! WOOHOO!!

As for Evolution, it seems like a great program and I did give it try when I 1st started with Ubuntu (6.06). It would crash, lock up and or take a while to load. Currently I don't have an email client installed, I'm using my Gmail account for now.[/SIZE][/FONT]

---

