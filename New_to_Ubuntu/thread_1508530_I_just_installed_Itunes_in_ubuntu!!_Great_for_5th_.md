---
title: "I just installed Itunes in ubuntu!! Great for 5th gen Ipod nano!!!"
date: 2010-06-13
forum: New to Ubuntu
---

### Post by bradmayne04 on 2010-06-13
WARNING!!!!! THIS IS UNDER CONSTRUCTION IF YOU DOWNLOAD ITUNES 7 IT WONT WORK OUT OF THE BOX!!!!!!!!!! YOU NEED A NEWER VERSION!!!! AND YOU MIGHT NEED A NEWER WINE !!!!!!!!!!!!!!!!!!!!!!!!!!  ITS 430 AM HERE IN DIRTY JERSEY AND I AM TIRED I WILL WORK ON THIS MORE IN THE MORNING!!!! YOU CAN DO THIS YOU JUST GOTTA TWEAK SOME STUFF !!!!!  DO THIS AT YOUR OWN RISK OF BLOOD SWEAT AND TEARS THE ONLY REASON I DID THIS IS CUZ I HATE WINBLOWS!!!!!!


Hey all!! I've been trying to switch over to ubuntu completely.  I just got samba running and added the printers on my moms desktop.  Now, I have a 5th generation Ipod nano.  The problems was that I could not get it to work with gtkpod or any other software that ubuntu has because the 5th gen is so new.  So, what can ya do?  Well, number 1 install wine from synaptic.  regular wine will be fine.  (no need to use that new version).  then go to a terminal and type this command:

winecfg  (you don't have to be sudo)

then choose the windows XP option, select autodetect from the drive tab, make sure the ALSA driver is checked and the OSS driver IS NOT checked in the audio tab.  the  So, install that then download itunes here's a old Itunes that I know will work cuz I just did it>>

[http://www.oldapps.com/itunes.php?old_itunes=20](http://www.oldapps.com/itunes.php?old_itunes=20) (maybe you can use a newer one but i didn't so please don't complain it didn't work if you do another Itunes version okay?  Then select the open w/ WINE when prompted.  At the welcome screen just accept the license.  Then make sure that no installer options are selected i.e. desktop shortcut etc.  when the popout appears asking about autorun select NO!! After another short download click finish.  Then when finished go back to the terminal and use this command:

wine ~/.wine/drive_c/Program\ Files/iTunes/iTunes.exe

And that's all she wrote folks.  I then went to my windows partition from >>places>>>
I'm on a emachine laptop (yeah i know but it actually works better than my toshiba satellite believe it or not!) then users brad (i'm brad btw lol) music.  I then opened my music folder in places and just dragged over my metallica folder to try this out and dragged the folder to the itunes icon and put it there.  it immediatly put the metallica folder in Itunes just like it would in windows! I'm going out to my car in a bit to get my ipod nano 5th gen.  I fully believe this is going to work at this point.  if it doesn't then I will play with this a bit more.  Any questions just ask away.  Please don't forget to say thanks in a reply cuz I could really use it here for my forums cred lol!!

---

### Post by Tahakki on 2010-06-13
I don't think Wine works for most USB devices like iPods. I've never heard of syncing being done before with wine.

---

### Post by d3v1150m471c on 2010-06-13
gtkpod + **[_Ibulk_]("http://www.mediafire.com/?4oq0iyi3ynu") **= Ipods done Tux style ;)

---

### Post by bradmayne04 on 2010-06-13
> **d3v1150m471c said:**
> gtkpod + **[_Ibulk_]("http://www.mediafire.com/?4oq0iyi3ynu") **= Ipods done Tux style ;)


What's Ibulk????? I think you should go into some detail cuz their page doesn't say anything!  Let everyone know man!!!

---

### Post by d3v1150m471c on 2010-06-13
> **bradmayne04 said:**
> What's Ibulk????? I think you should go into some detail cuz their page doesn't say anything!  Let everyone know man!!!

Ibulk is a small program I wrote and I'm still developing that converts a batch (several) of videos to work on an Ipod. For as long as it works and I'm working on it, it'll be on my signature. currently it only has one function, producing highest quality videos for an Ipod. I'm going to add more features soon. It works well if you want to convert an entire season of metalocalypse over in less than an hour \m/.

---

### Post by bradmayne04 on 2010-06-13
yeah I just woke up. so anyways i googled this and i guess i'm not the only one who thought of it.  so yeah this really can be done.  btw i like adult swim to. metalcolapyse isn't one of my fav's but i do like it!! I like aqua teen hunger force the best!!

---

### Post by bradmayne04 on 2010-06-15
sorry I haven't written and update as soon as I promised.  Due to serious health concerns I fell back.  Today I have to go to a district office of my parole as well.  I am not sure what is about to happen at this point.  My life has had some stability for quite some time and these forums have brought great joy in my life trying new things and all.  However like I said I don't know what's going to happen this morning in passaic.  I'm actually kind of scared lol.  however at this point due to my serious health problems there isn't much that the njdoc and the department of parole can do.  I am hoping that they allow me to stay home under the care of my doctors.  all of you who have posted have helped me especially old fred.  If i don't update this page by tomorrow i will be in a hospital.

---

### Post by 3rdalbum on 2010-06-15
> **d3v1150m471c said:**
> Ibulk is a small program I wrote and I'm still developing that converts a batch (several) of videos to work on an Ipod. For as long as it works and I'm working on it, it'll be on my signature. currently it only has one function, producing highest quality videos for an Ipod. I'm going to add more features soon. It works well if you want to convert an entire season of metalocalypse over in less than an hour \m/.

It sounds a lot like [Blacklight]("https://launchpad.net/blacklight"), but for iPods. Blacklight used to have "other features" too, but in the end all anyone ever used it for was the video encoding :-)  It has some nice features for video encoding, actually; three different bitrates and qualities, the ability to encode videos and keep them on hard disk so you can transfer them later, encoding multiple videos at the same time to occupy all your cores (a bit moot for x264 as it scales across cores anyway), and automatically generating thumbnails for your videos.

Nah yeah I'm not trying to sell my program to you :-)  But you might want to take a look at what I've implemented and borrow some ideas from it.

---

### Post by bradmayne04 on 2010-06-19
I am home now. I'm really tired but from what i understand there is a way to patch WINE and get usb support.  not sure though i'm really tired right now. thanx for all the pm's guys i got 'em today. that's pretty cool gettin all those messages from cat's that i don't know wishin me well btw.

---

### Post by zazootheparrot on 2010-07-16
I also wanted to install itunes so I did exactly as mentioned but I have encountered a problem. I first installed 1.1.42 version of wine. Then installed iTunes 7.2. The problem is, after installing iTunes it gives a message saying that ```
err:xrender:get_xrender_format_from_color_shifts No XRender format found!

```Could you please help me what to do? 

Thanks

p.s. I'm using a 32-bit ubuntu 10.04 LTS on a sony vaio VGN-SZ740.

---

### Post by zazootheparrot on 2010-07-23
Hello there,

Any updates on the issue? I really need help with this application. 

Thx

---

### Post by Nerflander on 2010-07-23
i think you can bette look for a replacing program then itunes. Itunes is already horrible proted to windows. It cant be rly beter to linux unless someone really programms his brains out and breaks steve jobs iturd copyrights and make a beutifull program but i quess that aint gonna happen for long time. 

And ye i am also looking for a itunes look alike program for ubuntu i dont like window anymore! so any1 who knows something about a good program for ubuntu thzat works for iphone and stuff ( inmport music on it etc )  i would be a happy man :)

---

### Post by zazootheparrot on 2010-07-27
I want to sync my iphone 3G, so I really need to install itunes. As well as that, I want to buy stuff using the itunes store. I could not install itunes using the method mentioned because it gave an error :
```
err:xrender:get_xrender_format_from_color_shifts No XRender format found!
```I still can't install itunes. 

Is it because my computer is a 32-bit one?
At the moment, I'm planning to install itunes using virtualbox but I would prefer to have itunes on linux rather than the virtualbox.

---

