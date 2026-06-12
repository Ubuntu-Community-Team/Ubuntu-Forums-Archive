---
title: "Trouble playing wmv files"
date: 2010-05-01
forum: New to Ubuntu
---

### Post by lolzwut on 2010-05-01
I downloaded a bunch of wmv files and they don't work on mplayer. I searched for codecs but there weren't any that supported those files. I installed vlc player and it doesn't work on that either. It gives me this error:[COLOR=#ff0000]
[/COLOR]
[COLOR=#ff0000]No suitable decoder module:[/COLOR]
 [COLOR=#000000]VLC does not support the audio or video format "MSS2". Unfortunately there is no way for you to fix this.[/COLOR]


[COLOR=#000000]I don't understand why it says MSS2 though because clearly it's a wmv. Anyone know how to fix this problem?
[/COLOR]

---

### Post by Marlonsm on 2010-05-01
Go to the Ubuntu Software Centre and install Ubuntu Restricted Extras.
It's a pack containing lots of codecs and things like Flash Player.
I'm not sure if it'll sove your problem, but it's worth a try and it's always good to have it installed.

---

### Post by mc4man on 2010-05-01
Vlc is pretty good at identifying codecs - mss2 (microsoft screen codec) is a type of wmv

Your best and pretty much only player for decoding mss2 is a 32 bit mplayer with w32codecs installed.
So if you can provide a 32 bit mplayer then download and install w32codecs from here. (pick your release and browse the package list, ect.

If you're using a 64 bit ubuntu then you'll need to do a bit of work

[http://packages.medibuntu.org/](http://packages.medibuntu.org/)

---

### Post by lolzwut on 2010-05-01
> **Marlonsm said:**
> Go to the Ubuntu Software Centre and install Ubuntu Restricted Extras.
It's a pack containing lots of codecs and things like Flash Player.
I'm not sure if it'll sove your problem, but it's worth a try and it's always good to have it installed.

That didn't change anything but thanks for the tip :)



> **mc4man said:**
> Vlc is pretty good at identifying codecs - mss2 (microsoft screen codec) is a type of wmv

Your best and pretty much only player for decoding mss2 is a 32 bit mplayer with w32codecs installed.
So if you can provide a 32 bit mplayer then download and install w32codecs from here. (pick your release and browse the package list, ect.

If you're using a 64 bit ubuntu then you'll need to do a bit of work

[http://packages.medibuntu.org/](http://packages.medibuntu.org/)


yeah unfortunately I have a 64bit. So to fix that all I have to do is install w64codecs?

---

### Post by mc4man on 2010-05-01
> So to fix that all I have to do is install w64codecs?
No, w64 codecs are worthless

A few ways (you may not like any

build a 32 mplayer (which can use w32codecs in a 64 bit install (this I've done - works quite well but isn't a simple task

install a pre-built 32 bit mplayer ( never tried, but I think it's possible

Install wine and run a windows mplayer build - depending on mplayer build you use ranges from very easy to a little  bit more. 
( there are some limitations in the wine route as far as playback and or quality

Edit - while for the really easy wine way the mplayer build I remember is no longer available did work out a quick (5 min or less ) way to use the smplayer windows build (mplayer is inc.)
Works quite well, plus with a minute or so extra can add the ability to r. click on a mms2 .wmv and have it open and play in smplayer 
scrren shows a mms2 in the win smplayer

---

