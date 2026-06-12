---
title: "iphone and mp4 fies"
date: 2010-05-07
forum: New to Ubuntu
---

### Post by mrgreaper on 2010-05-07
ok for the past 6 hours i have been trying to put a mp4 file onto my iphone

i started with a simple task... ditch my windows itunes and use my ubunut netbook to copy video, mp3, audiobooks and misc to my iphone

learnt 4 different methods of converting video files (why oh why do the guides not say HOW to copy the files to the iphone!?!?! just how to convert on linux) 

learnt how to ssh into my server pc inside terminal and get it to convert the videos in terminal 

learnt that if you close the terminal then the encoding stops (grrrr dam grrr arg)

now i have ubuntu 10.4 (updated specificlyy for the iphone features)

the music shows up in rhythem box both on the iphone and in the library and i can copy mp3 files no problem

i installed amok which freezes if i try to load it with my iphone plugged in

so i jailbroke my phone (i believed this to be necersary)

i managed to figure out mounting the phone using sshfs      (and found that mounting my servr pc like that is more effective then samba..learn something new every day)

i figured out how to install ipa files (wasnt what i was looking for and since itunes app on the phone does that anyway pretty useless, but interesting)

i tried to install itunes onto wine in ubuntu ....failed (its impossible)

installed gtkpod which shows the music but refuses to allow me to add the mp4 

came here to beg for help (im tired, im exhusted, im beaten) 

so how do i get mp4 files onto my iphone with out using itunes (and jpg files)

---

### Post by jbrown96 on 2010-05-07
Wow, you have pieced together some really outdated stuff that's overcomplicated your setup. 

1) Your iphone does not need to be jailbroken. It does not need ssh. You should probably undo this.
2) You need to install libimobiledevice0 and libimobiledevice-utils.
3) Install handbrake from handbrake.fr. It has a simple mode for converting for iphone/ipod touch. 
4) You should be able to sync the video using rhythmbox or gtkpod.

---

### Post by mrgreaper on 2010-05-07
> **jbrown96 said:**
> Wow, you have pieced together some really outdated stuff that's overcomplicated your setup. 

1) Your iphone does not need to be jailbroken. It does not need ssh. You should probably undo this.
2) You need to install libimobiledevice0 and libimobiledevice-utils.
3) Install handbrake from handbrake.fr. It has a simple mode for converting for iphone/ipod touch. 
4) You should be able to sync the video using rhythmbox or gtkpod.

1) ah crap...well 6 hours of searching i was bound to get outdated advice as well

2) libimobiledivice0 already installed the -utils one i added (thank you)

3)installed handbrake but it wont let me add anything to a queue i add an avi file and i can see the presets, set the destination etc but no add to queue button (it remains shadded out) (not a massive problem yet as i have some mp4 files i converted and copied with itunes before the change

4) ok maybe im missing something blindingly obviouse but how??????
i can drag music from my library in rythmbox no problem into my phone but i cant add videos to its library (i even tried dragging them straight from explorer(is it explorer on ubuntu? the folder view) to the library ...nothing tried draging directly to the phone icon in rythembox nothing

---

### Post by jbrown96 on 2010-05-07
> **mrgreaper said:**
> 1) ah crap...well 6 hours of searching i was bound to get outdated advice as well

2) libimobiledivice0 already installed the -utils one i added (thank you)

3)installed handbrake but it wont let me add anything to a queue i add an avi file and i can see the presets, set the destination etc but no add to queue button (it remains shadded out) (not a massive problem yet as i have some mp4 files i converted and copied with itunes before the change

4) ok maybe im missing something blindingly obviouse but how??????
i can drag music from my library in rythmbox no problem into my phone but i cant add videos to its library (i even tried dragging them straight from explorer(is it explorer on ubuntu? the folder view) to the library ...nothing tried draging directly to the phone icon in rythembox nothing

I've never tried videos. I was just going from the libimobiledevice website that said music/videos were working in amarok/rhythmbox/gktpod. I use Amarok and it can't do videos so I didn't suggest it. Best bet is gtkpod, but again, I have no experience with it. 
I'll check out the handbrake issue.

---

### Post by lashram on 2010-05-07
I use Rythymbox and I was able to synce my music as well as my video/movie files without any problems. I even tested transferring my music/videos by erasing the data on my iphone and letting it resync using rythymbox and it worked fine. Now I tried transferring a file in the acc format and received an error but i just converted it to mp3 then transferred it to my phone.

---

### Post by jbrown96 on 2010-05-07
I couldn't get handbrake to work, but after a gigantic fight, I now have ffmpeg working.


you need to install libavcodec-extra-52. If that package is not available then you need to add the Medibuntu repository with ```
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
``` You will also need ffmpeg and possibly a bunch of gstreamer files (all packages that start with gstreamer0.10-plugins- but don't install them unless they are necessary).

Now that ffmpeg is installed check to make sure that aac works. ```
ffmpeg -formats | grep aac
``` The output should look something like >  D  aac             raw ADTS AAC
 D A    aac             Advanced Audio Coding
  EA    libfaac         libfaac AAC (Advanced Audio Codec)
 As long as one codec is listed as "EA" then you will be fine. 
Install gtkpod and ifuse.

Now we are ready to convert. ```
 ffmpeg -i INPUT_FILE -f mp4 -vcodec mpeg4 -s 480?320 -acodec libfaac -ar 24000 -ab 65536 -ac 2 OUTPUT_FILE.mp4
``` 200000 bits/second is default and it seemed ok, but you can get a little better quality by increasing it. I tried 250000 and it looked nice on the iphone, specify with ```
-b 250000
``` and replace INPUT_FILE and OUTPUT_FILE. @200000 a 21min episode of Futurama was 41.9MB and @250000 the same episode was 49MB.
Now that you have your videos ready. Let's use gtkpod.

1) First time only. Make a directory to mount your iphone. ```
mkdir .iphone/
```
2) mount the iphone ```
ifuse iphone/
```
3) Open gtkpod
4) First time only. configure your iphone. Edit-->Repository/Ipod options. Add new ipod. Choose your model and change the mount point to /home/YOUR_USER_NAME/.iphone. Your iphone will show up on the left, and I just dragged my movies from the file manager over to it. It did not automatically copy them, I had to right click on the iphone and eject it, then it synced and took a couple minutes.
5) Be sure to unmount your phone before you remove it or ifuse can get angry. ```
sudo umount .iphone/
```

---

### Post by jbrown96 on 2010-05-07
Edit: It looks like Rhythmbox will be easier than gtkpod. I just don't have the heart to delete my previous post. It took way too long to research and write. The ffmpeg converting parts are still good. 

Looking up howto guides on this type of stuff is terrible on Linux. Methods change drastically between versions, so make sure to check the dates on articles/posts.

---

### Post by donaldt on 2010-05-08
You may want to try aTunes 2.0.0.

I have been running it under Ubuntu 9.04 for a couple of months.  It is an excellent substitute for Apple's itunes.  I've been using it with an iPod shuffle 2gb and it works as advertised.

Don't know if it will do all you want, but it is an active, free program that is still being developed.

---

### Post by mrgreaper on 2010-05-08
this is driving me nuts lol

ok atunes wont find my iphone

gtkpod wont let me add mp4 files (i need to install mp4v2)
i followed this guide [http://code.google.com/p/mp4v2/wiki/BuildRepository](http://code.google.com/p/mp4v2/wiki/BuildRepository)
but it still says i need to install mp4v2 library

so i went to [http://code.google.com/p/mp4v2/downloads/list](http://code.google.com/p/mp4v2/downloads/list) but the files are the same as the svn 

rythmbox wont accept video files



arghhhhhhhhhhhhhhhhh

for the love god apple why does the iphone not just have a folder for music a folder for video a folder for audiobooks a folder for pictures ...i mean really is that hard ARGHHHHHHHHHH

its looking like i will have to switch back to xp :(

---

### Post by mrgreaper on 2010-05-08
ok as you can imagine i havent been sat here just waiting for some kind soul to help me i have spent another 4 hours on google ...to no avail

i located mp4v2 library that gtkpod complains about not being there when i try to move an mp4 file

i downloaded it and compiled and installed it 

gtkpod still says i need it to be able to copy mp4 files (its there you stupid little program)

ok another search reveals i need gtkpod-aac not gtkpod

ah progress...
so i remove gtkpod and install gtkpod-aac

again it tells me i need mp4v2 library (BLEEP)

so i hunt down the main site for gtkpod (not hard to do)

i download the programme (it actualy gave me libgpod-0.7.93 and yes i checked i followed the right path to get it so i assumed it was part of that)

i removed gtkpod

and started to configure libgpod-0.7.93 but it said i needed liplist and sqlite3 

i installed sqlite3 

it said i still needed both of them

after some searching i found i needed to get the -dev versions...i did this

i installed libgpod-0.7.93 

gtkpod command not foud (expletitive beep expletitive)

i installed gtkpod-aac (the source on lucids repositrys is the same as the latest build mentioned on thier website)

again it told me i needed mp4v2 library

so i installed mp4v2 library again

gtkpod said no i needed it

so (incase it got broken when i installed gtkpod i reinstalled libgpod-0.7.93) 

gtkpod says ..no you need mp4v2 library ...


i am at a loss to what to do regarding gtkpod so i moved back to atunes to try and fix that

now ubuntu 10.4 mounts my iphone as afc://(lots of numbers) 

i couldnt find this anywhere on atunes when i added device, or tried, i couldnt find this in atunes but then i thought HA when i do the gtkpod thing i use ifuse to mount the iphone to mnt/ipod ...it worked i could see my iphone contents (after ages)

i tired to copy a mp4 to my iphone (placed it into a playlist then dragged to the device) a copy dialog apeared and stayed at 0% ..after 10 minutes i canceled it

on the root of the ipod mnt i found 8 megs of the 84meg OUTPUT FILE.mp4 
it would of copied across after a day or two but then only to the root of the mnt which does no one any good



so there you have it, this is what i have tried so far (please please help me) im stuck i have no more ideas... i dont want to go back to xp, i like being able to sshfs my server pc when at home, i like using the console, i like how much faster my netbook works on linux but this is becoming a deal breaker :(

---

### Post by jbrown96 on 2010-05-08
I've never done this before, but I was able to get it up and running in about an hour. Follow my earlier post.

---

### Post by sn1ckers on 2010-05-09
I so completely agree with you [mrgreaper]("http://ubuntu-ky.ubuntuforums.org/member.php?u=126395")

It seems you and I both spent last night trying beat apple.

I have not solution yet but some more insights:

[LIST]
[*]On the aTunes [wiki]("http://www.atunes.org/wiki/index.php?title=FAQ#What.27s_aTunes.3F") it is stated that "Currently aTunes can only **READ** iPod contents until 4th  generation.  It has not been tested with later versions. It **can't**  write songs to iPod". But I haven't tried it myself...
[*]To get Handbrake to work in Ubuntu 10.04 I followed the [this thread]("http://ubuntuforums.org/showthread.php?t=1452967&page=2") at Ubuntuforums. But as is noted this is the easy part!
[/LIST]
So where I am right now:

[LIST]
[*]Amarok finds my iPhone 3gs and any playlist on it. I can also add mp4s to these playlists but I can't make it sync.
[*]Using Rythmbox I can make it sync but nothing ends up on the iPhone...
[*]I can't get gtkpod to read mp4 files.
[/LIST]
How hard can this be?

And, oh yes, I even tried to used iTunes in Wine without success...

Frustration to say the least!!!

---

### Post by sn1ckers on 2010-05-09
Yayyyy:KS

I installed libmp4v2-0 using the Synaptic package manager and then I was able to add mp4s to gtkpod. When I then disconnected the iPhone (in gtkpod) the mp4 was synced to the device. AND THEN I COULD VIEW IT ON THE IPHONE!!!

So happy for so little!

---

### Post by takuhii on 2010-05-20
FFMPEG is a f*cking nightmare isn't it. I spent two hours installing this to get iPod/iPhone presets and ended up coding them myself!?

---

### Post by keithspg on 2010-08-14
> **jbrown96 said:**
> 
Install gtkpod and ifuse.

1) First time only. Make a directory to mount your iphone. ```
mkdir .iphone/
```2) mount the iphone ```
ifuse iphone/
```3) Open gtkpod
4) First time only. configure your iphone. Edit-->Repository/Ipod options. Add new ipod. Choose your model and change the mount point to /home/YOUR_USER_NAME/.iphone. Your iphone will show up on the left, and I just dragged my movies from the file manager over to it. It did not automatically copy them, I had to right click on the iphone and eject it, then it synced and took a couple minutes.
5) Be sure to unmount your phone before you remove it or ifuse can get angry. ```
sudo umount .iphone/
```
Awesome! a succinct recipe to get gtkpod working. I did this in Ubuntu 10.04. I wanted to use this to download podcast feeds until Rhythmbox can be fixed to use all feeds. I am unimpressed. gtkpod is very hack-y. It works, but not nearly as nice as rhythmbox. It does not have nearly as nice of an interface and it is not completely clear as to what to do or how to do it as in Rhythmbox. And, it does not seem to put podcasts as podcasts on the iphone. It transfers the file, but as music and not as a podcast. SO, you cannot run it as double speed nor can you delete it from the iphone interface. 

Am I missing something?

Keith

---

### Post by Bikku555 on 2010-12-16
Hi,

I suppose that you must have an answer by now but just in case you don't...  

I am using Ubuntu 10.10.
I plugged in my Iphone, 2nd Gen & jailbroken.
I then opened up a folder that contained a video that I wanted to upload to my Iphone.
I dragged and dropped the video onto the Iphone icon on the desktop.

bikku555

---

### Post by panderohit on 2011-03-02
The easiest method?

Download Virtualbox from their website > Install Windows > Download iTunes > Initiate USB connections > Sync away!

This is what I do.

FYI: conversion of .avi can be done with avidemux. But I didn't bother with this as long as I can use iTunes. All the best.

---

