---
title: "here we go again...  internet in linux blows"
date: 2006-10-01
forum: Networking &amp; Wireless
---

### Post by Bubs on 2006-10-01
ok I got a dell c400 on ebay(cheap!!)

but I go to plug an internet cable into it (don't have a wireless card yet, but it's on it's way) but it doesn't work.  I go to activate it useing dhcp and it says it's activated but it defaults to lo so I try to turn it to eht0 and click ok but as soon as I hit ok it goes back to lo.  I even grabbed the cable from my main box to see if it was the cable.

it seems to recognize my card but it doesn't activate it...  this is the same problem I had with the HP I had and never found out how to fix it. ](*,)   I think I'll bring this to school sometime and see if it is just my apartment and router. but Ubuntu on the hp worked for months but then one day just up and quit working :mad: 

so like I said here we go again...  can anyone help me?  better yet does anyone live in or near the Indianapolis, Indiana area that could help me out personally?  just a thought...  or know of or any members of a lug around here?

---

### Post by dmizer on 2006-10-01
need to have a lot more information.

first of all, post the output of lspci, ifconfig, dmesg | grep eth0, and post the contents of your /etc/network/interfaces

---

### Post by MetalMusicAddict on 2006-10-01
Why can't people post without being derogatory?

---

### Post by Bubs on 2006-10-02
@dmizer - I'll post all of that stuff later tonight I have to work today but wehn I get home I'll post everything

@MetalMusicAddict - it was just to get your attention... and getting a network to work in linux is one of the biggest newbie complaints in linux.  It's hard to do if you don't know what your doing.  and I have this problem a lot so yea it kinda pisses me off.

---

### Post by Iowan on 2006-10-02
> **MetalMusicAddict said:**
> Why can't people post without being derogatory?Because the "I'm gonna quit" and "Ubuntu Stinks" posts get noticed (like the screaming kid in the grocery store). I usually bite my tongue (or keyboard) and go to the next post, cuz what I'd post wouldn't be productive.

---

### Post by MetalMusicAddict on 2006-10-02
> **Bubs said:**
> @MetalMusicAddict - it was just to get your attention... and getting a network to work in linux is one of the biggest newbie complaints in linux.  It's hard to do if you don't know what your doing.  and I have this problem a lot so yea it kinda pisses me off.
So you think saying "Hey, you suck! Can you give me a hand?" is the best way to go about things? You gotta be a youngster or immature and you still didnt get an answer out of this.

Also, next week you'll have a new "getting [SIZE="1"][COLOR="Grey"](insert situation here)[/COLOR][/SIZE] to work in linux is one of the biggest newbie complaints in linux" problem.

Please ask in a straightforward manner. You will get more help that way. If you dont understand, read and search the forum. PM'ing someone who also had a simular problem is also a way to go.

You get what you give here, and in life.

---

### Post by Bubs on 2006-10-02
Damn I didn't mean to be offinsive I just stated a little frustration.

Jeez guys I Usually try to find answers myself but I have no Idea what to do when it comes to networking, so I thought I'd ask here and since this is a frustrating issue for me I let it out in the title.  I dind't mean to offend OR be derogatory I like Ubuntu and when everything works it's great I've been using it on another laptop of mine for about a year and the internet just hooked right up for me no problem.  

shit sorry my title was rude.  

y'all take things a little to seriously...

chill out, dudes

---

### Post by bluenova on 2006-10-02
I don't see anything wrong with your post Bubs. I think someone needs to get out more.

---

### Post by darth_vader_ca on 2006-10-02
why dont you statically set your IP, are you behind a router right now, or on cable mdm or dsl?

---

