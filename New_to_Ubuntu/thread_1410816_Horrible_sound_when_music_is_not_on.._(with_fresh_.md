---
title: "Horrible sound when music is not on.. (with fresh 9.10 install)."
date: 2010-02-19
forum: New to Ubuntu
---

### Post by kramer65 on 2010-02-19
Hello,


I used Ubuntu 8.04 for a long time, but recently things started to break down (no internet anymore, random freezes), so I  thought it would be smart to finally try a newer version. So I formatted and installed Ubuntu 9.10, which works like a charm.. apart from the following:

When I play music, a video file, or a youtube vid, all is good. When I then stop the music or the vid however, 16 seconds later (I checked with a stopwatch several times) this loud buzz suddenly starts. It's the same buzz as when my pc is turned off.

This is quite annoying behaviour, and I never had it with a previous version of Ubuntu. Can anybody help me out fixing this?

---

### Post by PeteyMcPetenPete on 2010-02-19
Seems like a bug to do with your sound card. Is the card integrated into your motherboard (built in) or is it a dedicated card (ie you bought a new one). You could try getting rid of pulse audio and moving to alsa or oss, they seem to have worked for me...

I decided to stick with 9.04 after they removed most of the sound features I used. You could always burn an iso and boot into live disc to see if you have the same problems as before :)

---

### Post by Peter09 on 2010-02-19
Yeah, think there is a known problem with Pulse Audio. When the sound card is not in use it turns the card off. This results in a thump or other such noise in some cards.

---

### Post by kramer65 on 2010-02-25
Wouldn't it be possible to run a script when I start up Ubuntu which constantly keeps the sound card in use? You could for example loop an mp3 with only silence or something..

Any other ideas?

This simple bug is really making working at this machine impossible, so I hope I can be able to solve it..


[edit] btw, I have an integrated sound card. [/edit]

---

### Post by joshd2189 on 2010-02-25
have you read this thread?

[http://ubuntuforums.org/showthread.php?t=1096628]("http://ubuntuforums.org/showthread.php?t=1096628")

in particular comment #7
good luck

---

### Post by kramer65 on 2010-02-25
That is great! As far as I can see now, it works like a charm!

Thanks a lot!

---

