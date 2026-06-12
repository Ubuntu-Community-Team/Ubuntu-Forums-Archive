---
title: "No sound after updating to 9.10"
date: 2010-02-06
forum: New to Ubuntu
---

### Post by h-town on 2010-02-06
Hello,

I haven't been using my Linux partition in quite a few months and I decided to boot it up and poke around. 

Update manager said that 9.10 is available so I went for it.

Everything works great, really snappy all round and my cpu monitor is very stable. However, I don't have any sound. 

The last time I updated a similar problem occurred and all that was required was to fiddle with the alsa mixer, but this time around it seems to not be the case. 

Sound Preferences shows no devices listed under the Hardware tab. So I'm guess it's a driver issue.. can someone put me in the right direction? 

Much appreciate :P

---

### Post by dolphinaura on 2010-02-06
did you try removing pulseaudio?
```

sudo apt-get remove pulseaudio pulseaudio-*
```
note that it might remove some of the backends of multimedia apps cause some of the apps have a pulseaudio specific backend.

EDIT: whats your sound card?

---

### Post by h-town on 2010-02-07
I'm not entirely sure what that did but it worked. 

Thanks dude, you rock. 

=D>

---

