---
title: "ubuntu cd"
date: 2009-12-14
forum: New to Ubuntu
---

### Post by arunkmohan18 on 2009-12-14
is there any other ubuntu cd image that i can play movie,mp3,vob and variety of players

---

### Post by HarrisonNapper on 2009-12-14
It doesn't come built-in with the cd. Install libdvdread4 and run the libdvdcss script in libdvdread's folder in /etc

Cheers.

---

### Post by arunkmohan18 on 2009-12-14
i heard about ubuntu mutimedia center what is  it really

---

### Post by HarrisonNapper on 2009-12-14
Dunno. Here's some more info about restricted formats: [https://help.ubuntu.com/community/RestrictedFormats/](https://help.ubuntu.com/community/RestrictedFormats/)

---

### Post by Physical Hook on 2009-12-14
[Ubuntu Studio]("http://ubuntustudio.org/") ( haven't used it so not sure whether it'll fulfill your needs ) ?

---

### Post by arunkmohan18 on 2009-12-14
can i play mp3 or video by using ubuntu studio

---

### Post by Anuovis on 2009-12-14
If you go to *Ubuntu Software Center* from *Applications* menu and install _*Ubuntu Restricted Extras*_, you should be able to play mp3s and the like.

---

### Post by lukjad on 2009-12-14
> **arunkmohan18 said:**
> is there any other ubuntu cd image that i can play movie,mp3,vob and variety of players
If you are willing to use another Linux Distribution and are only looking for a Live CD, I would personally recommend [TEENpup]("http://pupweb.org/wikka/TeenPup"). It's fast and can pretty much play any media file I threw at it. Here is a good review: [http://www.dedoimedo.com/computers/teenpup.html](http://www.dedoimedo.com/computers/teenpup.html)

---

### Post by arunkmohan18 on 2009-12-14
i want all types of media codecs for ubuntu 9.1 and i want exact files because i want to help my friends also 
please help me

---

### Post by ST3ALTHPSYCH0 on 2009-12-14
Usually the first time you try to play a restricted format Ubuntu gives you exact instructions on how to install the proper codecs.

---

### Post by Terl on 2009-12-14
> **arunkmohan18 said:**
> i want all types of media codecs for ubuntu 9.1 and i want exact files because i want to help my friends also 
please help me

You can install the codecs into the current installation you have.  Do you have Ubuntu installed?  As mentioned earlier in the thread you can easily install the ubuntu-restricted-extras which will get you the codes you need.  You can also install what is needed to watch dvd's as well.

---

### Post by arunkmohan18 on 2009-12-16
please anyone  can give me a link of all types of players that work in ubuntu 9.10

---

### Post by philinux on 2009-12-16
> **arunkmohan18 said:**
> please anyone  can give me a link of all types of players that work in ubuntu 9.10

Do you want to install 9.10 or just run the live cd?

---

### Post by rajeev1204 on 2009-12-16
> **arunkmohan18 said:**
> is there any other ubuntu cd image that i can play movie,mp3,vob and variety of players

Can you be a little more clear what you are trying to do?



rajeev

---

### Post by arunkmohan18 on 2009-12-16
i just want video and music players that work in ubuntu

---

### Post by Merk42 on 2009-12-16
> **arunkmohan18 said:**
> i just want video and music players that work in ubuntu

Players or codec?

If you **install** Ubuntu and then the aforementioned restricted extras you can run mp3, avi and many others in the preinstalled Rhythmbox and Movie Player. You can also go to Ubuntu Software Center and install VLC player for a player that will handle even more codecs.

Ubuntu legally cannot be able to play things like MP3 on the LiveCD, they must be installed after the fact.

---

### Post by mkvnmtr on 2009-12-16
If you open the package manager and in the search box type video player you should find all the video players that you can install with the repositories you have enabled. The same should work for music players.

---

### Post by 3rdalbum on 2009-12-16
Listen to what we're saying.

Video and music players do not contain the code to decode and play video and music files. Instead they use seperate files known as "codecs" that provide this support.

Ubuntu comes with codecs to play free, unpatented formats such as Ogg Vorbis, Theora, and FLAC. You can easily add codecs to play almost anything you encounter.

To add these codecs, you just go to Applications > Ubuntu Software Centre and look up "ubuntu-restricted-extras". Install this package. Then the audio and video players on Ubuntu will be able to play almost anything.

---

