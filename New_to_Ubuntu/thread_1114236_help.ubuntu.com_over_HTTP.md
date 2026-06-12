---
title: "help.ubuntu.com over HTTP?"
date: 2009-04-02
forum: New to Ubuntu
---

### Post by sheshbesh on 2009-04-02
**Problem:** I want to read pages from help.ubuntu.com through HTTP, rather than HTTPS.

ORIGINAL POST:
hi guys,
I'm new to ubuntu, and am taking the time to read some help files on ubuntu.com, before I post here with specific questions.

However, I would like to read these manuals (the official and the community's) on the go, and my mobile's browser does not support HTTPS.
Is there a way for me to read them as normal HTTP?

that is, rather than [https://help.ubuntu.com/community/TruecryptHiddenVolume](https://help.ubuntu.com/community/TruecryptHiddenVolume), i would like to have something like [http://some.other.site.com](http://some.other.site.com) 
of course, I could save these as PDF and post them somewhere online, but this is a lot of preparation work and does not let me be spontaneous with the topics I want to read on the go

Thanks in advance

PS what is the idea behind these pages being https anyway?

---

### Post by wolfen69 on 2009-04-02
[www.ubuntuguide.org](www.ubuntuguide.org) is a great place to learn about ubuntu. it's regular http.

---

### Post by cariboo on 2009-04-02
You don't have to stick with Ubuntu documentatiom, In most cases the only difference between distributions is the package manager. Check out Debian documentation as Ubuntu is based on Debian.

Jim

---

### Post by sheshbesh on 2009-04-02
> **wolfen69 said:**
> [www.ubuntuguide.org](www.ubuntuguide.org) is a great place to learn about ubuntu. it's regular http.

first, thanks a ton for the link, wolfen. i will definitly check it out.
HOWEVER, it links to HTTPS... for instance, regarding hard disk encription, this website says "With Ubuntu Intrepid ibex, you can create a folder whose contents are encrypted. See these instructions. " and links to the https link in my original post... so I guess this brings us back to square one.
Again, thanks a lot for the link- i'll check it out when i'm not on the go.

If I want to stick with the ubuntu community help pages, is there a website that will cache these links and then post them as http? i tried the google cache, but it does not work yet.

---

### Post by sheshbesh on 2009-04-03
Bump.
Surely someone out there had this problem before, that is, to read help.ubuntu.com with browsers that do not support https.

I'd really appreciate your help since, unfortunately, all my google searches end up with instructions for configuring apache for SSL...

---

### Post by sheshbesh on 2009-04-19
bump

---

### Post by ddrichardson on 2009-04-19
> **cariboo907 said:**
> You don't have to stick with Ubuntu documentatiom, In most cases the only difference between distributions is the package manager. Check out Debian documentation as Ubuntu is based on Debian.

Jim
Its documentation isn't from Debian, the Documentation Team writes it. There are upstream projects such as Gnome of course but the system documentation is not from Debian.

I'll bring it up with the rest of the team as to why its https, I remember it being discussed but don't remember why.

---

### Post by ddrichardson on 2009-04-19
It's https to protect usernames and passwords when users log in to the community part to make edits.

We're finding out if that now OpenID is used we can move back to http.

---

### Post by sheshbesh on 2009-04-20
> **ddrichardson said:**
> It's https to protect usernames and passwords when users log in to the community part to make edits.


Yes, that's what I was guessing. But I wounder if this is possible to allow users to just read the community part, maybe by mirroring it "read only" to http, and then if they click something like "contribute" or "edit", they'll be taken to https.

Anyways, thanks a lot for your reply.

---

### Post by ddrichardson on 2009-04-20
> **sheshbesh said:**
> Yes, that's what I was guessing. But I wounder if this is possible to allow users to just read the community part, maybe by mirroring it "read only" to http, and then if they click something like "contribute" or "edit", they'll be taken to https.

Anyways, thanks a lot for your reply.
We're discussing the options on the teams mailing list, I'll let you know the outcome.

---

