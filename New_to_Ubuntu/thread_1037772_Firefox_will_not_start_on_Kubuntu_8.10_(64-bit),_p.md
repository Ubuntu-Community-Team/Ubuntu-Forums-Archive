---
title: "Firefox will not start on Kubuntu 8.10 (64-bit), problem with Show Desktop widget"
date: 2009-01-12
forum: New to Ubuntu
---

### Post by david6 on 2009-01-12
Hi,

I recently installed the 64-bit version of Kubuntu 8.10.

For the most part, it runs fine. However, I cannot get Firefox to run.

I installed Firefox using:

```
sudo apt-get install firefox
```

then I opened Konsole, and tried to start it by typing firefox - nothing happened.

> firefox
>

I tried launching Firefox in safe mode

```
firefox -safe-mode
```

Same result as before.

I also tried launching the error console, but again nothing happened.

```
firefox -jsconsole
```

When I display the help by typing:

```
firefox --help
```

I do not see any option to run Firefox in debug mode.

Finally, I tried launching Firefox by Choosing:

K button > Internet > Firefox Fox Web Browser

The Firefox icon appears on the main panel/taskbar very briefly, and that is it.

So, can somebody advise what I need to do to get Firefox working on my system. Konqueror runs fine, but I'm not very fond of it.

I also have another problem.

Sometimes, when I click the Show Desktop widget on the main panel to show the desktop, the icons on the main panel become blurred and distorted (I don't know exactly how to describe it). If anybody knows what I'm talking about, can you suggest a fix.

Thanks,

David

---

### Post by blazemore on 2009-01-12
So when you run firefox from a terminal, what output do you get?

---

### Post by ajgreeny on 2009-01-12
I don't see why it should stop it running completely, but try renaming the .mozilla folder in home and a new config and profile will be made when you restart (if it will restart, of course).  You can then copy back the important things like your bookmarks (now places.sqlite, not bookmarks.html any more) etc etc.

---

### Post by david6 on 2009-01-12
> **ajgreeny said:**
> I don't see why it should stop it running completely, but try renaming the .mozilla folder in home and a new config and profile will be made when you restart (if it will restart, of course).  You can then copy back the important things like your bookmarks (now places.sqlite, not bookmarks.html any more) etc etc.

Hi,

I renamed the .mozilla folder, and Firefox started.

Previously, when I tried to run it from Konsole, absolutely nothing happened:

```
davidr@dt20:~$ firefox
davidr@dt20:~$
```

Thanks,

David

---

