---
title: "Get synaptic/apt to stop dowload of Translation Pkg's?"
date: 2009-05-11
forum: New to Ubuntu
---

### Post by cycle_mycle on 2009-05-11
Every time synaptic or apt is updated it tries to download Translation-en_PH and it fails. But since I don't need it anyway how do I get it to stop trying?

I've searched sources.list and I see no place where it has that entry....

I don't see a place to enter a language in the synaptic's preferences.

Language support is set to: English (United States)

Does it look for them because of my location?

---

### Post by philinux on 2009-05-11
> **cycle_mycle said:**
> Every time synaptic or apt is updated it tries to download Translation-en_PH and it fails. But since I don't need it anyway how do I get it to stop trying?

I've searched sources.list and I see no place where it has that entry....

I don't see a place to enter a language in the synaptic's preferences.

Language support is set to: English (United States)

Does it look for them because of my location?

Post the exact error message. Should be easy to fix.

---

### Post by cycle_mycle on 2009-05-11
Here's a sample of the output, it's not an error just trying to download useless package information:

Hit [http://ubuntu-archive.sit.kmutt.ac.th](http://ubuntu-archive.sit.kmutt.ac.th) jaunty Release.gpg
Ign [http://ubuntu-archive.sit.kmutt.ac.th](http://ubuntu-archive.sit.kmutt.ac.th) jaunty/main Translation-en_US                                                                                               
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty Release.gpg                                                                                                                   
Ign [http://ubuntu-archive.sit.kmutt.ac.th](http://ubuntu-archive.sit.kmutt.ac.th) jaunty/restricted Translation-en_US                                                     
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty Release.gpg                                                                               
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/free Translation-en_US 

In synaptic instead of ignoring it says "failed".

---

### Post by Paqman on 2009-05-11
Install the package localepurge. You can use it specify exactly which languages yu want to keep, it'll ditch all the others. After that you'll only get updates for what's actually installed.

---

### Post by cycle_mycle on 2009-05-11
OK, that stopped the Translation-en_PH from trying to load. I guess no matter what it wants to load Translations though right?

Now it's trying to load Translation-en_US...

Is that the normal behavior? I just never noticed it before, I guess.

---

