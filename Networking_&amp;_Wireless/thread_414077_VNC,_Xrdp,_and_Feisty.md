---
title: "VNC, Xrdp, and Feisty"
date: 2007-04-19
forum: Networking &amp; Wireless
---

### Post by Sunon on 2007-04-19
Has anybody upgraded to Feisty and tested out if the vnc4 bug has been fixed?
[https://bugs.launchpad.net/ubuntu/+source/vnc4/+bug/78282](https://bugs.launchpad.net/ubuntu/+source/vnc4/+bug/78282)

I use my Ubuntu box completely headless through Xrdp and Vnc and I'm very hesitant to upgrade at this point because the last vnc update wouldn't allow me to remote in.  I had to downgrade my vnc version.  I'm thinking that the update is included as part of Feisty and by upgrading I'll be unable to remote in again.  Any thoughts or first hand experiences??

---

### Post by Emblem Parade on 2007-04-20
It has not been fixed! On Edgy, I could just aptitude install vnc4server/edgy to downgrade the broken fix. On Feisty, I can't do that anymore... it seems like the default package is broken and there's no downgrade possible. How utterly disappointing.

---

### Post by antoniuk on 2007-04-20
I was able to downgrade back to edgy and get vnc working again but to do so I had to go into the synaptic package manager and enable third party software (I also enabled all 5 in the ubuntu software section but I doubt you would need to do the same).

To get to repositories after opening synaptic, go to settings > repositories

To downgrade after making sure you have the edgy repository back up to where it needs to be...

```
sudo apt-get install vnc4server/edgy
```

If you have nothing in the 3rd party software section then you can always add them:

```
http://us.archive.ubuntu.com/ubuntu/
```

Add this twice, once as binary and once as source. Components only need to be universe.

---

### Post by Sunon on 2007-04-21
Thanks for the update.  I guess I'll have to wait to upgrade.  I find it ridiculous that this bug hasn't even been addressed in the few months that it has been reported.

---

### Post by jmandawg on 2007-04-23
He's right, you can run the edgy version on feisty and it works.  Hopefully they fix the feisty version soon.

just follow these steps as root to install the edgy version:

remove the old version:

aptitude purge vnc4server

add feisty sources:

vi /etc/apt/sources.list

Add these 2 lines:
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe

aptitude update
aptitude install vnc4server/edgy

You should be in business now.

---

### Post by Emblem Parade on 2007-04-24
Thanks! I thought of doing that, but was a bit scared that mixing repositories would create disaster. I'm glad someone else tried it for me first. :)

HOWEVER,

New problem: though I can get the GDM login screen via VNC, it will not accept my user and password! I tried this on two of my host machines (one is Ubuntu, one Kubuntu, both Feisty). This is very bizarre! What on earth could be the issue? Is there something I need to do to enable remote logins somewhere?

---

### Post by Emblem Parade on 2007-04-25
I fixed my own bug! Hooray! It seems that Feisty has a new option under Administration->Login Window called "Disable multiple logins for a single user." It seems to be enabled by default. I disabled it, and voila.

I think it's not very nice that I don't get a message about this when I try to login! However, I also guess that had there been a message ("you are already logged in" or something like that), it could give information to potential hackers.

Anyway. Also, for those who, like me, are worried about adding anything Edgy on Feisty, you only need the "deb" repository, not the "deb-src" repository. So, only one extra line to sources.list, until they fix this debilitating bug. By the way, if it is fixed and somebody finds out, please post here about it!

---

### Post by Emblem Parade on 2007-04-25
Ah, and I should add one more comment about that "Disable multiple logins for a single user" checkbox. Apparently, when it's on, not only are logins disabled, but gksudo attempts are also rejected.

I found this by logging in via x11vnc rather vnc4server (my temporary workaround until I got this fixed). There, I found that whenever the screen darkened and I got asked for the "administrative password," I was rejected.

I'm imagining that somehow both operations, logging in and gksudo, are related. But gotta say, it's not very intuitive to have both disabled at once, and without any kind of warning message when you're rejected!

---

### Post by Sunon on 2007-04-26
Thanks for all of the good information Emblem Parade.  It looks like I may be able to upgrade after all.  I think I'll give it a try this weekend.  As for your authentication error try this:

Copy the root .Xauthority file to your user's home.
sudo cp /root/.Xauthority /home/username/
sudo chown username:group /home/username/.Xauthority

---

### Post by Emblem Parade on 2007-04-26
Oh, my problem was not VNC authentication, but the actual Gnome GDM login. But thanks, I'm sure that will help someone who's stuck.

Someone should write a nice GUI script to set this all up. gvncserver? Hmm, maybe it's time to brush up my Python skills...

---

### Post by c4mden on 2007-04-30
I was having that exact problem, Emblem Parade.  Thanks for posting the information here, it fixed my problem as well!

---

### Post by Sunon on 2007-04-30
Well, the upgrade failed horribly, so I had to re-install everything.  Good thing my /home was on a different disk, so I didn't loose any data.  I followed the instructions to install VNC from edgy and all is well now.  Hopefully they will address the bug soon!

---

### Post by Emblem Parade on 2007-04-30
Just so you know, using x11vnc may be just perfect for your needs and doesn't seem to have these bugs.

In fact, it's perfectly fine to have both x11vnc and vnc4server installed and running, like I do. I have them each set up with xinetd on different VNC displays.

---

### Post by Sunon on 2007-04-30
I'll have to give x11vnc a try, thanks for the tip Emblem Parade

---

### Post by breuerp on 2007-05-02
I'm following your instructions but I'm getting a grey screen when I enter my vncpasswd.  Any suggestions?

---

### Post by Emblem Parade on 2007-05-02
It could be a fonts bug. Apparently some guides on the internet use the wrong font directory for the xinetd configuration. If you used Grumpy Mole's, it should be correct. Here's some more info:

See here: [https://bugs.launchpad.net/ubuntu/feisty/+source/vnc4/+bug/78282](https://bugs.launchpad.net/ubuntu/feisty/+source/vnc4/+bug/78282)

(I never got this bug, so there's not much I can help.)

---

### Post by breuerp on 2007-05-02
> **Emblem Parade said:**
> It could be a fonts bug. Apparently some guides on the internet use the wrong font directory for the xinetd configuration. If you used Grumpy Mole's, it should be correct. Here's some more info:

See here: [https://bugs.launchpad.net/ubuntu/feisty/+source/vnc4/+bug/78282](https://bugs.launchpad.net/ubuntu/feisty/+source/vnc4/+bug/78282)

(I never got this bug, so there's not much I can help.)

*sigh*  Nope, took care of that one.  VNC is the *one* thing that breaks every time I do an Ubuntu upgrade.

---

### Post by mahiyabz on 2007-11-12
hi... am using ubuntu to run an xrdp ... i got tiny problem ... when i connect to server...at login screen my keyboard is ok... but when am in ... my keyboard layout changes to unknow... still it works but with different layout... i press D.. if goes F there.... 


am using UK keyboard... i try to change keyboard layout from current user setting... but its not working...

any body there to solve this error for me....

cheeers..

---

