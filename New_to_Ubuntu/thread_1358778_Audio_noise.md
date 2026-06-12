---
title: "Audio noise"
date: 2009-12-18
forum: New to Ubuntu
---

### Post by mvalviar on 2009-12-18
I'm hearing crackles whenever I boot ubuntu. I becomes even louder when it performs disk checks. What's wrong?

---

### Post by mvalviar on 2009-12-20
^^ bump V-^_^-V

---

### Post by LuisGMarine on 2009-12-20
See if this might work for you, I just did it on my system and waiting to see if it takes out the crackling.

[http://www.ubuntugeek.com/ubuntu-tip-how-to-fix-crackling-noise-on-hda-audio-cards-in-ubuntu-9-10.html]("http://www.ubuntugeek.com/ubuntu-tip-how-to-fix-crackling-noise-on-hda-audio-cards-in-ubuntu-9-10.html")

---

### Post by mvalviar on 2009-12-21
tried it. I can still hear it.

---

### Post by mvalviar on 2009-12-22
please

---

### Post by LuisGMarine on 2009-12-22
I tried it too and I can still hear it =(.  I honestly don't know what to do I'm thinking about falling back to Jaunty.  I know that ton of sound issues poped up from Jaunty to Karmic.  Afterall everyone tells me that the LTS versions are the more stable ones.

---

### Post by mvalviar on 2009-12-23
> **LuisGMarine said:**
> everyone tells me that the LTS versions are the more stable ones.

I have to agree. I should have stayed with HH. When LL comes out I'll upgrade to it and stay with it until a new LTS is out.

---

### Post by LuisGMarine on 2009-12-23
I think that I'm going to be crazy enough to backtrack all the way back to HH.  I'm not looking for a "bleeding edge" system anymore.  I want something stable that can replace windows for me, without as much hassle as possible.  

There is a thread out there in the forums that talks about the different options you can add to your alsa config depending on what sound chip you have.  I can't seem to find it anymore so try and look for it.  I'm thinking that maybe we need to recompile alsa with some special flags, or we'll have to tweak the hell out of the alsa.conf file in hopes that an option we evoke will fix this mysterious sound system.  

To be quite honest its scared me a couple of times at night, I'll leave the volume on max and it makes this horrible griding sound from a scary movie, and when you are half awake going to the bathroom noises like that tend to spook you a little.  I've lost so much sleep .....:lolflag:

---

### Post by mvalviar on 2010-01-03
Does anyone have a fix for this? Yesterday I plugged an amp and a pair of large speakers for a party and the hissing is so damn noticeable that I'd have to reboot to windows and use winamp. I just wish I can use ubuntu for simple needs like playing music.

---

### Post by LuisGMarine on 2010-01-03
I'm onto a new fix now that I'm back to my Karmic Computer.  There is some stuff that I've googled that talks about turning up the lvl to your PCM all the way up.

I just turned mine up and I haven't heard anything.  Then again it comes and goes so I can't say this fixed it for sure after just 5 minutes.

The PCM Volume can be access through alsamixer.

EDIT******************888

that dumb fix didn't work.  My machine just almost gave me a heart attack with that loud crack.  My speakers are officially trying to go poltergeist on me.

---

### Post by Marrkk on 2010-01-04
Pulseaudio is more than likely the problem. its mainly broken in 
ibex jaunty and karmic :(





[http://marrcuk.blogspot.com/](http://marrcuk.blogspot.com/)

---

### Post by LuisGMarine on 2010-01-04
Hey I actually ran into this howto last night, and followed Part A.  i honestly think it has fixed my problem.  I haven't had any popping or crackling from my system in quite some time now.

[http://ubuntuforums.org/showthread.php?t=789578]("http://ubuntuforums.org/showthread.php?t=789578")

---

### Post by mvalviar on 2010-01-09
I just discovered something amusing. I noticed that each time ubuntu accesses my hd there is a corresponding audio noise. I'm watching a movie and a can hear gzzt, gzzt gzzt that corresponds to the LED HD activity indicator going lit, lit, lit. When I launch and up the LED is lit for a couple of seconds and my speakers go gzzzzzzttttt. Wow! This is really annoying. Please help me fix it or a least tell me whats wrong so I can explain to my friends what's going on with my speakers.

---

### Post by mvalviar on 2010-01-09
Seriously. Please help me. Is this still related to the HDA power saving problem?

---

### Post by LuisGMarine on 2010-01-09
I'm still trying all sorts of fixes and I can't fix the problem.  In all honesty I think I'm doing more harm than good.

---

### Post by mvalviar on 2010-01-10
up. Is there a fix?

---

### Post by LuisGMarine on 2010-01-10
Not yet, if you google there are some things that reduce the amount of audio noise and the frequency.  But I have still not found a solid fix that completely removes it.

---

### Post by insane_alien on 2010-01-10
it could just be crappy build quality of the sound system. my Dell has horrendously obvious crackle especially if you're using earphones. as a result i bought myself a set of digital speakers and an interface card that gives me S/PDIF out. problem solved.

---

### Post by LuisGMarine on 2010-01-10
I hate to do this, but the problem *doesn't exist in windows* so I know it's not my hardware.  On top of that I've used older versions of Ubuntu like 8.04 and all works just fine.  Once I hit the Jaunty release that's when this problem started happening.

---

### Post by mvalviar on 2010-01-10
> **insane_alien said:**
> it could just be crappy build quality of the sound system. my Dell has horrendously obvious crackle especially if you're using earphones. as a result i bought myself a set of digital speakers and an interface card that gives me S/PDIF out. problem solved.

Sad to say, but I don't have problems with audio when I run windows. I thought this would be easy since audio a basic feature in a computer system. I give up.

---

### Post by mvalviar on 2010-01-27
up. Come on, updates has come and gone and this still hasn't been fixed?

---

