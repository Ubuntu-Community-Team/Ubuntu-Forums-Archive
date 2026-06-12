---
title: "Ubuntu will not play DVD's... (HELP)"
date: 2009-07-12
forum: New to Ubuntu
---

### Post by CharlesWelsh on 2009-07-12
I wanted to watch my dvd while i have nothing else to do and it will not play. Any decent movi players i can install via Synaptic Package Manager? Thanks in advance...:popcorn:

---

### Post by nynoah on 2009-07-12
Go here

[http://www.medibuntu.org/](http://www.medibuntu.org/)

More specifically here

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by CharlesWelsh on 2009-07-12
Still cannot get it to work...

---

### Post by Rocket2DMn on 2009-07-12
Specifically you need the libdvdcss2 package from the Medibuntu repositories given above.  I would also grab the w32codecs package (or w64codecs if you hav ea 64 bit install of Ubuntu) so you can play mp3s and other proprietary media formats.

---

### Post by earthpigg on 2009-07-12
ummm:

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by CharlesWelsh on 2009-07-12
I typed in the specifics libdvdcss2'' and i am installing the Ubuntu version of the restricted things. lol i cant remember. hopefully it helps me to solve my problem...

---

### Post by peakpc on 2009-07-12
Another option you can try is to install VLC media player and then try a DVD.

---

### Post by Garrovick on 2009-07-12
> **CharlesWelsh said:**
> I typed in the specifics libdvdcss2'' and i am installing the Ubuntu version of the restricted things. lol i cant remember. hopefully it helps me to solve my problem...

Just go to **earthpigg**'s link.  Two simple simple steps, just two...

And I like VLC

---

### Post by nynoah on 2009-07-12
Resticted extras package also Mencoder

---

### Post by LowSky on 2009-07-12
open a terminal enter these two commands and reboot and your good to go
```
sudo wget http://www.medibuntu.org/sources.list.d/`lsb_release -cs`.list --output-document=/etc/apt/sources.list.d/medibuntu.list; sudo apt-get -q update; sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring; sudo apt-get -q update

```

```
sudo apt-get install libdvdcss2 w32codecs
```

---

### Post by Marlonsm on 2009-07-12
You can also use Totem with Xine backend, it seems to work better with DVDs, specially with the menus.

---

### Post by CharlesWelsh on 2009-07-12
still a no- go

---

### Post by Garrovick on 2009-07-12
> **CharlesWelsh said:**
> still a no- go
 
Okay, I'm a complete novice with Ubuntu, but just today, I did a fresh install of 9.04 on this netbook of mine.

I'm sitting, looking at my computer. All I have installed is what is on the CD and updates using Update Manager. I haven't done any thig else.  Then I update Rhythmbox so it will play my 2000 or so podcasts.

Now, I want to play my new Stargate DVDs.  I install VLC, because I like it. 

Next, using Synaptic Package Manager, I install LIBDVDREAD4, after that, I go to terminal and type - 

sudo /usr/share/doc/libdvdread4/install-css.sh

I hit "enter", put in my password as requested, terminal runs for a second and does what it does.

I reboot, put in my Stargatge DVD and watch it.

And that's how I do it with 9.04

---

### Post by Marlonsm on 2009-07-13
If you can't get Ubuntu to play DVDs somehow, you can try Linux Mint, it's based on Ubuntu but is focused on the "out of the box", so right after installing it'll play DVDs, Flash, MP3...

---

