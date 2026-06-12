---
title: "ubuntu software center"
date: 2011-08-11
forum: New to Ubuntu
---

### Post by Aitashan on 2011-08-11
how do u remove and reinstall ubuntu software center

---

### Post by imortalninja161 on 2011-08-11
```
sudo apt-get purge software-center
```There ya go buddy then 

```
sudo apt-get install software-center
```

This all need's to be typed in the terminal

---

### Post by Aitashan on 2011-08-11
purge not working

---

### Post by imortalninja161 on 2011-08-11
is there a error message

---

### Post by amjjawad on 2011-08-11
> **Aitashan said:**
> how do u remove and reinstall ubuntu software center

Why you want to remove it and then re-install it?
Any good reason for that?

If you don't like it, use Synaptic or Terminal.

If you are trying to do some experiments, that's different story.

---

### Post by XDevHald on 2011-08-11
> **Aitashan said:**
> purge not working

Just run: sudo apt-get purge (in terminal) and you're good to go.

---

### Post by Aitashan on 2011-08-11
> **amjjawad said:**
> Why you want to remove it and then re-install it?
Any good reason for that?

If you don't like it, use Synaptic or Terminal.

If you are trying to do some experiments, that's different story.
  
ID3 tag manipulation library with full support for reading ID3v1, ID3v1.1, ID3v2.2, ID3v2.3, and ID3v2.4 tags, as well as support for writing ID3v1, ID3v1.1, and ID3v2.4 tags.

this has caused me to re install ot as when i access the centre it asks me to repair it but the update manager is unable to do so

---

### Post by Aitashan on 2011-08-11
it says unmet dependences

---

### Post by amjjawad on 2011-08-11
> **Aitashan said:**
> ID3 tag manipulation library with full support for reading ID3v1, ID3v1.1, ID3v2.2, ID3v2.3, and ID3v2.4 tags, as well as support for writing ID3v1, ID3v1.1, and ID3v2.4 tags.

this has caused me to re install ot as when i access the centre it asks me to repair it but the update manager is unable to do so

Update Manager doesn't fix things, it updates your system :)

The commands are correct so try these commands and post back in case you get any error message.
Alternatively, you can remove "Software-Center" from Synaptic.

I never use Software-Center, I always use The Terminal or Synaptic because simply these two ways are less headache and problems ;)

---

### Post by amjjawad on 2011-08-11
> **Aitashan said:**
> it says unmet dependences

Try to remove it form Synaptic.
Just type "Software-Center" on the box and choose to remove ALL.

Is this Wubi or Normal Installation?

---

### Post by Aitashan on 2011-08-11
normal through live usb

---

### Post by amjjawad on 2011-08-11
> **Aitashan said:**
> normal through live usb

So, what happened? did you manage to fix it?

---

