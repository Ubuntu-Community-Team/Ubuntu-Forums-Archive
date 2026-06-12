---
title: "A really, really basic question about installing"
date: 2011-09-07
forum: New to Ubuntu
---

### Post by Peter31 on 2011-09-07
Good morning
 
I'm new to Linux as of about two days ago (my Windows XP operating system crashed beyond repair, and rather than buy a new copy of Windows, I decided to take the plunge into Linux). I've successfully installed Ubuntu Linux v 11.04, found my way around the Ubuntu Software Centre and everything is looking pretty good so far. I have one really, really stupid question though, which will have you rolling in the aisles with laughter, but I can't figure this out:
 
when I see an instruction which looks like "install X using [FONT=Consolas][SIZE=2]$ sudo apt-get install vlc xine mplayer libdvdread3"[/SIZE][/FONT]
 
where exactly do I type this in?
 
A related question: I am trying to get my newly minted Linux machine to play DVDs, and so far, I have managed to get the right codecs installed, so it will now play MPEG-2 video files, but it is still having difficulty with DVD menus, so any help / suggestions with this would also be appreciated.
 
Thanks!
 
Peter

---

### Post by sanderd17 on 2011-09-07
> **Peter31 said:**
> Good morning
 
I'm new to Linux as of about two days ago (my Windows XP operating system crashed beyond repair, and rather than buy a new copy of Windows, I decided to take the plunge into Linux). I've successfully installed Ubuntu Linux v 11.04, found my way around the Ubuntu Software Centre and everything is looking pretty good so far. I have one really, really stupid question though, which will have you rolling in the aisles with laughter, but I can't figure this out:
 
when I see an instruction which looks like "install X using ```
$ sudo apt-get install vlc xine mplayer libdvdread3"
```

where exactly do I type this in?

you have to type it in the terminal (you can find the terminal in the menus or via the search thing or by using the shortcut CTRL+ALT+T)
> 
 
 
A related question: I am trying to get my newly minted Linux machine to play DVDs, and so far, I have managed to get the right codecs installed, so it will now play MPEG-2 video files, but it is still having difficulty with DVD menus, so any help / suggestions with this would also be appreciated.
 
Thanks!
 
Peter

What is the problem?

---

### Post by haqking on 2011-09-07
> **sanderd17 said:**
> you have to type it in the terminal (you can find the terminal in the menus or via the search thing or by using the shortcut CTRL+ALT+T)


What is the problem?


menu issue ?

DVD issues should be solved with above command when you install from terminal now you know how to ? and see here [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by kurok on 2011-09-07
did you follow the instructions here when installing the stuff for dvd?[http://ubuntuforums.org/showthread.php?t=766683]("http://ubuntuforums.org/showthread.php?t=766683")

---

### Post by Peter31 on 2011-09-07
Thanks - I will try that.  In answer to your question, what is happening with DVDs is that if I insert a DVD and press "play", either nothing happens, or I get an error message along the lines "unable to read DVD", "you may need to install decryption software" or similar.  I have installed about six different DVD players, and none of them will play DVDs properly, so the problem must be in Linux rather than specific to a particular player.  The problem occurs with both commercial DVDs, and DVDs I have burned myself without any encryption.
 
But I can open an individual video file in DVD (MPEG-2) format, and it will play with no problem, so the codecs must be there.

---

### Post by YesWeCan on 2011-09-07
I followed this: [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

Two console commands seemed to cover most everything.

---

### Post by Johnb0y on 2011-09-07
did you run an update after all/each install?

---

### Post by Peter31 on 2011-09-07
> **Johnb0y said:**
> did you run an update after all/each install?
 
No I didn't but I will try that as well.  Thanks, and I will try to give you an update tomorrow!

---

### Post by Johnb0y on 2011-09-07
Get update software list, enter:

```
sudo apt-get update
``` i belive is the correct cmd line

---

### Post by anewguy on 2011-09-07
You are just missing the codecs that allow for reading encrypted DVDs such as commercial movie DVDs.  I believe it is for legal reasons these are not installed by default.  Follow the instructions given back towards the beginning of the thread by sanderd17 and install the libdvdread"x" package - it should be Synaptic Package Manager.  It may also have a number different than "3" at the end - mine says "libdvdread4" in the package manager.  Just search for libdvdread and it will pull it up.

Depending on how your repositories are set up (places the software are kept on the net) you may need to update the list.  If the package is not found, please post back and we'll get you through that as well.

Dave ;)

---

### Post by Peter31 on 2011-09-08
I spent about an hour downloading and installing all the stuff you suggested, and everything now seems to be working perfectly.  Thanks very much for your help guys.

---

### Post by Johnb0y on 2011-09-08
nice one, glad to hear all is working. please remember to mark this thread as solved. thanks.

---

