---
title: "help with tor &quot;im a noob&quot;"
date: 2010-12-16
forum: New to Ubuntu
---

### Post by therealstig on 2010-12-16
Hi ,
I like to start with saying i love ubuntu.
I just installed tor in my firefox browser, ive got the tor buttun "tor disabled or tor enabled" on the bottom right on my screen, but when i enable tor it wont let me connect to any web sites saying proxy server is refusing connections.
I included a screenshot in an attach so you can see.
Thanks for looking hope somone can help!

---

### Post by Darkade on 2010-12-16
You have to have tor and vidalia installed. You should add the official tor repos. More instrucctions can be found [here]("https://www.torproject.org/docs/debian")


But it's not hard.
1) Install tor/vidalia.
2) Configure Polipo (or not)
3) Configure TorButton

Polipo is an HTTP Proxy, you should configure tor with polipo if you want to use tor with software that does not support Socks Proxies

---

### Post by therealstig on 2010-12-16
cheers buddy for the reply, so i think im in but what does this in the terminal mean?

---

### Post by therealstig on 2010-12-16
heres the screenshot

---

### Post by bodhi.zazen on 2010-12-16
See:

[http://bodhizazen.net/Tutorials/TOR](http://bodhizazen.net/Tutorials/TOR)

Or if you prefer , try the tor browser bundle

[http://www.torproject.org/projects/torbrowser.html.en](http://www.torproject.org/projects/torbrowser.html.en)

It is available cross platform =)

---

### Post by bodhi.zazen on 2010-12-16
> **therealstig said:**
> heres the screenshot

That is a Qt error, and my guess is you are not running KDE =)

From your screenshot it appears tor is working as expected.

---

### Post by SirGrant on 2010-12-16
You have to configure the browser proxy right.  Right click on the torbutton and select preferences.  Your settings should look like this.  For some reason the default settings are wrong.

---

