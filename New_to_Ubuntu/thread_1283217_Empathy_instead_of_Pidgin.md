---
title: "Empathy instead of Pidgin"
date: 2009-10-05
forum: New to Ubuntu
---

### Post by CaptainMark on 2009-10-05
So when karmic final release arrives theyve decided to ditch pidgin for empathy, does anyone use empathy who can tell me if it has webcam support, this is only thing i feel pidgin has always been a bit rubbish for.

---

### Post by wildman4god on 2009-10-05
empathy does have webcam support, though only a couple of protocols. They should be adding more in the year to come. that was the main reason they switched from pidgin to empathy, that and the fact that empathy integrates better into gnome. But if you still want pidgin then it's just a download away.

---

### Post by Dougie187 on 2009-10-05
Doesn't the newest pidgin support voice/video as well?

---

### Post by wildman4god on 2009-10-05
> **Dougie187 said:**
> Doesn't the newest pidgin support voice/video as well?
 
 
the technologies are now there to support video but currently no one has written and code that lets and end user take advantage of those technologies, so practically no it doesn't yet.

---

### Post by Dougie187 on 2009-10-05
From what I have read, it appears that voice/video support works through XMPP but not any other protocol, and that people have successfully used it in Pidgin.

---

### Post by CaptainMark on 2009-10-05
i have looked it up in the past for pidgin and had no luck, that was a while ago though.  I have no problem switching to empathy, may as well try it.

---

### Post by CaptainMark on 2009-10-05
i hope someone will make a screenlet for empathy though, i love having the pidgin screenlet in a widget layer.  Hmmm, decisions, im back to square one.

---

### Post by Dougie187 on 2009-10-06
> **CaptainMark said:**
> i have looked it up in the past for pidgin and had no luck, that was a while ago though.  I have no problem switching to empathy, may as well try it.

Yeah voice and video are new features for pidgin it supposedly works for any XMPP client, ie. Google Talk.

[http://pidgin.im/](http://pidgin.im/)

---

### Post by nhasian on 2009-10-06
at this time pidgin only has voice & video for the googletalk protocol while empathy has voice & video for googletalk as well as the MSN protocol.

I'm running karmic beta and have tested voice & video calls in both googletalk and msn messenger just fine.  I just hope empathy gets some sound effects by the time karmic is released.

---

### Post by mike555 on 2009-10-07
The part I don't like is the integration into gnome , if you try to completely uninstall empathy it wants to take out gnome desktop .......... didn't we all have enough problems with Windows integration ....

---

### Post by raven01 on 2009-10-07
i just actually heard about the switch so i have decided to try it out.  so far no sounds work. i have not been able to get the themes thing to work. and i cant seem to do voice or video over yahoo messenger. so yea maybe the protocol is not there yet. but first i have to get my stupid headset and video cam to work. i know its a bit off topic but what are some good webcam software for ubuntu.

---

### Post by nhasian on 2009-10-07
yes you are correct.  Empathy will do voice/video with the MSN Messenger & XMMP googletalk protocols, but not with yahoo yet.  I dont know of *any* programs that allow you to video conference in linux with yahoo's protocol.  

Empathy actually supports sounds, but doesnt come with any.  I guess its Gnome's job to package it with sounds.  Or Ubuntu's if they want to have a special ubuntu-sound theme.  The reason sound doesnt work for events yet in Empathy, I have found, is because currently there is no way to assign sounds to ANY events in gnome (includes incoming messages, etc)  here is the bugreport:

[https://bugs.launchpad.net/ubuntu/+source/gnome-media/+bug/324700](https://bugs.launchpad.net/ubuntu/+source/gnome-media/+bug/324700)


> **raven01 said:**
> i just actually heard about the switch so i have decided to try it out.  so far no sounds work. i have not been able to get the themes thing to work. and i cant seem to do voice or video over yahoo messenger. 

---

### Post by raven01 on 2009-10-07
i have been using it more and more but i am having pidgin still as a back up. i have a few complaints with people being on their mobile phones. like my friend will be on then switch to his phone. it appears empathy does not have any indications that he is on his phone. after all i hate to bug peoples phones with IM's. anyone think that will change soon?

but other than that i do like the format and the layout. it is clean.

im hoping to see a big upgrade and a lot more functionality. possibly some more preferences when it gets realeased with ubuntu 9.10 and later versions

---

### Post by kevdog on 2009-10-07
Ive got pidgin vv running in Intrepid if that matters for you -- had to compile from source mtn.  Yes it was a pain, but its possible.

---

### Post by raven01 on 2009-10-07
what is pidgin vv? im still sort of new to linux. lol even tho i have run slackware and all that when i didnt really understand it but that was a long time ago. so much has changed.

---

### Post by kevdog on 2009-10-07
pidgin voice and video -- that used to be the name of the development branch way before it was merged with the main branch.

---

### Post by raven01 on 2009-10-08
got ya. ill have to check it out :p

---

### Post by Kapitän Rotbart on 2009-10-08
Personally I find Pidgin a resource hog. I am really looking forward to the development of Empathy (and knowing that it's in the Gnome suite, development should be happening and Empathy will likely be becoming more awesome with each Ubuntu/Gnome release). I like Pidgin's plugin features, I really hope they get ported to Empathy, but surely with time Empathy should catch up on those little things (they're already leading in certain things like audio/video for msn).:guitar:

I'll still install Pidgin in Karmic, but once Empathy has all the feats found in Pidgin, I may become exclusively loyal to Empathy :P

---

### Post by raven01 on 2009-10-08
agreed. i love how empathy is smoooooth. its clean which is a big bonus. but yea they will catch up. the other thing that is going to be a big plus is that it has that new framework and it is integrated with gnome. much more better overall in time :) i am hoping when ubuntu 10 hits next year this lil client will have a big upgrade.

---

### Post by deancasino on 2009-10-08
I got Karmic yesterday and I did not come across anything that would allow me to use webcam with my MSN contacts or enable facebook chat. For those reasons I've decided to remove Empathy until they actually create a decent competitor for pidgin.

---

### Post by misfitpierce on 2009-10-08
Empathy is a nice app... Needs a bit more polishing but it is ready for the big time and has tons of potential!

---

### Post by nhasian on 2009-10-08
actually if you want to use your webcam with your MSN contacts, you need the updated telepathy-butterfly 0.5.1 which hasnt made its way over to the repos yet.  you can get it by enabling the telepathy PPA:

[https://launchpad.net/~telepathy/+archive/ppa](https://launchpad.net/~telepathy/+archive/ppa)

> **deancasino said:**
> I got Karmic yesterday and I did not come across anything that would allow me to use webcam with my MSN contacts or enable facebook chat. For those reasons I've decided to remove Empathy until they actually create a decent competitor for pidgin.

---

### Post by CaptainMark on 2009-10-08
i agree with kapitan rotbart, will probaly stick with pidgin through karmic, at least until lucid is out depending on how many decent plugins are around by then

---

### Post by deancasino on 2009-10-09
> **nhasian said:**
> actually if you want to use your webcam with your MSN contacts, you need the updated telepathy-butterfly 0.5.1 which hasnt made its way over to the repos yet.  you can get it by enabling the telepathy PPA:

[https://launchpad.net/~telepathy/+archive/ppa]("https://launchpad.net/%7Etelepathy/+archive/ppa")


Why thank you kind sir ;)

---

