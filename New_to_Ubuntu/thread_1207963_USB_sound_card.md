---
title: "USB sound card"
date: 2009-07-08
forum: New to Ubuntu
---

### Post by noorez on 2009-07-08
I have an external USB sound card but I'm having a bit of trouble using it. Here is the problem:

1) If the card is connected when Ubuntu starts, it doesn't work, even if I use the Pulse Audio device chooser to stream. It will only work if I disconnect and reconnect it.


Also, making the USB sound card the default doesn't work, I have to redirect streams manually for each application.

Is there a way to make a script that will redirect all sound automatically as soon as the USB sound card is attached to it and redirect all streams back to the default sound card when the USB sound card is removed.

---

### Post by Vadi on 2009-07-08
I'd be interested in this. Though PA has started remembering which stream did an app use last, so it's not such a pita. Default doesn't seem to have an effect though.

---

