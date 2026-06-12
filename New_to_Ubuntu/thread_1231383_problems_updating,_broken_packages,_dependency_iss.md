---
title: "problems updating, broken packages, dependency issues"
date: 2009-08-04
forum: New to Ubuntu
---

### Post by kevinbutler on 2009-08-04
If someone could help me out with a few problems I am having on ubuntu 9.04 32 bit, I would greatly appreciate it. I'm new to ubuntu, so I'll try to provide as much information as possible...most of my issues revolve around the simple fact that I understand almost nothing yet.

first, what does this message mean, and what do I do about it? it happened when i tried to check for updates in the update manager.

W: GPG error: [http://wine.budgetdedicated.com]("http://wine.budgetdedicated.com/") jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 58403026387EE263

then it said i had 2 broken packages, use the broken filter, which i found, but it didn't do anything to fix it. nor did i have any luck when i "fixed broken packages"

then, when i tried to install the updates, i received this message:

E: /var/cache/apt/archives/libnspr4-dev_4.7.3-0ubuntu2_i386.deb: trying to overwrite `/usr/share/aclocal/nspr.m4', which is also in package kompozer-dev

I can't copy the details of the error message that ensued. to paraphrase, basically it says, errors encountered while processing, that I have dependency problems preventing configuration of libnss3-dev. Package libnspr4-dev is not installed. errors encountered while processing: libnss3-dev and adobe-flashplugin

that's all for now. thanks!

---

### Post by markharding557 on 2009-08-04
1 you need to install the gpg key from wine instructions are on their website.
2 remove the last packages which caused the errors and try reinstall

---

### Post by kevinbutler on 2009-08-05
it worked. thanks!

---

