---
title: "Why do I have to authenticate with my wireless network when i reboot?"
date: 2010-12-30
forum: New to Ubuntu
---

### Post by bludshot on 2010-12-30
I want my wireless network to always work like it does in windows, but for some reason each time I reboot, ubuntu asks me for my WPA2 key again to access my wireless network.

How can I get it to stop doing that?

Thanks!

---

### Post by KlytusLord on 2010-12-30
I am no expert so this may do absolutely nothing.

Have you checked if the password is listed in the network connections tool? System/Preferences/Network Tools

If the password is not listed there, enter it and see if that changes anything. If it is listed there, try deleting and see if it will remember it once it asks for it again.

You may also want to delete the connection from here altogether, and have Ubuntu create it again from scratch.

---

### Post by bludshot on 2010-12-31
I am using mythbuntu, it doesn't have System/Preferences/Network Tools.

It seems my issue has something to do with Keyrings. I need to find out how to edit this keyring so that it doesn't ask for a password all the time...

---

### Post by Habeouscorpus on 2010-12-31
Is your login keyring being unlocked when you log in? I've had that happen sometimes... The login keyring has your WPA password on it.

---

### Post by oldsoundguy on 2010-12-31
I tried to use Mythbuntu and found it sorely lacking in any form of flexibility and many utilities had to be installed from Synaptic .. TOO MANY!!

So I installed Ubuntu and then installed the complete Myth package.  THEN everything worked as it should have done in Mythbuntu without tweaking!

YMMV, but that was my solution.  Many Myth only users say that is the coward's way out .. supposed to grit your teeth and flog away in terminal or whatever.  I am not a programmer .. I am a USER .. I want to install a system and basically have most of it work out of the box.

---

### Post by bludshot on 2010-12-31
Yeah so far mythbuntu is a little kooky. I mean, no text editor installed by default?!?

Anyhow, I fixed this problem. In the top right there is the wireless network connection menu thing, I just had to edit my wireless connection and add the password there, AND, check the box "available to all users".

---

