---
title: "WMA Conversion?"
date: 2010-05-26
forum: New to Ubuntu
---

### Post by jenkshacker on 2010-05-26
Is there a good program for Ubuntu that can convert the WMA files on my Windows partition to something else that would be more "Ubuntu-friendly?"

---

### Post by -humanaut- on 2010-05-26
WMA files should work fine on Ubuntu really there isn't much reason to convert them.

---

### Post by jenkshacker on 2010-05-26
> **-humanaut- said:**
> WMA files should work fine on Ubuntu really there isn't much reason to convert them.
Once, I tried to open one and it wouldn't work. Otherwise, I wouldn't be asking for help.

---

### Post by cascade9 on 2010-05-26
If you have the w32codecs installed they should play fine. (or w64codecs for 64bit users). '

If you dont know how to install the w32codecs, see here- 

[http://www.ubuntugeek.com/install-mplayer-and-multimedia-codecs-libdvdcss2w32codecsw64codecs-in-ubuntu-10-04-lucid-lynx.html](http://www.ubuntugeek.com/install-mplayer-and-multimedia-codecs-libdvdcss2w32codecsw64codecs-in-ubuntu-10-04-lucid-lynx.html)

---

### Post by jenkshacker on 2010-05-26
> **cascade9 said:**
> If you have the w32codecs installed they should play fine. (or w64codecs for 64bit users). '

If you dont know how to install the w32codecs, see here- 

[http://www.ubuntugeek.com/install-mplayer-and-multimedia-codecs-libdvdcss2w32codecsw64codecs-in-ubuntu-10-04-lucid-lynx.html](http://www.ubuntugeek.com/install-mplayer-and-multimedia-codecs-libdvdcss2w32codecsw64codecs-in-ubuntu-10-04-lucid-lynx.html)
How do I check to see which repositories I have enabled?

---

### Post by Paddy Landau on 2010-05-26
VLC is a great video and audio player because it supports so many codecs. It's worth trying your faulty WMA on VLC to check whether VLC can play it.

Interestingly, VLC can also convert files.

I've never used it to convert before, but it's worth a try.

[Install vlc]("apt:vlc") from the repositories.


[LIST]
[*]Start VLC.
[*]Media > Convert/Save
[*]Add > (choose your input WMA file)
[*]Convert/Save
[*]Destination file > (choose a directory and a name for the output file, including the extension)
[*]Profile > Audio Vorbis OGG (OGG is an open-source format. If you prefer, choose a different format, e.g. Audio MP3 or Audio AAC.)
[*](Optional) Press the tools button and make changes.
[/LIST]
Let us know how well it works.

---

### Post by cascade9 on 2010-05-26
> **jenkshacker said:**
> How do I check to see which repositories I have enabled?

Synaptic-> Settings-> Repositories (there are other ways, but thats nice and easy ;) )

---

### Post by jenkshacker on 2010-05-26
> **Paddy Landau said:**
> VLC is a great video and audio player because it supports so many codecs. It's worth trying your faulty WMA on VLC to check whether VLC can play it.

Interestingly, VLC can also convert files.

I've never used it to convert before, but it's worth a try.

[Install vlc]("apt:vlc") from the repositories.


[LIST]
[*]Start VLC.
[*]Media > Convert/Save
[*]Add > (choose your input WMA file)
[*]Convert/Save
[*]Destination file > (choose a directory and a name for the output file, including the extension)
[*]Profile > Audio Vorbis OGG (OGG is an open-source format. If you prefer, choose a different format, e.g. Audio MP3 or Audio AAC.)
[*](Optional) Press the tools button and make changes.
[/LIST]
Let us know how well it works.
It worked! Thanks!

---

### Post by Paddy Landau on 2010-05-26
> **jenkshacker said:**
> How do I check to see which repositories I have enabled?
System > Administration > Synaptic Package Manager > Settings > Repositories

You can add Medibuntu from there instead of at the terminal, if you prefer. Go to Other Software, press Add... and enter:
```
deb http://packages.medibuntu.org/ lucid free non-free
```Be sure to replace [FONT=Courier New]lucid[/FONT] with your installation, i.e. [FONT=Courier New]hardy[/FONT], [FONT=Courier New]jaunty[/FONT], [FONT=Courier New]karmic[/FONT], or whatever you have.

---

### Post by Paddy Landau on 2010-05-26
> **jenkshacker said:**
> It worked! Thanks!
Good to know that VLC yet again successfully rises to the challenge!

---

### Post by cascade9 on 2010-05-26
You are much better of playing the original WMA (if you dont have the Cd to rerip). Lossy-> lossy conversions are not a good idea, you just lose quality (you might not hear the difference on one conversion, but its there).

---

