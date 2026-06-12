---
title: "Can't connect to Livebox router"
date: 2008-05-30
forum: Networking &amp; Wireless
---

### Post by behindtheeye on 2008-05-30
Hi,

i've just installed 8.04 which went pretty smoothly, and now I'm trying to setup the wireless. Pleasingly it seems to have detected my hardware ok as when I open the network icon it detects my wireless network.

The router is an Orange livebox. I've tried the instructions here: [http://ubuntuforums.org/showthread.php?t=693013&page=2](http://ubuntuforums.org/showthread.php?t=693013&page=2) 
and I'm still unable to connect. If I turn encryption off I can connect but obviously this isn't ideal.

I'm a little confused over the passphrase options in Ubuntu, I'm getting the choice between 3 types of WEP and one called LEAP, nothing mentioning WPA, does this sound normal? I'm also unsure about the "authentication" setting, there is the choice between "open system" and "shared key", I don't know which I should be using. I've tried various combinations of settings with no joy.

Has anyone got any ideas?

Thanks!

---

### Post by behindtheeye on 2008-06-02
Well, after a bit of fuss I fixed it (perhaps not how I originally intended but at least it appears to work!). For reference here's how:

I installed [Wicd]("http://wicd.sourceforge.net/") by unsecuring my wireless network and connecting to it briefly. Wicd replaces the default Ubuntu network tool. I had a little play around with that and was still unable to connect using WPA. So I changed the settings on the key to WEP and then retried. This time it worked!

I'm hoping there are no problems with having WEP instead of WPA. Time shall tell I guess...

---

### Post by okey666 on 2008-08-07
I haven't been able to connect to a livebox with WPA using Wicd either. The reason I switched to it was that NM kept dropping the connection. As far as I know, the only problem with WEP is that it is not as secure.

---

