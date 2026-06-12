---
title: "streaming audio from ubuntu?"
date: 2013-12-18
forum: Networking &amp; Wireless
---

### Post by manchild63942 on 2013-12-18
I've ben trying to figure this out for a while now but can't find anything. I live in a house with paper thing walls and like watching tv but my sister on the otherside of a wall complains about the sound. i was wondering if there would be anyway to stream audio from my desktop (xubuntu 12.04) to my tablet (nexus 7) so i don't have to run another cable across my room

---

### Post by papibe on 2013-12-18
Hi manchild63942. Welcome to the forum ):P
> **manchild63942 said:**
> i was wondering if there would be anyway to stream audio from my desktop (xubuntu 12.04) to my tablet (nexus 7) so i don't have to run another cable across my room

Sure. Here are some options:
[LIST]
[*]Mediatomb on the desktop, and any UPnP app on Android (UPnPlay for instance).
[*]PlexMediaServer on the desktop, and either the tablet's web browser or the Plex client app (not free).
[*]Subsonic (similar to Plex).
[*]
[/LIST]
> **manchild63942 said:**
> I live in a house with paper thing walls and like watching tv but ...
I don't understand how this fit with your other request. Wireless headphones seem to be the best option for this situation.

Hope it helps. Let us know how it goes.
Come here often and have fun.
Regards.

---

### Post by manchild63942 on 2013-12-19
Thanks for the welcome.

I figured it out. I used Media tomb. Doesn't do exactly what I want but that is probably lack of experiance. What I did was ran what I was watching on both (kind of defeats the purpose but it works)

For future referance so anyone else intrested could figure it out for the video I used to install and configure mediatomb. 
[http://www.youtube.com/watch?v=Vj3aQX9TvMw](http://www.youtube.com/watch?v=Vj3aQX9TvMw)
The site it shows is dead but heres how it goes

sudo apt-get install mediatomb

sudo gedit /etc/mediatom/config.xml


change the following line
from
<ui enabled="no" show-tool tips="yes">
to
<ui enabled="yes" show-tool tips="yes">

and add change
<transcoding enabled="no">
to
<transcoding enabled="yes">

then save and run the command
sudo /etc/init.d/mediatomb restart

after that everything should be able to work through the GUI in your browser. The program is multimedia and not internet (I made that mistake).

From there on you just go through your filesystem tab and select what you want streamable

---

