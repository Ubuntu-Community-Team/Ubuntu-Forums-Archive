---
title: "can you use the ipod nano or ipod touch on linux ubuntu"
date: 2010-01-23
forum: New to Ubuntu
---

### Post by narutarded on 2010-01-23
i want to get a new mp3 player cuz my old one broke. somewhere i heard that ipods can work on linux ubuntu. is this true? is there a linux version of the software they take?

---

### Post by JiuJitsu500 on 2010-01-23
Without Jailbreaking your iPod it's possible, depending on the model. I'm no pro, someone correct me if I'm wrong pleaase, but a lot of my friends have all kinds of iPods/Zune (I'm in the Army, so we spend a lot of time with them)...

Rythmbox can read all models of Ipod, but can't change the music in them. Using Hipo or another managing software however you can change anything on some models (but not touch/phone).

However, I think the easiest way to do the iPod or Zune is VirtualBox with Windows XP or 7. You can simply start that machine and download the newest iTunes/Zune software to it, and use it to do everything you're already used to doing. Because of lack of commercial support for software in linux (for obvious reason...) it's a pain sometimes to do it through linux directly. It is possible, but simpler mp3 players are the way to go for me personally now on :) It's easier, faster, and doesn't require running Mac or Windows or iTunes/Zune inside it to make it easy...

---

### Post by stoogiebuncho on 2010-01-23
I haven't tried an iPod touch yet, but I have an old iPod nano and it works with Ubuntu pretty well (I've used Rhythmbox and gtkpod and they both work well).

However, if you're buying something new, I'll echo what JiuJitsu500 said and recommend that you go with something simple.  I've heard lots of good things about Sansa players. ([http://www.sandisk.com/consumer-products/music-player/sansa-players.aspx]("http://www.sandisk.com/consumer-products/music-player/sansa-players.aspx"))

---

### Post by kelvin spratt on 2010-01-23
I would recommend Atunes for any non Ipod it works with all mp3/mp4 players music only
it will rip and encode and transfer to the player. 
For mp3/mp4 players you should also be able to just drag and drop mp3 files and and converted avi video clips.

---

### Post by HermanAB on 2010-01-23
Howdy,

In my experience, the worst players are those made by Sony.  The Apple players mostly work with Linux, using Gtkpod.  So if you have money to burn then Apple is probably OK.

However, if you want a player that works generally beter than Apple for a fraction of the cost, then get a Samsung.

---

### Post by narutarded on 2010-01-25
thanks for the info guys 
if anyone wants to reply with some more info that would be great. :)

---

### Post by nishant.singh28 on 2010-01-25
I use an iPod Nano 4g with gtkpod. Works better than even iTunes. It's definitely an option.

---

### Post by baddog144 on 2010-01-25
Any somewhat recent iPod Touch will blatantly not work, unfortunately. Apple has done some encrypting and changing around of the library, so any music you copy to your ipod with gtkpod or similar won't actually show up, and you'll probably end up corrupting your ipod library and have to restore it with iTunes on Windows/OS X

---

### Post by tigerking615 on 2010-01-25
I have a Zune and it doesn't connect at all with Ubuntu (other than charging) without a virtual box :(. However, it's still an amazing mp3 player, so I find it worth booting into Windows (gasp!) to sync every couple weeks.

---

### Post by narutarded on 2010-01-26
ok so i can use the new ipod nano on linux, which is good. but i really can't use the ipod touch? i mean the nanos fine but the touch is like the cooliest thing ever. any ideas how the use the ipod touch on linux?

---

### Post by perce on 2010-01-27
> **narutarded said:**
> ok so i can use the new ipod nano on linux, which is good. but i really can't use the ipod touch? i mean the nanos fine but the touch is like the cooliest thing ever. any ideas how the use the ipod touch on linux?

I don't own any apple gadget, and I never will, so take this for what it is: third hand information. Apple decided that the ipod touch will not work with anything different with itunes, but apparently you can jailbreak it (thus voiding the warranty and maybe infringing the DMCA if you live in the US) and install a ssh server in in the ipod, and put music into it by scp.
You can look at here for instructions: [http://www.ipodtouchhacks.com/ipod-touch/detailed-instructions-on-how-to-ssh/]("http://www.ipodtouchhacks.com/ipod-touch/detailed-instructions-on-how-to-ssh/")

Honestly, I don't understand why Apple made a device which is apparently able to run every program in the world, and then blocked it so that only few are easily available to the user, and I understand even less users who want to buy it nonetheless.

---

### Post by 3rdalbum on 2010-01-27
> **HermanAB said:**
> Howdy,In my experience, the worst players are those made by Sony.

What experience is that? All Walkmans made in the last few years will work plug 'n' play on Linux. Which is more than you can say for iPods.

Please, original poster, if I'm not too late: Buy a Walkman or something else that accepts music just by dragging and dropping it onto the player. I'm personally a fan of the X-series Walkmans; they do a much better job of playing music and videos than any iPod. The screen has to be seen to be believed, and you get real noise-cancelling headphones.

EDIT: I notice you're interested in the iPod Touch. Archos have a new MP3 player that is actually based on the (Linux-based) Android mobile phone OS. This is probably the closest thing to an iPod touch, and it might work drag 'n' drop. You definitely want to buy something that you can just drag 'n' drop music onto in your file manager, because then it will ALWAYS work no matter what.

---

### Post by drzoo2 on 2010-01-27
Any fifth generation Ipod which includes the Nano and the Touch is not supported. 

See here on the gtkpod site....

[http://sourceforge.net/tracker/?func=detail&aid=2894503&group_id=67873&atid=519276]("http://sourceforge.net/tracker/?func=detail&aid=2894503&group_id=67873&atid=519276")

---

### Post by narutarded on 2010-01-28
[U]what do you mean jailbreak it? what does that do? and what does the ssh server do?...and why the crap am i underlining this...
[/U]

---

### Post by driven1 on 2010-01-28
I have had little success with my 2Gen iPod touch. I did the jailbreak (safe and simple, you can always restore). I can transfer files to and fro, but it will definitely not sync nor will it integrate with desktop apps. Music isn't available through the iPod music player and you **can't** transfer playlists. Videos are easier to transfer and watch, but I have only been able to transfer using WiFi, which is much slower than usb. I find this impractical and I hope to "upgrade" to Android-based device.

My iPod classic (60GB v5.5 with video playback) and iPod shuffle (2 Gen model) both sync flawlessly on Jaunty using Banshee, which btw has become my favorite music player.

Latest iPod nano with video camera will not sync with Ubuntu, or at least my humble skills haven't risen to the challenge. It seems to use the same type of file system as the touch/iphone. I understand that previous versions of the nano may work, but I have no direct experience.

I hear good things about the sansa players... again third hand. Depends really on what you expect the device to do. Music only, +video, more? Good luck

---

### Post by driven1 on 2010-01-30
[http://redsn0w.com/]("http://redsn0w.com/")

go here for more info on jailbreaking. Basically it allows the iPod Touch/iPhone to be modified with software that isn't approved or controlled by Apple. Basically you are free to use it anyway you see fit. There are some cool mods and helpful programs available, but it will not completely solve you sync issues with Ubuntu. My work around was a dual boot of XP that I only use for iTunes.

---

### Post by narutarded on 2010-02-02
thanks guys i'm definitly gonna get some kind of ipod someday. but good news. my zen that got water damaged is working again. i have another problem. i don't and can't put on the program for creative zen mossiac. i don't know how to put the music i rip and download from frostwire onto my mps player. any ideas how to do this with out using the zen program you normally download?:KS

---

### Post by Jeff Seager on 2010-02-28
I have a Latte Neon that I really like, and on this thing I can save and play mp3s and watch avi files and read txt files, and listen to the radio and record notes to myself ... which seems enough to ask of a tiny little device that costs less than $100.

When I plug it in, using Windows or Ubuntu or a Mac, it simply shows up as an external drive into which I can drop files. How hard is that? All I'm saying is that it's your choice: You can buy devices that force you to interact in only one way, or you can buy devices that are versatile.

Zune won't work in Ubuntu because Microsoft engineers chose not to make it compatible. Caveat emptor!

---

### Post by demonickronik57 on 2012-06-25
i have RockBox on my ipod 5th gen. its not too hard and add many many cool features.

---

### Post by lisati on 2012-06-26
Back to sleep, old thread

---

