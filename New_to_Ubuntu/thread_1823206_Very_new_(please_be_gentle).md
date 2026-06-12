---
title: "Very new (please be gentle)"
date: 2011-08-11
forum: New to Ubuntu
---

### Post by frontman555 on 2011-08-11
Hi from a newbie,

I have (like many others) been in the grip of windows for all of my computing life and was quite enjoying win95 mainly because of the amount of understanding needed to keep it all working smoothly. Now having been made "idiot proof" through it's various incarnations it has become boring. frustrating and expensive!

I am really looking forwards to getting into the whole Ubuntu way of doing things but at the moment am still a bit nervous with the terminal, but have managed to do a couple of things that seem to have worked (so far).

My only initial issues are with the graphics. Driver and settings for nvidia ge force card, and also the fact that I can not transfer photos from my finepixAV220 and my finepixS 5500.

I do realize that there are a huge amount of posts on both these subjects, but I would be grateful for any help pointing me in the right direction for my specific needs.

(I know I need a new PC but times are hard)

Looking forwards to hearing & chatting in the future

Cheers Col.


ubuntu 11.04 (natty)
gnome; 2.32.1
Kernel;  2.6.38-10-generic

OS Type ; Linux
GCC Version; 4.5.2 (i686-linux-gnu)
Xorg version ; 1.10.1 (21 May 2011  11:38:35AM)

Model; AMD Athlon(tm) XP 2200+
Fq : 1798.503 MHz

Graphics Card; nVidia Corp NV17 (geForce4 MX 420) Rev a3

---

### Post by kaldor on 2011-08-11
I have a Finepix camera and it is fully compatible with both of my Linux PCs. How is it not working? All I do is plug in the USB cable and load up the Shotwell application and import from Camera.

---

### Post by oldfred on 2011-08-11
If you install nVidia drivers you want to be sure to install the older version that matches your card. Do the  current drives work ok?

GeForce4 and older GPUs are supported through the 96.43.xx and 71.86.xx NVIDIA legacy graphics drivers. 
GeForce FX GPUs are supported through the 173.14.xx NVIDIA legacy graphics drivers.


Even with XP, I never used any direct connections to connect any of my cameras to the computer. I always have used a memory card reader and extracted memory card from camera and plugged it into the reader. Then I am just copying from one file system to another.

---

### Post by kaldor on 2011-08-11
> **oldfred said:**
> Even with XP, I never used any direct connections to connect any of my cameras to the computer. I always have used a memory card reader and extracted memory card from camera and plugged it into the reader. Then I am just copying from one file system to another.

That works too (I think it's pretty fool proof also) but I always have a cable by my PC so it's easier for me to just plug it in.

---

### Post by frontman555 on 2011-08-11
Hi, and thank you for the speedy reply. I initially tried shotwell and had no luck with it, so after seeing you post I re installed it and it worked !!!
So thank's for the heads up, it may have been a very long time before i got round to trying it out again ( after a few hundred hours of reading posts and trying codes.

Cheers Col.

---

### Post by kaldor on 2011-08-11
> **frontman555 said:**
> Hi, and thank you for the speedy reply. I initially tried shotwell and had no luck with it, so after seeing you post I re installed it and it worked !!!
So thank's for the heads up, it may have been a very long time before i got round to trying it out again ( after a few hundred hours of reading posts and trying codes.

Cheers Col.

As for your NVIDIA driver, what do you do on your PC? If you're not into gaming or much multimedia, you might be fine without it.

---

### Post by Johnb0y on 2011-08-11
> **oldfred said:**
> If you install nVidia drivers you want to be sure to install the older version that matches your card. Do the  current drives work ok?

GeForce4 and older GPUs are supported through the 96.43.xx and 71.86.xx NVIDIA legacy graphics drivers. 
GeForce FX GPUs are supported through the 173.14.xx NVIDIA legacy graphics drivers.


Even with XP, I never used any direct connections to connect any of my cameras to the computer. I always have used a memory card reader and extracted memory card from camera and plugged it into the reader. Then I am just copying from one file system to another.

> Even with XP, I never used any direct connections to connect any of my  cameras to the computer. I always have used a memory card reader and  extracted memory card from camera and plugged it into the reader. Then I  am just copying from one file system to another
best option... also cheapest and quickest...lol! go forth and simplify! lol!

---

### Post by frontman555 on 2011-08-11
Thank's again Kaldor/oldfred. i have seen a post re; older geforce drivers and will now have a go (with more confidence than before)
The only things I do graphics wise are youtube which is not to bad, but i also have some DVDs that I would like to edit (taken of my band and put onto DVD as one track ,so I want to split the tracks up)
The movie player will not recognize "shop bought" DVDs but this may be a different issue (DVD encryption  library not installed ?)

---

### Post by kaldor on 2011-08-11
> **frontman555 said:**
> Thank's again Kaldor/oldfred. i have seen a post re; older geforce drivers and will now have a go (with more confidence than before)
The only things I do graphics wise are youtube which is not to bad, but i also have some DVDs that I would like to edit (taken of my band and put onto DVD as one track ,so I want to split the tracks up)
The movie player will not recognize "shop bought" DVDs but this may be a different issue (DVD encryption  library not installed ?)

Ah, that's not a graphics issue. Due to patent laws and such some codecs and libraries are not allowed to be distributed by default. You need to install libdvdcss. Copy and paste these two commands in the terminal:

```
sudo apt-get install libdvdread4
```
```
sudo /usr/share/doc/libdvdread4/install-css.sh
```

Also note you can install VLC Media player in the Software Centre which can play DVDs without extras.

---

### Post by Johnb0y on 2011-08-11
> **kaldor said:**
> Ah, that's not a graphics issue. Due to patent laws and such some codecs and libraries are not allowed to be distributed by default. You need to install libdvdcss. Copy and paste these two commands in the terminal:

```
sudo apt-get install libdvdread4
``````
sudo /usr/share/doc/libdvdread4/install-css.sh
```Also note you can install VLC Media player in the Software Centre which can play DVDs without extras.

> Also note you can install VLC Media player in the Software Centre which can play DVDs without extras VLC is the best for all round vids... not seen anything yet that it cant play... (not that i am looking at the mo... just enjoying a great simple program) :D

---

### Post by frontman555 on 2011-08-11
Well thank you all for your quick response and excellent advice. In one evening I have uploaded my photographs and played both types of DVD (and pics stored on CD).
I can now get on with enjoying my PC again and hopefully try out a few more tweaks without fear of total collapse.
The only other thing is mp3 and other audio ....................... no let's leave that for another night!!!

Cheers to you all again from a very rainy Lancashire UK. (but happy bloke)

Col

---

### Post by kaldor on 2011-08-11
> **frontman555 said:**
> Well thank you all for your quick response and excellent advice. In one evening I have uploaded my photographs and played both types of DVD (and pics stored on CD).
I can now get on with enjoying my PC again and hopefully try out a few more tweaks without fear of total collapse.
The only other thing is mp3 and other audio ....................... no let's leave that for another night!!!

Cheers to you all again from a very rainy Lancashire UK. (but happy bloke)

Col

Mp3 and other audio is extremely simple. You need to install the restricted extras package.

Run this:

```
sudo apt-get install ubuntu-restricted-extras
```

Flash, Java, Microsoft Fonts, and codecs will now work.

Cheers :)

---

### Post by frontman555 on 2011-08-11
Cheers Downloading it now

---

### Post by frontman555 on 2011-08-11
hi me again, i have entered the restricted extras cod and now have a Package configuration screen re; license agreement ending in <ok> but I can't seem to do anything else, any ideas ??

---

### Post by frontman555 on 2011-08-11
think I have sorted it

---

### Post by frontman555 on 2011-08-11
Done Cheers matey

---

### Post by ExileAmongYou on 2011-08-11
From what I remember, there's a couple of license agreement screens that come up when you're installing the restricted extras, one for Java and one for the truetype fonts. I think I had a problem once where I accidentally clicked decline on one of them, and it gave me no way to go back, so I just had to go back, reinstall, and make sure I accepted them the next time around.

---

### Post by kaldor on 2011-08-11
Yeah, for future readers I will reply:

You may need to hit the Tab key to reach "OK" and then press enter. You can also find ubuntu-restricted-extras in the software centre.

---

### Post by frontman555 on 2011-08-11
Yes I got there eventually. & thank's again

---

