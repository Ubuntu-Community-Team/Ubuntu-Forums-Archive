---
title: "TV Tuner on ubuntu Lucid"
date: 2010-06-21
forum: New to Ubuntu
---

### Post by 4chan on 2010-06-21
hi i need help. 
i have a tv tuner with **[COLOR=Black]phillips saa 7130 chipset[/COLOR]**. but i don't know how to play it on ubuntu and i'm not sure weather it is compatible or not. please help me. thanks :tongue:

---

### Post by howefield on 2010-06-21
It should work out of the box, or if not, be fairly easy to make work.

What application do you plan on using ?

---

### Post by 4chan on 2010-06-21
i don't know what software to use. back in windows i'm using media player classic to play my tv.
can i use VLC? 'cause i like that software. and if yes. can you please tell me step-by-step. thanks b4 howefield

---

### Post by howefield on 2010-06-21
Yes, VLC will do fine.

Open VLC and select Open Capture Device from the Media menu.

Select the Capture mode, which should be DVB ?

Then place a check beside DVB-T and type in the Transponder/multiplex frequency for the channel you want to watch and press the play button.

I don't know if it is possible to do an automatic channel search with VLC, it probably is but someone else will need to help you.

The only real issue with the above is that you need to know the Transponder/multiplex frequency for your channels. 

I normally use Kaffeine to play tv, but as this is a KDE application, it pulls in lots of KDE dependancies which doesn't bother me, but some would prefer not to.

---

### Post by pdlethbridge on 2010-06-21
I apologize if this is a thread stealer, but I have tried to get my saa 7134 based tv card to work with 10.04 but it won't. It quit after 9.04.
I use tvtime and you mention kde, should I go that route to make it work?

---

### Post by howefield on 2010-06-21
I'd doubt that KDE will make any difference, it's just that I have always liked the Kaffeine application. I use Gnome along with 3 or 4 KDE applications that I like.

A TV tuner I used to have that was based on the saa 7134 chipset didn't work out of the box, but was fairly easy to get working, unfortunately I recently gave it away so can't play about with it and tell you how it was done, but there are plenty tutorials out there based on the saa 7134, just look for a recent one.

Are you getting any output relevant to the card in dmesg ?

---

### Post by 4chan on 2010-06-22
sorry but vlc isnt detecting my tv tuner.

[IMG]http://dl.dropbox.com/u/2075532/ubuntuforums/screenshot1.png[/IMG]

[IMG]http://dl.dropbox.com/u/2075532/ubuntuforums/screenshot2.png[/IMG]

what should i do now?:cry:

---

