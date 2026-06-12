---
title: "I removed Chrome but have a lot of leftovers."
date: 2010-05-02
forum: New to Ubuntu
---

### Post by captgadget on 2010-05-02
I removed chrome with this: sudo aptitude purge google-chrome-beta
but after doing a search of the computer I have tons of chrome stuff still on my hard drive. How can I get rid of all that stuff?

---

### Post by snova on 2010-05-02
> **captgadget said:**
> I removed chrome with this: sudo aptitude purge google-chrome-beta
but after doing a search of the computer I have tons of chrome stuff still on my hard drive. How can I get rid of all that stuff?

Where in particular?

I believe Chrome stores its configuration files in **~/.config/google-chrome** and its cache in **~/.cache/google-chrome**; both of those should be removed without too much issue. Elsewhere on your system, though, would be strange.

---

### Post by WinterRain on 2010-05-02
```
sudo apt-get clean && sudo apt-get autoremove
```

---

### Post by captgadget on 2010-05-02
I already ran both of these.

---

### Post by WinterRain on 2010-05-02
> **captgadget said:**
> I already ran both of these.

I think someone mentioned that there was a slight issue with autoremove, but I'm not 100% sure.

---

### Post by captgadget on 2010-05-02
I don't know if this will help but here is a screen shot of what I found.

---

### Post by WinterRain on 2010-05-02
Did you delete the chrome config files in /home?

---

### Post by captgadget on 2010-05-02
Sorry, don't know how to do that one.

---

### Post by WinterRain on 2010-05-02
> **captgadget said:**
> Sorry, don't know how to do that one.

Just go to your home folder and do Ctrl-H. You will then see folders beginning with a (.)

I'm not sure if chrome's folder will be obvious, but you could also check in the .config folder. It is safe to delete the chrome folder once you find it.

---

### Post by captgadget on 2010-05-02
OK, thank you

---

### Post by snova on 2010-05-02
> **captgadget said:**
> I don't know if this will help but here is a screen shot of what I found.

That doesn't look like Google Chrome to me... if you use Firefox, you might find you have a lot of "chrome" directories in ~/.mozilla- the word refers to the user interface of a browser. I found I have fifteen "chrome" directories, and all but one seems to all be a different addon.

---

