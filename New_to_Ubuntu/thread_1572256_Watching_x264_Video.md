---
title: "Watching x264 Video"
date: 2010-09-10
forum: New to Ubuntu
---

### Post by completeidiot on 2010-09-10
Hello,
I'm trying to watch an "x264" video with the file extension .mkv

Movie Player- crashed
VLC- good audio, zero video
gxine- ok audio, slowed and choppy video

any ideas?
I guess it could be a graphics card issue, seeing as though I'm attempting this on my netbook, but hopefully it's a codec issue. Thanks!!!

---

### Post by clhsharky on 2010-09-10
completeidiot

c/p
```
lspci -nn | grep VGA
```
Will give chip info.

Sharky

---

### Post by kerry_s on 2010-09-10
do you got ubuntu-restricted-extras installed?

that will get everything you need for media.

---

### Post by JohnnyC35 on 2010-09-10
I gave up on vlc, I just use xbmc with everything and it all runs beautifully

---

### Post by completeidiot on 2010-09-11
> **clhsharky said:**
> completeidiot

c/p
```
lspci -nn | grep VGA
```
Will give chip info.

Sharky

Intel Corporation Mobile 945GME Express Integrated Graphics Controller

---

### Post by kerry_s on 2010-09-11
> **completeidiot said:**
> Intel Corporation Mobile 945GME Express Integrated Graphics Controller

did you grab the "ubuntu-restricted-extras"?

totem has some issues with certain media no matter what.
you might also want to grab "gnome-mplayer" & add some tweaks that play most vids for me.

```
-lavdopts skipframe=nonref:skiploopfilter=all
```

i'm running an atom nettop. i can play up to 720p, some 1080p, depends on how well it was encoded.

---

### Post by Jazzy_Jeff on 2010-09-11
> **JohnnyC35 said:**
> I gave up on vlc, I just use xbmc with everything and it all runs beautifully

I have never had any problems with VLC. It plays every video format I have ever thrown at it.

---

### Post by completeidiot on 2010-09-11
i believe i have all of the restricted extras... i was hoping for 1080p

---

### Post by Jakey_TheSnake on 2010-09-11
I have the same problem too, same chipset. I know Ubuntu has had lots of issues with this particular one in the past, it wouldn't surprise me if we're both screwed. Some video players are better than others for me - but worryingly it behaves exactly the same when I'm booted into Windows 7.

---

### Post by krackersk on 2011-01-25
I also have this chipset on my ASUS eee PC and am trying to play HD video. Anybody get this to work?

I have read that netbooks just don't have the guts to play HD, is there any hope?

---

### Post by Grenage on 2011-01-25
> **krackersk said:**
> just don't have the guts to play HD, is there any hope?

Generally no;  You need either a powerful CPU, or a GFX card capable of handling the excess.

---

### Post by darthspringbok on 2011-01-25
> **Grenage said:**
> Generally no; You need either a powerful CPU, or a GFX card capable of handling the excess.
 
Grenage is correct. A netbook is just that - a NETbook, primary purpose is surfing the net. Sadly they do not have the gumption (CPU power and GFX capabilities) built in to handle video decoding, HD video more specifically. In saying that some low powered laptops will also run into the same, if not so severe, problems.
 
This is no fault of Ubuntu or any of the above mentioned video players.

---

