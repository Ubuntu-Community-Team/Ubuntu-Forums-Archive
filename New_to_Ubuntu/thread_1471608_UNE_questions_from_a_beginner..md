---
title: "UNE questions from a beginner."
date: 2010-05-03
forum: New to Ubuntu
---

### Post by constellanation on 2010-05-03
Long story short, last night i needed to partition the drive on my asus eeepc 1000he running xp.  So in an effort to kill two birds with one stone, i made a live disc/usb of the newest ubuntu netbook edition 10.04 to use gparted and check out the distro.  I liked my initial impressions and decided to install it to my hard drive.  So here I am 24 hours into linux and though i like a lot of this there are some small things that are frustrating me to no end, and no google search is finding me an answer. 
first i found out that there is very little customization in unr for the top notification bar (which i found odd, but then found a workaround [here]("http://www.webupd8.org/2010/05/how-to-add-remove-applets-from-gnome.html").  so in theory i'm running gnome made to look like une... but here are my current questions, hopefully you can help.



1. hopefully simple, i removed the gwibber icon from the top notification bar and i can't seem to restore the stock one. (i've found a temporary work around in adding a launch icon, but i would like the original back)

2. Some windows refuse to be resized, and it leaves some essential parts of the windows off screen. In particular I'm trying to do some video work in avidemux and all of the useful buttons are off screen (after i load a video)

3.  I much prefer google chrome as a browser over mozilla, and i can't seem to get it to sync my bookmarks, it just spins on the "setting up" page for what seems like way to long (20-25 minutes)


currently those are my only three questions (I'm  sure there will be more, because truth be told I really would like this to work and have already installed gparted in anticipation of the day I feel i can cut the cord on xp completely.  Thanks in advance.

edit: a fourth question, I'm really used to using the backspace button on the keyboard as a back button in my browser, is there anyway to implement this?

---

### Post by Temposs on 2010-05-03
> 1. hopefully simple, i removed the gwibber icon from the top notification bar and i can't seem to restore the stock one. (i've found a temporary work around in adding a launch icon, but i would like the original back)

There shouldn't actually be a gwibber icon in the notification bar. The way to open gwibber from the notification bar would be to click the messaging menu(the one that looks like an envelope), and then click "Broadcast". That should open Gwibber.

> 2. Some windows refuse to be resized, and it leaves some essential parts of the windows off screen. In particular I'm trying to do some video work in avidemux and all of the useful buttons are off screen (after i load a video)

Some apps make some of their windows for a minimum vertical resolution of 800 pixels. There's nothing to be done about this directly, but the way you use this kind of window is to hold the Alt button and then click on the window and drag it to the position you need(to be able to see those bottom buttons, for example).

---

### Post by undecim on 2010-05-03
1: I think you are looking for the "indicator applet" from the add to panel menu.

2: You can use ALT+Click+Drag to move windows around. I found this to be an invaluable feature when I was using a netbook. You may have to configure metacity or compiz (i forget which one UNE uses) to let you move the windows further upwards though.

---

### Post by constellanation on 2010-05-03
it was the indicator applet that i was looking for and alt click drag is exactly what i needed to know how to do!  Thanks for the quick responses on those two, I really appreciate it.
and synching bookmarks?
any ideas on the using backspace to go back in the browser? 
edit: found a work around on backspace, alt+left arrow will work.  i just wanted to avoid the trackpad.

---

### Post by constellanation on 2010-05-06
Hello guys, a couple more questions.

I've been editing some home videos (mostly all mpg's) and occasionally i get the following error in the stock movie player.
pa_stream_writable_size() failed: Connection terminated
I downloaded vlc, and haven't noticed the error in there yet, but can i remove the stock movie player safely, and make vlc my default? and if so, what would the steps be?

in doing the home video editing i had one file that was part of another video but it was avi format, so i tried converting it with the following:
mencoder video.avi -o video.mpg -ovc lavc -oac lavc
which successfully converted the video, but it lost the sound, what did i do wrong?

Thanks in advance again!

---

