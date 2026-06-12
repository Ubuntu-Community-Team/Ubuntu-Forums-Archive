---
title: "[SOLVED] Streaming Divx movies?"
date: 2008-12-11
forum: New to Ubuntu
---

### Post by germanix on 2008-12-11
Hi, I have Ubuntu 8.10 installed. I found a site on the Internet where I can stream/watch movies. These movies are either Flash or Divx. I can watch the movies which are "Flash" but most are only playable in Divx, and will not play. I am told to download the latest Divx player but it is only offered for Windows. I do have the VLC player installed which can play Divx but it seems that my browser does not know this. Under the button, preferred applications, in Ubuntu, totem movie player is the set standard. Does anyone know how I could get my browser (Firefox) to stream these movies or how to get a divx player that would do it?

---

### Post by taurus on 2008-12-11
What if you install mozilla-plugin-vlc?

```
sudo apt-get update
sudo apt-get install mozilla-plugin-vlc
```
Then, restart firefox.

---

### Post by germanix on 2008-12-11
It seems I already have the latest mozilla-plugin installed
I just realised that the Vlc player is not installed. Cannot seem to find it under add/remove. Where/how do I find this?
oops, wrong again, it is installed, found it under the package manager.

---

### Post by taurus on 2008-12-11
Do you mean the vlc plugin?  It's not installed by default when you install vlc.  Also, you should consider removing the totem plugin from the list so vlc plugin would be a default video player with firefox.

You can also change the default in Edit -> Preferences -> Applications.

---

### Post by germanix on 2008-12-11
The vlc player and the plug-in is installed. The defaults are set as vlc player. Now when I try to run the movie I get this notice:
A text/html decoder plug-in (which is not installed) is required to see this movie

---

