---
title: "ubuntu music players"
date: 2011-03-19
forum: New to Ubuntu
---

### Post by bluemoonshine on 2011-03-19
OK, I installed Ubuntu 10.10 got my music on it ,

my problem is the music players ,I tried the one it had (Rhythmbox) and Audacious and the default movie player if they work at all they sound kinda like a scratched cd ( and as if they are playing kinda fast ) 

1: they may not play at all but act as if they want to
2: if they do play they stop then back to num. 1.
3: if I reboot they will work again  then its back to  num,2 then num,1

I tried converting one music file ,it did not change , I checked to the best of my ability the sound setting and and to see if my sound card was present, it is.

I'm not sure what is going on. 

Maybe some one knows how to help me with this ?

oh ya why is everything on the internet so small?

---

### Post by bluemoonshine on 2011-03-19
> **bluemoonshine said:**
> OK, I installed Ubuntu 10.10 got my music on it ,

my problem is the music players ,I tried the one it had (Rhythmbox) and Audacious and the default movie player if they work at all they sound kinda like a scratched cd ( and as if they are playing kinda fast ) 

1: they may not play at all but act as if they want to
2: if they do play they stop then back to num. 1.
3: if I reboot they will work again  then its back to  num,2 then num,1

I tried converting one music file ,it did not change , I checked to the best of my ability the sound setting and and to see if my sound card was present, it is.

I'm not sure what is going on. 

Maybe some one knows how to help me with this ?

oh ya why is everything on the internet so small?



I apparently loose all sound after  , I just tried watching a youtube vid and i had no sound untill i rebooted .
could this be a sound card driver problem? 
i believe this is my sound card , Aureal semiconductor vortex 1 / voyetra technologies montego.

---

### Post by bluemoonshine on 2011-03-19
> **bluemoonshine said:**
> OK, I installed Ubuntu 10.10 got my music on it ,

my problem is the music players ,I tried the one it had (Rhythmbox) and Audacious and the default movie player if they work at all they sound kinda like a scratched cd ( and as if they are playing kinda fast ) 

1: they may not play at all but act as if they want to
2: if they do play they stop then back to num. 1.
3: if I reboot they will work again  then its back to  num,2 then num,1

I tried converting one music file ,it did not change , I checked to the best of my ability the sound setting and and to see if my sound card was present, it is.

I'm not sure what is going on. 

Maybe some one knows how to help me with this ?

oh ya why is everything on the internet so small?



I apparently loose all sound after all that  , I just tried watching a youtube vid and i had no sound untill i rebooted .
could this be a sound card driver problem? 
i believe this is my sound card , Aureal semiconductor vortex 1 / voyetra technologies montego.

---

### Post by Dutch70 on 2011-03-19
See if one of these two links helps to find your problem.
[[COLOR="Blue"]https://help.ubuntu.com/community/SoundTroubleshooting[/COLOR]]("https://help.ubuntu.com/community/SoundTroubleshooting")
[[COLOR="Blue"]http://ubuntuforums.org/showthread.php?t=205449[/COLOR]]("http://ubuntuforums.org/showthread.php?t=205449")

As far as why everything is so small on the internet. You'll have to be a little more specific as to what you're talking about. You can try pressing >cntrl & "+"< to increase the size.

---

### Post by bluemoonshine on 2011-03-19
> **Dutch70 said:**
> See if one of these two links helps to find your problem.
[[COLOR=Blue]https://help.ubuntu.com/community/SoundTroubleshooting[/COLOR]]("https://help.ubuntu.com/community/SoundTroubleshooting")
[[COLOR=Blue]http://ubuntuforums.org/showthread.php?t=205449[/COLOR]]("http://ubuntuforums.org/showthread.php?t=205449")

As far as why everything is so small on the internet. You'll have to be a little more specific as to what you're talking about. You can try pressing >cntrl & "+"< to increase the size

.
I'm a little brain dead at the moment , but in attempt to be more specific lets say I log in to facebook the page is small like I changed my screen resolution I tried the zoom it just made things distorted , even this that I'm doing is small almost to small to read otherwise after it's posted it is fine.
some pages i go to seem fine others are just plane tiny.
At the moment I'm more concerned about the music play/sound problem. thanks for the links I will see how that goes.

---

### Post by bluemoonshine on 2011-03-20
I checked out the links,I found I had been there before. I cant say they helped me with my problem they did help me find my sound card, sound controls, ect. 

Maybe I just don't understand what there saying, because I did try some things but still have the same problem.

 If the players play they are skippy twichy like a scratched cd then just stop and won't play at all and then I loose sound , I reboot and then they play then stop then no sound all over again.
 does not matter what player i use or that i converted the file. 

Its possible even if I do any other program the music wont work after that, lets say i dont even try and use a player but open something else then go back and try and play music it won't play just sits there timer shows 00:00 then 00:01 then back to 00:00 just back and forth . 

I think I'm explaining this the best I can. my idea is if all music players are doing this then the problem is else where , I just don't know where or what if anything went wrong with the install.
If you need i could do my best to give more info if needed about the pc it self. 

I'm confused . I've tried things some that were simple some i didnt understand no change.

---

### Post by terry_gardener on 2011-03-20
this sounds like a pulseaudio problem or sound card driver problem.
you could try opening the terminal and typing "alsamixer" and try adjusting the volume sliders. because i have found some sound cards if set to high it sounds awful but reduce the volume by about 20% it sounds alot better. 

or you could try removing pulseaudio completely, just do a search in these forums or use google and you will get step by step guide to remove pulseaudio.

---

