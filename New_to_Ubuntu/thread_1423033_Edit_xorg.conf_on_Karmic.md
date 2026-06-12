---
title: "Edit xorg.conf on Karmic"
date: 2010-03-06
forum: New to Ubuntu
---

### Post by mahy on 2010-03-06
Hello people,

I'm running a computer with ATI Radeon 9200 (AGP) graphics card and Ubuntu Karmic. I found out on the Web ([http://www.phoronix.com/forums/showthread.php?t=14805](http://www.phoronix.com/forums/showthread.php?t=14805)) that in order to boost its performance, I should add the line ```
Option "AccelMethod" "EXA"
``` to the xorg.conf file. I know how to do that on older Ubuntu versions, but here in Karmic there's no such file. Is there any workaround available? TIA for any help.

---

### Post by nathand28 on 2010-03-06
Is it not still in /etc/X11/xorg.conf ?
It is on my system.

---

### Post by viralmeme on 2010-03-06
> **mahy said:**
> .. I know how to do that on older Ubuntu versions, but here in Karmic there's no such file ..

Karmic doesn't use it but you can generate one using Xorg -configure and then copy it to /etc/X11.

---

### Post by mahy on 2010-03-06
> **ymitchell said:**
> Karmic doesn't use it but you can generate one using Xorg -configure and then copy it to /etc/X11.

Theoretically maybe, but when i try it out, this is the output:

```
Fatal server error:
Server is already active for display 0
	If this server is no longer running, remove /tmp/.X0-lock
	and start again.


Please consult the The X.Org Foundation support 
	 at http://wiki.x.org
 for help. 

 ddxSigGiveUp: Closing log

```

---

### Post by wojox on 2010-03-06
Try rebooting and running:

```
sudo X -configure
```

---

### Post by mahy on 2010-03-06
Oh, you needn't bother, I found the solution in here: [http://www.osguides.net/operation-systems/217-how-to-create-xorgconf-in-ubuntu-910.html](http://www.osguides.net/operation-systems/217-how-to-create-xorgconf-in-ubuntu-910.html)

Finally it works!

---

### Post by wojox on 2010-03-06
> **mahy said:**
> Oh, you needn't bother, I found the solution in here: [http://www.osguides.net/operation-systems/217-how-to-create-xorgconf-in-ubuntu-910.html](http://www.osguides.net/operation-systems/217-how-to-create-xorgconf-in-ubuntu-910.html)

Finally it works!

Cool, yeah you have to kill x to configure it that way. Glad to see you got it. ;)

---

