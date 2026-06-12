---
title: "rtorrent &quot;on_finished&quot; does not exist"
date: 2010-02-24
forum: New to Ubuntu
---

### Post by lautarop on 2010-02-24
Hey guys, I've been trying to get this rtorrent working

I compiled rtorrent 0.8.6 from svn using this guide [http://www.howtoforge.com/how-to-compile-rtorrent-from-svn-in-ubuntu-9.10-karmic-koala-debian-5-lenny-with-magnet-link-support](http://www.howtoforge.com/how-to-compile-rtorrent-from-svn-in-ubuntu-9.10-karmic-koala-debian-5-lenny-with-magnet-link-support) BUT ONLY with the patch for colors


But for some reason, when I put in my config

on_finished = move_complete,"d.set_directory=$d.get_custom1= ;execute=mv,-n,$d.get_base_path=,$d.get_custom1="

I can't execute rtorrent, I get the message
"on_finished" does not exist.

If I erase the line with the on_finished thing, It starts up.


any ideas?

---

### Post by ubudog on 2010-02-24
Do you have to use rtorrent?  Transmission that comes with Ubuntu is pretty good.

---

### Post by kmsalex on 2010-02-24
> Do you have to use rtorrent?  Transmission that comes with Ubuntu is  pretty good.

no magnet url's :(

---

### Post by lautarop on 2010-02-24
> **ubudog said:**
> Do you have to use rtorrent?  Transmission that comes with Ubuntu is pretty good.

i don't like it, it lacks features.

Now I got the solution, it was a dumb one: The command is deprecated (they should update the manual on the site)

the new one is:

[PHP]system.method.set_key = event.download.finished,move_complete,"execute=mv,-u,$d.get_base_path=,$d.get_custom1= ;d.set_directory=$d.get_custom1="[/PHP]



thx everybody, thread's solved

---

### Post by sircolin on 2011-03-13
> Now I got the solution, it was a dumb one: The command is deprecated (they should update the manual on the site)
Hmm.. yes they should i compiled rtorrent 0.87 from source and have been searching for the answer for two days, thanks to you it's solved now

---

### Post by ubudog on 2011-03-13
Transmission may still lack features you want, but at least it came out with magnet links now... :-)

[http://lifehacker.com/#!5454790/transmission-bittorrent-client-updates-to-support-magnet-links-and-more](http://lifehacker.com/#!5454790/transmission-bittorrent-client-updates-to-support-magnet-links-and-more)

---

