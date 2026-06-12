---
title: "Ok...What does this mean"
date: 2009-01-31
forum: New to Ubuntu
---

### Post by uwave on 2009-01-31
I've search but I keep getting more and more confused

W: GPG error: [http://apt.wicd.net](http://apt.wicd.net) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY FEC820F4B8C0755A

I got this at the beginning of my updates
Could this be the reason my Atheos wireless just quit?

I'm runnin Hardy on a Panasonic CF-28

---

### Post by vikramaditya on 2009-01-31
try this, it can't hurt.  open terminal and paste in the following...
```
gpg --keyserver hkp://subkeys.pgp.net --recv-keys FEC820F4B8C0755A
gpg --export --armor FEC820F4B8C0755A | sudo apt-key add -
```

---

### Post by uwave on 2009-01-31
Thank You Sir / Madam ...That gave it back the missing key, I'm guessing.

It just bugged me  everytime it was to download, figured I might be missing something.

Now, to fix my Atheos wireless

---

### Post by vikramaditya on 2009-01-31
> **uwave said:**
> Now, to fix my Atheos wireless
Glad that did the trick, but I rot at wireless! :)

---

### Post by uwave on 2009-01-31
Thats ok, just glad this one was simple

---

### Post by uwave on 2009-02-01
I'd like to mark this as SOLVED 

I didnt know how till I looked it up.

but it doesn't show in the thread tools for me.

---

### Post by HotShotDJ on 2009-02-01
> **uwave said:**
> I'd like to mark this as SOLVED 

I didnt know how till I looked it up.

but it doesn't show in the thread tools for me.Yeah... that feature (among a few others) has been disabled due to some instability issues with the forum software a few weeks back.  Perhaps you can simply edit the title of your original post and add [SOLVED] to the beginning of it (really not sure if that will work or not).

---

### Post by leonardo_neo on 2009-02-01
> **HotShotDJ said:**
> Yeah... that feature (among a few others) has been disabled due to some instability issues with the forum software a few weeks back.  Perhaps you can simply edit the title of your original post and add [SOLVED] to the beginning of it (really not sure if that will work or not).

Thanks. Even I was looking for how I could make my posts as solved, but I was not able to find any tool for that.

---

### Post by zvacet on 2009-02-01
@ **leonardo_neo**

Just follow **HotShotDJ´s** advice.

---

### Post by zika on 2009-02-01
> **vikramaditya said:**
> try this, it can't hurt.  open terminal and paste in the following...
```
gpg --keyserver hkp://subkeys.pgp.net --recv-keys FEC820F4B8C0755A
gpg --export --armor FEC820F4B8C0755A | sudo apt-key add -
```
thanks, it helped me with the similar "problem".

---

### Post by uwave on 2009-02-01
> **HotShotDJ said:**
> Yeah... that feature (among a few others) has been disabled due to some instability issues with the forum software a few weeks back.  Perhaps you can simply edit the title of your original post and add [SOLVED] to the beginning of it (really not sure if that will work or not).

Thanks HotShotDJ, I thought it was me 

I have edited the title now as Solved
Thanks to all that helped :D

---

