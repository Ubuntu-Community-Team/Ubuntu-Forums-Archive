---
title: "Ubuntu Will Not Connect to the Internet"
date: 2009-01-07
forum: New to Ubuntu
---

### Post by Dragon M. on 2009-01-07
Just today, I got Comcast internet.  At first, only only of my PCs with Windows Vista could connect.  I eventually did SOMETHING to get another computer with Windows XP and a laptop with Windows Vista to work with my base station.

Now on my laptop and my desktop computer with Vista, I have Ubuntu freshly installed two days ago.  I've used Ubuntu before, except with versions much older.  Back then, I had a DSL connection, and all was fine.

Now, Windows can connect to the base station and automatically configure the settings.  When Ubuntu tries, it'll say it's looking for an address.  Then it will say "The network connection has been disconnected." without connecting at all.

I tried manually inserting the information and it'll say it's connected.  But there's no connection.  I'm quite positive it has nothing to do with Comcast, because I cant even connect to my base station administrator panel either with the given URL.

Any help would be appreciated.  Thanks!

---

### Post by linuxisevolution on 2009-01-07
I had the *EXACT* same problem. I had to go to system >> administration >> network and click properties and change to "dhcp". If dhcp doesn't work try roaming mode. It is a simple networking problem, not an Ubuntu one. You could try right clicking on the little networking thingy, and select your network device to activate it, or left click to enable networking. Worked for me, and no command line :D

---

### Post by 73ckn797 on 2009-01-07
Agree with above post. DHCP set to auto works for my cable modem system. I am wired to the router.

---

### Post by linuxisevolution on 2009-01-07
I am wired, too. Never tried wireless with Ubuntu.

---

### Post by Dragon M. on 2009-01-07
That sounds like Ubuntu 8.04.

I am using Ubuntu 8.10 though...  it's vastly different.

[IMG]http://i261.photobucket.com/albums/ii74/dragonmxx000/screeny.png[/IMG]

That's how it's set right now, but it doesn't work.

---

### Post by 73ckn797 on 2009-01-08
> **Dragon M. said:**
> That sounds like Ubuntu 8.04.

I am using Ubuntu 8.10 though...  it's vastly different.

[IMG]http://i261.photobucket.com/albums/ii74/dragonmxx000/screeny.png[/IMG]

That's how it's set right now, but it doesn't work.

I am running 8.10 also. My screen matches what you show. What does the info show under the wired tab? Is there a mac address? What is the mtu showing?
What is the security setting tab show? I do not have security enabled through Ubuntu but via the router.

---

### Post by Dragon M. on 2009-01-08
Security is off.

[IMG]http://i261.photobucket.com/albums/ii74/dragonmxx000/Screenshot-EditingAutoeth0.png[/IMG]

---

### Post by Dragon M. on 2009-01-12
It's been a few days and wondering if anyone else has any solutions?

---

