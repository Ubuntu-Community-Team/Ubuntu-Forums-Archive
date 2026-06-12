---
title: "Embedded with Wine and VST"
date: 2010-03-06
forum: New to Ubuntu
---

### Post by dirk.bruere on 2010-03-06
To start off, I'm a total noob, so what I'm about to say may sound trivial or naive.
I have a project where I have to use an Intel Atom based board to do some audio processing. Right now I can use XP to run a VST host and its plugins, plus asio4all and Virtual Audio Cable, to feed audio in and out of one or more souncards. Works great.

The first problem is that I want to embed all of this and run it from flash. I can obviously use embedded XP, but that costs a lot. The alternative is an embedded Linux - which is why I'm here.

Since I want to run from flash I have downloaded the netbook version since that will obviously save me tweaking the desktop version to be compatible for flash. Not that I have a clue how to tweak Linux in any way whatsoever, since all my previous work has been on Windows.

Anyway, what it seems I need is Ubuntu netbook, running Wine and then loading on my Windows VST host and it's dll plugins. Probably booting from compact flash. Which brings me to another question - how long will it take to boot up and start working? Ideally, I need better than 20 seconds.

Next, what happens with souncard drivers? Are they Windows drivers loaded with Wine, or Ubuntu drivers? Ditto asio4all - will that still work?

Where do I go from here?

---

### Post by mikewhatever on 2010-03-06
You should take a look at wine compatibility list or ask the community, if VSThost works with wine. Regardless, a less then 20 seconds boot from flash is out of the question with current stable versions. The upcoming Lucid Lynx is supposed to boot in 10 seconds from hdd, but I don't know it's there yet.

---

### Post by dirk.bruere on 2010-03-06
> **mikewhatever said:**
> You should take a look at wine compatibility list or ask the community, if VSThost works with wine. Regardless, a less then 20 seconds boot from flash is out of the question with current stable versions. The upcoming Lucid Lynx is supposed to boot in 10 seconds from hdd, but I don't know it's there yet.

VSThost works with Wine.
So, do I have to have a souncard that has Linux drivers, or will XP drivers work?
As for boot times, since this is embedded I assume there might be some stuff I can leave out to speed up the loading?

---

### Post by mikewhatever on 2010-03-06
I don't know about the drivers. Are windows drivers supposed to work under wine?

---

### Post by dirk.bruere on 2010-03-06
> **mikewhatever said:**
> I don't know about the drivers. Are windows drivers supposed to work under wine?

You're asking me???!

---

