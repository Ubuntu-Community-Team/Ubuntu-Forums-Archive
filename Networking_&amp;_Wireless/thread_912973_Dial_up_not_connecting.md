---
title: "Dial up not connecting"
date: 2008-09-07
forum: Networking &amp; Wireless
---

### Post by Winston_Smith on 2008-09-07
I have a Dell Inspiron 2200 that I have just installed Ubuntu on. I downloaded the dell Conexant drivers and installed them, it looked like everything went ok.

I then setup my connection in the networkadmin, found under the administration menu. I have setup my connection, number, username, password all that. But when I go to connect It goes through the normal annoying noise but then it goes silent. I'm not real sure how to check to make sure if it's connected or not. I assume it would show up as having a network connection in the network status icon in the top right.

Could someone please help me out with this? Up in the sticks I only can get dial up, I'd like to start using linux more.

---

### Post by Shazaam on 2008-09-07
When your modem stops the handshake noise it usually means you are connected. The only way to tell is by trying to surf the net/update your pc or by picking up a phone and listening to the noise.
BTW, if you set up your connection in Network Manager it will default to connect when you bootup your pc (or on demand if you have that set up). To have a regular gui connect app install gnome-ppp or kppp if using kubuntu. I think gnome-ppp is on the livecd so add the cd to your sources list- System>Administration>Software Sources.
You can also use wvdial (command line app) to connect.

---

### Post by Winston_Smith on 2008-09-07
Ok I'll give that a go then.

I did trying to browse but Firefox was not connecting. I'll try adding in the cd and installing that program.

---

### Post by Winston_Smith on 2008-09-07
I have it figured out now, turns out I'm just an idiot lol. I was trying to browse with firefox, but it kept saying it was offline. Well it was in offline mode, so click it over to online mode and it works fine now. I typed out this reply from my now internet enabled Ubuntu.

I figured it out after I pinged google, which I should have done right off anyway. I saw that pinging google was working so I did have an internet connection, just firefox was not working.

---

