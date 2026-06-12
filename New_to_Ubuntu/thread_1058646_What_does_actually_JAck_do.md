---
title: "What does actually JAck do?"
date: 2009-02-03
forum: New to Ubuntu
---

### Post by gackt on 2009-02-03
Ok so i just installed Jack, browsed the web site, google it and here i am sitting wondering about what does actually jack do? I mean for end user like who only use ubuntu for making some document, listen to music, play dvd and wesnoth. It does not have any effect on my buntu. Can somebody tell me in plain english?

---

### Post by Crafty Kisses on 2009-02-03
Read this: [http://lau.linuxaudio.org/jack/](http://lau.linuxaudio.org/jack/).

---

### Post by kostkon on 2009-02-03
> **gackt said:**
> Ok so i just installed Jack, browsed the web site, google it and here i am sitting wondering about what does actually jack do? I mean for end user like who only use ubuntu for making some document, listen to music, play dvd and wesnoth. It does not have any effect on my buntu. Can somebody tell me in plain english?
Why did you install Jack?

It is a sound server used by pro audio applications because it offers low latencies among others.

Ubuntu by default has PulseAudio and not Jack.

---

### Post by gackt on 2009-02-03
Because somebody recommend me to install that to get a better sound quality out of my ubuntu(the sound is not too loud nor too small, and the bass is also poor), i think just messed up my system then ^^. Thanks so Jack is only for pro or programmer i guess.

---

### Post by kostkon on 2009-02-03
> **gackt said:**
> Because somebody recommend me to install that to get a better sound quality out of my ubuntu(the sound is not too loud nor too small, and the bass is also poor), i think just messed up my system then ^^. Thanks so Jack is only for pro or programmer i guess.
Yes, it's not a solution to your sound problems. And, I suppose, you will have difficulty making most of the desktop applications to work with it.

You are saying that you have low sound... Have you checked your volume levels and how?

What Ubuntu version do you have?

---

### Post by jrusso2 on 2009-02-03
> **gackt said:**
> Ok so i just installed Jack, browsed the web site, google it and here i am sitting wondering about what does actually jack do? I mean for end user like who only use ubuntu for making some document, listen to music, play dvd and wesnoth. It does not have any effect on my buntu. Can somebody tell me in plain english?

I don't know.  I know its a sound server and causes lots of things not to work.  However I think its the same as pulse audio which kind of has me confused.

---

### Post by gackt on 2009-02-03
> **kostkon said:**
> Yes, it's not a solution to your sound problems. And, I suppose, you will have difficulty making most of the desktop applications to work with it.

You are saying that you have low sound... Have you checked your volume levels and how?

What Ubuntu version do you have?

well not so low though but not so loud either, volume are up to 100%. what is with the bass anyway? my creative mp3 player sound more bassy. I'm using amarok with ubuntu 8.10 intrepid. Now i dont want to know what is jack for as long as it will not improve my ubuntu sound quality ^^

Thanks guys

---

### Post by kostkon on 2009-02-03
> **gackt said:**
> well not so low though but not so loud either, volume are up to 100%. what is with the bass anyway? my creative mp3 player sound more bassy. I'm using amarok with ubuntu 8.10 intrepid. Now i dont want to know what is jack for as long as it will not improve my ubuntu sound quality ^^

Thanks guys
No, *Jack* will not work in your case, it's only used by pro audio apps, as I have already said. It'll be a mess to make it work with regular apps and it will change something.

I would recommend you to check your volume levels. You can right-click on the speaker in your taskbar, and then select *Open Volume Control* from the menu.

In the volume control make sure that all the volume levels have reasonable values. To add more volumes, select *Edit &#8594; Preferences*.

To be sure double-check them using the *alsamixer* utility. Open a terminal (*Applications &#8594; Accessories &#8594; Terminal*) and give
```
alsamixer -Dhw
```
and again make sure that all your volume levels are up.

Furthermore, I believe that *Amarok* comes with an equaliser. Check its current values and change them accordingly.

Also, you could use an system-wide equaliser that may improve your sound in general. Go to [this guide]("http://ubuntuforums.org/showthread.php?t=789578") and do what *Appendix D* says.

---

### Post by gackt on 2009-02-03
> **kostkon said:**
> No, *Jack* will not work in your case, it's only used by pro audio apps, as I have already said. It'll be a mess to make it work with regular apps and it will change something.

I would recommend you to check your volume levels. You can right-click on the speaker in your taskbar, and then select *Open Volume Control* from the menu.

In the volume control make sure that all the volume levels have reasonable values. To add more volumes, select *Edit &#8594; Preferences*.

To be sure double-check them using the *alsamixer* utility. Open a terminal (*Applications &#8594; Accessories &#8594; Terminal*) and give
```
alsamixer -Dhw
```
and again make sure that all your volume levels are up.

Furthermore, I believe that *Amarok* comes with an equaliser. Check its current values and change them accordingly.

Also, you could use an system-wide equaliser that may improve your sound in general. Go to [this guide]("http://ubuntuforums.org/showthread.php?t=789578") and do what *Appendix D* says.

I did, I did exactly that and the next thing i know there is no sound at all...at all, so i install jack and at least some application are working. Fiuhh^^

---

