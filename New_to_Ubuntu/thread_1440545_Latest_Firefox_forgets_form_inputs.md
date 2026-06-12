---
title: "Latest Firefox forgets form inputs"
date: 2010-03-27
forum: New to Ubuntu
---

### Post by Tryer(ForLife) on 2010-03-27
hello everyone

well i downloaded firefox 3.6.2 and from what i understand i don't install it i just run it the way it is, and it works great. Only thing that kinda anonys me is that it doesn't remember form inputs, when i restart ubuntu everything's gone from forms, so i have to type my usernames and email every time i login somewhere. I copied the firefox folder to \usr\firefox so that it kinda looks like it's installed;), and i had to copy it there as root, could that be the problem maybe? and it's not the settings they are ok, rest of the history seems to be ok, i see sites i visited before but forms are disappearing.

---

### Post by Pollox on 2010-03-28
A few questions:
Does it just not remember the form inputs you had saved before installing 3.6, or is it not remembering them at all now? (I'm sure you double checked the "save form data" box is still checked, right?)
If you reinstall the old firefox from the repositories, does it work again, i.e. is all your old form data back?
Have you tried installing firefox 3.6 from a .deb?  I'm not sure where you'd get one, maybe the Mozilla daily build?

Just some ideas to try.  Good luck.

---

### Post by Tryer(ForLife) on 2010-03-28
thanks for your reply, it's actually both, it didn't remember the ones before, and every new one that i enter since install are also not remembered, and yes "save form data" is checked. I now did a "complete upgrade" i don't know how else to call it, when i run *firefox* command from terminal i go to the 3.6.2 version, before when i just had the downloaded version and a link to firefox in that folder,  if i ran the command i would go to the old 3.0.X or whatever it was. i followed this
[http://www.techdrivein.com/2010/03/install-latest-firefox-362-in-ubuntu.html](http://www.techdrivein.com/2010/03/install-latest-firefox-362-in-ubuntu.html)

i still have the same bug, i know it's not anything big, but it's an anomaly and i wanna know why it's happening :D. I also think that maybe cache isn't being used, cause i visit my usual sites and i spend a lot more traffic then before.

weird.

---

### Post by l.billon on 2010-03-28
Hi!
I do not have such problems with the latest version installed from the Daily Team PPA, maybe you should try it.

---

### Post by Tryer(ForLife) on 2010-03-28
> **l.billon said:**
> Hi!
I do not have such problems with the latest version installed from the Daily Team PPA, maybe you should try it.

could you please give me a link to that, i have no clue what you are talking about...
thanks...

---

### Post by l.billon on 2010-03-28
Hi!
The Firefox Daily Build PPA:
I detailed the process in the first part of this article:
[http://pausehitech.com/2010/03/28/max-your-firefox-experience-in-ubuntu/](http://pausehitech.com/2010/03/28/max-your-firefox-experience-in-ubuntu/)

---

### Post by Tryer(ForLife) on 2010-03-28
when i run this

sudo add-apt-repository ppa:ubuntu-mozilla-daily/ppa


i get this error

me@Heaven:~$ sudo add-apt-repository ppa:ubuntu-mozilla-daily/ppa
sudo: add-apt-repository: command not found
me@Heaven:~$ 

what's wrong?

---

### Post by l.billon on 2010-03-28
Which version of ubuntu do you have?
It should work great in karmic.

---

### Post by Tryer(ForLife) on 2010-03-28
i have 9.04 jaunty, does this mean it won't work for me?

i don't know anymore, i will try and use it like this and see how it goes.
but if all else fails i will switch to opera....

---

### Post by l.billon on 2010-03-28
Isn't upgrade an option?
 if not, add this source:
```
deb [http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu) karmic main 
deb-src [http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu) karmic main 
```
It has the same effect as using add-apt-repository, but doesn't fetch the security key

---

### Post by Frogs Hair on 2010-03-28
> **Tryer(ForLife) said:**
> i have 9.04 jaunty, does this mean it won't work for me?

i don't know anymore, i will try and use it like this and see how it goes.
but if all else fails i will switch to opera....

Hi, [http://www.ubuntugeek.com/how-to-install-firefox-3-6-stable-from-ubuntu-ppa](http://www.ubuntugeek.com/how-to-install-firefox-3-6-stable-from-ubuntu-ppa)

[URL="http://www.ubuntugeek.com/how-to-install-firefox-3-6-stable-from-ubuntu-ppa"]
[/URL]

---

### Post by Tryer(ForLife) on 2010-03-28
> **Frogs Hair said:**
> Hi, [http://www.ubuntugeek.com/how-to-install-firefox-3-6-stable-from-ubuntu-ppa](http://www.ubuntugeek.com/how-to-install-firefox-3-6-stable-from-ubuntu-ppa)

[URL="http://www.ubuntugeek.com/how-to-install-firefox-3-6-stable-from-ubuntu-ppa"]
[/URL]

**[SIZE=2]Error 404. You're looking for something that isn't here[/SIZE]**



hey, i just deleted all the versions of firefox and everything related to firefox from synaptic and installed the old version back (actually i selected 3.5 version but i got 3.0.2. :() and i'm gonna just leave it the way it is, i got all my history and forms and everything back, and i hope it will work ok now. 

thank you all for your suggestions, but it wasn't meant to be...;)

---

