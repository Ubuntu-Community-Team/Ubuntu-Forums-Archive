---
title: "Network Proxy settings work in Firefox, but not other programs"
date: 2007-12-02
forum: Networking &amp; Wireless
---

### Post by ugm6hr on 2007-12-02
I am a happy Ubuntu 7.10 user.  At home, my internet access works 100% via either ethernet or wifi ADSL router.

I have "discovered" the proxy settings for my work network, and found that entering them in the Firefox Network Preferences allows Firefox to connect to both my work Intranet (with no proxy settings) as well as the internet (with proxy settings).

However, entering the same proxy settings in Preferences->Network Proxy does not allow GAIM or Synaptic Package Manager to connect.  Interestingly, Thunderbird doesn't connect either, with the same settings in its Preferences.

Has anyone else encountered this?

My proxy settings are as the attached screenshot for Firefox.  At work, the Domain is **ITNTDOM1**, and I obviously know my username and password.

---

### Post by gpredrag on 2007-12-02
If your proxy requires authentication, you should also set credentials in Preferences->Network Proxy. Then all gnome apps would use it.
Synaptic has it's own settings, thunderbird also.

---

### Post by ugm6hr on 2007-12-02
> **gpredrag said:**
> Synaptic has it's own settings, thunderbird also.

Using the same settings in Thunderbird as work in Firefox does not work though.  Hence my confusion.  In fact, Thunderbird asks for my username and password when it tries to authenticate - but it does not connect, unlike Firefox.  Firefox works with **username** and password.

Synaptic requires you to enter the authentication settings prior to attempting connection (as does Gnome Network Proxy).  However, whether I use **username** or **Domain\username** with my password, they don't connect.

So my question is - why the difference between Firefox and Thunderbird?  And also - why does Synaptic / Gnome not work, despite using the same settings.

Importantly, when I enter the same settings in Firefox in Windows, it doesn't connect.  So presumably there is some kind of network protection preventing non-work computers from connecting.  But why does Firefox manage to connect then (and only in Linux - not Windows)?

---

### Post by EdThaSlayer on 2008-02-23
The same thing is happening to me, I have tried to connect via the system settings(I'm using Kubuntu by the way) and put the proxy settings in all correctly with the user name and all, but it just wont connect. Because of this, I can't install the apps I want and have to use Ebuddy for all my im'ing needs. Still researching on this though, will report back to this thread later. I'm using Firefox at the moment and the internet works smoothly with Firefox.

EDIT:

Maybe this thread could help you, 
[http://ubuntuforums.org/showthread.php?t=183093&highlight=proxy+only+works+with+firefox](http://ubuntuforums.org/showthread.php?t=183093&highlight=proxy+only+works+with+firefox)

---

### Post by ugm6hr on 2008-02-24
I have moved job locations since then, and haven't had to try connecting my home laptop to my new work network yet.

Hope you work this out though, cos it still bugs me!

---

