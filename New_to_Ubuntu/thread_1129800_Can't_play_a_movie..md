---
title: "Can't play a movie."
date: 2009-04-19
forum: New to Ubuntu
---

### Post by Roadkill Bill on 2009-04-19
I just tried to play a DVD and I don't have what ever it is I need to play a movie. I have "Movie Player" but I guess that's not enough. What do I need to get?

---

### Post by pbpersson on 2009-04-19
I would recommend installing the following two packages:

ubuntu-restricted-extras
vlc

Then try using VLC to play the DVD and see if that works

---

### Post by Simrn on 2009-04-19
You can get all you need to know here: [http://ubuntuforums.org/showthread.php?t=661833](http://ubuntuforums.org/showthread.php?t=661833)
hope this helps :)

---

### Post by spcwingo on 2009-04-19
It wouldn't hurt to add the Medibuntu repos.  Then install libdvdcss2, libdvdread3, libdvdnav4, and w32codecs.  Instructions for adding the Medibuntu repo, check this out:

[https://help.ubuntu.com/community/Medibuntu]("https://help.ubuntu.com/community/Medibuntu")

---

### Post by pbpersson on 2009-04-19
> **spcwingo said:**
> It wouldn't hurt to add the Medibuntu repos.  Then install libdvdcss2, libdvdread3, libdvdnav4, and w32codecs. 

You know what?  I just want Ubuntu to WORK.  I want to be able to DO STUFF with it - play MP3s, watch movies, surf the web.....

I thought that ubuntu-restricted-extras covered it all.

Now along comes these libdvd packages and non-free-codecs

Now my movie player can actually play movies - imagine that.  It has been "broken" ever since I upgraded to Intrepid Ibex.

Is there a guide somewhere that can tell me exactly what I need to install....that was left out on purpose.....to make all the applications actually function?

Thank you for telling me about this.....but how many other "bugs" in my system are due to packages that were left out on purpose?

---

### Post by spcwingo on 2009-04-19
Pbpersson, ubuntu-restricted-extras covers most things, but DVD playback and Win32 codecs aren't included.  I don't know of much more that is left out on purpose.  I don't know if you knew this, but there are also some other pretty nice to have packages in the Medibuntu repos.  For a full list of Medibuntu packages, check out this page:

[http://packages.medibuntu.org/]("http://packages.medibuntu.org/")

---

### Post by 3rdalbum on 2009-04-19
Dude, chill out for a second. The legality of the DVD decryption software is a grey area in many parts of the world and Ubuntu can't risk being raided by the police over distributing it. There's the option of distributing licensed DVD decryption software, but guess what; that costs money, and Ubuntu is free.

Just install the ubuntu-restricted-extras package, and install the DVD decryption support from Medibuntu, and you'll have everything you need. It might sound like a lot of work, but trust me it only takes two minutes.

---

### Post by pbpersson on 2009-04-19
No, I was not thinking that it was a lot of work.

What I was thinking is this.....

Let us say that John or Jane Doe installs Ubuntu

Twenty different things do not work, they get an error message saying "lib missing" or "codec missing" and from their point of view, it is broken.  They cannot use their computer.

How are they supposed to know to install an entire list of things that are not included automatically?

This is where I am coming from.

So they go to all their friends and they say, "I tried this Ubuntu thing everyone is talking about, but it does not work very well, a bunch of stuff is broken"

If by choice Ubuntu leaves out a bunch of stuff, I think they should include in the installation instructions some clue for people.  

"We are omitting twenty packages that are not free and therefore, your new operating system will not be able to perform these tasks.  For more information on how to install these non-free packages, click here" or something so people know.

---

