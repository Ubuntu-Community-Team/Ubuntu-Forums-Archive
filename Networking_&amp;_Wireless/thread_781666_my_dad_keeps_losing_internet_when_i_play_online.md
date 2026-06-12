---
title: "my dad keeps losing internet when i play online"
date: 2008-05-04
forum: Networking &amp; Wireless
---

### Post by plecebo.mc on 2008-05-04
(i didnt know where i should place this this one seem'd like a good catagories to post

i have a vista laptop that i do a lot of gaming on and my dad has a dell linux computer with THE NEW Hardy Heron version. we have a Linksys wireless router w/swich and a voip box by linksys and a paket8 web to phon converter for his office lol ok

well when ever i get on the internet to play teamfortress or stuff like that he claims his email wont send and its really anoying me

he uses evloution mail and has three accounts two are web mail and the other is his office servers which is messing up so he cant send his emails out (like you hear on this cat. all the time) he can recive but not send BUT he can browse the internet fine.

while this is happening im in there playing away and my ping will all the sudden jump from 49 (wich was my usual average ping(latenacy) severs i paly on TO A SHOCKING (948 and going but i exit the program) so i get off and he asks me if im on the internet 

so i learned that when he sends emails it ties me up

( he says when he resets all the network boxes they send fine)

so (a mouth full) how might i attempt to resolve or start resolving this problem its only me and him

hes connected to the first port on the wifi sw/rout adn im number 2

is there a way to set up a seperate gateway or is this just becuse theres not enogh band width i never lag unless he trys sending wich hes tryed many options on the smtp.

wich is smtp.comcast.net ill need to check back on that when he gets home but plz help its very upseting to his work and my play thx i just dont want to sign up for more forums i got to many and i figured i use this one becuse its linux related

THNK YOU

---

### Post by niobos on 2008-05-04
From your post I don't have enough information to be sure about this, but it looks like a "bandwidth problem". Basically you and your dad are competing for bandwidth: your online game vs his email. both packets end up in the outgoing queue of the router/modem and have to wait their turn.

The "good" solution would be to implement some quality of service on the router/modem to decrease its buffer-size (and hence the lag), while distributing bandwidth fairly between the different streams. I don't know what router you have, but most of them are not capable of providing this QoS.

this website lists some of the problems and the solution on a linux router: [http://lartc.org/howto/lartc.intro.linux.html](http://lartc.org/howto/lartc.intro.linux.html)

---

### Post by zdude on 2008-05-04
Check your father computer download times and see if it is the same as yours. I noticed on Hardy that it was killing other wireless users when I had the system busy. I normally get 5000kb/s downloads and the Hardy version I was only getting 100kb/s. It just took everyone down if my machine was busy downloading or whatever. I went back to Gutsy and problem went away.

---

