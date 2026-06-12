---
title: "no sound anymore on ubuntu 10/10"
date: 2010-11-29
forum: New to Ubuntu
---

### Post by Georgia De La Salle on 2010-11-29
I had sound on the Ubuntu 10/4. Then with the upgrade, I had sound here and there on the Ubuntu 10/10, and if no sound at all, would restart until I got sound. Then I reinstalled the Ubuntu 10/10 cleanly. Again I had sound halfway, but enough to play music videos. Now after running some AlsaDriver updates, I have no sound anymore, even if I restart. Friends have suggested to look at the AlsaMixer, PulseAudio, and Sound Mixer, but I don't know where to find that. I found the others on the terminal, but am not sure exactly what I should do. I'm new to Linux. It's not the sound card, because I have sound Windows-side. So please any advice? Another friend thinks that I must wait until the next Ubuntu version update in 6 months, to fix this sound problem. I have an Acer-Aspire 7736ZG laptop.

---

### Post by 00arthuryu on 2010-11-30
try going into alsamixer through terminal
```
alsamixer
```
make sure you have not muted anything
M for mute
Arrow keys for navigation
:popcorn:

---

### Post by Georgia De La Salle on 2010-12-01
Thankyou, I'd already checked AlsaMixer on the Terminal from advice on the French Ubuntu forum, as I live in France. I didn't know about the arrow keys for navigation. All the registers on the left, starting with Master, are up in the red. On the right, all the registers, except Mic(rophone) are empty, so I put them up into the white with the arrow keys. However after checking YouTube, I still have no sound. I haven't restarted yet, but I doubt this will make a difference. I've been advised to get rid of PulseAudio completely, but I'm not confident to do so, because I'm just a beginner, and this might make things worse. Do you know where the Sound Mixer is? I've also been told to find it. Thanks again for any help.

---

### Post by mrwaistcoat on 2010-12-02
I've got the same problem

Strange thing is on sound/preferences/output, the option for speakers has just disappeared !  How do I get it back?

I upgraded to 10.10 and it's been working great for weeks until today.

---

### Post by mrwaistcoat on 2010-12-03
Mine is back !

Other users on the same PC seemed to be fine, then when I went back to mine, all was fine again.

Strange but true!

---

### Post by mrwaistcoat on 2010-12-03
Mine is back !

Other users on the same PC seemed to be fine, then when I went back to mine, all was fine again.

Strange but true!

Just tried again and same thing happened - no sound my settings, tried on my daughters settings, no problem, then mine OK again

Any ideas how I can fix this and as to why it's happening?

Thanks

---

### Post by Georgia De La Salle on 2010-12-03
All sound is still dead on Ubuntu 10/10, so I have no advice for you, sorry. I now just go into Windows side to stream music, YouTube videos, Skype calls, play DVD's, as France has HADOPI2 law--illegal to download films, even if one pays--only country in the world! So I checked both AlsaMixer and Gnome-AlsaMixer and I changed their sound preferences higher, but when I reboot, all changes are lost. The last alternative is to remove PulseAudio which may create the conflict, but I'd rather wait till a very busy computer nerd friend either does this for me, or tells me it's OK to uninstall it. I'm also supposed to look for the Sound Mixer? Do you know where it is, or is it just Alsa? Thanks.

---

### Post by Georgia De La Salle on 2010-12-28
The problem is resolved. A nerd friend spent hours looking and finally installed a package, Alsa-Base.Conf I think, I can't remember exactly, and now all sound works fine on Ubuntu 10/10 again.

---

### Post by oldrocker99 on 2010-12-28
That filename is gnome-alsamixer. It solved my problem.

---

