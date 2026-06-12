---
title: "firefox crashing in pogo games"
date: 2010-12-23
forum: New to Ubuntu
---

### Post by gmenfan83 on 2010-12-23
when i try to play online pogo games i can only get so far and firefox crashes...any suggestions as to why?

---

### Post by earthpigg on 2010-12-24
hi,

has it worked in the past? when you first installed ubuntu, what did you have to do to get it to work?

until very recently, my mother spent a lot of time on pogo and i picked up a few tricks relating to ubuntu+pogo over the years.

---

### Post by gmenfan83 on 2010-12-24
> **earthpigg said:**
> hi,

has it worked in the past? when you first installed ubuntu, what did you have to do to get it to work?

until very recently, my mother spent a lot of time on pogo and i picked up a few tricks relating to ubuntu+pogo over the years.
well i have been using ubuntu for about 3 months but have just now went ahead and tried to play pogo ...scrabble in general and it acts very weird ,either it stops responding or crashes my browser right in the middle of set up for the game or play

---

### Post by sammiev on 2010-12-24
All games on pogo seem to work fine here. My kids play them often. Ran into a bug a while back with 2 java versions installed at the same time. Icedtea-java doesn't work with pogo. GL :)

---

### Post by earthpigg on 2010-12-24
yup, poster above me is correct.

search for 'iced' in the software center, and remove 'icedtea java browser plugin'. if i recall correctly, that's all i had to do for my mom.

---

### Post by DijitalX on 2010-12-28
I have the same issue.  When I open up the error console in Firefox there is the following error, which may relate to the issue (I have no idea how to fix it).

Error: Permission denied for <http://ad.doubleclick.net> to call method Location.toString on <http://game3.pogo.com>.

I also have icedtea and sun java 6 plugin as well as openjdk all installed.

---

### Post by gmenfan83 on 2010-12-28
thank you guys for the suggestions ..will try to remove icedtea  java

---

### Post by sammiev on 2010-12-28
> **DijitalX said:**
> I have the same issue.  When I open up the error console in Firefox there is the following error, which may relate to the issue (I have no idea how to fix it).

Error: Permission denied for <http://ad.doubleclick.net> to call method Location.toString on <http://game3.pogo.com>.

I also have icedtea and sun java 6 plugin as well as openjdk all installed.

I had to remove icedtea java for pogo to work. GL :)

---

### Post by gmenfan83 on 2010-12-28
> **sammiev said:**
> I had to remove icedtea java for pogo to work. GL :)
does anyone know if removing iced tea java would have any adverse effects on anything?

---

### Post by earthpigg on 2010-12-29
> **gmenfan83 said:**
> does anyone know if removing iced tea java would have any adverse effects on anything?

nope.

remove the icedtea package.

---

### Post by gmenfan83 on 2010-12-29
> **earthpigg said:**
> nope.

remove the icedtea package.
cool thanks

---

