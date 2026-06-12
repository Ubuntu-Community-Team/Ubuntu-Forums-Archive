---
title: "[SOLVED] How Do I Get a DVD to Play?"
date: 2008-12-27
forum: New to Ubuntu
---

### Post by Hotel California on 2008-12-27
I'm new.  Just installed 8.04 a couple of days ago and can get most everything to work except the DVD player.

How do I get a DVD to play?  Nothing happens when I insert the DVD.

If I open the Totem Player I am unable to locate the D drive to try to manually start the movie.  How do I navigate to the DVD drive?

I'm not a complete moron, but this sure seems like it should be something pretty basic.

Thanks.

---

### Post by taurus on 2008-12-27
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by w4ett on 2008-12-27
To install DVD playback use:
```

    sudo aptitude install libdvdcss2
```

To install non-free codec support: (If allowed in your locality)
```

    sudo aptitude install w32codecs
```

the Medibuntu repository has all the required packages.

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by Hotel California on 2008-12-27
So, is the short answer that an install of Ubuntu 8.04 will not play a DVD without downloading additional stuff mentioned in the 2 responses above?

---

### Post by taurus on 2008-12-27
Yes.  The default install doesn't come with any codecs since it's illegal here in the US (and some other countried).  In fact, bet you can't play a DVD movie even on windows unless you install some media codecs first.

---

### Post by w4ett on 2008-12-27
The movie players provided in Ubuntu are capable of reading DVDs that are not encrypted. However, most commercial DVDs are encrypted with CSS (the Content Scrambling System) and currently for legal reasons it is not possible to include support for these DVDs in Ubuntu

---

### Post by Hotel California on 2008-12-27
Thank you.  I understand better now and will start downloading stuff and then go watch my movie.

---

### Post by Hotel California on 2008-12-27
Uh, oh!  More problems.

When I enter the following command in Terminal:  sudo wget [http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list) --output-document=/etc/apt/sources.list.d/medibuntu.list

I get the following error:  Resolving [www.medibuntu.org](www.medibuntu.org)... failed:  Name or service not known

Any further assistance greatly appreciated.

---

### Post by linux_tech on 2008-12-27
Here is a link on playing dvds in ubuntu 8.1-
[https://help.ubuntu.com/8.10/musicvideophotos/C/video.html#video-dvd](https://help.ubuntu.com/8.10/musicvideophotos/C/video.html#video-dvd)

---

### Post by taurus on 2008-12-27
> **linux_tech said:**
> Here is a link on playing dvds in ubuntu 8.1-
[https://help.ubuntu.com/8.10/musicvi...html#video-dvd](https://help.ubuntu.com/8.10/musicvi...html#video-dvd)

The link is no good because you have ... in there.

---

### Post by w4ett on 2008-12-27
> **Hotel California said:**
> Uh, oh!  More problems.

When I enter the following command in Terminal:  sudo wget [http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list) --output-document=/etc/apt/sources.list.d/medibuntu.list

I get the following error:  Resolving [www.medibuntu.org](www.medibuntu.org)... failed:  Name or service not known

Any further assistance greatly appreciated.

Looks like the server is down...I am having trouble resolving that address too.  Wait a little while and try again. :)

---

### Post by lswest on 2008-12-27
Seems the server is down for maintenance or so, but the packages are still accessible.  If you can't wait for the package to watch your movie, download libdvdcss2 from [here]("http://packages.medibuntu.org/hardy/libdvdcss2.html") (pick the package for your architecture, which you can check by running uname -a in a terminal).  However, you should try again later to add the medibuntu repository, it's useful and will automatically update the libdvdcss2 package then as well.

*EDIT* Nevermind, site's back up.

---

### Post by CarolinaGuy on 2008-12-27
[https://help.ubuntu.com/8.10/musicvideophotos/C/video.html](https://help.ubuntu.com/8.10/musicvideophotos/C/video.html)

---

### Post by Hotel California on 2008-12-27
Thanks to all.  I'm now watching The Thomas Crowne Affair.

Only problem now is that even at maximum volume, I can barely hear the audio.  Is there anything Ubuntu can do about that?

---

### Post by moredhel on 2008-12-27
type alsamixer into terminal. see if the first volume controller is at 100% perhaps?

---

### Post by Hotel California on 2008-12-27
Yep, already at 100%.

---

### Post by lswest on 2008-12-28
What program are you using to view the movie?  I usually use VLC, had fewer issues with it than totem or mplayer.

---

