---
title: "Tracker Index corrupted after upgraging ti 9.04"
date: 2009-05-15
forum: New to Ubuntu
---

### Post by realmoonstruck on 2009-05-15
I get this error message:
```
Tracker
There was an error while performing indexing:
Index Corrupted
```I purged Tracker form SPM and reinstalled it, but the error still persists.

---

### Post by cariboo on 2009-05-15
I don't use tracker, so I'm not sure exactly which directory you have to remove. Open Nautilus (Places-->Home Folder) and press Ctrl-h, this will reveal the hidden files and directories, you should be able to find the tracker directory and remove it.

---

### Post by realmoonstruck on 2009-05-16
but isn't there a way to fix this?

---

### Post by TimTang on 2009-05-16
> **realmoonstruck said:**
> but isn't there a way to fix this?
Hi realmoonstruck!

I found a Solución:

Step 1: Learn to read and speak Spanish

Step 2: Just joking! you should be able to do the following with out Spanish. It worked for me anyway. Cheers!

Abrimos una ventana de terminal desde el menú **Aplicaciones -> Accesorios -> Terminal**.


**sudo apt-get install tracker-utils**

Pulsamos la tecla Enter **y** Si a todo. Se instalará las utilidades para el Tracker.

**At this point I was notified that it was already installed. If you upgraded you'll probably get the same message.**

Despues tecleamos:

**tracker-processes -r**

Pulsamos Enter de nuevo. **Y** ya esta solucionado.

I could have translated it but it's kinda fun doing it in a different language.

I have to agree with Miguel, who responded:

**"Perfecto.Solucionado.Gracias.Muchas gracias."**

You don't have to know Spanish to figure out He's pretty happy about the solution.

---

### Post by realmoonstruck on 2009-05-17
***Gracias, que hizo el truco ...):P***

---

### Post by jonbey on 2009-05-28
Excellent, this has been bugging me for a while now.

---

### Post by Andy06 on 2009-05-29
Don't mean to hijack the thread but where exactly ARE the indexing options in 9.04. They were under system up until 8.10 but have disappeared now. Even trying to run tracker-preferences bring nothing up. Am working from a clean install

---

### Post by realmoonstruck on 2009-05-29
Don't know about a fresh install cause i've been upgrading from hardy to jaunty.
I still have **search and indexing **under **System->Administration**.
An applet that can be added to the panel can be found with the name **Search for Files...**
but if **tracker** is not installed by default in jaunty then it can be easily installed from synaptic.

---

