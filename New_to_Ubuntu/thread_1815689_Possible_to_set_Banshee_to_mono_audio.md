---
title: "Possible to set Banshee to mono audio?"
date: 2011-07-31
forum: New to Ubuntu
---

### Post by Jmob on 2011-07-31
Not much more to say than that.  Sometimes I would like to pump mono to the two output channels.  Is this possible?

---

### Post by Frogs Hair on 2011-07-31
I see no mono option in sound preferences under the output tab . If it could be done it would require some type of mixer software . There are a few options in the software center .

---

### Post by directhex on 2011-07-31
> **Jmob said:**
> Not much more to say than that.  Sometimes I would like to pump mono to the two output channels.  Is this possible?

Banshee just plays out through your default gstreamer output sink, which goes through pulseaudio. You can insert a "monoify this please" filter at either of those points, but not in Banshee itself

---

### Post by Jmob on 2011-07-31
Thanks.  I'll look into that.  

Learning my way up the learning curve.

---

### Post by cbennett926 on 2011-08-02
You can go into sound preferences and change the balance to one side, not sure if that helps but just an idea

---

