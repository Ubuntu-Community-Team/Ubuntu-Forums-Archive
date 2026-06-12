---
title: "Two quick questions about VNC"
date: 2010-10-01
forum: New to Ubuntu
---

### Post by Legendary_Bibo on 2010-10-01
Okay so I got a new Notebook running Windows 7, and I have TightVNC running on it, and I can connect to my laptop, but the thing is when I click on stuff nothing happens, but when I look at my laptop, stuff has happened. I looked up if it might have to do with having compiz on, but it was from threads 3 years ago. Is this the case still?

My other question was is there a way to turn on my laptop remotely without going into the BIOS? It's just that my laptop won't let me access my BIOS for some apparent reason, it never has.

---

### Post by oregonbob on 2010-10-01
As for getting into bios, find your model number of laptop, google it with words "setup bios". I'll bet you get your answer. My hunch is you need to keep taping rapidly F2 or F8 or F10 as it starts up from a cold start.

If your laptop is linux, for remote access look at [www.nomachine.com](www.nomachine.com) NX. You install the server NX on linux, then run client on Windows or any OS. Nothing is better for remote linux desktop access.

---

### Post by CharlesA on 2010-10-01
You'd need to turn on wake on LAN or something similar. I don't know if the laptops support it or not.

As for the Windows 7 thing. Try installing UltraVNC. I've used TightVNC, but have had problems with Windows 7 and Vista, I think it might have something to do with Aero, I don't know.

---

### Post by oregonbob on 2010-10-01
As for getting into bios, find your model number of laptop, google it with words "setup bios". I'll bet you get your answer. My hunch is you need to keep taping rapidly F2 or F8 or F10 as it starts up from a cold start.

To make it boot linux default, bios won't fix it, you have to modify boot config depending on what version you have.

---

### Post by JBAlaska on 2010-10-01
> **Legendary_Bibo said:**
> Okay so I got a new Notebook running Windows 7, and I have TightVNC running on it, and I can connect to my laptop, but the thing is when I click on stuff nothing happens, but **when I look at my laptop, stuff has happened. I looked up if it might have to do with having compiz on, but it was from threads 3 years ago. Is this the case still?**

My other question was is there a way to turn on my laptop remotely without going into the BIOS? It's just that my laptop won't let me access my BIOS for some apparent reason, it never has.

In my experience, It is still the case, If you disable Compiz you should be able to remote access.

As far as entering your BIOS, also try tapping F1 or Del on startup.

And, getting drunk before 3PM is bad...Mkay :P

LOL!

---

### Post by Legendary_Bibo on 2010-10-01
Hey it was compiz! Now I just have to figure out how to start it up from VNC.

Hey it's nighttime somewhere. :D

---

### Post by CharlesA on 2010-10-01
> **Legendary_Bibo said:**
> Hey it was compiz! Now I just have to figure out how to start it up from VNC.

Hey it's nighttime somewhere. :D
Start what from VNC? Compiz?

---

### Post by Troublegum on 2010-10-01
I assume he means his laptop. 
You can power up machines over your wired network, it's called wake on lan. If you use wireless, you can not.

---

