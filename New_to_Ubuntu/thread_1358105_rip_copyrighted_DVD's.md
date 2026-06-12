---
title: "rip copyrighted DVD's"
date: 2009-12-18
forum: New to Ubuntu
---

### Post by SpatzST on 2009-12-18
in windows i used to use slyfox's AnyDVD + DVDCopy or whatever it was called. is there an ubuntu equivalent to rip movie DVD's to my harddrive?

i have dvd::rip but it just gave me errors when ripping, im assuming its due to protection.

---

### Post by steveneddy on 2009-12-18
[handbrake]("http://handbrake.fr/downloads.php")

---

### Post by PaulReaver on 2009-12-18
Not that I rip Copy protected DVD's (Cough Cough) but,
make sure you have  libdvdcss2 installed to play DVD's

but put the disk in the tray
right click
"copy disk"

Brasero should be able to do what you want.

Avidemux is also a good app if you want to convert a dvd to other formats.

---

### Post by SpatzST on 2009-12-18
blah, all this software is confusing... in handbrake i have to rip 4 individual files? the first part only says 23m, there 4 files that are about 1gb, do i have to rip each one separately?

i dont see libdvdcss2 in synaptic, but i have libdvdread4

---

### Post by PaulReaver on 2009-12-18
Can you play DVD's on your ubuntu yet?
if not
in a terminal:
sudo apt-get install ubuntu-restricted-extras
sudo /usr/share/doc/libdvdread4/install-css.sh



that should install libdvdcss2
It'll also install ,fonts, java, flash player and various codecs for playing many different music and video formats
it also gets round the copy protection.
Then just right click and copy disk(to take an .iso)

remember its only legal in europe (not in the USA)to have one backup of anything you own.
if you don't own it, you shouldn't be copying it.

---

### Post by cybergalvez on 2009-12-18
k9copy is what you want

---

### Post by PaulReaver on 2009-12-18
i think he just wants the .iso

k9copy is a good app,
but Brasero does the job and is already installed.
either way he'll still need libdvdcss2



merry christmas

---

### Post by scottuss on 2009-12-18
> **PaulReaver said:**
> Can you play DVD's on your ubuntu yet?
if not
in a terminal:
sudo apt-get install ubuntu-restricted-extras
sudo /usr/share/doc/libdvdread4/install-css.sh



that should install libdvdcss2
It'll also install ,fonts, java, flash player and various codecs for playing many different music and video formats
it also gets round the copy protection.
Then just right click and copy disk(to take an .iso)

remember its only legal in europe (not in the USA)to have one backup of anything you own.
if you don't own it, you shouldn't be copying it.


Are you sure it's not the other way around? I was under the impression that it was legal to have a backup in the USA? Also, you can't really lump the legal issue into "it's only legal in Europe" because Europe has so many countries in it.

It certainly isn't legal to have ANY copies, not even for backup purposes here in the UK (which, as I'm sure you are aware, is in Europe)

---

### Post by Some Penguin on 2009-12-18
> **scottuss said:**
> Are you sure it's not the other way around? I was under the impression that it was legal to have a backup in the USA? Also, you can't really lump the legal issue into "it's only legal in Europe" because Europe has so many countries in it.


CSS qualifies as a 'technological access protection method' under the DMCA, unless that's been overturned, so in practice you'd need to violate the DMCA to do de-CSSing in order to rip it.

---

### Post by bkmfs on 2009-12-18
First unmount the disk while it is in the tray and then type:

sudo readom dev= /dev/cdrom f=/*/*.iso

(the "*" represents your personal choice of file path) in a terminal.  Please make sure that you have legal permissions to copy the disc.

---

### Post by steveneddy on 2009-12-20
> **SpatzST said:**
> blah, all this software is confusing... in handbrake i have to rip 4 individual files? the first part only says 23m, there 4 files that are about 1gb, do i have to rip each one separately?

i dont see libdvdcss2 in synaptic, but i have libdvdread4

I use Handbrake all the time. It makes a nice file in any format that you prefer, and I put mine in .avi with no titles or menus, just the movie.

---

### Post by Groucho Marxist on 2009-12-21
> **scottuss said:**
> Are you sure it's not the other way around? I was under the impression that it was legal to have a backup in the USA? Also, you can't really lump the legal issue into "it's only legal in Europe" because Europe has so many countries in it.

It certainly isn't legal to have ANY copies, not even for backup purposes here in the UK (which, as I'm sure you are aware, is in Europe)

In terms of the US and our current frustrating laws, it's illegal to make any copies of any discs, including legally obtained ones. The MPAA and other like-minded groups are attempting to exacerbate matters by marketing on-demand programming over traditional disc-based media. As such, the result would be pay for play content at the whim of the distributor rather than the control of the consumer.

---

### Post by scottuss on 2009-12-21
> **Groucho Marxist said:**
> In terms of the US and our current frustrating laws, it's illegal to make any copies of any discs, including legally obtained ones. The MPAA and other like-minded groups are attempting to exacerbate matters by marketing on-demand programming over traditional disc-based media. As such, the result would be pay for play content at the whim of the distributor rather than the control of the consumer.

Ah right. I was under the impression you guys were allowed to make backups of media for your own personal use only. The last time I read about that was quite a long time ago so I guess things must have changed.

---

### Post by blur xc on 2009-12-21
> **SpatzST said:**
> blah, all this software is confusing... in handbrake i have to rip 4 individual files? the first part only says 23m, there 4 files that are about 1gb, do i have to rip each one separately?

i dont see libdvdcss2 in synaptic, but i have libdvdread4

I think, if you've installed the ubuntu-restricted-extras package and the medibuntu stuff, you are covered.

And handbrake is awesome- if you are making individual files, you are using it wrong.  On the import media page (it's been a while since I've used it) there's an option to box that you click on that grabs all the chapters in one shot.  I use it to rip dvds to play on my ipod and/or iphone.  It's great.

Of course, last time I checked you still needed itunes to put the video onto the ipod.

BM

---

### Post by Statik on 2009-12-21
K9copy is good to take you from DVD9 to DVD5, or to Xvid AVI. Or, if you're in a rush, make a DVD5 ISO, then later, open the ISO and make your Xvid AVI. Works great.

---

### Post by stinger30au on 2009-12-21
make sure you can play dvds first off in ubuntu

if you want to make a mirror image of the dvd movie and shrink it at same time to fit a 4.7 gig signle sided dvd disc, k9copy is the go

plenty of tutorials round on how to do this

if you want to rip it to a mp4 or the likes theres a few alternatives

dvd::rip

or handbrake

again plenty of tutorials round on how to do this

---

### Post by audiomick on 2009-12-21
In Germany (also in Europe...:) ) you are allowed to make yourself a backup copy of stuff you have legally bought, I think.

---

