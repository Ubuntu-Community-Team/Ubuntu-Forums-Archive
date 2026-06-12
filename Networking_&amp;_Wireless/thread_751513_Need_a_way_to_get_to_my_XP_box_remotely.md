---
title: "Need a way to get to my XP box remotely"
date: 2008-04-10
forum: Networking &amp; Wireless
---

### Post by DianeHelen on 2008-04-10
So, maybe my last big hurdle, before I can accept taking a smaller PC when I travel, the new Asus EEEPC I bought today, with Linux, of some flavor or another.. is my need to connect thru the internet, from wherever I am, back to my XP Media Center Box, back home.(odly Media Center supports Remote access, like XP Pro, while Home does not)

I have tried GoToMyPC, adn while it does let me log on, after I did some Java update, it gave me a choice of 3 plugins, I chose the first, 

But when I do get to log on, thru the Universal Viewer, I have no control of any of my desktop icons, or taskbar.

Currently when I travel, with my XP laptop, I just use Remote Desktop, and have Remote Desktop enabled on the home box, and I have it mapped to a different port.. I just have to log in, and give it the port I set it up on, from the laptop, and voila, Im in and its faster than gotomypc. 

But Id be ok, to use gotomypc IF it worked..

So, any easy, or at least well documented way to accomplish seeing my FULL XP desktop and have use of it, from my Ubunto, or whatever comes on the Asus, that I am getting?


OK GOT IT!

I wound up getting lead to my answer on another post from some kind forum admin.

I was in the right direction, using the Terminal Server Client, but stupidly, I was entering my computer NAME as the prompt said, instead of my IP and port, that should have made ssence at first to me. There is the danger of relying on a gui, its only as good as the prompts whover wrote it gives you.

Anyway, PROBLEM SOLVED! Works well, fast, and Im ready to tackle it on my next business travel trip, to check back to see whats happening back on my home XP box.

Looking foward to a day in the future, to not have to HAVE an XP box to look home to.., but thats a while away.. 

Thanks

Diane

---

### Post by eDRoaCH on 2008-04-11
I see you solved this but I cant resist adding my 2 cents.

First for web based remote access I recomend logmein. It is free, with the only shortcoming being you cant transfer files, but my FTP solves that for me. It also only allows windows as the SERVER, but clients can be any web browser.

If you want to control MCE on the road, google up webguide4. The program absolutely rocks, but it is only an interface to MCE. It has stream support, but in my testing its not good on slow (cell) networks. Still enough to set up that recording you forgot about!

---

### Post by DianeHelen on 2008-04-12
OK, thanks for the info, but Im about to show my noobness, or cluelessness to some of this.

I am familiar with Logmein, but Id rather have some non web base one more step to go thru process, which the termincal client seems fine.

So what is MCE? And What REcording I forgot about..

Again, sorry for seeming so dumb.. Im really NOT :), 

just OLD ;) heeh

---

