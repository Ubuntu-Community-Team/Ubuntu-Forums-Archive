---
title: "Audio streaming problem"
date: 2009-01-06
forum: New to Ubuntu
---

### Post by vividia on 2009-01-06
I've had Ubuntu for 6 months and this is the first time I've had to ask for help rather than just find it in the forums.  I am having problems with streaming audio.  When I try to in firefox, I get a window saying this: /tmp/groovesalad-4.pls could not be opened, because the associated helper application does not exist. Change the association in your preferences.

So I checked in preferences and it has it set for mplayer which should work fine but doesn't.  I can listen to streaming audio using the screenlet aerial radio.  I also am having problems in streamtuner.  On top of all this audacious won't do anything.  It is unresponsive and I have to force it to close.  It won't play any files at all. Amarok is the same.

I've tried uninstalling and reinstalling with no affect.  I've also tried updating my ubuntu restricted extras and gstreamer .10... nothing works.

Please Help!

---

### Post by gettinoriginal on 2009-01-06
Not sure where you problem lies, but here are some threads that should help, start with the bottom 2 first:  :P
[http://ubuntuforums.org/showthread.php?t=997506](http://ubuntuforums.org/showthread.php?t=997506),
[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012),
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)
[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

---

### Post by vividia on 2009-01-06
Thanks for posting the threads.  I tried the bottom two first and did find I had the evil libflashsupport.  In the end, none of these worked.  Still have the same problem.  

I'd be less confused if I couldn't stream at all.  I can still get it on the screenlet which really stumps me.

---

### Post by gettinoriginal on 2009-01-06
Just out of curiosity, do you have "ubuntu-restricted-extras" installed ?? And what kind of sound card do you have ??

---

### Post by vividia on 2009-01-06
I did install ubuntu-restricted-extras when I found that in a thread last week.

This is going to sound dumb but I don't know what my sound card is.  I've tried searching but all I get is High Definition.  I am using a Gateway MT3422 if that helps.

---

### Post by markbuntu on 2009-01-06
I never had a problem with groovesalad, I listen to it all the time. Hmmm. I just tried it with streamtuner and got an error message 

"Couldn't look up host scfire-chi-aa03.stream.aol.com" and then it started playing and then xmms crashed. weird. Sofaspace works, drone zone works, space station soma works...

Amarok is playing Groove Salad 1 NPR monitor (182) [Soma FM] from the shoutcast list and the Groove Salad; a nicely chilled plate of..... channel but I got error loading media from the Groove Salad from Soma FM channel (aacPlus). i think xine has no decoder yet for that. I have the Amarok Engine set to xine and the Output plugin to pulseaudio

---

### Post by vividia on 2009-01-06
Thanks for checking.  I have had problems with any streaming audio.  That is just example.  The situation is not dire.  I can use Banshee to listen to Groove Salad (which is my favorite).  I'm more puzzled by the random problems I'm having.  Some programs work just fine like Banshee.  Amarok has some functionality and Audacious loads but is unresponsive.  

I know my sound card works, whatever it is.  Its just a puzzling problem that I'd rather fix since there may be other larger problems I've yet become aware of.

---

### Post by markbuntu on 2009-01-06
You are probably missing some packages that make those apps work better. There are some extra packages for audacious and amarok and xine which you can find with the Synaptic package manager. This will get you more plugins etc.

You can also go here and follow the directions, you can skip all the stuff you know you already have

[http://ubuntuforums.org/showthread.php?t=997506](http://ubuntuforums.org/showthread.php?t=997506)

You can also go here and look in the Sound Server Setup section to make sure your sound is properly configured and get a better idea about how it all works

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

Happy to help a fellow groove salad listener. I also listen to Sofaspace and Bluemars a lot, and Space Station Soma. 

...........chillin out is hot.............

---

### Post by vividia on 2009-01-09
I got around to working on audio problems again and tried those suggestions.  But I'm still having the same problems.  And on top of that, i can no longer control volume using the keys.  I have to go to the tray to do that.  Though not a problem per se, just inconvenient.

I'm debating whether there must just be some critical failure somewhere and maybe I should just install Intrepid...

---

### Post by sam-c on 2009-01-10
> **vividia said:**
> I got around to working on audio problems again and tried those suggestions.  But I'm still having the same problems.  And on top of that, i can no longer control volume using the keys.  I have to go to the tray to do that.  Though not a problem per se, just inconvenient.

I'm debating whether there must just be some critical failure somewhere and maybe I should just install Intrepid...
I have this Problem Since Intrepid on Ubuntu 8.10
Kubuntu OK.

---

### Post by vividia on 2009-01-24
I did switch over to Intrepid after all.  Sorry for the delay in updating this thread.  I'm in college and the new semester started and there was this inauguration I got to go to... I'm having no problems with sound any longer so thats good.  I have another problem that I shall have to take elsewhere.

Thanks to all who left suggestions. :)

---

