---
title: "Desktop Memory (Not what you're thinking)"
date: 2009-03-01
forum: New to Ubuntu
---

### Post by davbran on 2009-03-01
I recently moved into Kubuntu 8.10, and after several gui crashes I decided to try Kubuntu 8.04.2 but found myself in Ubuntu 8.04.2. I found it was very snappy, and while I am not fond of Gnome, I decided to live with it for performance sake. Now I have had a couple reasons to reboot, and a couple crashes of the power variety. During these I noticed something very different about the Gnome/KDE worlds, KDE if you crash/reboot will have all your previous windows (if not sessions) waiting for you. Gnome will not. My questions are, how do I make gnome function in this manner, or is this something inherent in KDE alone?

Thanks,
Davbran

---

### Post by Bodsda on 2009-03-01
I believe there is an option to remember your open applications in 

System >> Admin >> Sessions

Im not on gnome at the moment so i cant be sure, it may be 

System >> Pref >> Sessions

i think it is in one of the session window's tab.

Also please make your thread titles more specific like 

**How to make gnome remember opened applications**

rather then just telling people your being obscure, thank you

Bodsda

---

### Post by JoshuaRL on 2009-03-01
> **davbran said:**
> I recently moved into Kubuntu 8.10, and after several gui crashes I decided to try Kubuntu 8.04.2 but found myself in Ubuntu 8.04.2. I found it was very snappy, and while I am not fond of Gnome, I decided to live with it for performance sake. Now I have had a couple reasons to reboot, and a couple crashes of the power variety. During these I noticed something very different about the Gnome/KDE worlds, KDE if you crash/reboot will have all your previous windows (if not sessions) waiting for you. Gnome will not. My questions are, how do I make gnome function in this manner, or is this something inherent in KDE alone?

Thanks,
Davbran

If snappy is what you're wanting, you could try out XFCE.  It also has an option to save sessions too.  So if it crashes, everything should just jump right up.

To get it, search in Synaptic or Adept for:
```

xubuntu-desktop

```
Or, in the terminal:
```

sudo aptitude install xubuntu-desktop

```
That will install the whole desktop environment, the whole Xubuntu shebang and user experience.  I think Thunar (XFCE file manager) alone is worth the price of admission.  XFCE is a lightweight desktop environment that aims to be full featured too.  It has its own compositing manager, and runs pretty quick.

---

### Post by davbran on 2009-03-01
Bodsda - Thanks, and I will take it under advisement, I wasn't sure how to phrase it, it's not a feature I ever thought to be asking about.

JoshuaRL - Thanks, I will look into Xubuntu as well.

---

### Post by irfan9727 on 2009-03-01
Yeah, in GNOME, System->Preferences->Sessions works!
Just click the "Options" tab -> Check "Automatically remember currently running aplications". Thanks Bodsda!

---

### Post by davbran on 2009-03-02
I tried it, and while it remembers the sessions, it doesn't remember the windows that were open. Which is fine, it was just a convenience that I liked from KDE.

---

### Post by egalvan on 2009-03-02
> **davbran said:**
>  it was just a convenience that I liked from KDE.

Yes, this is one of the "problems" with the different Desktop Environment...

A convenience in one may or may not be present in another.

I like, and use, KDE,
and also Gnome
and also XFCE (Xubuntu)

I have all three installed on most of my Linux machines, and switch between them.
I just wish I was programmer enough to migrate features from one to the other...

---

