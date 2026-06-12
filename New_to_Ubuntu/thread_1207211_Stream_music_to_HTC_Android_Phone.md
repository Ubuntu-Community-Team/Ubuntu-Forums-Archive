---
title: "Stream music to HTC Android Phone"
date: 2009-07-07
forum: New to Ubuntu
---

### Post by abhiroopb on 2009-07-07
So, I may be purchasing an HTC G1 quite soon and I would like to be able to stream my 11,000 songs over the internet and to my HTC G1.

What apps would I need on the phone (i.e. Android apps) and what would I have to do in Ubuntu?

Obviously I'd prefer the simplest solution, but I am not scared to poke around in the terminal if that does provide an easier alternative.

Many thanks!

---

### Post by nhasian on 2009-07-08
Give [Vibe Streamer]("http://www.raymond.cc/blog/archives/2009/06/29/create-jukebox-server-and-stream-mp3-over-network-or-internet-with-free-vibe-streamer/") a try.

---

### Post by abhiroopb on 2009-07-08
this does not appear to be a ubuntu/linux application...? Will it work in ubuntu? Thanks

---

### Post by tgalati4 on 2009-07-08
sudo apt-get install mt-daap

Install fireplay on the server (google for instructions)

Open a brower on the phone and point to:

yourserverwithyourmusic:3689/

yourserverwithyourmusic:3689/FirePlay.html

And see what you get.  Works well on a Nokia n800.

---

### Post by abhiroopb on 2009-07-08
Sounds good but is there an app I could use in Android that would work? Keeping the browser pointed to that one page seems a bit of a pain!

---

### Post by nhasian on 2009-07-08
maybe you can use Edna instead?  [http://edna.sourceforge.net/](http://edna.sourceforge.net/)

---

### Post by tgalati4 on 2009-07-08
Someone would need to write a native app to talk to the mt-daap server.  Or make an existing G1 music player daap-aware.

---

### Post by abhiroopb on 2009-07-09
I actually assumed there was something similar to ORB for ubuntu/android...

[http://www.orb.com/](http://www.orb.com/)

---

### Post by DeeMenace on 2009-08-08
you could use gmote it will stream mp3s and is available in the app market.

---

### Post by abhiroopb on 2009-08-08
> **DeeMenace said:**
> you could use gmote it will stream mp3s and is available in the app market.

I have been using gmote, but it only seems to work if I am connected in the same wireless network. How would I use it if I was out of my house and using the 3G network?

---

### Post by midwesterndirt on 2009-08-15
> **abhiroopb said:**
> I have been using gmote, but it only seems to work if I am connected in the same wireless network. How would I use it if I was out of my house and using the 3G network?

Open Gmote, go to server list, wait a few seconds, it will ask you for an IP. You can put the public IP of your home computer or router (in which case, you would need to forward port 8889 to your computer). If you have DynDNS, you can type in your dynamic domain name instead.

I works beautifully over 3G. I can't even believe this kind of technology exists.

---

### Post by abhiroopb on 2009-08-16
port forwarding is always a pain :(...never really works for me. Will have to give it a go though I guess.

---

