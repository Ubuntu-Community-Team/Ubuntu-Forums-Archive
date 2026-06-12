---
title: "Jack fails to connect to server"
date: 2009-12-25
forum: New to Ubuntu
---

### Post by nick_geetar on 2009-12-25
Okay so i have Qjack installed. I have Qsynth and virtual keyboared installed. I keep getting a midi driver fault when I open up Qsynth. Also the only way Qsynth and Qjack work is if I sudo them.  I can get the keyboard to work if I open the keyboard then sudo Qjack in terminal. then go to connections and go virtual keyboard and connect that toTiMidity.
But how do I tie the Qsynth in with the virtual Keyboared and Qjack. I just switch from windows about three days ago because of the workstation I heard I could build. But it's looking like it could be a little work with linux. If i'm doing something wrong help plz. This is the fault I get on qsynth btw.
8:56:14.224 : Creating synthesizer engine...
18:56:15.247 : Creating audio driver (jack)...
18:56:15.338 : Creating MIDI router (alsa_seq)...
18:56:15.338 : Creating MIDI driver (alsa_seq)...
18:56:15.709 : Failed to create the MIDI driver (alsa_seq). No MIDI input will be available.
Also I get this weird error or something in terminal when I go to open up Qsynth. Then it opens.
[COLOR=Navy]nick@nick-laptop:~$ sudo qsynth
[sudo] password for nick: 
Warning: no locale found: /usr/share/locale/qsynth_en_US.UTF-8.qm
[COLOR=Black]I'm brand new to linux in every way,shape and form. Any explanation or any help would be much appreciated.[/COLOR]
[/COLOR]

---

### Post by nick_geetar on 2009-12-25
Okay I fixed the whole having to sudo qjack and qsynth. Still trying out how to to combine Qjack and Qsynth. Am I just screwing up the connection process or am I looking at it wrong. Am I able to play the vkeybd and adjust the settings on Qsynth and it should sythesize right? I'm also trying to figure out Creox is there a way so I can hear playback while I'm recording? I'm also wandering if there is a way to record with Creox through Audactiy and Qjack and all that craziness? Help Plz

---

