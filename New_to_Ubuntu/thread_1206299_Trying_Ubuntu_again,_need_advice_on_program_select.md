---
title: "Trying Ubuntu again, need advice on program selection."
date: 2009-07-07
forum: New to Ubuntu
---

### Post by TwanDeezy on 2009-07-07
Hey everyone, I've decided to try Ubuntu once again (I don't know if I want to buy an Acer Aspire One netbook, or just use my old Dell Latitude D600; help me decide on that as well).. Anyway, below is a list of stuff I want to do with it, and I hope you folks could tell me exactly what programs would work, and which ones are the best.

For the majority of the day (8 to 10 hours), my system will be used as a media player.  I want to save my music (downloaded, copied from CD's, etc.) on the laptop and listen throughout the day while working at my desk.  I can't connect through wi-fi at the office, but its in a 3g area, so I might setup my phone to use as a modem.  This is a reason I would like the netbook, easier to carry around and such.  But either way, what would you consider my best option for a music player?  I want to be able to organize all of my music, and I'll probably use download helper to save videos from the net onto the hard drive (see below)

Next primary use is internet, that's self-explanatory, sticking with firefox.  But any "necessary add-ons" other than the download helper?  

Games: those small random games that can be found through synaptic, (I personally like foobillard to kill time, and for some reason my girlfriend LOVES angry drunken dwarves).  Also, I would like to somehow get the latest Sims game installed and running (See below, once again).  Any other linux-based or linux compatible games that you guys think I would enjoy? I like RPG's and RTS's, word games, sudoku-type stuff, etc..

Desktop Virtualization:  I want to be able to run MicroXP inside of a virtual desktop.  Pretty simple, what's the best virtualization program (free of course)

typing/word processing, no need to explain this one, Open Office.

Some sort of accounting/finance program (or maybe a pre-built OOo spreadsheet to help me keep up with that stuff).  I'm an independent contractor, and I want to keep all my money info easily accessible.  I have a checkbook spreadsheet saved on my laptop, but if there's a better open source program out there, that would be awesome.

MAC-style dock.  no explanation needed, which one offers the most customizing options?

themes/wallpaper packages - guess I'll search gnome look, i just hate the original orange and brown stuff.  my ideal color schemes are nature or abstract inspired, with dark blues or greens, something calm and peaceful

So, that's about all I can think of at the moment.  Thanks for your input and advice.

---

### Post by jbrown96 on 2009-07-07
For a media player, I suggest Songbird or Amarok. Songbird is pretty cool. It's got all kinds of web-based stuff built-in; it even has firefox, so you don't need to run that separately. The only problem that I've had is that it doesn't perform very well, especially searching. It's slow if you have a decent sized collection (mine is ~6000). I like Amarok a lot, but they just did a re-write for their 2.0 release, so there are a few features still missing. I really like to dynamic playlists. It's a KDE program, so it will drag in quite a few dependencies, but nothing too unreasonable. Since it's developing quickly, you should keep up-to-date. At kubuntu.com there are instructions to add a repository that will keep you updated to the newest version. 

For virtualization, I recommend Virtualbox. I'm not too sure how happy you will be with virtualization on either of those laptops though. Virtualbox is very simple and has a great setup/manager utility. the USB pass-through is cool (it allows the guest OS to natively use USB devices), but requires the proprietary version, which is available for free from virtualbox.org (or maybe .com I can't remember). One thing to note is that after you download the package and install it, you need to add yourself to the vboxusers group. Easiest way is to ```
sudo usermod -aG vboxusers $USER
``` the $USER will automatically use the current username, but if other users need to be able to run virtualbox, then repeat and replace with their name. 

For docks, kiba-dock has some cool options, but I think they are mostly eye-candy. It's also (or at least used to be) fairly difficult to setup. Gnome-do is a very popular task launcher, and they now have a setting to turn it into a dock. I tried it almost a year ago, and it worked well, but was pretty basic. It was a new feature at the time, so maybe they have added functionality. I would definitely try gnome-do first because it's much easier to install/remove. 

Add-ons for Firefox, I would recommend Ad-block plus and possibly no-script. The first keeps a blacklist of advertisers, so they don't take up space in the browser. It works very well, and it would be particularly good on a 3g modem where bandwidth and capcity is limited. That way you don't spend time and money downloading ads. No-script blocks javascript and flash, so it blocks lots of advertising and dramatically improves security when browsing, but I've found it to be really annoying. It makes most pages unusable until you allow most scripts, which puts you right back in the original position, but you've wasted time allowing each one. I would also recommend updating to Firefox-3.5. It's a separate download now ```
sudo apt-get install firefox-3.5
``` but it's a great improvement over 3.0.x.

---

### Post by ainsworth_t on 2009-07-07
You can probably get a thousand replies to this thread because everyone has their favorite picks for software because there are so many options available. So I guess I'll put in my two cents. I'm still primarily a Windows XP user, but from what I've used with Ubuntu so far, these are the programs I've come to like.

> But either way, what would you consider my best option for a music player? 
I've found Rhythymbox, the default audio player, to suit my needs (organizing music, listening to Shoutcast stations, etc). If this doesn't do it for you, check out Songbird.

Best option for video player in my opinion is VLC.

> But any "necessary add-ons" other than the download helper? 

That's really up to you I guess.

> Any other linux-based or linux compatible games that you guys think I would enjoy?

Check these out, you might find something you like:
[http://techgage.com/article/top_10_free_linux_games/](http://techgage.com/article/top_10_free_linux_games/)
[http://www.icculus.org/lgfaq/gamelist.php](http://www.icculus.org/lgfaq/gamelist.php)
[http://linuxgames07.blogspot.com/2007/09/top-21-linux-games-of-2007.html](http://linuxgames07.blogspot.com/2007/09/top-21-linux-games-of-2007.html)

> Pretty simple, what's the best virtualization program (free of course)

VirtualBox - you can either install the Open Source Edition from the repository (virutalbox-ose), or download a binary installer for the full edition from the [website]("http://www.virtualbox.org").

> Some sort of accounting/finance program

Never used one, but it seems like GnuCash is pretty standard for that. You could also check these out: [http://www.linuxjournal.com/article/5669](http://www.linuxjournal.com/article/5669)

> MAC-style dock. no explanation needed, which one offers the most customizing options?

Avant Window Navigator (aka Awn) - can be installed from the repositories, and you can find themes all over the internet

> themes/wallpaper packages

I'm pretty partial to Blubuntu, which is available in the repositories, though the package is a little broken, so you have to install the *gtk2-engines-ubuntulooks* package before the *blubuntu-theme* package.

And then there is always these sites with tons of options:
[Gnome Look]("http://www.gnome-look.org")
[Gnome Art]("http://art.gnome.org")

Also, if you're unsure about your transition to Ubuntu, try running it in a VM within Windows (using VirtualBox mentioned above) or maybe try a dual-boot environment either by true installation or using the [Wubi Installer]("http://wubi-installer.org")

Hope this helps!

---

