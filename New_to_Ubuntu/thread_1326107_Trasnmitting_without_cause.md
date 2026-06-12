---
title: "Trasnmitting without cause?"
date: 2009-11-14
forum: New to Ubuntu
---

### Post by OllieGab on 2009-11-14
Using Ubuntu 9.10

When I went to my computer this morning I noticed that it was transmitting out onto the net at about 180 kbps. I realised that I had had 'pavucontrol' open during the night (which presents itself as a volume control) and when I closed it down the 'traffic' stopped.
What on earth is a volume control sending out?
If I put my Windows hat on I may think I've got some kind of virus 'emptying' my computer!!?? :)

---

### Post by NickJones on 2009-11-14
It could be Ubuntu One, have you put a lot of files into that folder?

---

### Post by WitchCraft on 2009-11-14
> **OllieGab said:**
> Using Ubuntu 9.10

When I went to my computer this morning I noticed that it was transmitting out onto the net at about 180 kbps. I realised that I had had 'pavucontrol' open during the night (which presents itself as a volume control) and when I closed it down the 'traffic' stopped.
What on earth is a volume control sending out?
If I put my Windows hat on I may think I've got some kind of virus 'emptying' my computer!!?? :)


PulseAudio Volume Control (pavucontrol) is the sound control server for Linux.
Please note that previously, this program could only be configured as local server, and required that a special module module-gconf was loaded for networking mode.
Since PulseAudio 0.9.5 this modules is loaded by default.


The solution is to edit /etc/pulse/default.pa and to comment out the lines:
File: /etc/pulse/default.pa
```

# load-module module-x11-publish
...
# load-module module-gconf

```

---

### Post by OllieGab on 2009-11-14
I only just discovered Ubuntu One the other day and signed up. But at the moment there are only two small files there.
Are you saying that 'things' could be sent 'up there' without me requesting it?

---

### Post by camaron1 on 2009-11-14
> **OllieGab said:**
> I only just discovered Ubuntu One the other day and signed up. But at the moment there are only two small files there.
Are you saying that 'things' could be sent 'up there' without me requesting it?

Every time you put something in ubuntu one folder you are requesting to upload them (that is if ubuntu one is running...)

---

### Post by Paqman on 2009-11-14
UbuntuOne is a service that automatically syncs that folder on your machine with some remote storage hosted on Canonical's servers. But there's no way it should be sucking 180Kbps when you've only got a couple of wee files.

---

### Post by OllieGab on 2009-11-14
> **WitchCraft said:**
> 
The solution is to edit /etc/pulse/default.pa and to comment out the lines:
File: /etc/pulse/default.pa
```

# load-module module-x11-publish
...
# load-module module-gconf

```

the load-module module-x11-publish line was already commented out.
Commenting out the other one helped, ie I don't seem to transmitting anything when pavucontrol is open.
Remians to be seen if it works as I want it to....?

Cheers for that!

---

### Post by 3rdalbum on 2009-11-14
It is probably just trying to find other Pulseaudio servers or sinks on your local network. Nothing to worry about.

---

### Post by WitchCraft on 2009-11-14
> **3rdalbum said:**
> It is probably just trying to find other Pulseaudio servers or sinks on your local network. Nothing to worry about.

Probably, but it's always better to switch off services you don't need, especially if they are network servers, and certainly if they need 128 k.

---

