---
title: "Ipod"
date: 2010-04-26
forum: New to Ubuntu
---

### Post by jnmjr on 2010-04-26
Hey guys, I've got a dilemma here, my daughter asked me to copy some song from her IPOD to CD, first I want to say I'm not at all familiar with the music thing on the computer so bear with me, the problem I've encountered is that some songs don't play at all, those with .m4p file names, the rest play fine, I'm using Rhythmbox cause it lists the songs by name and that's easier for me, can you music guys out there suggest what I may need to add to Rhythmbox to play these songs or whether I need a different player? the message I get when I try to play the songs is... **The stream is encrypted [B]and decryption is not supported.....**[/B]BTW I have no problem burning CDs I know how to to this quite well but I believe until these files are supported I can't copy them ....THX

---

### Post by sxmaxchine on 2010-04-26
no idea how to play those files in rythmbox but they should play in vlc and vlc has a converter built into it. hope this helps

---

### Post by mcoleman44 on 2010-04-26
You could try using Amarok instead. And Im thinking that if you install the restricted extras from the software center that the files should play.

---

### Post by jnmjr on 2010-04-26
Thanks for the suggestions, VLC is not very intuitive for me and I have found it difficult, Amarok is similar to RB the only problem is that I get no sound and can't figure out why...also the restricted add ons you suggested I don't know where to get them from, please advice, I would like to get Amarok going if possible....THX

---

### Post by mcoleman44 on 2010-04-26
This should help you out 
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by spydeyrch on 2010-04-26
I don't know if things have changed but, typically when one buys music from iTunes in the .mp4 format, the music has DRM in it. Therefore it won't play on anything else besides iTunes and the associated iPod. There are a few options when buying the songs from iTunes that allow you to buy the un-DRM'ed versions, those would work on any player that supports .mp4. But usually they cost a little mroe than the normal amount.

I have a few suggestions on how you could resolve the issue but I have a few questions first. Did your daughter get the songs via iTunes on a Windows or Mac machine?

Let me know. I have a few simple solutions and some not so simple yet very creative solutions. Both have worked for me in the past. :-)

-Spydey:guitar:

---

### Post by spydeyrch on 2010-04-26
Sorry, I meant in my previous post to say .m4p, as you had written in your original post. Sorry to confuse you. :-)

-Spydey:guitar:

---

### Post by jnmjr on 2010-04-26
> **spydeyrch said:**
> I don't know if things have changed but, typically when one buys music from iTunes in the .mp4 format, the music has DRM in it. Therefore it won't play on anything else besides iTunes and the associated iPod. There are a few options when buying the songs from iTunes that allow you to buy the un-DRM'ed versions, those would work on any player that supports .mp4. But usually they cost a little mroe than the normal amount.

I have a few suggestions on how you could resolve the issue but I have a few questions first. Did your daughter get the songs via iTunes on a Windows or Mac machine?

Let me know. I have a few simple solutions and some not so simple yet very creative solutions. Both have worked for me in the past. :-)

-Spydey:guitar:

As far as I know at this moment the answer to both parts of your questions is YES.... May i ask you as well... Is it possible to burn these files to CD as is without converting them and will they play on CD? THX
More specifically Windows machine.

---

### Post by jnmjr on 2010-04-26
> **mcoleman44 said:**
> This should help you out 
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

THX...I got that part but still no sound out of Amarok....any suggestions on that front? THX

---

### Post by spydeyrch on 2010-04-26
Ok, so it is possible to burn them to CD but it will have to be don't from the machine where her iTunes account is located. What you do is from within iTunes, make a play list of the songs that you want on CD. Insert a blank cd into your CD burner drive. Then either right click on the new playlist and select, burn to CD or select the play list so that it is shows the songs in the main viewer then down towards the bottom, there should be a "burn this list" button. It may not be called exactly the same, but very close and it will be quite obvious what it is. Make sure that the number of songs in the play list doesn't exceed the available space on the cd. Typically it is between 17 & 21 songs per CD. iTunes will convert the songs for you and burn them to the cd. Then you can rip the cd in ubuntu and add the songs as either .wav, .mp3, .ogg, or any other format that you like. :-)

The only issue that I find with doing it this way is that it uses a cd when in reality, I personally am not going to use it anywhere. So it is kind of a waste to burn a cd, just to convert the songs. That said, there are two different ways that you can get around that, legally. It doesn't waste a CD and it gives you the same out come. One of them is pretty simple and straight forward, but requires that you do it in windows, while the other one lets you do it from with in Ubuntu (in a round about fashion). I personally use the second option because it allows em to stay in ubuntu. Either option will convert the songs for your from .m4p to, for example, .mp3 on the fly and not need a cd to do it! Let me know if you would like to try one of them. If not, at the very least you know how to burn the cd via itunes.

-Spydey:guitar:

---

### Post by mcoleman44 on 2010-04-26
> THX...I got that part but still no sound out of Amarok....any suggestions on that front? THX   *	    
[http://ubuntuforums.org/showthread.php?t=215301](http://ubuntuforums.org/showthread.php?t=215301)

---

### Post by JK3mp on 2010-04-26
Do you not get ANY sound out of Amarok even playing MP3's? When amarok first boot i believe it asks u if u want it to check for the proper codecs (Mp3, m4p etc). If you clicked "YES" it download and installs them and all u need is a restart, if u click no, it is difficult to get it too ask again, but I'm sure the restricteds' FOR amarok will help.

---

### Post by jnmjr on 2010-04-26
> **spydeyrch said:**
> Ok, so it is possible to burn them to CD but it will have to be don't from the machine where her iTunes account is located. What you do is from within iTunes, make a play list of the songs that you want on CD. Insert a blank cd into your CD burner drive. Then either right click on the new playlist and select, burn to CD or select the play list so that it is shows the songs in the main viewer then down towards the bottom, there should be a "burn this list" button. It may not be called exactly the same, but very close and it will be quite obvious what it is. Make sure that the number of songs in the play list doesn't exceed the available space on the cd. Typically it is between 17 & 21 songs per CD. iTunes will convert the songs for you and burn them to the cd. Then you can rip the cd in ubuntu and add the songs as either .wav, .mp3, .ogg, or any other format that you like. :-)

The only issue that I find with doing it this way is that it uses a cd when in reality, I personally am not going to use it anywhere. So it is kind of a waste to burn a cd, just to convert the songs. That said, there are two different ways that you can get around that, legally. It doesn't waste a CD and it gives you the same out come. One of them is pretty simple and straight forward, but requires that you do it in windows, while the other one lets you do it from with in Ubuntu (in a round about fashion). I personally use the second option because it allows em to stay in ubuntu. Either option will convert the songs for your from .m4p to, for example, .mp3 on the fly and not need a cd to do it! Let me know if you would like to try one of them. If not, at the very least you know how to burn the cd via itunes.

-Spydey:guitar:

Yes, certainly your Ubuntu workaround would be my first option, please feel free to elaborate... THX

---

### Post by jnmjr on 2010-04-26
Thanks with the help on Amarok, I got it to play everything except the M4P (MP4) files, I'm going to start a new thread to address this issue specifically....THX

---

### Post by spydeyrch on 2010-04-26
> **JK3mp said:**
>  When amarok first boot i believe it asks u if u want it to check for the proper codecs (Mp3, m4p etc). If you clicked "YES" it download and installs them and all u need is a restart, if u click no, it is difficult to get it too ask again, but I'm sure the restricteds' FOR amarok will help.


So, are you saying that amarok with the restricteds for amarok can play DRM'ed .m4p 's? So if I buy a DRM'ed song via iTunes, it downloads it in the .m4p format. From what I understood about .m4p, it is encoded with DRM which requires that the user be logged in to the iTunes account associated with that music file in order to play that file. And no other player can play that file due to the DRM. Correct me if I am wrong, as it would be very convenient to be able to play my songs in amarok with out the need to capture the audio stream from iTunes and convert on the fly to another format JUST to play it in ubuntu/linux/pmp (other than iPod). That would be awesome!!

:KS:):P:lolflag:

-Spydey:guitar:

---

### Post by spydeyrch on 2010-04-26
> **jnmjr said:**
> Thanks with the help on Amarok, I got it to play everything except the M4P (MP4) files, I'm going to start a new thread to address this issue specifically....THX


Have you started that thread yet? What is the link to it, please? I am interested in seeing where it leads you as it could be quite beneficial.

-Spydey:guitar:

---

### Post by oleink on 2010-04-26
Mp4a is not supported by amarok.  Or rhtyhmbox and that is your problem

---

### Post by oleink on 2010-04-26
I would suggest banshee but I dont think it is supported in banshee either.  It should be supported in songbird

---

### Post by oleink on 2010-04-26
You could always convert them or since banshee uses gstreamer you could install banshee and then install the appropriate gstreamer plugin probabvly in synaptic package manager

---

### Post by spydeyrch on 2010-04-26
> **jnmjr said:**
> Yes, certainly your Ubuntu workaround would be my first option, please feel free to elaborate... THX

Ok, so I am going to try and make this as easy as is possible. I will actually tell you how to do it the first way and then the second way. The reason being that the second way builds off of the first one so it might make things a little easier. Also, just as a warning upfront, the second way can be somewhat time consuming to set everything up and get it running but once you do, then the rest is pretty much easy sailing from there on out.

Before I start completely, I need to know what the specs of the machine that you will be doing this on are: CPU, RAM, HDD, ODD, OSs, etc.

Example:

My machine:

AMD Phenom 9950 2.6GHz o'cd 3.2GHz
4 GB DDR2 1066
1TB, 3 x 500GB
DVD/CD Burner
Windows 7 Pro x64
Ubuntu x64
Mint 8 x64

This will give me an idea of if the second option will even work on your machine or not. :-)

-Spydey:guitar:

---

### Post by jnmjr on 2010-04-26
Hey Spidy I'm still waiting for the workaround you promised??????????


Sorry didn't see your last post

---

### Post by spydeyrch on 2010-04-26
> **oleink said:**
> Mp4a is not supported by amarok.  Or rhtyhmbox and that is your problem

That is the issue. That .m4p is a proprietary format owned by Apple and unless the DRM is broken, there is no other way to get around it except by either converting a play list, via burning it to a CD, or by using a virtual cd burner.

Here is an exerpt taken from sharedrmusic.com:

 			**What is M4P files?**
 			File in .M4P format are "Protected AAC File". Songs purchased via  iTunes are in the protected m4p format. 
 			AAC is the audio layer from the follow-on format to MP3 (see [.M4A  extension]("http://www.sharedrmusic.com/music-file/m4a-music-file.htm")). The .M4P extension  			is AAC purchased from Apple's Music Store (iTune) and is protected by  a Digital Rights Management scheme.  			
 			 			
 			 			**How to play M4P music files?**




 			 			  			If they're DRM protected, it probably goes to reason that the only  DRM M4P music player is... iTunes.
 			 				If you've got an iPod, you go and buy music but then your machines  dies, or have many many computers and devices you listen to  				music on, or maybe sometimes you use an operating system not  supported by iTunes, how can you listen to your purchased music?  				Well, usually you can't- why? Because the songs you purchased are  DRM protected, that means you can only listen to them on  				specific computers and devices. For most folks the limits of a few  computers or devices are fine, but for the gadget geek- nope,  				we have too many computers and devices. It would be like buying a  DVD but only being able to watch it in some rooms, or only some TVs. 



Hopefully that sheds a little light on the situation.


-Spydey:guitar:

---

### Post by spydeyrch on 2010-04-26
> **jnmjr said:**
> Hey Spidy I'm still waiting for the workaround you promised??????????


Sorry didn't see your last post


That is ok. Don't sweat it.  :lolflag:

I am at work right now so I might lag a little in between posts. Sorry about that. :(

Let me know what your machine specs are and we will see if it will even work for you.  :popcorn:

-Spydey:guitar:

---

### Post by jnmjr on 2010-04-26
> **spydeyrch said:**
> Ok, so I am going to try and make this as easy as is possible. I will actually tell you how to do it the first way and then the second way. The reason being that the second way builds off of the first one so it might make things a little easier. Also, just as a warning upfront, the second way can be somewhat time consuming to set everything up and get it running but once you do, then the rest is pretty much easy sailing from there on out.

Before I start completely, I need to know what the specs of the machine that you will be doing this on are: CPU, RAM, HDD, ODD, OSs, etc.

Example:

My machine:

AMD Phenom 9950 2.6GHz o'cd 3.2GHz
4 GB DDR2 1066
1TB, 3 x 500GB
DVD/CD Burner
Windows 7 Pro x64
Ubuntu x64
Mint 8 x64

This will give me an idea of if the second option will even work on your machine or not. :-)

-Spydey:guitar:

My Machine

AMD XP2400+
2GB DDR 2100
2 500gb HD's
Ubuntu x32
WinXP Pro
DVD-CD Burner

---

### Post by oleink on 2010-04-26
I hate how everything about apple is proprietary.  It's garbage.  I'd say just convert to mp3

---

### Post by oleink on 2010-04-26
I'm actually interested on how to crack the coding on the files too.  I have a sansa now and lost the music I got with itunes because it wont let you convert them because they are apple codecs

---

### Post by spydeyrch on 2010-04-26
Ok, so I am typing up the walk-through right now in word then will copy it over. Give me a little time to get it done. Not all day obviously but being at work can sometimes hinder the progress of the document. I will get it up asap within the next hour or so. :-)

-Spydey:guitar:

---

### Post by jnmjr on 2010-04-26
Spydey, on the same note as the last poster, I can't sync my daughter's IPOD to my WinXP without loosing the files so "cracking the code" is the only alternative, at this point I only prefer to use Linux so your workaround would be the way to go if my machine is up to the task...THX

---

### Post by spydeyrch on 2010-04-26
> **jnmjr said:**
> Spydey, on the same note as the last poster, I can't sync my daughter's IPOD to my WinXP without loosing the files so "cracking the code" is the only alternative, at this point I only prefer to use Linux so your workaround would be the way to go if my machine is up to the task...THX


Yeah, unfortunately, your iTunes account is different than your daughters, at least I am assuming so by what you have described. itunes says that it wants to format your daughters iPod to be able to sync with your itunes account, right? It is a HUGE pain!!!

FYI, I am currently working on typing up the work around for your first issue. Like I said before, it has worked for me and is an acceptable way for me to convert my songs. But that is me so I hope it works for you. It will be your choice if you want to do it or not.Just letting you know. :-)

-Spydey:guitar:

---

### Post by jnmjr on 2010-04-26
> **spydeyrch said:**
> Yeah, unfortunately, your iTunes account is different than your daughters, at least I am assuming so by what you have described. itunes says that it wants to format your daughters iPod to be able to sync with your itunes account, right? It is a HUGE pain!!!

FYI, I am currently working on typing up the work around for your first issue. Like I said before, it has worked for me and is an acceptable way for me to convert my songs. But that is me so I hope it works for you. It will be your choice if you want to do it or not.Just letting you know. :-)

-Spydey:guitar:

I hear you, the only reason I got involved in this Itunes-IPOD thing is because of my daughter, I'm just an old fashioned CD guy, I buy one if it interests me or else I listen to my favorite satellite stations, the thing now is I'm intrigued by your solution, a learning experience for me, and this way I can help her out whenever she needs me.

---

### Post by spydeyrch on 2010-04-26
Ok guys, I have finished part 1. Here it is. If you have questions, let me know please.

   How to convert .m4p to other formats


  So there are two parts to this: 



  1.)   doing this in windows natively and 
  2.)   doing it in Ubuntu


  I am going to go through part one first because part two builds upon part one and they just flow together well. Do be advised that part two, converting in ubuntu, does take some time consuming setup (no terminal codes needed) to get it ready but once it is, it is a pretty cool setup!


  Intro:


  Apples .m4p format is proprietary. Meaning it is their property and it is closed ended software. Something we FOSS people don’t like very much. It is laced with DRM, Digital Rights Management, software that makes it so that only iTunes and iPods/iPhones can open and play them. Same thing goes for their movie downloads. (There is away to get by that one too but that is for a later time.)


  If any of you have used itunes, you know there is a physical way to get around the DRM. You create a play list in iTunes of your 17 – 21 songs that you wanted converted to, for example, .mp3. Then you burn the playlist to a physical CD. iTunes converts the songs to CD audio format and then burns it for you. You then have to take the newly burnt CD with your songs on it and rip it back to your computer and convert it to .mp3, or what ever other format you want.


  WHAT A PAIN IN THE NECK!!! Plus if you are like me, it is a huge waste of a perfectly good CD that could have been used to make a live cd for a friend and convince him/her of the total awesomeness that is Linux (Ubuntu)!!
  So how to we get around this issue of converting, burning, ripping, and converting (again!) to get the desired format and not waste a CD?


  Well, you could use a CD-RW (re-writable cd) but those are hard to come by these days. So how do we get rid of the CD part and go completely virtual? Well, that is the key, going “virtual”. [FONT=Wingdings]:P[/FONT]
[FONT=Wingdings]
[/FONT]
  **_Part 1:_**
****
  If you have ever had a .iso file on your computer, you can load it via a virtual cd/dvd drive. There is no physical drive in your computer and you don’t insert a disk to read the .iso file. You just point the virtual drive to the location of the .iso and it loads it as if it were a real physical disk in your ODD. Your OS won’t know the difference! [FONT=Wingdings]:lolflag:[/FONT]
  iTunes can be tricked in to the same thing. If you google “virtual cd burner” you will get a large list of different virtual burners. I personally have note burner and it works great! There are other options out there too incase that one doesn’t work for you. Also, setup the options in the new software before you do anything else. Things such as file locations, converted format, etc. Also, I am writing these instructions as if you are using note burner because that is what I am familiar with. 



  FYI, I haven’t used note burner for about 8 months now so I might get some of the names of the options wrong and maybe some of the locations, but it is pretty much straight forward and easy to use. A 12 year old could figure it out. But, I apologize in advance if I get something wrong.


  Basically the way it works is that you do everything like you would before: create a playlist of ALL the songs that you want converted. The reason I say ALL is because with a physical CD, there is a space limit, with the virtual CD, there is none, so you can “burn” all of them in one single go! YAY!!!


  Anyway, back to the topic at hand. Create a playlist with all the songs you want converted. In the iTunes options, make sure that you have the virtual cd burner selected as your primary media burner. This triggers the software to receive the incoming audio stream from itunes and convert it to .mp3 on the fly.


  Then, select your recently created playlist and select burn to disc. The virtual cd burner should intercept the audio stream from itunes and convert it to the format that you selected in your options menu. Depending on the number of files, size of them, format to convert to, and the specs of your machine, it could take a while. I did it once where I did all my songs at once, every single last one. And it took about 3 hours. So for me, that is a good time frame, for others it might not be.


  Once it has converted all the songs, you can go to your output folder and do what you want with them. You can also boot into ubuntu and add them to your preferred music player’s media library.


  Also, there is another way to do the above. There is a program called Tunebite (for windows and mac) that does it a little differently. It doesn’t create a virtual burner but instead intercepts the audio stream directly from your sound card and converts on the fly. Also, you don’t burn the playlist, you just play it like normal. (If I remember correctly.) The cool thing about Tunebite is that it can convert iTunes video/movies too!!


  Both of these products have a trial period and if they work, I encourage you to purchase them. The trial periods will allow you to see if they will work on your system and to what degree of quality. The reason I give two programs is because Noteburner didn’t work on my Windows 7 x64 install. Where as tunebite did work in windows 7.


  Now, for us open software types of guys, this kind of bytes (pun intended) because it means that we have to use windows and not our open OS. But, that is where Part 2 comes into play. It allows us to get around this issue to some degree but not completely. You will see. Keep reading. [FONT=Wingdings]:KS[/FONT]

[FONT=Wingdings][/FONT]
  -Spydey:guitar:


  That is the end of part 1.

---

### Post by spydeyrch on 2010-04-26
> **jnmjr said:**
> My Machine

AMD XP2400+
2GB DDR 2100
2 500gb HD's
Ubuntu x32
WinXP Pro
DVD-CD Burner

@jnmir

After looking over your specs and doing some quick research, I have two outcomes. 

1.) You should be able to run the first way, part 1, on your winxp os. Probably the best option.

2.) If you opt to go the second way, doing it in ubuntu, it is going to get kind of sketchy because your hardware doesn't support hardware virtualization. Don't get it confused with a virtual cd burner, two different concepts, both dealing with virtualization.

Just because it doesn't support hardware virtualization doesn't mean that option number 2 won't work. We can still go that route but because there is no hardware virtualization support, it will be anywhere from a little slower than if it had virtualization support to a lot slower. but it is up to you if you want to try it. If it works for you, great then it works. If not, then at least you can mark that one off of your list, right.

I have hardware virtualization support via my CPU so it works fine for me. Your out come might be somewhat different.

-Spydey:guitar:

---

### Post by spydeyrch on 2010-04-26
Currently working on part two. Should be done soon.

-Spydey:lolflag:

---

### Post by jnmjr on 2010-04-26
> **spydeyrch said:**
> @jnmir

After looking over your specs and doing some quick research, I have two outcomes. 

1.) You should be able to run the first way, part 1, on your winxp os. Probably the best option.

2.) If you opt to go the second way, doing it in ubuntu, it is going to get kind of sketchy because your hardware doesn't support hardware virtualization. Don't get it confused with a virtual cd burner, two different concepts, both dealing with virtualization.

Just because it doesn't support hardware virtualization doesn't mean that option number 2 won't work. We can still go that route but because there is no hardware virtualization support, it will be anywhere from a little slower than if it had virtualization support to a lot slower. but it is up to you if you want to try it. If it works for you, great then it works. If not, then at least you can mark that one off of your list, right.

I have hardware virtualization support via my CPU so it works fine for me. Your out come might be somewhat different.

-Spydey:guitar:

Correct me if I'm wrong.... ITUNES doesn't play my daughter's IPOD on my WinXP because it's not synced, how would the virtual burner burner be able to create a playlist? I'm just confused!!

---

### Post by spydeyrch on 2010-04-26
> **jnmjr said:**
> Correct me if I'm wrong.... ITUNES doesn't play my daughter's IPOD on my WinXP because it's not synced, how would the virtual burner burner be able to create a playlist? I'm just confused!!

Does your daughter have a separate machine that she access her itunes on?

-spydey :lolflag:

---

### Post by spydeyrch on 2010-04-26
Hey guys, as I was writing up part two, I found this post: [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

In the audio/video conversion part, it talks about possibly converting AAC files (itunes files) via some linux native programs. I haven't tried them personally but they may work. I don't know. Just a possible lead.

I am almost don't with part 2.

-Spydey :popcorn:

---

### Post by spydeyrch on 2010-04-26
Ok guys, I have finished part 2. It is really unpolished so forgive me  if there are mistakes or it is unclear. Take a look and see if it works  for you.

P.S. There are a number of screen shots so hopefully they showup ok. :confused: If not, I  will see what I can do about that.

edit: the pictures didn't upload correctly. I am working on it. Sorry about the delay.

-Spydey

---

### Post by spydeyrch on 2010-04-26
Ok, I have edited it to not show pictures. Here it is:

---------------------------

   How to convert .m4p to other formats
  **_Intro:_**
  Ok, so in the last part we learned how to get around iTunes .m4p format in a legal way. We didn’t break the DRM from the file. We “burnt” a virtual cd and, ripped it, and converted it al in one go without the need of physical media.
  But what if we don’t want to stick to windows as our main OS? What if we have an open, awe inspiring, purely magnificent open source os that we want to use? (FYI, I still use windows for a mainly gaming and a few other things but I primarily use linux for all my main things.) Is there a way to do the same thing in, for example, Ubuntu?
  To be completely honest with you: No there isn’t. I am sorry, the truth hurts. The reason being is that we need to keep this legal, 100%. The ubuntu community, myself included, don’t support illegal operations and thwarting (cool word huh!?) of DRM. So no, we can not strip the DRM out of a file and there is no easy way to do it.
  The DRM can only be read, legally (at least to my knowledge), by itunes and associated devices/programs. There is no iTunes for linux and/or ubuntu. So what are we to do to get this to work!!!???
  Well, do you remember part 1? That was the building block for part 2.
  “Huh? What am you talking about?”
  Well, here we go:
  **_Part 2:_**
  Ok, so I said that there was no 100% way to do what we did in windows, but in ubuntu without windows. And I wasn’t lying. There isn’t, at least not to my knowledge.
  But, we have kind of a tricky, geeky work around to do it. And the cool thing, it works!!! The un-cool thing, we still have to depend on windows to some degree to get it done. But the OTHER cool thing is that we get to learn something new (maybe for you, maybe not) that will serve us for years to come, not just for the music issues that we are being plagued with by Apple but for many other things too!
  Ok, so in part one, we talked about virtualizing a cd burner, right? Well lets take it to the next level. From within Ubuntu, lets virtualize a complete OS!!!!! In this case it has to be windows, sorry. [FONT=Wingdings]L[/FONT]
  NOTE: I mentioned in part one that this method does take quite some time to get up and running. I am just letting you know again. [FONT=Wingdings]J[/FONT]
  Now, to virtualize windows an accomplish our goal, we will need a few things: Our windows install disk, OS virtualization software, virtual cd burner software, and anything else that I mention later on that I can’t think of right now.
  First, off, we need to install our OS virtualization software. Don’t get this confused with the virtual cd burner software. Two different things completely!
  For the OS virtualization software, I prefer virtualbox. Therefore, this guide will be written assuming that you use virtual box. One of the reasons why I like to use virtual box, it is open source (ding ding ding ding!! We have a winner!!), and if you don’t have virtualization support via your CPU, you can still run a virtualized OS, just that it may respond a little slower than if you had the VM support.
  Ok, first things first, go to the virtualbox.org website, click on downloads on the left side, then virtual box for linux hosts (at the time fo this writing, the version was 3.1.6), then select your linux distro and version of that distro from the list. Then download via the appropriate link either the x32 (i386) or the x64 (AMD64) installer. It should be a .deb package for ubuntu. Once downloaded, go to the folder where it downloaded and install it. Because it is a .deb package, it will run automatically. You should know have virtual box installed on your ubuntu machine.
  Now we need to configure it before we install the OS.
  Below you should find a how-to that I had already put together. Hopefully it is clear and understandable. I originally made it for Windows Vista but the same steps can be applied for basically any OS, changes being made where needed. Also, some of the steps may not be exactly the same for the linux version as for the windows version, but they are pretty close. I am at work right now so I can’t really get into my system at home and check it. sorry. [FONT=Wingdings]L[/FONT]
  [FONT=&quot]Hey, this is a quick guide to make a VM for windows vista business using Virtual Box.[/FONT]
  [FONT=&quot]Minimum hardware requirements:[/FONT]
  [FONT=&quot]- A CPU that supports virtualization. If you don't know if yours does, Google it. All AMD Athlon X2 64 and higher/newer CPUs do support virtualization. Only some of the newer Intel CPUs and older Core 2 CPUs support virtualization. Even if your CPU doesn't have virtualization capabilities, Virtual Box has some special coding to still do virtualization, but at a HEAVY cost to your system. It will go slow![/FONT]
  [FONT=&quot]- Preferably 2GB of RAM, you could technically do with just 1GB, but trust me, 2GB is better. If you are patient, you can do it with 1GB.[/FONT]
  [FONT=&quot]-At least 50GB of free HDD (Hard Disk Drive) space, preferably 60 - 100GB.[/FONT]
  [FONT=&quot]- Familiarity with your system's BIOS. You need to enable virtualization support in your BIOS. Some Bios automatically detect it and enable/disable it if needs be. While others need you to manually enable/disable it in the BIOS.[/FONT]
  [FONT=&quot]- Patience!!!! Lots and lots of patience!!![/FONT]
  [FONT=&quot]Here we go:[/FONT]
  [FONT=&quot]-Make sure you BIOS's virtualization options are enabled. Every BIOS is different so I really can't help you too much with setting yours up. You could go to the manufacturer's website and check their documentation to see if your BIOS has it and where to find it in the BIOS.[/FONT]
  [FONT=&quot]-After installing VB, start the program.[/FONT]
  [FONT=&quot]- When VB (Virtual Box) comes up, yours should look similar to the screenshot below.[/FONT]
  [FONT=&quot]- You need to click on the New button.[/FONT]
  [FONT=&quot]- Click on Next.[/FONT]
  [FONT=&quot]- Give your VM (virtual machine) a name, like Vista Business. Then make sure that you select the Operating System as Windows and the Version as Windows Vista. If you have a 64 bits (x64) version of Vista, elect that otherwise, if you just select Windows Vista, it assumes it is a 32 bit (x32) of Vista. Then click next.[/FONT]
  [FONT=&quot]*Side step out of guide*[/FONT]
  [FONT=&quot]For the ubuntu forum readers, you will want to select the appropriate linux distro, version, and either x32 or x64.[/FONT]
  [FONT=&quot]*Side step in to the guide*[/FONT]
  [FONT=&quot]- Now you need to share your systems RAM with the VM. You should never give it half or more than half of the total system ram in your machine. In VB, it is shown as MB (megabytes). So if you have 1GB (Gigabyte) of ram, that is actually 1,024 MB. In my system I have a total of 4GB, so that is 4 x 1024 = 4,096 MB. The green goes to half your RAM. I usually go just a little less than half. So in the screen shot, you see that I have set 2040 as my VM ram. 2048 is the half way point. If you have only 1GB of ram, half would be 512MB, which is JUST barely enough to run Vista. So, I would recommend getting more ram. Then hit next. [/FONT]
  [FONT=&quot]- Next you need to create a virtual HDD for your VM. Check "Boot Hard Disk (primary Master)", click "create new hard disk", then click next.[/FONT]
  [FONT=&quot]- Click next.[/FONT]
  [FONT=&quot]- Mark "Dynamically expanding storage", then next.[/FONT]
  [FONT=&quot]- Make sure that the Location name is the same as your VM name that you gave it in the beginning. It should automatically pre-fill it already. Select the size of your VM HDD (virtual machine hard disk drive). Make it at least 50GB. The cool thing here is that because we previously selected dynamically expanding hard disk, it won't actually take up 50GB on your real physical HDD. It will expand as stuff gets added to your VM HDD and it has a max capacity of 50GB. This means that it will never take up more that 50GB on your real HDD. Pretty cool, huh. :-) Then click next.[/FONT]
  [FONT=&quot]- click finish.[/FONT]
  [FONT=&quot]- click finish.[/FONT]
  [FONT=&quot]- You should now see your new VM, named Vista Business, in the list of available VMs in Virtual Box. But it isn't installed just yet. That is where the fun begins![/FONT]
  [FONT=&quot]- Click once on your new vista business vm, then on settings. We need to optimize the vm to accept installation of windows vista.[/FONT]
  [FONT=&quot]- General [/FONT][FONT=Wingdings]à[/FONT][FONT=&quot] Advanced [/FONT][FONT=Wingdings]à[/FONT][FONT=&quot] Shared Clipboard: Bidirectional; Mini toolbar: show in fullscreen/seamless-CHECKED, Show at top of screen-CHECKED.[/FONT]
  [FONT=&quot]- System [/FONT][FONT=Wingdings]à[/FONT][FONT=&quot] Motherboard [/FONT][FONT=Wingdings]à[/FONT][FONT=&quot] Boot order: CD/DVD-CHECKED, HDD-CHECKED; Extended Features: Enable IO APIC-CHECKED[/FONT]
  [FONT=&quot]-System [/FONT][FONT=Wingdings]à[/FONT][FONT=&quot] Processor [/FONT][FONT=Wingdings]à[/FONT][FONT=&quot] Extended Features: Enable PAE/NX-CHECKED[/FONT]
  [FONT=&quot]*As a rule of thumb, give your VM half the total number of cores that your CPU has and enable PAE/NX. My CPU has 4 cores, therefore I have given it 2 cores. Yours may be different.*[/FONT]
  [FONT=&quot]-System [/FONT][FONT=Wingdings]à[/FONT][FONT=&quot] Acceleration [/FONT][FONT=Wingdings]à[/FONT][FONT=&quot] Hardware Virtualization: Enable VT-x/AMD-V – CHECKED, Enable Nested Pagin-CHECKED[/FONT]
  [FONT=&quot]*These two options will either be available or shaded out/grey if your hardware can't use them. If you can use them, check the box to enable the option.*[/FONT]
  [FONT=&quot]-Display [/FONT][FONT=Wingdings]à[/FONT][FONT=&quot] Video [/FONT][FONT=Wingdings]à[/FONT][FONT=&quot] Extended Features: Enable 3D Acceleration-CHECKED, Enable 2D Acceleration-CHECKED[/FONT]
  [FONT=&quot]*Depending on your GPU's (Graphic Processing Unit (Graphics Card)) VRAM, you may need to adjust the amount of video memory your VM has. Also, if you have a higher end GPU and can give it more VRAM, then enable both 3D and 2D acceleration.*[/FONT]
  [FONT=&quot]-Storage [/FONT][FONT=Wingdings]à[/FONT][FONT=&quot] ODD Host [/FONT][FONT=Wingdings]à[/FONT][FONT=&quot] Passthrough-CHECKED[/FONT]
  [FONT=&quot]*When you go to storage, click on the image that looks like the CD, click on the drop-down menu next to CD/DVD Device and select your actual physical CD/DVD optical drive, then mark the Passthrough box. This will allow you to install your vista business from a physical CD/DVD in your optical drive.*[/FONT]
  [FONT=&quot]*Leave Audio, Network, and Serial Ports alone.*[/FONT]
  [FONT=&quot]-USB [/FONT][FONT=Wingdings]à[/FONT][FONT=&quot] Enable USB Controller-CHECKED, Enable USB 2.0 (EHCI) Controller-CHECKED[/FONT]
  [FONT=&quot]*Make sure that both check boxes are marked/checked.*[/FONT]
  [FONT=&quot]*Don't worry about Shared Folders at this Point.*[/FONT]
  [FONT=&quot]*Click OK*[/FONT]
  [FONT=&quot]Now we are back to installing your Vista Business in a VM.[/FONT]
  [FONT=&quot]- Next, from the main VM menu window, select your Vista Business VM, then click start.[/FONT]
  [FONT=&quot]*Side Step out of guide*[/FONT]
  [FONT=&quot]For the ubuntu forum readers, if you don’t have an .iso of your install disc, you will need to hit, I believe, F2 to get to the virtual machine’s bios screen. In there you should be able to set the ODD to boot first.[/FONT]
  [FONT=&quot]*side step back into the guide*[/FONT]
  [FONT=&quot] *During the next parts, there will be little message windows that will pop up. I suggest you read them as I won't be going over them in any details/steps. I have mine checked "don't show this message again". I will give you one hit, during the first little bit, if you need to get from your host OS to the VM guset OS, click on the guest os. If you need to get from your guest os to your host os, press the right control (ctrl) button.[/FONT]
  [FONT=&quot]- Once you hit start, you should see a few screen changes in the VM window, and then familiar windows install screens, all within the VM window. Nice huh. :-)[/FONT]
  [FONT=&quot]- Proceed to install windows as your **_normally_** would.[/FONT]
  [FONT=&quot]- Once it is installed and**_ before_** you update, you need to install the guest os additions.[/FONT]
  [FONT=&quot]- Your installed VM should look something like this (I am running Windows 7 as my host and Vista Business as my guest. Vista business is the window, that is how VMs originally start out, as windows, but we are going to change that.):[/FONT]
  [FONT=&quot]- From within the guest os, go to the VM menu, Devices, CD/DVD Devices, VBoxGuestAdditions.iso, click it. Give your VM a moment or so. If you don't see the auto run pop up, go to computer, and then in your optical drive for your vm, you should see the VBoxGuestAdditions in there. Double click it to run it.[/FONT]
  [FONT=&quot]- It is a pretty straight forward installation, just make sure that you check the D3D box when you see it and then proceed with the installation. The additions allows you to move from your host to guest without having to hit the right-ctrl button and it allows you to copy things form one to the other that are located on the clipboard, i.e. images that you right-clicked > copied, text that you copied, etc.[/FONT]
  [FONT=&quot]- That should do it. Once the machine reboots, install windows updates, programs, etc.[/FONT]
  [FONT=&quot]If you have questions, feel free to ask or read the manual that virtual box has online. It is easy to understand and is full of great info![/FONT]
  [FONT=&quot]END GUIDE[/FONT]
  [FONT=&quot]Ok, so that gives you a basic idea of how to get windows installed into ubuntu as a VM (virtual machine). This then allows us to install that virtual cd burner within windows and do what we did in part 1. But the cool thing is that we don’t have to restart the machine and boot into ubuntu to get to our freshly baked .mp3 files. Just through in a usb flash drive, open it up via your VM, transfer your files to it, safely eject/remove the usb flash drive. Then reconnect it to your machine but open it up via ubuntu now. Viola! You can do everything in one OS now. Even though we are still bound to windows in a round about way. [/FONT][FONT=Wingdings]L[/FONT][FONT=&quot][/FONT]
  [FONT=&quot]Anyway, this is how I do it and even though it is cumbersome to some degree, I am able to achieve what I wanted. Hopefully it works for you too.[/FONT]
    [FONT=&quot] [/FONT]
  
  [FONT=&quot]Another way you could do it is just install wine. Then through wine, install itunes and the virtual cd burner. I haven’t tried this one personally but it might work.[/FONT]

---

### Post by spydeyrch on 2010-04-26
I am going home for the night. I might check up during the rest of the evening. If not, I will be back tomorrow evening.

-Spydey :KS

---

### Post by jnmjr on 2010-04-26
> **spydeyrch said:**
> Does your daughter have a separate machine that she access her itunes on?

-spydey :lolflag:

Yes but in her house, so I guess that means I have to do it through Linux :P

---

### Post by jnmjr on 2010-04-26
I'm out of business Spydey, my Bios has no support for VM, motherboard too old, I want to give you a big Thanks for all your effort, atleast the Windows thing should work on my daughter's machine I made a copy and will give it to her.... no choice for me other than burn CD and go from there, still greatly appreciated....:popcorn:

---

### Post by spydeyrch on 2010-04-26
> **jnmjr said:**
> I'm out of business Spydey, my Bios has no support for VM, motherboard too old, I want to give you a big Thanks for all your effort, atleast the Windows thing should work on my daughter's machine I made a copy and will give it to her.... no choice for me other than burn CD and go from there, still greatly appreciated....:popcorn:

Sorry to hear that. :( You know, I would still try it if I were you. Even though your BIOS doesn't have any VM options, sometimes virtual box will still run .... just a little slower.

Another thing you might try is this: Install WINE on your ubuntu computer. Then under wine install iTunes and the virtual cd burner. I might work.

One other try you could go for is from one of my earlier posts in this thread, #36. there is mention of a linux native program that can read .m4p. I haven't tried it yet but it might be worth it.

I am sorry that it didn't work out. :( And you are welcome. At least it might help someone else in the future. :)

One last idea that just occurred to me. Make an account on your xp machine for your daughter. Install itunes and set it up with your daughters itunes account info (username and password). Try to sync her ipod with her itunes account in her xp account on your computer. See if it wants to format her ipod. It may just want to sync it and download the content on the ipod to the mahcine, leaving the content still intact/present on the ipod. Just an idea. If it works, then you have a way to do it.

Let me know how it turns out. :)

-Spydey:lolflag:

---

### Post by spydeyrch on 2010-04-27
@jnmjr

So after doing some research, this is what I found on the apple website. Hopefully it helps. I will still do some more research, for personal reasons too, and see if I can figure anything out. I think that the best solution for your situation is to be able to pull your daughters songs onto your computer and use that virtual cd burner I mentioned. I will keep looking into it.

 	 		            **Summary**

 You can manage your iPod with different computers as long as the  computers are running the same operating system (Mac OS X or Windows)  and you have set the iPod to "Manually manage music." If you're not  using iTunes 7 or later, click [here]("http://docs.info.apple.com/article.html?artnum=304271").
 
    **Products Affected**

 iPod nano, iPod shuffle, iPod mini, iPod, iPod touch
 
    	Using an iPod formatted for Macintosh on a Windows computer is not  supported. Using an iPod formatted for Windows on a Macintosh computer  is not supported. To determine your iPod's hard disk format see "[iPod:  How to determine iPod's hard disk format]("http://support.apple.com/kb/HT1335")." To change the iPod  format you will need to restore iPod using iTunes. For more information  on the how to restore iPod with iTunes see "[Restoring  iPod to factory settings]("http://support.apple.com/kb/HT1339")."
 **Modes**

 By default iPod is set to "Automatically sync songs to my iPod"  sometimes called automatic mode. In order to transfer music from  multiple computers iPod must be set to "Manually manage music" sometimes  referred to as manual mode.
 **Automatic Mode**

 When iPod is set to automatic mode iTunes automatically updates  iPod's music library whenever you connect iPod to your computer. iTunes  transfers new songs you've added, and erases songs you've removed.  However, the first computer you connect iPod to is its "home" computer,  and the music library from that computer is copied to iPod. When you  connect iPod to another computer, an alert box appears with this  message:
 [INDENT] "The iPod "iPod" is synced with another iTunes library. Do  you want to erase this iPod and sync with this iTunes library?" [/INDENT]  	[INDENT] "An iPod can be synced with only one iTunes library at a  time.  Erasing and syncing replaces the contents of this iPod with the  contents of this iTunes library."[/INDENT] If you want to delete the music library on iPod and make the second  computer iPod's "home" computer, click Erase and Sync. iTunes will  delete all songs and playlists on the iPod, and then will copy the music  library and playlists from the new home computer to iPod.
 **Manual Mode**

 If you want to keep the music library on iPod, but copy songs or  playlists from the music library on the second computer, click Cancel to  this dialog box, and then set iPod to manual mode.
 You change the iPod synchronization mode to manual mode in iTunes:
 
[LIST=1]
[*]Open iTunes, if necessary.
[*]Select iPod in the Source pane.     [IMG]http://km.support.apple.com/library/APPLE/APPLECARE_ALLGEOS/HT1202/HT1202-1.jpg[/IMG]
[*]Click the Summary tab.
[*]Click "Manually manage music and videos" to enable that option.     [IMG]http://km.support.apple.com/library/APPLE/APPLECARE_ALLGEOS/HT1202/HT1202_2.jpg[/IMG]
[*]Click OK in the resulting dialog box.
[*]Click Apply.
[/LIST]
 It is normal for iPod to take a few seconds to change from automatic  mode to manual mode.
 When in manual mode, to add songs or playlists drag them from iTunes  to the iPod icon in the sidebar. To remove songs or playlists select  them on the iPod in iTunes and hit the delete key. You can also create  playlists directly on the iPod.
 **Important:** Synchronization generally occurs only in  one direction, from your computer to your iPod. However, if you are  legally allowed to transfer song files, you can use your iPod as a [_hard  disk_]("http://support.apple.com/kb/HT1478"). An exception is the [transfer  purchases feature]("http://docs.info.apple.com/article.html?path=iTunesMac/8.1/en/15480.html"), which allows you to restore purchased iTunes  content to an authorized computer from your iPod.
 **Note:** iPod shuffle is intended for use with a single  computer. You cannot load music from multiple computers or iTunes  libraries onto iPod shuffle like you can with other iPods.

---

### Post by spydeyrch on 2010-04-27
Also, I found this: [http://forums.ilounge.com/showthread.php?t=71349](http://forums.ilounge.com/showthread.php?t=71349)

It may be a little out dated bit it has some good ideas.

And finally I found this too: [http://www.ilounge.com/index.php/articles/comments/copying-music-from-ipod-to-computer/](http://www.ilounge.com/index.php/articles/comments/copying-music-from-ipod-to-computer/)

Check them out and see if they help at all. :)

-Spydey:lolflag:

---

### Post by oleink on 2010-04-27
I've heard that you can simply change the formats for the nonprotected files in itunes.  That I know is possible but there is something I recently discovered that I have yet to try (so don't know if it actually works yet) but if you want to here it is:
If you have the itunes account that has the music stored you can copy the protected (DRM's) to cd and then have itunes read the cd like any other cd and upload them to the library.  At that point you should be able to convert them because when it uploads them it will not upload the protected file format but rather m4a or aac

---

### Post by mcoleman44 on 2010-04-27
Somewhere in itunes theres an option that lets you convert your whole library to AAC

---

### Post by oleink on 2010-04-27
> **mcoleman44 said:**
> Somewhere in itunes theres an option that lets you convert your whole library to AAC

Yes but it won't let you convert their protected files unless you make them unprotected

---

### Post by oleink on 2010-04-27
If you still have the itunes files there is a way to make them unprotected and AAC or mp3 (I still use mp3 i guess im a bit old fashioned in that way)

---

### Post by spydeyrch on 2010-04-27
The way the "convert to unprotected" works is that Apple releases the song in two versions. The DRM'ed version and the non-DRM'ed version. If you want to "upgrade" the DRM'ed ones to non-DRM'ed ones, then apple charges you to do so. Normally DRM'ed files are around $0.99 but the non-DRM'ed versions are usually $1.30. It can get spendy to "convert" via allowing itunes to upgrade for you.

As far as burning them to a CD and then re-ripping them. We already discussed that. I even wrote a quick how-to (part 1)on how to use a virtual cd burner to convert all of your songs at once instead of burning actual physical CDs.

I am still looking into the issue. :)

-Spydey:lolflag:

---

### Post by oleink on 2010-04-27
> **spydeyrch said:**
> The way the "convert to unprotected" works is that Apple releases the song in two versions. The DRM'ed version and the non-DRM'ed version. If you want to "upgrade" the DRM'ed ones to non-DRM'ed ones, then apple charges you to do so. Normally DRM'ed files are around $0.99 but the non-DRM'ed versions are usually $1.30. It can get spendy to "convert" via allowing itunes to upgrade for you.

As far as burning them to a CD and then re-ripping them. We already discussed that. I even wrote a quick how-to (part 1)on how to use a virtual cd burner to convert all of your songs at once instead of burning actual physical CDs.

I am still looking into the issue. :)

-Spydey:lolflag:

Oh somehow I missed part 1 even though i saw part 2 was labelled part 2.  Thanks.  I could actually use the virtual cd burner cause I've gotta do that with my files

---

### Post by oleink on 2010-04-27
I'm excited to try it

---

### Post by spydeyrch on 2010-04-28
It works quite well! I tried it on my XP machine and runs just fine. I converted all my songs at once. It took a long time to do so. But I just let it do its stuff. 

I tried the program on Win 7 and it didn't work. I don't remember if it didn't work on Win7 due to being Win7 or due to being the x64 version. But, Tunebite does work on Win7. but it isn't a virtual CD burner. It intercepts the audio stream via your sound card and encodes it on the fly.

Let me know how it goes and if you have any issues.

-Spydey:lolflag:

---

### Post by oleink on 2010-04-28
> **spydeyrch said:**
> It works quite well! I tried it on my XP machine and runs just fine. I converted all my songs at once. It took a long time to do so. But I just let it do its stuff. 
 
I tried the program on Win 7 and it didn't work. I don't remember if it didn't work on Win7 due to being Win7 or due to being the x64 version. But, Tunebite does work on Win7. but it isn't a virtual CD burner. It intercepts the audio stream via your sound card and encodes it on the fly.
 
Let me know how it goes and if you have any issues.
 
-Spydey:lolflag:
 Alright thanks.  I've got XP so it doesn't even matter if doesn't work on Win7 to me.  :)  I'm mostly done with windows except getting my music off itunes.  I use a sansa fuze now and am planning on getting something with a 5 inch hd screen for other stuff soon

---

### Post by spydeyrch on 2010-04-28
> **oleink said:**
> Alright thanks.  I've got XP so it doesn't even matter if doesn't work on Win7 to me.  :)  I'm mostly done with windows except getting my music off itunes.  I use a sansa fuze now and am planning on getting something with a 5 inch hd screen for other stuff soon

Awesome. That is what I use too!! Check out [this thread]("http://ubuntuforums.org/showthread.php?t=1355235") I started a while ago. It has some good info in it about what we have been discussing, as far as a pmp (personal music player) goes.

I am glad that you will be able to use the virtual cd burner. It woks very well in XP and gets done exactly what is needed. :)

Also, I would recommend from here on out, once you have your iTunes music converted, to go either one of two routes to get your music. Either use Amazon's music store, which I have heard is not DRM'ed and come in a few different formats (I haven't done it personally but have heard good things about it from friends), or wait until tomorrow, April 29th, 2010. Ubuntu 10.4 comes out and it is going to have the ubuntu music store which is partnered up with [7 Digital.]("http://us.7digital.com/") I browsed through their music selection and they have a very decent amount of the music that I listen to. I listen to country, classical, new age, latin, pop, etc etc. So I have several genres that I listen to and they had all of my songs plus a few that I couldn't find in iTunes. The ones coming from the ubuntu music store are, as I have heard it, non-DRM'ed .mp3 files.   :KS:popcorn::KS

So, those would be my suggestions as this would release you from the strangle hold that iTunes has on alot of us.

Just my $0.02

-Spydey :lolflag:

Let me know how it goes.

-Spydey :lolflag:

---

### Post by spydeyrch on 2010-04-28
Hey guys, I just found some sites that claim to be able to convert .m4p protected files. Here they are:

[http://addons.songbirdnest.com/addon/23](http://addons.songbirdnest.com/addon/23)

[http://www.freedownloadscenter.com/Best/m4p-convert-mp3.html](http://www.freedownloadscenter.com/Best/m4p-convert-mp3.html)

[http://itunesm4ptomp3.wordpress.com/2008/07/04/how-to-convert-itunes-m4p-to-mp3-with-tuneclone/](http://itunesm4ptomp3.wordpress.com/2008/07/04/how-to-convert-itunes-m4p-to-mp3-with-tuneclone/)

[http://www.bpurcell.org/BLOG/index.cfm?mode=entry&entry=1036](http://www.bpurcell.org/BLOG/index.cfm?mode=entry&entry=1036)

[http://all-streaming-media.com/streaming-media-faq/faq-playing-DRM-protected-m4p-AAC-Apple-iTunes-files.htm](http://all-streaming-media.com/streaming-media-faq/faq-playing-DRM-protected-m4p-AAC-Apple-iTunes-files.htm)



I haven't read all of the sites yet, just browsed them quickly but they look promising and probably not as complex as my two solutions.

Plus, I know that songbird, the first link, works in ubuntu!!!!!   :KS:KS:KS:P:P:P:)  I just don't know if the plug-in / add-in will work as I have never tried either (songbird / plug-in)

What do you guys think?

-Spydey :lolflag:

p.s. here is a wiki page that goes over how apple's DRM works and a brief history of it.

[http://en.wikipedia.org/wiki/FairPlay#How_it_works](http://en.wikipedia.org/wiki/FairPlay#How_it_works)

---

### Post by oleink on 2010-04-28
> **spydeyrch said:**
> Awesome. That is what I use too!! Check out [this thread]("http://ubuntuforums.org/showthread.php?t=1355235") I started a while ago. It has some good info in it about what we have been discussing, as far as a pmp (personal music player) goes.

I am glad that you will be able to use the virtual cd burner. It woks very well in XP and gets done exactly what is needed. :)

Also, I would recommend from here on out, once you have your iTunes music converted, to go either one of two routes to get your music. Either use Amazon's music store, which I have heard is not DRM'ed and come in a few different formats (I haven't done it personally but have heard good things about it from friends), or wait until tomorrow, April 29th, 2010. Ubuntu 10.4 comes out and it is going to have the ubuntu music store which is partnered up with [7 Digital.]("http://us.7digital.com/") I browsed through their music selection and they have a very decent amount of the music that I listen to. I listen to country, classical, new age, latin, pop, etc etc. So I have several genres that I listen to and they had all of my songs plus a few that I couldn't find in iTunes. The ones coming from the ubuntu music store are, as I have heard it, non-DRM'ed .mp3 files.   :KS:popcorn::KS

So, those would be my suggestions as this would release you from the strangle hold that iTunes has on alot of us.

Just my $0.02

-Spydey :lolflag:

Let me know how it goes.

-Spydey :lolflag:



Already planning on buying from the Ubuntu store.  That is one thing I'm truly looking forward to with this release:)

---

### Post by oleink on 2010-04-28
> **spydeyrch said:**
> Hey guys, I just found some sites that claim to be able to convert .m4p protected files. Here they are:

[http://addons.songbirdnest.com/addon/23](http://addons.songbirdnest.com/addon/23)

[http://www.freedownloadscenter.com/Best/m4p-convert-mp3.html](http://www.freedownloadscenter.com/Best/m4p-convert-mp3.html)

[http://itunesm4ptomp3.wordpress.com/2008/07/04/how-to-convert-itunes-m4p-to-mp3-with-tuneclone/](http://itunesm4ptomp3.wordpress.com/2008/07/04/how-to-convert-itunes-m4p-to-mp3-with-tuneclone/)

[http://www.bpurcell.org/BLOG/index.cfm?mode=entry&entry=1036](http://www.bpurcell.org/BLOG/index.cfm?mode=entry&entry=1036)

[http://all-streaming-media.com/streaming-media-faq/faq-playing-DRM-protected-m4p-AAC-Apple-iTunes-files.htm](http://all-streaming-media.com/streaming-media-faq/faq-playing-DRM-protected-m4p-AAC-Apple-iTunes-files.htm)



I haven't read all of the sites yet, just browsed them quickly but they look promising and probably not as complex as my two solutions.

Plus, I know that songbird, the first link, works in ubuntu!!!!!   :KS:KS:KS:P:P:P:)  I just don't know if the plug-in / add-in will work as I have never tried either (songbird / plug-in)

What do you guys think?

-Spydey :lolflag:

p.s. here is a wiki page that goes over how apple's DRM works and a brief history of it.

[http://en.wikipedia.org/wiki/FairPlay#How_it_works](http://en.wikipedia.org/wiki/FairPlay#How_it_works)

I hate how everything they do has to do with being proprietary.  Why not let the people do what they want this is computers not a dictatorship (although ubuntu is possibly turning into one as well with the way shuttleworth is turning)

---

### Post by oleink on 2010-04-28
> **spydeyrch said:**
> Hey guys, I just found some sites that claim to be able to convert .m4p protected files. Here they are:

[http://addons.songbirdnest.com/addon/23](http://addons.songbirdnest.com/addon/23)

[http://www.freedownloadscenter.com/Best/m4p-convert-mp3.html](http://www.freedownloadscenter.com/Best/m4p-convert-mp3.html)

[http://itunesm4ptomp3.wordpress.com/2008/07/04/how-to-convert-itunes-m4p-to-mp3-with-tuneclone/](http://itunesm4ptomp3.wordpress.com/2008/07/04/how-to-convert-itunes-m4p-to-mp3-with-tuneclone/)

[http://www.bpurcell.org/BLOG/index.cfm?mode=entry&entry=1036](http://www.bpurcell.org/BLOG/index.cfm?mode=entry&entry=1036)

[http://all-streaming-media.com/streaming-media-faq/faq-playing-DRM-protected-m4p-AAC-Apple-iTunes-files.htm](http://all-streaming-media.com/streaming-media-faq/faq-playing-DRM-protected-m4p-AAC-Apple-iTunes-files.htm)



I haven't read all of the sites yet, just browsed them quickly but they look promising and probably not as complex as my two solutions.

Plus, I know that songbird, the first link, works in ubuntu!!!!!   :KS:KS:KS:P:P:P:)  I just don't know if the plug-in / add-in will work as I have never tried either (songbird / plug-in)

What do you guys think?

-Spydey :lolflag:

p.s. here is a wiki page that goes over how apple's DRM works and a brief history of it.

[http://en.wikipedia.org/wiki/FairPlay#How_it_works](http://en.wikipedia.org/wiki/FairPlay#How_it_works)

I want the cowon j3 but only if it supports wifi

---

### Post by spydeyrch on 2010-04-28
> **oleink said:**
> I hate how everything they do has to do with being proprietary.  Why not let the people do what they want this is computers not a dictatorship (although ubuntu is possibly turning into one as well with the way shuttleworth is turning)

What do you mean by the way that shuttleworth is turning? Expand on your comment please. :)

Yeah, I also heat how they do everything with proprietary-ness. With the major computer/technology companies greed/pride/selfishness/ego longer than the distance from the earth to the sun and back again thrice, it really really REALLY puts a hamper on the progress of technology.

Just think for a moment what the world could possible have been like if instead of proprietary stuff, they all shared their ideas, without the need of self-gratification and self-glorification. What if they built upon the success of others because the ones that came before them shared their ideas/concepts. Think about the posibilities. What if ...... love, peace, rainbows, unicorns, doves, babies, kisses, hugs ....... whoa!!! got off on a tangent there, sorry!!!   :lolflag:

But seriously, if they had shared their ideas, we would be in, I hope and like to think, a much better place technologically speaking. But no, they wanted the billions and billions of dollars to line their coffins with.

At least we have OSS and FOSS.

-Spydey :lolflag:

---

### Post by spydeyrch on 2010-04-28
> **oleink said:**
> I want the cowon j3 but only if it supports wifi

Yeah, me too but, I would spend too much time online then. Way more than I do now and that wouldn't be good for me, my wife, or my kids. hahahahahaha  :lolflag::lolflag::lolflag:

-Spydey :guitar:

---

### Post by Zappanale on 2010-04-28
Hmm, just went to 10.04, and my iPod mounts and appears in Rhythmbox, but it doesn't seem to actually sync any files it sends across...

Yeah, it doesn't actually update, is there a step I'm missing out?

---

### Post by spydeyrch on 2010-04-28
> **Zappanale said:**
> Hmm, just went to 10.04, and my iPod mounts and appears in Rhythmbox, but it doesn't seem to actually sync any files it sends across...

Yeah, it doesn't actually update, is there a step I'm missing out?

I don't remember exactly what the plug-in or library is to sync with it is called, but I think that is what you are missing. Search the forums with keywords of ipod, rythmbox, sync and you should find a thread already started with the info that you need. :popcorn:

As far as getting songs from .m4p to open formats or more un-restricted formats, that is what we are trying to do here. :)

I stopped using my ipod because it would fail once the battery died on me.

-spydey :lolflag:

---

### Post by oleink on 2010-04-28
> **spydeyrch said:**
> What do you mean by the way that shuttleworth is turning? Expand on your comment please. :)

Yeah, I also heat how they do everything with proprietary-ness. With the major computer/technology companies greed/pride/selfishness/ego longer than the distance from the earth to the sun and back again thrice, it really really REALLY puts a hamper on the progress of technology.

Just think for a moment what the world could possible have been like if instead of proprietary stuff, they all shared their ideas, without the need of self-gratification and self-glorification. What if they built upon the success of others because the ones that came before them shared their ideas/concepts. Think about the posibilities. What if ...... love, peace, rainbows, unicorns, doves, babies, kisses, hugs ....... whoa!!! got off on a tangent there, sorry!!!   :lolflag:

But seriously, if they had shared their ideas, we would be in, I hope and like to think, a much better place technologically speaking. But no, they wanted the billions and billions of dollars to line their coffins with.

At least we have OSS and FOSS.

-Spydey :lolflag:

He said it himself about the changes that people don't like about 10.04  He said that "this is not a democracy" and something else to the effect of implying other types of government (kind of like dictatorship)

---

### Post by spydeyrch on 2010-04-28
> **oleink said:**
> He said it himself about the changes that people don't like about 10.04  He said that "this is not a democracy" and something else to the effect of implying other types of government (kind of like dictatorship)

Wow, I wasn't aware of him saying that. That is too bad. But I suppose that there are always going to be things that people don't like, right. But that is what is so cool about linux and ubuntu. It is made in a way that people new to ubuntu can get going with it right away but it gives us the open possibilities to change it to what we like. Perhaps he was thinking in line of trying to be more appealing to new users and I can understand his line of thinking. Not saying I like it, just saying that I can understnad it if it was for the reasons I stated. :)

-Spydey:lolflag:

---

