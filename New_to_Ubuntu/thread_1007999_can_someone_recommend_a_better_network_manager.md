---
title: "can someone recommend a better network manager?"
date: 2008-12-11
forum: New to Ubuntu
---

### Post by tegnoto89 on 2008-12-11
Right now I'm using the ubuntu default, and I get booted off ALL THE TIME.  I know it's not the network, because I never had this problem with windows.  In kubuntu the knetwork manager was a little better but not much.  Are there network managers that are a little bit better?

---

### Post by nothingspecial on 2008-12-11
I always install wicd.

[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

---

### Post by carney1979 on 2008-12-11
Try [http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

It's what I use.

Far, far better than network manager in my humble opinion.

Best of luck.

David

---

### Post by iaculallad on 2008-12-11
+1 to Wicd. It has an intuitive GUI for configuring both wired and wireless interface.

---

### Post by tegnoto89 on 2008-12-11
Actually one step ahead of you.  I looked at some old posts and downloaded wicd but Wicd isn't connecting me at all.  It said I had to use encryption (my college requires it) so I enabled encryption.  My provider says to use PEAP, so I did PEAP with GTC because PEAP with TKIP has another field to fill out for authentication that I don't have information for.

I go to connect and when it gets to "validating authentication" it just stops.

---

### Post by tegnoto89 on 2008-12-11
the university offers a slower connection that doesn't require encryption and that works fine... so it must be the security features that are messing it up, right?

This is what the technology service department gives me in terms of requirements for linux:

    *  WPA-1 protocol (WPA).
    * TKIP session encryption.
    * PEAP authentication type.
    * MSCHAPv2 password encryption.
    * AuthServers secure1.syr.edu;secure2.syr.edu; 

These settings are NOT required for AirOrangeX and can be ignored:

    * Anonymous Identity
    * Client Certificate File
    * CA Certificate File
    * Private Key File
    * Private Key Password 


PLEASE help me, I haven't had a solid internet connection since I went to linux.

---

