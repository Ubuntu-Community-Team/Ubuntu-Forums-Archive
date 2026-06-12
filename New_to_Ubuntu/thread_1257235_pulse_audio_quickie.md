---
title: "pulse audio quickie"
date: 2009-09-03
forum: New to Ubuntu
---

### Post by moominboy8668 on 2009-09-03
hi all. just a quick one which im sure has a very simple answer.

every time i boot up pulse sets my default sound card at 0% volume and mute.

so every time i start i have to change it myself and it is still ticked as default.

any clues please?

running jaunty btw

---

### Post by moominboy8668 on 2009-09-04
anybody? somebody? lol!

---

### Post by moominboy8668 on 2009-09-06
thanks for the help folks. much obliged...:x

---

### Post by themusicalduck on 2009-09-06
This is the closest I can find that resembles your problem:

[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/352732](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/352732)

Running ```
/etc/init.d/alsa-utils restart
``` manually apparently unmutes everything.

One suggestion was updating to the latest pulseaudio package which supposedly has fixed the bug (but some people report that it hasn't helped them). I'm not sure of the best way to do this but someone else might be able to help.

Another suggestion was removing pulseaudio and going ALSA only with this guide -http://idyllictux.wordpress.com/2009/04/21/ubuntu-904-jaunty-keeping-the-beast-pulseaudio-at-bay/

Or this was posted as a possible workaround. This might be the easiest thing to try first:

> Ok,
I've found a fix that works for me. I was find that if I didn't shut down my computer gracefully (and there letting /etc/init.d/alsa-utils run it's stop procedure) that the sound levels would be set and un-muted on next boot.

Therefore, I commented out line 372 in /etc/init.d/alsa-utils:

# mute_and_zero_levels "$TARGET_CARD" || EXITSTATUS=1

Now when I reboot gracefully, the sound levels are correct. I would suspect that there is a bit a race condition happening. I am supposing the alsa-utils script is being called twice and as the levels have been "muted and zero'd" the first time around, the second time around sees the zero'd levels get saved as the Alsa state.

I think the udev and rc.d is invoking the script twice......

This is however just a theory, but it makes sense!!! (I Hope)

To do this run:

```
sudo cp /etc/init.d/alsa-utils /etc/init.d/alsa-utils.backup
```

```
sudo kate /etc/init.d/alsa-utils
```

And then edit and save as it says.

Only some on there reported these as working so it isn't guaranteed to help in your case, but they might be worth looking at. Though it might just be a case of waiting until the bug gets fixed.

It's definitely worthwhile reading through that report though. And be careful if you decide to remove pulseaudio taking care to know what you're doing in case anything needs to be undone.

Hope this helps a bit.

---

