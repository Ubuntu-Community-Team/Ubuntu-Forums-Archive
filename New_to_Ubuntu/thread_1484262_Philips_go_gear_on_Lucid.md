---
title: "Philips go gear on Lucid"
date: 2010-05-15
forum: New to Ubuntu
---

### Post by vivek40 on 2010-05-15
Hii I just got this Philips Go gear mp3 player from a friend as a gift. The manual says when plugged in the usb drive it will install some software etc etc.. but that is supposed to be for windows.I am on lucid , but even after I plug it in the USB drive, I dont see anything getting mounted. I did a little bit of google and came to know that i had to insatll gnomad2 for it.. I did that but still after plugging in I dont see anything being mounted.. Gnomad 2 returns"No jukeboxes found on usb bus".. it is the same usb port where i plugin my cameras, phones, usb drives etc and everything works... Please help someone

---

### Post by Temposs on 2010-05-15
First thing to do is to type in the terminal:

```
lsusb
```

And see if your device is being detected at all.

---

### Post by Sealbhach on 2010-05-15
Just want to say that I have one of those, the Go Gear SA 2825 and it works for me, so it's not a compatibility issue, I would say.

Try installing Gpodder and see if that can find it for you.

.

---

### Post by vivek40 on 2010-05-15
Thanks Temposs... Please find the output of lsusb here.. I have the gogear plugged in but dont know if it is being detected.. Can you please check this...

```
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

---

### Post by vivek40 on 2010-05-15
Well I dont know how but it has suddenly mounted..... Now could someone please tell me how could I sync the music with it......would be a great help .. .

---

### Post by Temposs on 2010-05-16
It would probably be done best with Rhythmbox. See if it mounts in Rhythmbox, and try to drag music onto it in there.

---

### Post by vivek40 on 2010-05-16
Thanks for replying Temposs. but how do I mount it in rythmbox.. I opened rythmbox but the philips go gear is not visible there at all.. Do i have to do anything to get it mounted there

---

### Post by blue_naveen on 2010-06-20
I have Gogear on Lucid and I use Rythmbox to manage it. To do so, I read in a forum somewhere that you have to initially:
 * plug the GoGear,
 * open it with Nautilus,
 * create a text file named ".is_audio_player" which contains in it the text "audio_folders=Music/" [without the quotes; in my case the Go Gear already had the folder Music],
 * this file should be placed on the root of the file system of the Go Gear.

This says to Rythmbox that Go Gear is an audio player and that music/podcast files should be placed in the folder Music of the Go Gear. So now when you open Rythmbox the Go Gear should appear and you can drag / delete files with Rythmbox.

Hope that it helps.

Deva

---

### Post by vivek40 on 2010-06-22
That worked beautifully blue_naveen.. thanks a ton.... !

---

### Post by dveej on 2010-07-26
When I tried blue naveen's solution, I found that I could not put a text document or a folder in my GoGear. When I clicked on "Properties" / "Permissions", it said "You are not the owner, so you can't do this." Can anyone help me get recognized as the owner so I can try blue naveen's solution?

---

### Post by dveej on 2010-07-30
bump

---

### Post by libihero on 2010-12-11
wow worked for me! now how would i make it recognize the video on banshee?

---

