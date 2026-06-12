---
title: "Boot computer with no monitor?"
date: 2010-08-05
forum: New to Ubuntu
---

### Post by darkeale on 2010-08-05
Hi, 

Does anyone know if it is possible to get linux to boot without a monitor plugged in?  I am using vista to remote desktop to the Xubuntu box, and when a monitor is plugged into the xubuntu I have no problems.  but with no monitor I don't think xubuntu boots properly because I am unable to connect to it.  Does anyone know if it is possible to force Xubuntu to boot with no monitor?

Thanks,
Alex

---

### Post by ironic.demise on 2010-08-05
Are you using Server edition?
I'm not going to pretend I know exactly what your problem is but I think it might help if you told me how you're connecting to it?

I assume VNC?

---

### Post by darkeale on 2010-08-05
Hi,

Yes using UltraVNC but with Xubuntu Desktop 10.04

Thanks,
Alex

---

### Post by Darkness Des on 2010-08-05
Did you sign in? If you have it set to automatically log in, did you unlock the keyring?

---

### Post by ironic.demise on 2010-08-05
I'll assume ultraVNC runs before login, that was the main issue I have had whenever I've set up VNC, that it runs like a program AFTER logging in even though that's not much use to anybody really.

So, does it run at start-up.
Sorry I can't be of much help, most of my VNC experience was on a Win machine.

Only advice I can really give is to check ports on both machines, check port-forwarding and make sure that it is running with correct permissions and the like.

---

### Post by darkeale on 2010-08-05
Hi,

I have set to login automatically and I have disabled the keyring (not recommended I know).  Works fine with monitor, only when I take away the monitor that I can't connect.

Also the VNC is on the Vista machine.

I am sure it is something to do with booting without a monitor rather than a problem with the remote connection because the remote connection works fine with a monitor is plugged in

---

### Post by ironic.demise on 2010-08-05
Graphics card issue?
Why are you taking the monitor off anyway?

Try updating the graphics card drivers?

---

### Post by Peaches491 on 2010-08-05
I have no idea if it will help, but you could try plugging in an extra monitor cable. 

I once read that soldering a resistor on the right pins tricks your computer into seeing a monitor. But of course, i cant find it again. 

sorry im of such little help.

---

### Post by Miljet on 2010-08-05
There was a quite extensive thread about this very subject a few weeks back in this forum. I didn't bookmark it because I didn't think I would need it. Perhaps a search would turn it up. If I remember correctly, there was also a bug report filed too.

---

### Post by JBAlaska on 2010-08-05
> **darkeale said:**
> Hi, 

Does anyone know if it is possible to get linux to boot without a monitor plugged in?  I am using vista to remote desktop to the Xubuntu box, and when a monitor is plugged into the xubuntu I have no problems.  but with no monitor I don't think xubuntu boots properly because I am unable to connect to it.  Does anyone know if it is possible to force Xubuntu to boot with no monitor?

Thanks,
Alex

Not trying to be rude, but I have to got to work soon.

Try Googling xubuntu headless install

That should bring up some pertinent hits

---

### Post by ironic.demise on 2010-08-05
> **JBAlaska said:**
> Not trying to be rude, but I have to got to work soon.

Try Googling xubuntu headless install

That should bring up some pertinent hits

Give the man a win!:KS

---

