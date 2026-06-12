---
title: "Ethernet card driver installation"
date: 2009-03-06
forum: New to Ubuntu
---

### Post by sks24 on 2009-03-06
Anybody point me to a/some step-by-step info on how to install network card drivers with Ubuntu?  I'm  to get a LNE100TX card up and running on my old desktop.  I've loaded the drivers on a DVD; there's no internet capability, so I'll have to install from the file on that DVD.  I guess

Thanks in advance for your help,
SKS

---

### Post by ibuclaw on 2009-03-06
95% of all ethernet devices should work out of the box without the need for external modules (drivers) at all.

On your Ubuntu machine, can you post the output of these issued commands in the terminal?
```
ls /sys/class/net/
```
```
lspci | grep -i ethernet
```

Also, What DVD are you implying on using? What drivers? and where did you get them?

Regards
Iain

---

### Post by dwasifar on 2009-03-06
You should not need to install drivers for that card.  It's a common card and is supported natively in a standard Ubuntu installation.  I have a few of those myself and have never needed to do anything special for them.

---

### Post by egalvan on 2009-03-06
> **sks24 said:**
>  get a LNE100TX card up and running on my old desktop.

Native support (no driver install needed) under:

Hardy (8.04) & Intrepid (8.10)

Puppy 4.1 & 4.2

Mandriva 2008 (several versions)

The above all installed and connected on a machine with a LNE100TX card.

If your card is not being recognized, there are other problems.

Follow the other posters advice, and run those command & show us the results.

ErnestG

---

### Post by sks24 on 2009-04-11
I apologize for taking so long to say "thank you."  As soon as I can find the time, I'm going to fire up that old desktop and follow the advice you all have so kindly - and promptly - provided.

---

