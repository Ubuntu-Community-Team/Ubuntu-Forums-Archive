---
title: "Absolute Idiot Beginner Here"
date: 2009-10-25
forum: New to Ubuntu
---

### Post by seacaptain on 2009-10-25
Greetings!
 
My 2002 desktop computer, using Windows 98 (old!), was recently subjected to the PC equivalent of the Dresden bombing by my 14 year old son. Windows disks were obviously no longer on-hand to re-load.
 
Not wanting to waste money on a new computer or new Windows operating system, I searched the Internet and happened upon Ubuntu.
 
I've just loaded version 9.04 and it appears pretty easy to use. My basic Internet searching (I'm something of a news junkie) has been satisfied.
 
But I also use my PC for watching movies (I've rented more than 1200 films using Netflix to-date). 
 
Can anyone provide really (I mean really dumbed-down, easy enough for Homer Simpson to understand) directions for downloading a video player on Ubuntu for me to enjoy Johnny Depp's "Public Enemies" by the time it arrives from Netflix???
 
Thanks in advance for any help a non-techie like me can use.
 
Regards,
seacaptain

---

### Post by tubasoldier on 2009-10-25
In order to watch DVD's on Ubuntu you need to install libdvdcss. 
It is available from the medibuntu repository.

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

all information is on that page.

---

### Post by jmszr on 2009-10-25
seacaptain,

After you install Medibuntu, if you haven't already, open the Terminal (Applications > Accessories > Terminal) and copy and paste this into it:

```
sudo apt-get install ubuntu-restricted-extras
```
 
then press Enter, when it asks for your password type it in (will not be visible-security) and press Enter.
 
Also, I would suggest the VLC media player:

```
sudo apt-get install vlc
```

VLC will play just about anything.

Edit: As part of installing Medibuntu be sure to install "libdvdcss2" and "w32codecs".

---

### Post by ndefontenay on 2009-10-25
yeah. VLC is The Tool for media.

---

### Post by martrn on 2009-10-25
type these command first in the Terminal 
(Applications &#8594; Accessories &#8594; Terminal):

```
sudo wget http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list \
 --output-document=/etc/apt/sources.list.d/medibuntu.list &&
sudo apt-get -q update &&
sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring &&
sudo apt-get -q update
```

and then

```
sudo apt-get install mplayer
sudo apt-get install gmplayer
gmplayer
```

---

