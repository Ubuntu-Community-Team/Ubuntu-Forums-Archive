---
title: "gimme a movie maker alternative for 8.10 Intrepid"
date: 2009-04-29
forum: New to Ubuntu
---

### Post by Ubunser on 2009-04-29
If possible I need only soft to work with sound I don't need to edit video. If you know some sound editor to make different parts of audio together please tell or give link.
Thank you!

---

### Post by elliotn on 2009-04-29
Try Kino

---

### Post by ad_267 on 2009-04-29
Audacity is pretty good and easy to use for that kind of work. (Kino is more for video)

It's available from the Ubuntu repositories (Applications - Add/Remove).

---

### Post by Ubunser on 2009-04-29
Ok, Audacity then...

---

### Post by Ubunser on 2009-04-29
Thank you I installed Adacity.

I'm "Getting started"

:P

---

### Post by Ubunser on 2009-04-29
I imported a file to Adacity and clicked play and there went a message: "Error while opening sound device. Please check the output device settings and the project sample rate."

what that might be?

---

### Post by ad_267 on 2009-04-29
Do you have something else open that might be using audio? Eg. flash on a website or a video or audio player. Audacity seems to hog all the sound and can't play when other applications are using sound.

---

### Post by Ubunser on 2009-04-29
No everything closed, tried even closing browser, lol.
I need that done

---

### Post by ad_267 on 2009-04-29
Ok weird, well maybe the output device is wrong. Check Audio - Preferences - Audio I/O - Playback Device. Try the different options listed there and see if another device works.

---

### Post by Ubunser on 2009-04-29
In audacity preferences I clicked Audio I/O and switched playback devices, there were three Alsa. Then clicked play and there was no more error message. But no any sound too.

---

### Post by ad_267 on 2009-04-29
Looks like Audacity doesn't work well with Pulse Audio in Intrepid. I found this site which says you can kill pulse audio before running audacity, use a ppa to apply a patch or redirect it's output: [http://www.pulseaudio.org/wiki/PerfectSetup](http://www.pulseaudio.org/wiki/PerfectSetup)

Try pressing Alt+F2 and running "padsp audacity". If that works you can change the menu link later.

Seems like a lot of work just to get audio playback sorry!

---

### Post by ad_267 on 2009-04-29
You could also try Jokosher. I haven't used it myself but looks like it should be pretty good too.

---

### Post by Ubunser on 2009-04-29
I installed jokosher - I already tried and it does playback neatly. Thanks and I hope I can do what I wanted in Jokosher:)

I wouldn't kill any pulseaudio as I don't know how it will affect other applications, its way too last resot

---

### Post by ad_267 on 2009-04-29
> **Ubunser said:**
> I installed jokosher - I already tried and it does playback neatly. Thanks and I hope I can do what I wanted in Jokosher:)

I wouldn't kill any pulseaudio as I don't know how it will affect other applications, its way too last resot

Yeah, well logging out and in again would restart pulse audio so it wouldn't be too major. I think Intrepid was the first version to use pulse audio so there were a few issues like this. If you run "padsp audacity" to start audacity it doesn't kill pulse audio but will redirect the output from audacity through pulse audio, which should also work. 

Glad jokosher is working well though. I installed it myself and it does seem alright but doesn't have a lot of the effects that audacity has, eg I couldn't find a way to do simple fading in and out of tracks.

---

### Post by Ubunser on 2009-04-29
know what? when I ran audacity using the command you gave in playback devices appeared thrice as many options as before, and I found one of those that works. Thats great!

---

### Post by ad_267 on 2009-04-29
That's good! You can edit the menu so that it always runs that command when you open audacity. Just right click on the menu, select Edit Menus, find and select the Audacity menu item and click properties, then change the command to "padsp audacity".

---

### Post by mark.giblin on 2009-07-23
DeVeDe has been a consistant performer for me, it has worked when others fail to run / open the files / read audio / read the media stream and so on.

I occasionally use WinFF when DeVeDe throws a wobbler and refuses to do anything.

Audio editors... Audacity has the Audacity to say its a sound editor... Hmmm, I just used it on an mp3 and the thing has locked up and refuses to close and the force quit dialogue does not show.

I tried Jokosher and while it worked, if did sweet FA to the file that I had inserted a compressor on to beef up the quiet recording but it rendered the audio as it originally was... Not at all helpful.

---

### Post by 4ebees on 2009-07-23
> **ad_267 said:**
> Looks like Audacity doesn't work well with Pulse Audio in Intrepid. I found this site which says you can kill pulse audio before running audacity, use a ppa to apply a patch or redirect it's output: [http://www.pulseaudio.org/wiki/PerfectSetup](http://www.pulseaudio.org/wiki/PerfectSetup)

Try pressing Alt+F2 and running "padsp audacity". If that works you can change the menu link later.

Seems like a lot of work just to get audio playback sorry!

There's a very useful 'how to' here on the pulse audio site. I used it to fix my problems in Hardy 8.04 LTS.

[http://pulseaudio.org/wiki/PerfectSetup#Audacity](http://pulseaudio.org/wiki/PerfectSetup#Audacity)

---

