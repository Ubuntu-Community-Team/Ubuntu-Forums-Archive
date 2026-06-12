---
title: "Movie Player and VLC close immediately on opening"
date: 2009-07-05
forum: New to Ubuntu
---

### Post by Wisey on 2009-07-05
Hello! I am completely new to Ubuntu or Linux or anything that is not Windows. 
I installed Ubuntu today, but still kept Windows XP.

Everything seemed to be working fine until I tried to play an .avi video on Movie Player. Initially it asked me to install some codecs or packages or something, which I did. 
However now whenever I open a video file on Movie Player, it displays a blank screen for a second and closes.
I tried opening files with VLC, but the same problem persisted. 

How do I rectify this problem? As I said earlier, I am completely new to Ubuntu, I don't even know how to use the terminal properly, still fooling around trying to get to know the commands.

---

### Post by nothingspecial on 2009-07-05
The first thing I would do is try opening the avi file in the terminal and see what errors it gives. So type 

```
totem /path/to/movie.avi
```

```
vlc /path/to/movie.avi
```

So if the movie is Ghostbusters and it`s located in your Videos open a terminal and type ```
vlc Videos/Ghostbusters.avi
``` if you see what I mean.

---

### Post by HavocXphere on 2009-07-05
I think nothingspecial's suggestion is solid.

If it doesn't yield any info then try opening VLC without playing any actual media. i.e ALT-F2 -> vlc

Then you can edit the settings without it bailing immediately. I'd try disabling sound and also changing the video output module (You'll probably need to select advanced view to do this).

I get the closing immediately thing too if I select some of the video output types.;)

---

### Post by Wisey on 2009-07-05
Well I tried opening it from the terminal, and took a screenshot of the error. 
It's in the attachment.

---

### Post by HavocXphere on 2009-07-05
Weird. Looks like Totem is requesting memory and the X system is denying it. Could also be that I'm reading it wrong.

Is there sufficient free memory available?

---

### Post by Wisey on 2009-07-05
Well I really don't know, where do I look to check the memory usage? On the System Moniter I have 245 Mib (51%) of 480 Mib being used, 62.2 MiB(4.4%) of 1.4 GiB of swap.

I have 496 MiB of RAM on the PC, and the videos work fine on Windows XP, so I guess it should be enough for Ubuntu.

---

### Post by austinpsycho on 2009-07-05
usually vlc uses less memory; but is the error identical?

---

### Post by ivanvajar on 2009-07-05
What does > topsay?

---

### Post by Wisey on 2009-07-05
The VLC error isn't identical, but something about bad allocation again. 
Here are the screenshots with VLC and top.

---

### Post by ivanvajar on 2009-07-05
What version of Ubuntu are you using?

---

### Post by Wisey on 2009-07-05
About Ubuntu says Ubuntu 9.04
                - the Jaunty Jackalope - released in April 2009.

---

### Post by mc4man on 2009-07-05
you most likely solution was in an eariler post, try changing your video output,

For vlc

 Open vlc -> tools -> preferences, highlight the video icon and change the 'output' dropdown on the right side from 'default' to something specific (**try X11** )
**click save**, try

For totem, open a terminal and go 
```
gstreamer-properties
```

Under the video tab choose X Window System (No Xv)

---

### Post by Wisey on 2009-07-05
That worked, both VLC and Movie Player are working fine right now. Thank you for the help!

---

### Post by ivanvajar on 2009-07-05
Did you do [this]("https://help.ubuntu.com/community/RestrictedFormats/")

---

### Post by Wisey on 2009-07-05
> **ivanvajar said:**
> Did you do [this]("https://help.ubuntu.com/community/RestrictedFormats/")
Yes, but it didn't fix the problem. Now everything is working fine though.

---

### Post by rahulr88 on 2010-02-08
i am also experiencing the same problem. I tried wat u said still its not working... I changed the video o/p format to (No XV). should I change the audio format too ? VLC is having no problems. Pls help

---

