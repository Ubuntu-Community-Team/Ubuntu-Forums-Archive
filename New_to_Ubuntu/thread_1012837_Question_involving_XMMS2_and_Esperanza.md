---
title: "Question involving XMMS2 and Esperanza"
date: 2008-12-16
forum: New to Ubuntu
---

### Post by thepenguinonthetelly on 2008-12-16
Hi, I'm new to this forum (not too new to Ubuntu, but still learning)!

I'm looking for some help with XMMS2.  I wanted to install it because I was already familiar with how XMMS works on my Nokia n800.  It installed just fine, but I went poking around for a gui to work with it, found Esperanza, and got it to install almost all of the way, but am stuck at this point (from a HowTo somewhere):

> 4) compile the code, this should not fail as you have the dependencies. if it does fail read the details, you should be able to figure out what other dependencies you may need to satisfy. It will always be a -dev package you'll need:

./configure
make


5) Copy the binary file to the bin folder so it can be run from anywhere. I am not sure why a make install didn't suffice, but it really doesn't matter:

sudo cp ./src/ui/esperanza /usr/bin


You can now run esperanza with last.fm support etc. You might want to create a menu item as well, your choice, personally I run it in a session script so it is there when I login.


As noted, the make install didn't work right, but I am unsure as how to complete the rest of it.  That's where my knowledge of Ubuntu fails.  If someone could help me out, I'd appreciate it.

---

### Post by |{urse on 2008-12-17
esperanza is in the repositories, I'm using it right now, very nice =)

```
sudo apt-get install xmms2 esperanza
```

then launch it with this (or make a script containing this line)

```
esperanza && gksudo killall xmms2d
```

if you dont add the bit about killall xmms2d then the xmms2 daemon will continue to play music after you've closed esperanza.

---

### Post by thepenguinonthetelly on 2008-12-17
Thanks for the help. :)  Actually, it wasn't popping up in Synaptic for some reason, but it did after a reinstall of Ubuntu (old copy must have been corrupted).

Can you tell me how to get Last.fm running on it?  I see the dialog box, but nowhere to enter my login information.

---

