---
title: "No sound in 10.10"
date: 2010-10-19
forum: New to Ubuntu
---

### Post by Captainflowers91 on 2010-10-19
Since updating from Ubuntu 10.04 to 10.10 on my HP DV7 notebook, I've lost any and all audio. This includes flash video as well as music from rythmnbox. Has anyone else had this problem and if so, how did you fix it?

---

### Post by Captainflowers91 on 2010-10-19
Even system sounds arn't working. Although oddly, it plays the music when showing the login screen, but not the actual startup music when I log in

---

### Post by Gone fishing on 2010-10-19
If you create a new account does the sound  work from that account?

---

### Post by Captainflowers91 on 2010-10-19
Strangely yes. This makes absolutely no sense to me. I've checked and I know my computers not muted, but I have no clue whats happening

---

### Post by sandyd on 2010-10-19
> **Captainflowers91 said:**
> Strangely yes. This makes absolutely no sense to me. I've checked and I know my computers not muted, but I have no clue whats happening
you got a .asoundrc file in your home dir?

if yes, move it.

---

### Post by Captainflowers91 on 2010-10-19
I did a search and didn't find anything whatsoever

---

### Post by Captainflowers91 on 2010-10-20
Ok so I removed Pulseaudio and now the audio works fine :/. I don't understand it, but hey whatever works

---

### Post by Gone fishing on 2010-10-20
Sorry I didn't get back earlier - shame I'm not rich and have to work. 

The Pulse Audio settings were messed up (technical term ;);)
when you removed the .pulse file it would have been recreated using the default setting and and making everything OK. 

The account you created would have had the default setting hence the test.

---

### Post by caro on 2010-10-20
I was having sound problems too.  Videos played fine in Firefox, but Rhythmbox or any other music player sounded bad.  The music would skip and jump around.  I removed Pulseaudio via Synaptic and everything is fine now.

---

