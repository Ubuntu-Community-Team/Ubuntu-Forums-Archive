---
title: "New User..."
date: 2009-12-27
forum: New to Ubuntu
---

### Post by jokei on 2009-12-27
Just a hello really, I'm using Xubuntu and greatly enjoying it, glad to be away from the nightmare of Windows.

I'll probably be trying to pick some brains as this is all quite new to me.

My first question is that the volume seems to be considerably lower on my laptop now than what it was previously - mostly using VLC, but this is also the case in audio apps.

I've maxxed the volume on sound card settings, in the mixer and on whatever application I'm using at the time...

Is there a way around this?

---

### Post by presence1960 on 2009-12-27
> **jokei said:**
> Just a hello really, I'm using Xubuntu and greatly enjoying it, glad to be away from the nightmare of Windows.

I'll probably be trying to pick some brains as this is all quite new to me.

My first question is that the volume seems to be considerably lower on my laptop now than what it was previously - mostly using VLC, but this is also the case in audio apps.

I've maxxed the volume on sound card settings, in the mixer and on whatever application I'm using at the time...

Is there a way around this?

Open a terminal (Applications > Accessories > Terminal) and run ```
alsamixer -Dhw
```

See if PCM has some volume left. If it does raise it higher.

---

### Post by jokei on 2009-12-27
Hey, thanks for the swift reply.

Unfortunately, the PCM volume is maxxed.

:(

---

### Post by Sir Jasper on 2009-12-27
Hi,

I use Xubuntu 9.04 and under Multimedia > Volume Control > Preferences there is an option Mic Boost (+20dB).

My regards

---

### Post by jokei on 2009-12-27
Couldn't find that, but mic boost would be for an input signal???

Also, if anyone can advise on torrent settings (Transmission), that would be nice.

:)

---

### Post by gsmanners on 2009-12-27
When dealing with torrents it really depends on your service provider. You mainly need to play around with the upload and download rate caps until you find the best settings. Just keep bumping up the values until you start seeing serious lag on loading most web pages (that's what I do).

---

