---
title: "Sound is dead."
date: 2009-05-27
forum: New to Ubuntu
---

### Post by projecthikari on 2009-05-27
When I updated to Ubuntu 8.10 and then 9.04, both updates, my sound refused to work. Previous to this, it'd always just refused to work for Youtube. Now nothing plays. It won;t even beep at me for doing something wrong.
My laptop is a Toshiba Satellite A135-S4427. Thanks.

---

### Post by Ben Crisford on 2009-05-27
Hmm...

First of all, I suggest you report this as a bug :).  Because if the only way you changed your system was an upgrade, it certainly sounds like a bug to me.

Second, try this.  It might not work, and what with me not being the brightest spanner in the toolbox, I don't know how to reverse it :-/, so you might be better off not trying it.
```

killall pulseaudio
sudo apt-get remove pulseaudio
sudo apt-get install esound
sudo rm /etc/X11/Xsession.d/70pulseaudio

```
I'm particurlaly unsure of the last command, because I haven't tested it in jaunty.  But it might work.  If I was to try and reverse it I would do this, but it might not work, so its at your own risk.  I have tested it on my PC though.
```

killall esound
sudo apt-get remove esound
sudo apt-get install pulseaudio
sudo rm /path/to/esound/stuff

```

Like I say, im unsure whether that'll work for you, but it does for me.

Hope this helps,
Ben

---

### Post by projecthikari on 2009-05-27
Didn't work out, but thanks anyway!!

---

### Post by billgoldberg on 2009-05-27
Try using asoundconf or asoundconfig (I'm on Windows, can't check) or it's gui asoundconfig-gtk.

It will allow you to set your sound card.

It's worth a shot.

---

Under system -> preferences (could be administration) -> sound, have you tried switching to ALSA or OSS and use the test option next to it to see if that works?

---

