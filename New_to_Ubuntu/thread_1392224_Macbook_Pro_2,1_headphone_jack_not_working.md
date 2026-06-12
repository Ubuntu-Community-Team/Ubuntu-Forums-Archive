---
title: "Macbook Pro 2,1 headphone jack not working?"
date: 2010-01-27
forum: New to Ubuntu
---

### Post by cabse7en on 2010-01-27
Hey guys,

I just installed Ubuntu 9.10 on my MacBook Pro 2,1 running in Dualboot with Mac OS Leopard and the internal speakers have been working great, however the headphone jack just isn't working. I've done a bunch of research and still haven't found a solution.

I tried installing updated alsa drivers and libraries but the jack is still not functioning. Forgive me for my ignorance as I'm new to Linux and Ubuntu, but I'd really like to solve this problem because I absolutely love the OS. Thanks for the help!

---

### Post by cabse7en on 2010-01-27
Any ideas? This is killing me and I'm all out of options :(

---

### Post by ramjet_1953 on 2010-01-27
Hi,There and Welcome!

Have you tried right-clicking on the [COLOR="Blue"]speaker icon[/COLOR] in the upper task-bar?

If you do this you get a drop-down menu.

Click on [COLOR="Blue"]sound preferences[/COLOR] and a tabbed window will open, allowing you to configure your sound.

If this still fails, come back and we'll try some other things.

Regards,
Roger :D

---

### Post by cabse7en on 2010-01-27
I pulled up the sound preferences and didn't find anything referring to headphone volume, perhaps I'm missing something in there? I've also checked out the alsamixer and didn't seem to find anything there either.

Thanks for the welcome! These forums are an incredible source of information, I've found solutions to every problem I've had except this particular one, and I look forward to participating in the community!

Cheers,
Murphy

---

### Post by ramjet_1953 on 2010-01-27
When in the '[COLOR="Blue"]Sound Preferences[/COLOR]' Window, click on the [COLOR="Blue"]Output tab[/COLOR].

Near the bottom is a drop-down menu with the heading [COLOR="Blue"]Connector[/COLOR] next to it.

Click on the down arrow and play with these settings.

If still no-go try this:

Open [COLOR="Red"]Synaptic Package Manager[/COLOR]. [COLOR="Blue"]System>Administartion>Synaptic Package Manager
[/COLOR]
You will need to enter your login password.

Now click on [COLOR="Blue"]Settings>Repositories[/COLOR] in the top bar of Synaptic.

A window will now open.

Put a tick in every box except 'Source Code'

Close the window and click on [COLOR="Blue"]Reload[/COLOR] near the top of the window.

When that has finished, click on the [COLOR="Blue"]Search Button[/COLOR].

When the search window opens, copy and paste this into it : 

[COLOR="Red"]linux-backports-modules-alsa-karmic[/COLOR]

When the search finds this package, put a [COLOR="Blue"]tick in the box[/COLOR] to the left of it and then click [COLOR="Blue"]Apply[/COLOR].

When the package has installed back-out and then re-boot.

Hopefully things will now work OK.

Regards, Roger

---

### Post by cabse7en on 2010-01-28
I feel like I'm missing something very obvious, because in my sound preferences there is definitely no "connector" drop down menu under the output tab. Here is a screenshot of my sound preferences I'm looking at, hopefully it will help:

[IMG]http://img269.imageshack.us/img269/3766/soundpreferences.png[/IMG]

There were two options for  [COLOR=Red]linux-backports-modules-alsa-karmic [COLOR=Black]in Synaptic with identical names as well, I ended up installing them both and rebooting to no avail. [/COLOR]
[/COLOR]

---

### Post by cabse7en on 2010-01-28
Bump ;)

---

### Post by jweston on 2010-04-01
same problem, same machine. i did:

sudo apt-get install gnome-alsamixer

then under applications->sound&video I opened it, seeing:

[IMG]http://imgur.com/VIgeo.png[/IMG]

uncheck the furthest right hand side 'mute'. did the trick.

---

