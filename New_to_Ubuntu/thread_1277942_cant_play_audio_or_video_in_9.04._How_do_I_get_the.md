---
title: "cant play audio or video in 9.04. How do I get the decoders?"
date: 2009-09-28
forum: New to Ubuntu
---

### Post by penguinv on 2009-09-28
cant play audio or video in 9.04. How do I get the decoders?

This is bogus. Makes the distribution pretty useless.

Why is this?  I have a list of 6 or more decoders that there are not. I'm not on the internet there so I have to get them here or there. Is there a package available? 

Why was this left out?

I cant play music. I cant look at a video, avi. I cant look at a dvd. I cant look at a disk containing a 3-D demo program. 

I can play solitaire. Whoopee.


NO :popcorn:

--
some old Dell with 9.04

---

### Post by humphreybc on 2009-09-28
Install this package:

ubuntu-restricted-extras

And then you can also install the Medibuntu repository and get the gstreamer codecs, libdvdcss and a few other things.

---

### Post by 3rdalbum on 2009-09-29
Certain codecs are patented in many parts of the world, and if Ubuntu shipped with them without paying a rather hefty licensing fee, they would be open to litigation. DVDs are illegal to decrypt unless you have licensed decryption software, so the same issue applies there but even worse; if you have an unlicensed DVD decryptor on your hard disk YOU can be sued (not just Ubuntu).

Of course, since Ubuntu is free to distribute, it's not possible to pay for the licensing fees for absolutely every single copy that gets made.

Out-of-the-box, Ubuntu supports Ogg Vorbis, FLAC and WAVE audio formats; and the Ogg Theora video format. These are open-source and unpatented, and nearly as good as the best patented codecs.

On an internet-connected Ubuntu machine, the first time you play (say) an MP3 it will prompt you if you want to install the codec, and advise of the reason why the codec is not included. When you click "Ok" it will automatically download and install the codec for you, and then play the file you requested.

DVD decryption is not handled by this system because of the extra risks, but you are able to purchase LinDVD which gives you a legal license to play DVDs. Alternatively, do what the rest of the community does and install the "libdvdcss2" package from Medibuntu.org, which gives you "probably-not-legal" DVD decryption. Of course you should check with a lawyer first before installing this package, as laws vary between countries.

If you can get a quick wired internet connection (or wireless, if you have it), you should click the Reload button in Synaptic Package Manager and install the "ubuntu-restricted-extras" package. This will get everything except DVD playback support; all the codecs, Flash, Java, Microsoft fonts, and other restricted formats and packages.

Add the Medibuntu repository using the instructions at Medibuntu.org and you can get DVD playback (I recommend installing the VLC media player from Synaptic Package Manager to handle your DVDs too).

If you can't get any internet connection to that computer, then you will need to go to [http://packages.ubuntu.com](http://packages.ubuntu.com) and manually download and install the packages listed as "depends" on the ubuntu-restricted-extras package, and install the libdvdcss2 package straight from the Medibuntu website. This is a pain in the backside because you manually have to download and install the dependency packages yourself; so I definitely recommend finding an internet connection because then Ubuntu will do all the work for you.

---

### Post by nhasian on 2009-09-29
the codecs are left out due to licensing issues, but you can easily add them from a terminal with these two commands:

```
sudo apt-get install ubuntu-restricted-extras
```

then to dvd playback:

```
 sudo /usr/share/doc/libdvdread4/install-css.sh
```

for more info see [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by dvn3ch on 2009-09-29
Damn, 3rdalbum, that was agreat post.  I am straining to find something to add to that.

How about, never brush your teeth in the dark.  ???

Any way, great post. Can't go wrong with any of that advice.

---

### Post by penguinv on 2009-10-05
Thank you all.

---

### Post by MoebusNet on 2009-10-05
If you haven't read this thread yet, I highly recommend it.


Comprehensive Multimedia & Video Howto
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)


:guitar:

---

