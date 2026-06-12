---
title: "problem with sound"
date: 2009-08-21
forum: New to Ubuntu
---

### Post by derectionfree on 2009-08-21
hi guys I'm a new user of ubuntu and I liked it
but still dont get the sound
everytimes I startup my system it start biping like bip bip bip bip bip bip bip bip bip
and it does not stop 
I'm trying to play a music but nothing seem to work

I'm runing in hp laptop with a core2deu 2ga
4g ram 
I instaled this system besid windows vista so I'm still runing vista 
but I want to switsh to ubuntu as soon as I got this problem resolved

thank you for your help

---

### Post by candtalan on 2009-08-22
Welcome!
1) first obvious thing (sorry) how is the volume controlled, there may be more than one method. thumbwheel, keys, on screen.? They can all reduce or mute any sound.

2) does sound work on using a live CD (not installed)?

3) what ubuntu version are you trying? 8.04 and 8.10 both had a few problems with sound on my machines. Note that 8.04 has a latest image, is 8.04.3
Latest ubuntu is 9.04

4) if there is a small jack socket fo rheadphones, also try them

5) try System>Preferences>Sound (tests)

6) be aware of (lodspeaker icon)
>Open Volume Control>Edit>Preferences

7) in a terminal, type
lspci
and notice if an audio device is listed

8 ) when connected to the internet an dafter obtaining a launchpad ID, do the tests:
System>Administration>HardwareTesting

hth, good luck

---

