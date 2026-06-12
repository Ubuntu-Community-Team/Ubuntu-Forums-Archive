---
title: "Movie Player Very Choppy"
date: 2008-12-15
forum: New to Ubuntu
---

### Post by bcondemi111 on 2008-12-15
Not sure why, maybe setting, but any movie I play is real choppy and slow.

Same movies/video on the drive plays fine on the windows partition, but on the Ubuntu os, video very slow. 

Installed VLC media player package and is a lot better but not smooth flowing. 

My video card is fine with the right 3d driver ect.....

Is there a setting perhaps that will play smoother? maybe another player?

Also, How do I choose a default player?

TY
BC

---

### Post by alwayshere on 2008-12-15
try turning compiz off 

heres an application to switch compiz on and offf

[http://forlong.blogage.de/entries/pages/Compiz-Switch](http://forlong.blogage.de/entries/pages/Compiz-Switch)

---

### Post by jpoRS on 2008-12-15
I have had similar problems, and here are a few of the tricks I came up with.

1) If it is a laptop, make sure it is plugged in,  For whatever reason, this works and works well.

2) Don't "fullscreen" videos.  Again, I don't know why this works, but it seems to help.  If you just maximize in VLC and switch to the minimal view (Left Click>Interface>Minimal View) you get nearly the same effect, but with much smoother video.

3) Making VLC your default
     -Left Click a Movie
     -Properties>Open With
     -Select VLC

Hope this helps!
jim

---

### Post by fiatguy85 on 2008-12-15
As alwayshere said, try turning compiz off.  There is also a program in the repositories called "fusion-icon" that can be used for this.  I think this problem is usually related to ATI graphics cards with Compiz Fusion enabled.

---

### Post by bcondemi111 on 2008-12-15
Ok Yes I do have an ati video card. 256m ati Radeon 9600xt

the compiz switch off/on didn't do anything unfurtunately.

will try the fusion-icon.

How do I disable compiz fusion off on my card? can't see it in the ati catalyst control centre? is it called something else?

Thanks

BC

---

### Post by Pconfig on 2008-12-15
You could try to alter this setting:

Tools -> Preferences -> Video -> Output 

and set it to X11

---

### Post by bcondemi111 on 2008-12-15
tools? from where? what program? its not on the ati catalyst centre?

I see at the top of the screen application,places, system, that's it....

BC

---

### Post by Pconfig on 2008-12-15
Woops, forgot to mention it was in VLC :)

---

### Post by bcondemi111 on 2008-12-15
Nope! Doesn't do anything different....Still choppy...

This is the one thing that lost me to Linux last year...Is that I spend days and days and days just getting one thing to work. I spend a month configuring PCLinuxOS until I finally went back to Windows where 'everthing just works'. I hate the damn 'this program is not responding and needs to shut down crap' every day but at least it worked.... 

Anyway enough ranting...Whjat can I use now to get this video to run smooth, and how do I uninstall that 'compiz-switch' without using a terminal? if that's possible..

Thanks

BC

---

### Post by bcondemi111 on 2008-12-15
well, it seems to play smooth now, I exited full screen and its fine....

However, If I want to watch a tv show on full screen I can't. I guess I have to live with it...

Thank-for the help!


BC

---

### Post by bcondemi111 on 2008-12-15
That only worked for that one movie. VLC opened for that particular video I chose the prefrences for.
How about the default player for the whole system?

thank-you

---

### Post by bcondemi111 on 2008-12-15
That only worked for that one movie. VLC opened for that particular video I chose the prefrences for.
How about the default player for the whole system?

thank-you

---

### Post by jpoRS on 2008-12-15
I told you how make VLC default already.  Item number three in my first post.  You will need to assign VLC as the default for every type of file you want it to be default for.  If you want it to be the default for all movies, you will have to set it as the default for .avi, .wmv, .mpeg, and whatever other file formats you have. Sorry about that, I should have been more specific.

Furthermore, Terminal isn't scary, and if you are having this much issue getting things to work in Linux it is likely related to your difficulty with Terminal.  All you need to do to get the Compiz Fusion Icon in terminal is-

1) Open Terminal (Applications>Accessories>Terminal)
2) Type or paste (Shift+Ctrl+V) this into the terminal
```
sudo apt-get install fusion-icon
```
3) Press Enter, type in your login password.  Don't worry if it doesn't look like you are typing anything, this is normal, press Enter again.
4) Press y to install fusion-icon
5) Wait for it to finish (probably about 10 seconds give or take), when you see ```
yourname@yourcomputer:~$
``` fusion-icon is installed and can be found under Applications>System Tools>Compiz Fusion Icon

Once you have Compiz-Fusion Icon running, you can turn Compiz off by going over to the new blue box in your notification area, Left Click, and set your window manager to Metacity instead of Compiz.

Hope this helps, and good luck to you,
jim

---

### Post by northern lights on 2008-12-15
> **jpoRS said:**
> 2) Don't "fullscreen" videos.  Again, I don't know why this works, but it seems to help.  If you just maximize in VLC and switch to the minimal view (Left Click>Interface>Minimal View) you get nearly the same effect, but with much smoother video.
Jim, I don't dare doubt this works for you, but it's certainly not the smoothest solution. So for the sake of both of you, let's find a better one.

@the OP:
If all video, regardless of format, size, source and/or codecs is choppy (is it?), compiz is indeed the likeliest culprit.

Can you confirm that it isn't by running```
metacity --replace
```and trying to play the same video again?

---

### Post by bcondemi111 on 2008-12-15
I understood that vlc mediaplayer would be the default player for all video. Anyway I guess it will work by default once I have it open for every type of video format.

As for the video quality, It's very good now, even high def... I used the compiz-switch and switched to x11 video in vlc settings. I don't want to touch it. Its good.

As for the terminal, I just hate typing, otherwise I don't mind it.

Last question, 'movie player' that is the dfault application, can I uninstall it? I can re-install in future if I want right? I looked in the package manager to 'mark for removal' but 'movie player' is not listed. Is it called something else? Is there perhaps another way to uninstall it?

thank-you
BC

---

### Post by northern lights on 2008-12-15
The package is called *totem*.

---

### Post by northern lights on 2008-12-15
The package is called *totem*.

[EDIT]
frickin' 502 Proxy errors - what's happenin' lately?
[/EDIT]

---

### Post by bcondemi111 on 2008-12-15
Got it thanx very much

Everything work good now....

only 3 hours today! thats good!


BC

---

### Post by wasutton3 on 2008-12-16
but this still doesnt solve the problem of playing videos properly with compiz. i have been using this solution for a while now and i would very much like to find a solution.

---

### Post by jpoRS on 2008-12-16
Wasutton,

I think the reason why it isn't a "solution" is because there isn't one.  In my experience this problem only presents in systems with not-high end graphics.  Compiz is very demanding on resources, as is watching a video.  When you put the two together it can be too much for some systems, and you get the problem we are discussing here.

I could be wrong about all this, but I think that this problem isn't with Linux, Compiz, or Totem, but with the limits of your hardware.

jim

---

### Post by pmains on 2008-12-16
Huh? You're typing vlc into the terminal?

Right-click on "Applications." > Edit Menus > Sound & Video. Unless that's too many clicks, in which case you may prefer the terminal. I'm guessing not, though.

---

### Post by jpoRS on 2008-12-16
pmains, I don't get your point.  Who is typing vlc in?

jim

---

