---
title: "Abnormal color of videos in movies in Ubuntu 10.04"
date: 2010-05-03
forum: New to Ubuntu
---

### Post by babloo75 on 2010-05-03
I have dual boot Win 7 & Ubuntu 10.04. Whenever I open a video file, it displays abnormal colors of the entities in the movie. 
Can anybody help me out in this matter.
(All is fine in Win 7).

---

### Post by Temposs on 2010-05-03
Try opening the video in VLC, and let me know if it is improved in that program.

---

### Post by babloo75 on 2010-05-03
Its the same abnormal colors in both vlc and movie player

---

### Post by Temposs on 2010-05-03
Have you installed the ubuntu-restricted-extras package?

Have you tried installing the media codecs included in medibuntu?

[http://medibuntu.org](http://medibuntu.org)
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

They have some stuff that isn't included in ubuntu-restricted-extras. If this doesn't work, then you might just be out of luck.

---

### Post by babloo75 on 2010-05-03
I had installed restricted package, as my NVidia graphic card was not recognized by ubuntu. When I tried to apply desktop effects, especially the rotating feature, I installed restricted packages.
Now the desktop is rotating but color of movies is very bad... as an example the blue color of people in the movie 'Avatar' is appearing as yellow.....

---

### Post by babloo75 on 2010-05-03
> **Temposs said:**
> Have you installed the ubuntu-restricted-extras package?

Have you tried installing the media codecs included in medibuntu?

[http://medibuntu.org](http://medibuntu.org)
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

They have some stuff that isn't included in ubuntu-restricted-extras. If this doesn't work, then you might just be out of luck.

I went through these websites, but am confused as to how to rectify this problem.
Please help.

---

### Post by Sealbhach on 2010-05-03
In Totem Movie Player, try adjusting the saturation and hue in Edit/Preferences, see if you can get normal colours that way.

.

---

### Post by babloo75 on 2010-05-03
No this doesn't help........... Moreover if this problem were in Totem, vlc shouldn't display abnormal colors........
One thing I have noticed, whenever I play videos on youtube, colors are perfectly normal.

---

### Post by babloo75 on 2010-05-03
Now my problem is solved. Opened
System> Admin > NVIDIA X Server settings > XServer xvideo settings > Reset hardware defaults.

Now all is fine.
Thanks to all......... Bye

---

### Post by xumuk37 on 2010-05-04
I had it once, exactly the same... After rebooting was all right. Did you tried? vlc opens anything!

---

### Post by babloo75 on 2010-05-05
The problem recurred again and again today........ Now I have changed the driver for nVIDIA Graphic card. I hope this doesn't recur now.

---

### Post by neanderslob on 2010-05-11
> **babloo75 said:**
> Now my problem is solved. Opened
System> Admin > NVIDIA X Server settings > XServer xvideo settings > Reset hardware defaults.

Now all is fine.
Thanks to all......... Bye

Hey this worked great for me; I had the same problem.  Let's see if it kicks back over after a while like it did for you.

:guitar::guitar:

---

### Post by efy96001 on 2010-05-25
Thanks, this worked for me too. 

:guitar::guitar:

---

### Post by blur xc on 2010-05-26
I just noticed this as well.  I'll try your fix... thanks.

BM

---

### Post by neanderslob on 2010-05-26
Hey, it did work for me (and still does).  But I have to keep refreshing the nvidia setting by displacing the hue bar over each time a I want to watch a movie.   It isn't a matter of the hue being at the wrong setting.  It's always at the right one, it's just that without moving it in some way the color comes up all funky every time a load a movie.  (It's as though it has to be reminded to work right.)  This goes for all players including vlc.  Anyone else running into this?

---

### Post by blur xc on 2010-05-28
> **babloo75 said:**
> Now my problem is solved. Opened
System> Admin > NVIDIA X Server settings > XServer xvideo settings > Reset hardware defaults.

Now all is fine.
Thanks to all......... Bye

Ok- now this is going to soud psycho...  

We have a two user account setup at home, my wife, and myself.  This morning while eating my breakfast I thought I'd fix a few things relating to my wife's user account while she was still sleeping, and at the same time I tried this fix for the funny colored videos.  When I clicked reset hardware defaults, I noticed the hue slider, which was all the way to the left, went to the center of the adjustment range.  I click close- no dice.  So, I do it again, but it was already at the middle, so I click save settings to config file (xorg.conf), but still, not fixed.  Then I think maybe if I log out and back in again, that might work.  Since I was already on my wife's account, and I was not logged in, I just logged into my user account (a bit faster, and she had some windows open that I didn't want to close) and I played the same video I was testing her user account with, and the colors looked great.  So, I logged out, saved all my wife's junk, logged her out and back in again, but still - colors are still jacked up!  So, now I'm frustrated- I reboot, but no- the colors are still goofy on her user but fine on mine.  

WTF?  

I was under the impression that nvidia x server settings were system wide settings that should globally affect all users, right?

So, anyway, I'm still scratching my head on this one...any help would be immensely appreciated.

Thanks,
BM

---

### Post by neanderslob on 2010-05-28
> **blur xc said:**
> Ok- now this is going to soud psycho...  

We have a two user account setup at home, my wife, and myself.  This morning while eating my breakfast I thought I'd fix a few things relating to my wife's user account while she was still sleeping, and at the same time I tried this fix for the funny colored videos.  When I clicked reset hardware defaults, I noticed the hue slider, which was all the way to the left, went to the center of the adjustment range.  I click close- no dice.  So, I do it again, but it was already at the middle, so I click save settings to config file (xorg.conf), but still, not fixed.  Then I think maybe if I log out and back in again, that might work.  Since I was already on my wife's account, and I was not logged in, I just logged into my user account (a bit faster, and she had some windows open that I didn't want to close) and I played the same video I was testing her user account with, and the colors looked great.  So, I logged out, saved all my wife's junk, logged her out and back in again, but still - colors are still jacked up!  So, now I'm frustrated- I reboot, but no- the colors are still goofy on her user but fine on mine.  

WTF?  

I was under the impression that nvidia x server settings were system wide settings that should globally affect all users, right?

So, anyway, I'm still scratching my head on this one...any help would be immensely appreciated.

Thanks,
BM

You seem to be describing exactly what my problem is.  I've been needing to open the movie, tweek the hue slider (just by displacing it ever so slightly) and everything's fine.  BUT when I open another movie I have to go back and do it all over again.  Indeed nvidia settings do affect all users (as far as I know).  The issue seems to be that it re-screws itself up the instant that a video reaches a close.  I don't have a solution yet, but I thought you'd enjoy the increase in nonsensical frustration that seems to surround this issue. ):P

PS.  While I saw the Steve Ballmer mayhem as a rare point in Microsoft's favor (who doesn't love a pudgy balding nerd going apeshit on stage), wtf was the first video?  Was that something released by Microsoft?  If so: wtf?  ELSE wtf?  seriously man, that made me uncomfortable watching it

---

### Post by blur xc on 2010-05-28
> **neanderslob said:**
> PS.  While I saw the Steve Ballmer mayhem as a rare point in Microsoft's favor (who doesn't love a pudgy balding nerd going apeshit on stage), wtf was the first video?  Was that something released by Microsoft?  If so: wtf?  ELSE wtf?  seriously man, that made me uncomfortable watching it

Cnet did a video about that win7 launch video, and as far as I can tell, that's a legitimate MS advertisement.  There was a whole thread about it a while back when Win7 was first released.

Here it is- [http://www.youtube.com/watch?v=MmC7d2hMaqk](http://www.youtube.com/watch?v=MmC7d2hMaqk)
Decide for yourself...

BM

---

### Post by neanderslob on 2010-05-28
> **blur xc said:**
> Cnet did a video about that win7 launch video, and as far as I can tell, that's a legitimate MS advertisement.  There was a whole thread about it a while back when Win7 was first released.

Here it is- [http://www.youtube.com/watch?v=MmC7d2hMaqk](http://www.youtube.com/watch?v=MmC7d2hMaqk)
Decide for yourself...

BM

Dude that's creepy as hell.  On a more useful note, I decided to forgo my lab research this afternoon to figure this problem out.  In my hunting, I found that one has to edit the gstreamer settings to manually set up the default hue values.  The instructions are really straightforward and work like a charm: [http://www.wiredrevolution.com/ubuntu/fix-blue-tinted-video-in-ubuntu](http://www.wiredrevolution.com/ubuntu/fix-blue-tinted-video-in-ubuntu)  Cheers!

:guitar:

---

### Post by blur xc on 2010-05-28
> **neanderslob said:**
> Dude that's creepy as hell.  On a more useful note, I decided to forgo my lab research this afternoon to figure this problem out.  In my hunting, I found that one has to edit the gstreamer settings to manually set up the default hue values.  The instructions are really straightforward and work like a charm: [http://www.wiredrevolution.com/ubuntu/fix-blue-tinted-video-in-ubuntu](http://www.wiredrevolution.com/ubuntu/fix-blue-tinted-video-in-ubuntu)  Cheers!

:guitar:

that's fantastic!  I'll be sure to try it out once I get home...


BM

---

### Post by s.odaugherty on 2010-07-27
> **babloo75 said:**
> Now my problem is solved. Opened
System> Admin > NVIDIA X Server settings > XServer xvideo settings > Reset hardware defaults.

Now all is fine.
Thanks to all......... Bye



tried this and it worked, but i have to do it for each video i put on.  even for the ones i shot.  watching video of blue lava just isnt right.  is there a way to permanently reset nvidia?

---

### Post by neanderslob on 2010-07-27
> **s.odaugherty said:**
> tried this and it worked, but i have to do it for each video i put on.  even for the ones i shot.  watching video of blue lava just isnt right.  is there a way to permanently reset nvidia?

Yea, it's frustrating as hell.  The procedures described here [http://www.wiredrevolution.com/ubunt...ideo-in-ubuntu](http://www.wiredrevolution.com/ubunt...ideo-in-ubuntu) should fix it.  It was simply a matter of explicitly defining default values for color.  :guitar:

---

### Post by nitzan.dori on 2010-12-16
hi ,

that fixed my problem too , unfortunately it fixed the problem only on Totem , in VLC it remains the same...

any one fixed it for all players?

---

