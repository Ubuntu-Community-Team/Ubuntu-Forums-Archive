---
title: "i'm completely lost at this point"
date: 2010-07-26
forum: New to Ubuntu
---

### Post by mrsleeps on 2010-07-26
ok what my problem was when i first tried to get things going is i couldn't watch any video's while i surfing the internet, so i talked to some people online and they said it was more then likely my video card and i'm sure this was part of the problem i have since then bought a video card its a geforce 6 series PNY and i'm running 36bit version on ubuntu and since i'm not a PC gamer and i just surf the net i would think this card would be fine it not please correct me and tell me why. at this point i'm assuming i have the drivers i need for linux with the video card i got but i am not a 100% percent sure or even 50%, so i started thinking maybe my its my flash player so i started downloading like crazy hoping to god something would work i downloaded real player for linux i downloaded and flash plugin for linux at the adobe site i downloaded something for java i mean at this point i'll do almost anything just to get it to work i love this system it works well i'm just completely lost as to what i should do who can lead me in the right direction, i can't even seem to find out how to take programs off my computer that i downloaded trying to fix the problem and that only made it worse because now when my windows open i can't even see the whole page now i mean i just need some help SOMEONE PLEASE POINT ME IN THE RIGHT DIRECTION! i just want to be able to surf the net without fighting my computer.

---

### Post by Zzl1xndd on 2010-07-26
What happens when you attempt to play a video online? If I was to guess it is likely Flash that was causing the issue.

Can you tell us what package you selected from the adobe site to install Flash?

---

### Post by Zeike on 2010-07-26
The easiest and most error free way to install flash is by installing the 'flashplugin-installer' package from the repositories.

---

### Post by Ony on 2010-07-26
Hello, mrsleeps

Welcome sorry to hear about your problem :-(  I am new to Ubuntu I also had the same problem as yourself one thing you will learn real fast around here is these guys will help you out. This link I am posting here will let you know if you have installed flash or not sometime even if it does seem like it was installed you may find this was not the case.

[http://www.adobe.com/products/flash/about/](http://www.adobe.com/products/flash/about/)

Best of luck

---

### Post by wojox on 2010-07-26
Have a look here [Flash Issues & Solutions]("http://firefox-tutorials.blogspot.com/search/label/flash")

---

### Post by mrsleeps on 2010-07-27
ok i have a flash player and its version 10.1.53.64 it wasn't a package at all i just figured i didn't have the right thing and started surfing the net to find something that would work since i can't find what i need in the software center not to say its not there but i have no idea what i'm looking for exactly so i could spend all day just downloading stuff that won't help so i googled linux flash player downloads and this is the page i downloaded everything from [https://addons.mozilla.org/en-US/firefox/browse/type:7](https://addons.mozilla.org/en-US/firefox/browse/type:7) and i downloaded everything that would go on linux and was hoping something good would happen because like the title says i'm completely lost with this, love linux though want to figure it out. if anymore info is needed on my part just let me know and i will get it to you. i didn't think it would be so hard just to be able to surf the net.

---

### Post by mrsleeps on 2010-07-27
i forgot the problem is the video is choppy its almost like watching still frames jump from one to another i have no idea what causes these problems there for i don't know what solves them either.

---

### Post by 3rdalbum on 2010-07-27
What are the specifications of your computer? You say you have a GeForce 6; this is quite a few years old now and I'm wondering if your CPU is up to handling Flash content on a modern operating system.

Does the problem occur only on full-screen mode in Flash, or does it happen in the normal-sized Flash window too?

Do you have the Nvidia proprietary graphics driver? Go to System > Administration > Hardware Drivers to check. You should be using it; if not, then use this program to install it.

If you can watch Flash videos then you probably have Flash already. (or, at least, one of the open-source Flash players which should work fine for video).

---

### Post by sandyd on 2010-07-27
this is an adobe issue. flash player support actually really, really suks on linux. If you have installed the hardware drivers (system -> administration -> hardware drivers), theirs nothing you can do.

---

### Post by lovinglinux on 2010-07-27
> **mrsleeps said:**
> ok what my problem was when i first tried to get things going is i couldn't watch any video's while i surfing the internet, so i talked to some people online and they said it was more then likely my video card and i'm sure this was part of the problem i have since then bought a video card its a geforce 6 series PNY and i'm running 36bit version on ubuntu and since i'm not a PC gamer and i just surf the net i would think this card would be fine it not please correct me and tell me why. at this point i'm assuming i have the drivers i need for linux with the video card i got but i am not a 100% percent sure or even 50%, so i started thinking maybe my its my flash player so i started downloading like crazy hoping to god something would work i downloaded real player for linux i downloaded and flash plugin for linux at the adobe site i downloaded something for java i mean at this point i'll do almost anything just to get it to work i love this system it works well i'm just completely lost as to what i should do who can lead me in the right direction, i can't even seem to find out how to take programs off my computer that i downloaded trying to fix the problem and that only made it worse because now when my windows open i can't even see the whole page now i mean i just need some help SOMEONE PLEASE POINT ME IN THE RIGHT DIRECTION! i just want to be able to surf the net without fighting my computer.

> **mrsleeps said:**
> ok i have a flash player and its version 10.1.53.64 it wasn't a package at all i just figured i didn't have the right thing and started surfing the net to find something that would work since i can't find what i need in the software center not to say its not there but i have no idea what i'm looking for exactly so i could spend all day just downloading stuff that won't help so i googled linux flash player downloads and this is the page i downloaded everything from [https://addons.mozilla.org/en-US/firefox/browse/type:7](https://addons.mozilla.org/en-US/firefox/browse/type:7) and i downloaded everything that would go on linux and was hoping something good would happen because like the title says i'm completely lost with this, love linux though want to figure it out. if anymore info is needed on my part just let me know and i will get it to you. i didn't think it would be so hard just to be able to surf the net.

I'm intrigued. Is there a particular reason why you don't use punctuation and upper case letters? I couldn't finish reading your posts.

---

### Post by ThesaurusRex on 2010-07-27
> **lovinglinux said:**
> I'm intrigued. Is there a particular reason why you don't use punctuation and upper case letters? I couldn't finish reading your posts.

They're readable, just pretend that someone's talking really fast to try to get your help.

Anyway, as far as Flash on linux goes, I usually just install Gnash instead. On Ubuntu, you can just type: ```
sudo apt-get install gnash-plugin
``` and it will work for either Firefox or Chromium. Or you could just go to the software repositories and find it. Have you restarted your computer since you installed Flash? Try that first, it often helps to refresh your plugins and such.

---

### Post by lovinglinux on 2010-07-27
> **ThesaurusRex said:**
> Anyway, as far as Flash on linux goes, I usually just install Gnash instead. On Ubuntu, you can just type: ```
sudo apt-get install gnash-plugin
``` and it will work for either Firefox or Chromium. Or you could just go to the software repositories and find it. Have you restarted your computer since you installed Flash? Try that first, it often helps to refresh your plugins and such.

I wouldn't recommend gnash. I have already assisted tons of users with flash problems due to gnash or swfdec.

---

### Post by li(fe)sp on 2010-07-27
you might wanna settle with flash...not gnash..

I am assuming in your attempts to make things work you might have installed every possible thing thats out there.

I recommend you clean it first..use synaptic manager and search for flash..see what are all the stuff u have installed...usually you'll have a clear description....

uninstall all of them..and then install flash

---

### Post by Jazzy_Jeff on 2010-07-27
> **lovinglinux said:**
> I'm intrigued. Is there a particular reason why you don't use punctuation and upper case letters? I couldn't finish reading your posts.

Just take a couple of shots of tequila before you read :D .

---

### Post by candtalan on 2010-07-27
> **Zeike said:**
> The easiest and most error free way to install flash is by installing the 'flashplugin-installer' package from the repositories.

The Ubuntu Restricted Extras package from the Software Centre (or add remove programs) includes flash I believe.

---

### Post by mrsleeps on 2010-07-27
ok here is what i got for system info once again if you need more let me know. for one i'm running ubuntu 10.04 my CPU is old and i know it, its a AMD Athlon with a freq of 1000.334, i have a total memory of 1254 MiB, my sound card is old to but i can't remember that i think its a sound blaster though. it doesn't matter at all what i do with full screen or making it small, its just choppy whenever i open a window that has a video on it.

---

### Post by mrsleeps on 2010-07-27
how do i uninstall programs on ubuntu i can't figure out how.

---

### Post by mrsleeps on 2010-07-27
yes there is a reason actually, normally when i have a little time to try to get help on these things its in the morning before work and that leaves me like 15 mins to try to get it all out on the screen before i have to leave and won't be able to mess with it til i get home but, most of the time when i get home i don't have a lot of time to deal with it although i'm really trying to make time so a lot of the time i rush through making sure it makes some kind of sense and take off to work. like they said just imagine someone talking really fast, either way thats why.

---

