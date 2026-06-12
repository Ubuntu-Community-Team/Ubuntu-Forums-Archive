---
title: "Getting Back my White Ubuntu Logo"
date: 2009-12-31
forum: New to Ubuntu
---

### Post by neu5eeCh on 2009-12-31
This is probably trivial, but it helps me learn how Linux works...  Last week I installed the Kubuntu-Desktop. Ever since, my nice, simple white ubuntu splash screen logo has been replaced by a blue Kubuntu splash screen. The kubuntu splash screen is then followed by the brown (spotlit) Ubuntu Splashscreen.  How do I get rid of the Kubuntu splash screen and get back that nice, clean, white Ubuntu logo?  Just figured it out (for the next beginner) - Installed USplash using Ubuntu Software Center. USplash installs the Startup Manager. Opening that, I found the option allowing me to restore the original Gnome Logo.

---

### Post by marco123 on 2010-01-08
What I do after installing kubuntu-desktop is to remove kubuntu-artwork-usplash using apt, or you can use synaptic.  Seems to work every time for me.

---

### Post by sandyd on 2010-01-08
```

sudo update-alternatives --config usplash-artwork.so

```
i believe its the one called
```

/usr/lib/usplash/usplash-theme-ubuntu.so

```

---

