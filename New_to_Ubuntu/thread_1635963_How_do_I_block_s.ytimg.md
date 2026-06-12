---
title: "How do I block s.ytimg?"
date: 2010-12-02
forum: New to Ubuntu
---

### Post by WatchingThePain on 2010-12-02
Hi,

The title says it all.
Since a few updates this morning this s.ytimg crap is delaying my youtube vids.
Now I would appreciate is anyone knows how to basically get rid of s.ytimg.

Afaik it's related to flash player and webcam. I use flashplayer but not webcam.

I'm using Ubuntu Lucid.
Processor is intel.

---

### Post by philinux on 2010-12-02
> **WatchingThePain said:**
> Hi,

The title says it all.
Since a few updates this morning this s.ytimg crap is delaying my youtube vids.
Now I would appreciate is anyone knows how to basically get rid of s.ytimg.

Afaik it's related to flash player and webcam. I use flashplayer but not webcam.

I'm using Ubuntu Lucid.
Processor is intel.

Adblockplus addon.

---

### Post by Redmage913 on 2010-12-02
I'm assuming you're using Firefox.

If you are, I suggest you subscribe to both the Easylist and the Fanboy's List in the Adblock Plus add-on. You can initially subscribe to one, then you have to go to Tools>Adblock Plus Preferences window, then click Filters>Add Adblock Plus filter subscription to get the other. Since I started using both, I've had virtually no ads display on all the sites I use regularly.

Cheers!

--Red

---

### Post by sandyd on 2010-12-02
> **WatchingThePain said:**
> Hi,

The title says it all.
Since a few updates this morning this s.ytimg crap is delaying my youtube vids.
Now I would appreciate is anyone knows how to basically get rid of s.ytimg.

Afaik it's related to flash player and webcam. I use flashplayer but not webcam.

I'm using Ubuntu Lucid.
Processor is intel.
you can also add it to your hosts file
```

sudo nano /etc/hosts
```
add
```

127.0.0.1 **domain-you-want-to-block**

```

---

