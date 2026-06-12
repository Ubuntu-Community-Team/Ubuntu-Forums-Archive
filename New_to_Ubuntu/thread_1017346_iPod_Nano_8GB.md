---
title: "iPod Nano 8GB"
date: 2008-12-21
forum: New to Ubuntu
---

### Post by sp00ner on 2008-12-21
I have searched and read many threads concerning syncing the NANO 4th gen with Ubuntu. I have tried Amarok, Rhythmbox, Banshee, and GTKpod. None of them seem to work. They all see the device and "appear" to transfer the songs. The songs do get transferred to the IPOD_Control\Music folder, but when I eject the device and goto Music it always shows 0 songs. Can anybody help me? I really dont want to resort to using Itunes on my Windows machine.

---

### Post by aheckler on 2008-12-21
You could erase the native iPod firmware and use [iPodLinux]("http://www.ipodlinux.org/") or [Rockbox]("http://www.rockbox.org/").

---

### Post by Kareeser on 2008-12-21
Are you ejecting using Nautilus, or are you just pulling out the USB cord?

Ubuntu might have some functionality (although I can't see the benefit) of not writing information to flash drives until it is ejected...

---

### Post by sp00ner on 2008-12-21
I right click on the iPod icon that appears on the desktop and select eject. The device then tells me it is safe to unplug. As for replacing the Firmware,   that sounds a little dicey. I looked at the ipodlinux web page and it looked like the Nano 4th gen is not yet supported. Would it permantly ruin the device if it did not go "well"?

---

### Post by adobrakic on 2008-12-21
I had rockbox on a 80gb video iPod, and to tell you the truth it was a lot better than the normal ipod firmware. It allows you to put different filetypes on your ipod (.flac was the most important for me) and it acts as a normal mp3 player, so it just opens a folder and you drag-n-drop your music into that. And yes, it's very easy to take off and make your ipod "normal" again.

---

### Post by sp00ner on 2008-12-21
> **adobrakic said:**
> I had rockbox on a 80gb video iPod, and to tell you the truth it was a lot better than the normal ipod firmware. It allows you to put different filetypes on your ipod (.flac was the most important for me) and it acts as a normal mp3 player, so it just opens a folder and you drag-n-drop your music into that. And yes, it's very easy to take off and make your ipod "normal" again.


I wouldnt mind giving it a shot, but I checked the Rockbox website and it seems 2nd, 3rd, and 4th gen Nanos are not suppotred. I guess if no other solutions present themselves, I will probably give it a shot anyway.

---

### Post by adobrakic on 2008-12-21
You're right, I have the iPod nano (2nd gen), and it does not work. The reason those generation nano's don't work is because the encryption is different, alongside the very firmware, and they haven't found out how to do what they've done with the rest of the mp3 players.

I'm not sure how it would run with the 4th gen., but I highly doubt it'll suffice. Maybe you can restore your iPod to factory settings, and try again via one of those programs. I have used Amarok, GTKPod, and songbird to transfer songs to my iPod, and all of those worked very well. 

Good luck.

---

### Post by sirsean1227 on 2009-01-31
hello! i am having the same problem with my friends 4th gen ipod nano under linux.... the songs transfer to it ... but after ejected(right click ipod icon)  ipod says 0 songs.... when i plug it back in the songs show up under Floola.... so it seems that it is actually being put on the ipod but there is some sort of new "brick" in these newer ipod nanos keeping you from using any other software besides bloated a$$ "itunes".... any help would be much appreciated... using ubuntu 7.10... thanks Sean

---

### Post by jimmy the saint on 2009-01-31
check out the link below for an explanation (and some background) on why newer ipod and iphones won't work with linux.  Also, why those of us who mistakenly paid apple for anything shouldn't make that mistake again (I won't)

[http://distorted-loop.com/2008/11/25/iphone-on-trial-while-apple-attacks-ipodhash/](http://distorted-loop.com/2008/11/25/iphone-on-trial-while-apple-attacks-ipodhash/)

The article discusses the iphone, but the hash issue is the same.

---

### Post by 4MD D4D on 2009-02-05
I have the nano 3rd gen 4gb was having the same issue and using gtkpod and putting the music in as a podcast or selecting the podcast folder before transferring music has allowed me to successfully have it recognized in the music folder when ejected although I learned the hard way to click save changes when done transferring music or it wont recognize the transfer at all.

---

### Post by erlguta on 2009-02-15
I have the same problem with Ipod nano 4 generation. I'm tired of trying to transfer music with Rhythmbox, amarok and gtkpod. It seems that it transfer the songs ok, but then when i ejected it the songs not appears in music section of the Ipod.
I do not think to do a damn workaround or lose a second of my life to make it work. 
Apple, is you who have to worry about that works in linux. 
We are a large and increasingly powerful community that you have to worry about.
So tomorrow I will go back to the store and they returned the money to me.
I will send a mail to Apple to explain my complaint and the reason for my return.

---

### Post by clconway on 2009-02-17
I wrote a [step-by-step guide]("http://procrastiblog.com/2009/02/16/using-an-ipod-nano-on-linux/") to using a 8GB Nano 4G with Amarok on my blog. There are two fundamental problems you need to work around:

1. The song database is (weakly) encrypted, so you have to write the serial number to a config file to let Ubuntu access it.

2. You need a fairly recent libgpod in order to get cover art working correctly on newer iPods. You can get a compatible version of Amarok from [my PPA]("https://launchpad.net/~cconway/+archive/ppa") .

---

