---
title: "I want to play a DVD now"
date: 2009-12-29
forum: New to Ubuntu
---

### Post by Chris Edgell on 2009-12-29
All the learning I'm trying to do is for one purpose: to understand enough to do things with the computer.  

I have Sound, I have Totem installed, I thought I could stick a DVD in and it would begin to play, but no.....

Can we do this?  Here's my screenshot:

---

### Post by lisati on 2009-12-29
You might need to install some more codecs to let your system play encrpyted DVDs

Have a look here: [https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

---

### Post by Gone fishing on 2009-12-29
There are a few things you need to do.

Install the restricted extras, then goto [http://www.medibuntu.org/](http://www.medibuntu.org/) and follow the instructions on the Repository Howto and you will be able to play DVDs. I also suggest you install VLC and SMPlayer as they are much better media players.

---

### Post by Mahngiel on 2009-12-29
'sudo apt-get install ubuntu-restricted-extras'

this will download and install all the codecs you should need to play mp3s and movies.

---

### Post by thatguruguy on 2009-12-29
go into Synaptic (System>Administration>Synaptic Package Manager) and install the "ubuntu-restricted-extras" package and libdvdread4.

---

### Post by Chris Edgell on 2009-12-29
Okay, I have gone into Synaptic and both the package and the libdvdread4 were marked as installed.  My click brought me reinstall, so I did.  Now I opened the Totem and presssed play, pressed open...nothing.  Now what, shall I install one of those other DVD players, or are thre some finer points about how to work this Totem player...I can overlook the most seemingly obvious things.

Any ideas now or suggestions...

---

### Post by Chris Edgell on 2009-12-29
lisati, (hi)
I went to that link you posted and found:


Ubuntu 9.04 and 9.10 (i386, amd64)

      Install the libdvdread4 package (no need to add third party repositories) via Synaptic or command line: 

 sudo apt-get install libdvdread4

    * Then open a terminal window and execute: 

 sudo /usr/share/doc/libdvdread4/install-css.sh



SO, since I installed lib.. via synaptic, shall I now go and put that sudo line into the terminal?

---

### Post by HappyFeet on 2009-12-29
Just copy and paste the following (all at once) into a terminal and press enter
```
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
```
then
```
sudo apt-get install libdvdcss2
```
enjoy your movie.

---

### Post by Mahngiel on 2009-12-29
the sudo line i recommended is just a shortcut.  When i first began using Ubuntu, i was afraid of it.  Then i realized it was much quicker to install something that i knew the name of, instead of sifting through Synaptic Package Manager.

however you do it, you'll need the codecs from "ubuntu-restricted-extras".

you can use synaptic to find it and click the box, or you can use the terminal. 
if you choose the terminal, the input is:
```
sudo apt-get install ubuntu-restricted-extras
```

however you do it, it'll work the same, and shoudl get your dvd to play. enjoy.

---

### Post by Chris Edgell on 2009-12-29
I went and put that line into the terminal and this is the output in the screenshot.
It seemed to be asking for my password and I tried to type it in but it wasn't showing any type.  Why would that be?

---

### Post by Some Penguin on 2009-12-29
Because there might be somebody looking over your shoulder.

---

### Post by lisati on 2009-12-29
> **Chris Edgell said:**
> I went and put that line into the terminal and this is the output in the screenshot.
It seemed to be asking for my password and I tried to type it in but it wasn't showing any type.  Why would that be?

Type it in as normal. It is "hidden" as a security precaution.

---

### Post by Chris Edgell on 2009-12-29
Like last time, I get that, is it a password request?

Here's the screenshot.

---

### Post by zoglesby on 2009-12-29
> **Chris Edgell said:**
> I went and put that line into the terminal and this is the output in the screenshot.
It seemed to be asking for my password and I tried to type it in but it wasn't showing any type.  Why would that be?

This is a security measure, so that no one steals your password.Just type in your password, slowly if you have to insure its right, and hit enter.

---

### Post by Chris Edgell on 2009-12-29
It's working!

Thanks very much to all

And a happy new year!

---

### Post by Sir Jasper on 2009-12-29
Hi,

Is your DVD running in Totem or did you have to install VLC or another program?

My regards

---

### Post by Chris Edgell on 2009-12-29
Yes it is running in Totem.  However, I'm wondering if I should try another player; what do you use?

---

### Post by spiky001 on 2009-12-29
i use VLC you can get it easy from software package

---

### Post by Sir Jasper on 2009-12-29
Hi,

I use VLC which I installed after I spent about 90 minutes trying (though failing) to get Totem to play my DVD properly.

My regards

PS I spent about another four hours reading and testing before getting VLC to work. Anyway, congratulations and well done getting Totem to work.

---

### Post by sandy8925 on 2009-12-29
Better still just install mplayer. Plays just about anything and everything.

---

### Post by Chris Edgell on 2009-12-29
If I were to try....no...that's the thing...why would I go to try that if this one is working perfectly well.

If I do want to try it, I guess I would just install it and then uninstall this one, or I guess if I have the space, I can just have both until I would decide.

I see it so often here, something works immediately for one and takes hours for another, but when I hear it took 4 hours for you to get VLC working, I do resort to the old advise, "If it ain't broke, don't fix it."

---

### Post by issih on 2009-12-29
The main issue with playing dvds on linux is the dvdcss package...which is what you installed by entering the command into the terminal.

Once that is in place almost any media player will be okay.

I think I'm right in saying that vlc and mplayer have their own specific built in code for decoding mpeg2 content (which is what dvds actually are) and consequently once the dvdcss issue is solved (which it now is in your case) both should work fine...obviously there are no guarantees though.

Totem on the other hand uses a framework called gstreamer for video and audio playback, and the default install of gstreamer does not have mpeg2 playback codecs installed. Therefore to play DVDs in totem you also need the restricted extras package, which pulls in the necessary gstreamer plugins.

Hope that helps clarify things a bit.

---

### Post by Chris Edgell on 2009-12-29
Very good clarification, issih.

---

### Post by lfanterickson on 2009-12-29
I'm learning how to read and use Ubuntu, and have made great strides, especially with Totem.  I finally got DVDs to play, but one DVD stalled with 30 minutes to go (maybe a cat nudged my mouse and it clicked on something?), I can't get Totem to search forward or backward, and I can't get to the seecond movie on the disk.  I'd also like to get to the Special Features.  I hope I'm  just missing one command fix...Please help!  Thanks!

I think I ran across something addressing these issues, but can't remember where.

---

### Post by Sir Jasper on 2009-12-29
Hi Ifanterickson,

This thread is marked ¨solved¨ so you are more likely to get individual help by opening a new thread describing your particular problem(s).

---

### Post by SuperSonic4 on 2009-12-29
Compiled mplayer :D - you can add all kinds of stuff (such as x264 encoding)

Although repo mplayer and vlc are pretty good

---

### Post by pacofvf on 2009-12-30
same problem easier solution: install mplayer, you may use it or not but it comes with all plugins you need 
```

sudo apt-get install mplayer

```

---

