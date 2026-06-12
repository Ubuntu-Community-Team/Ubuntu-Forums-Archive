---
title: "How to install Google Earth"
date: 2009-04-29
forum: New to Ubuntu
---

### Post by elleppahc on 2009-04-29
Has anyone a how to do it to install Google earth in ubuntu 8.10

Thanks to whoever can assist

---

### Post by Paqman on 2009-04-29
You need to add the [Medibuntu repository]("https://help.ubuntu.com/community/Medibuntu"). Once you've done that you can get Google Earth through Synaptic.

---

### Post by elleppahc on 2009-04-29
Thanks for that. How do I do that?

---

### Post by yellerKat on 2009-04-29
> **elleppahc said:**
> Thanks for that. How do I do that?

Follow the instructions [HERE]("https://help.ubuntu.com/community/Medibuntu#Adding%20the%20Repositories").

---

### Post by Paqman on 2009-04-30
> **elleppahc said:**
> Thanks for that. How do I do that?

So just to spell that out, open a terminal at Applications > Accesories > terminal and copy/paste these commands in:
```

sudo wget http://www.medibuntu.org/sources.list.d/`lsb_release -cs`.list --output-document=/etc/apt/sources.list.d/medibuntu.list; sudo apt-get -q update; sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring; sudo apt-get -q update

```
then:
```

sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update

```

Normally i'd avoid giving obscure terminal commands to a new user. It's entirely possible to do that using the GUI at System > Admin > Software Sources if you prefer, but we'll stick to the method referred to on the official page to avoid confusion.

All you're doing here is adding a new software library (called a repository) and an authentication key for it. It's a semi-official repo called Medibuntu that contains things like Google Earth, codecs for encrypted DVDs, Skype, etc. Once you've added it you can get all these packages through Synaptic just like the official Ubuntu packages.
[URL="http://www.medibuntu.org/"]
www.medibuntu.org[/URL]

---

