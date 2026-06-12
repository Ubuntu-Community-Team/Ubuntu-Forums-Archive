---
title: "How to play 3GP/3GPP2 media files"
date: 2009-07-03
forum: New to Ubuntu
---

### Post by Andy06 on 2009-07-03
I have Ubuntu-restricted-extras installed and all of the ffmpeg stuff. I still can't play this format and it comes up with a search for plugin dialog. How do I play this format?

---

### Post by andrew.46 on 2009-07-04
Hi Andy06,

> **Andy06 said:**
> I have Ubuntu-restricted-extras installed and all of the ffmpeg stuff. I still can't play this format and it comes up with a search for plugin dialog. How do I play this format?

If you are using Jaunty or Intrepid you should be able to install the [Medibuntu]("https://help.ubuntu.com/community/Medibuntu") MPlayer and play these files. To make it a more pleasant experience you could install SMPlayer as well for a better gui than the default.

All the best,

Andrew

---

### Post by petronell on 2009-07-04
I can play this type of files fine with vlc. Just install it from the repositories.

daveR

---

### Post by abhigyan91 on 2009-07-04
vlc rulz.. plays anything except rm and rmvb files..
if you want to play these files google w32codecs and install the deb.. itll make totem play rm and rmvb

i dnt know the link but the file name is
w32codecs_20071007-0medibuntu3_i386.deb

---

### Post by Andy06 on 2009-07-05
Don't w32codecs come as part of the restricted extras package as well?
I have VLC on windows and yes it rules :D but I was reluctant to install VLC on Ubuntu since it will pull in all sorts of qt libraries that I won't be using for anything else. Is there a GTK VLC like player?

Thanks a lot

Have Mplayer installed, that works too.

---

### Post by andrew.46 on 2009-07-06
Hi Andy06,

> **Andy06 said:**
> Don't w32codecs come as part of the restricted extras package as well?

Hmmm.... I hate to give conflicting information / advice but I am not so sure that the so-called w32codecs are required for *[I]most*[/I] 3gp files. Common 3gp files contain h263 video and amr sound although several other codecs *could* be in there. A nice page [here]("http://en.wikipedia.org/wiki/3GP") for further discussion.

 Most media players can cope with h263 but the amr codecs are not available under a standard Ubuntu install as they cannot really be distributed as part of a free OS. For MPlayer, which is the media player I know best, amr playback can be achieved in all versions of Ubuntu except Karmic by using the MPlayer version provided by Medibuntu. This version has been compiled against the amr libraries.

MPlayer can be checked as follows:

```

andrew@skamandros~$ **[COLOR="Purple"]mplayer -ac help | grep 'amr'[/COLOR]**
ffamrnb     ffmpeg    working   AMR Narrowband  [libamr_nb]
ffamrwb     ffmpeg    working   AMR Wideband  [libamr_wb]

```

Sorry to add to the confusion :-).

Andrew

---

