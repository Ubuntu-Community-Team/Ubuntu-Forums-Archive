---
title: "DAAP music sharing - Win to Ubuntu"
date: 2007-04-03
forum: Networking &amp; Wireless
---

### Post by radicalbeatz on 2007-04-03
I am setting up a small (Compaq iPaq) computer to use as a sort of music server for my church. The rest of the network is on windows. This is my first foray in to linux, so I choose ubuntu.  But I need help with two things:

1. If I remember correctly, iTunes doesnt allow DAAP music sharing across networks to media players other then itunes itself. Does iTunes successfully emulate under Wine?

and 

2. If not, what media player should I use (I was thinking Banshee or Songbird) to get around this? Since other people that are used to using iTunes are going to be using this, the program has to look and feel remotely like iTunes.

---

### Post by spd106 on 2007-04-03
For the server side there's [Firefly Media Server]("http://www.fireflymediaserver.org/") or [Tangerine]("http://www.snorp.net/log/tangerine"), both have windows support though I doubt they'll run on an ipaq without modification.

On the Ubuntu side of things what's wrong with Rhythmbox?

---

### Post by sloggerkhan on 2007-04-03
I see itunes share fine on rhythmbox, though I don't know if they see me.

---

### Post by reacocard on 2007-04-06
> **radicalbeatz said:**
> I am setting up a small (Compaq iPaq) computer to use as a sort of music server for my church. The rest of the network is on windows. This is my first foray in to linux, so I choose ubuntu.  But I need help with two things:

1. If I remember correctly, iTunes doesnt allow DAAP music sharing across networks to media players other then itunes itself. Does iTunes successfully emulate under Wine?

and 

2. If not, what media player should I use (I was thinking Banshee or Songbird) to get around this? Since other people that are used to using iTunes are going to be using this, the program has to look and feel remotely like iTunes.

1) iTunes does allow other players to access it, but iTunes 7 implemented some changes in the protocol that haven't been reverse-engineered yet, so no non-iTunes 7 player can connect to an iTunes 7 share (yet). Also, iTunes under wine isn't good. At all.

2) [Tangerine]("http://www.snorp.net/log/tangerine"). It can even read the libraries of several linux media players to know what songs to share, so it's a perfect solution. I have an edgy package patched for Exaile support in my repo (see my sig), and it also supports Amarok, Rhythmbox, LSongs, and Banshee, so you can choose whatever player you think best. Rhythmbox is probably closest to iTunes for interface, and is the Ubuntu default media player. Banshee is also good.

---

