---
title: "How do I change The default applications in Ubuntu?"
date: 2009-04-17
forum: New to Ubuntu
---

### Post by scrypt on 2009-04-17
I have just installed Kubuntu-Desktop Into my Ubuntu instalation.

But it seems that now some of Kubuntu's applications have become the default packages when it comes to opening things such as KTorrent for donwnloading Torrents!

How do I change my settings so that  Ubuntu's original default applications are used instead of Kubuntu's

Since I installed Kubuntu-Desktop. KTorrent is now used as the default torrent downloader.

But I want to revert back to Transmission as my Default Torrent downloader.

It seems not only KTorrent has become the default application. But also various other Kubuntu applications have took over as the main applications used opening torrents, music files etc etc...

How can I change all the original Ubuntu applications as the default applications used when using any file or program in future??

---

### Post by swoll1980 on 2009-04-17
Do you want to switch back to Gnome?

---

### Post by scrypt on 2009-04-17
No I want to keep the installed Kubuntu applications along side my Ubuntu ones, just to chack them out.

I did choose gdm as my default desktop when installing Kubuntu-Desktop.

I just want to have trnasmission as my default torrent downloader.

and also all the original ubuntu applications as the default apps that are used when i want to open a file or program??

---

### Post by scrypt on 2009-04-17
I see that if I right click on a file/torrent I can choose what I want to use to open it.

But transmission is no longer there.
so when i choose:- "open with another application"

Where would I find transmision so I can have it as the default torrent downloader??

---

### Post by swoll1980 on 2009-04-17
> **scrypt said:**
> 

Where would I find transmision so I can have it as the default torrent downloader??

/usr/bin

---

### Post by Mulenmar on 2009-04-17
Assuming for a moment that my memory is working today, from "Open with Other Application" browse to /usr/bin.

There should be a file named "transmission", if I'm not mistaken. *crosses fingers*

---

### Post by llamabr on 2009-04-17
It ought to be in /usr/bin

to find any application, from terminal, type:

```
which transmission
```

and bash will tell you its location

---

### Post by Agent.Logic_ on 2009-04-17
I'm not familiar with KDE, but if you have an option to enter a custom "command" value when trying to assign a default application, you can enter
```

transmission %F

```

That will do the trick.

---

### Post by scrypt on 2009-04-17
It is indeed in /usr/bin

Thank-you for the clear replies guys...

That has solved my question..

---

