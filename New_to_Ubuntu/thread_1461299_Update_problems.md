---
title: "Update problems"
date: 2010-04-24
forum: New to Ubuntu
---

### Post by orphanlast on 2010-04-24
I'm having trouble trying to update my system and to refresh my synaptic repository. When I try doing either one, it gives me this message:

>  W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783 The only odd thing that I've been doing has been with wine... trying to finagle a way to get photoshop on my Ubuntu.  Here's the tutorial that I've been following to try and get that done: [http://www.junauza.com/2010/02/how-to-install-adobe-photoshop-on.html](http://www.junauza.com/2010/02/how-to-install-adobe-photoshop-on.html)

For some reason it hasn't worked. The furthest I got was getting the .dll file where they specified... and also be able to add it into that menu and press "apply" but I was never able to install photoshop.

I'm kind of at a loss at this point.

Is there just technical difficulties going on with the Ubuntu community or something?

---

### Post by zipperback on 2010-04-24
As per the medibuntu.org website...
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

Issue the following into a terminal window.

```

sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update

```

As for photoshop... Sorry, but I can't help you with that one. I stopped using photoshop a long long time ago and learned that Gimp can do just about everything photoshop can, it just took a little while to learn it.

- zipperback
:popcorn:

---

### Post by orphanlast on 2010-04-24
> **zipperback said:**
> As per the medibuntu.org website...
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

Issue the following into a terminal window.

```

sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update

```As for photoshop... Sorry, but I can't help you with that one. I stopped using photoshop a long long time ago and learned that Gimp can do just about everything photoshop can, it just took a little while to learn it.

- zipperback
:popcorn:

Thanks man... Other than the ubuntu pocket guide, what's a good comprehensive place to figure out that sort of stuff on my own?  I mean how and when will I be able to just go -- OH! I'm having this problem. Well time to pull out my handy dandy terminal and type THIS!

lol

Also, with the photoshop issue. I just like photoshop's vector masking. And to my knowledge Gimp doesn't have anything like that. I also like Photoshop's ability to morph things rather than just eyeing it with the Imorph filter with Gimp. 

I'm planning on moving into Graphic Design for freelance... so... I think I'll need that.

---

### Post by zipperback on 2010-04-24
> **orphanlast said:**
> 
Also, with the photoshop issue. I just like photoshop's vector masking. And to my knowledge Gimp doesn't have anything like that. I also like Photoshop's ability to morph things rather than just eyeing it with the Imorph filter with Gimp. 

I'm planning on moving into Graphic Design for freelance... so... I think I'll need that.


I mentioned GIMP because most people who "need" photoshop don't actually understand how to use it, and can get by with GIMP if they just use it for a while.

If you are doing Professional work and require photoshop however, perhaps we can start a new thread and mark this one solved since it was about the update issue.

If you started a new thread about photoshop, send me a message and I'll see if I can help you with that one too.

- zipperback
:popcorn:

---

### Post by orphanlast on 2010-04-24
> **zipperback said:**
> I mentioned GIMP because most people who "need" photoshop don't actually understand how to use it, and can get by with GIMP if they just use it for a while.

If you are doing Professional work and require photoshop however, perhaps we can start a new thread and mark this one solved since it was about the update issue.

If you started a new thread about photoshop, send me a message and I'll see if I can help you with that one too.

- zipperback
:popcorn:

Oh yeah, this one is totally resolved. Thanks for the help. That magical code did everything. Lol.

---

