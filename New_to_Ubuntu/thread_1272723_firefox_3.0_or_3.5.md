---
title: "firefox 3.0 or 3.5"
date: 2009-09-22
forum: New to Ubuntu
---

### Post by amschmid on 2009-09-22
I have just installed Kubuntu 9.04 and used the built in installer to add firefox.  I was careful tomake sure I installed the latest version 3.5, but under help-about, it says that it is still only 3.0.  If I search for firefox again in the ad/remove program thing, there are about five things that show that they are installed including a few packages for firefox and both 3.0 and 3.5.  How do I use the latest firefox?

---

### Post by lovinglinux on 2009-09-22
> **amschmid said:**
> I have just installed Kubuntu 9.04 and used the built in installer to add firefox.  I was careful tomake sure I installed the latest version 3.5, but under help-about, it says that it is still only 3.0.  If I search for firefox again in the ad/remove program thing, there are about five things that show that they are installed including a few packages for firefox and both 3.0 and 3.5.  How do I use the latest firefox?

```
sudo apt-get install firefox-3.5
```

The launch it from the Internet menu. It will be listed as Shiretoko Web Browser, which is the exact same thing with a different name.

If you want other methods of installation than see [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567).

---

### Post by t0p on 2009-09-22
> **amschmid said:**
> I have just installed Kubuntu 9.04 and used the built in installer to add firefox.  I was careful tomake sure I installed the latest version 3.5, but under help-about, it says that it is still only 3.0.  If I search for firefox again in the ad/remove program thing, there are about five things that show that they are installed including a few packages for firefox and both 3.0 and 3.5.  How do I use the latest firefox?

Run the following command in a terminal:

```
which firefox-3.5
```

You'll get a response something like

```
/usr/bin/firefox-3.5
```

You can put a launcher on your panel or desktop, using that path as the command for the launcher.

---

### Post by amschmid on 2009-09-22
I ran the code and it said that 3.5 is the most up to date version, as if I already had it, but firefox is still 3.0 and I don't see shiretoko

---

### Post by t0p on 2009-09-22
> **amschmid said:**
> I ran the code and it said that 3.5 is the most up to date version, as if I already had it, but firefox is still 3.0 and I don't see shiretoko

Did you see my post above?  You *do* have 3.5 already.

On your computer, Firefox 3.5 is called **firefox-3.5**.  You can run it by typing into a terminal the command:

```
firefox-3.5
```Alternatively, you can make a launcher for it, to put on your desktop or panel.  Or you can edit your menu, replacing the current Firefox entry with one that will run "firefox-3.5".  You may need to specify its path, which is probably /usr/bin/firefox-3.5.

If you run "firefox", it will run version 3.0.  If you want to run 3.5, you must specify "firefox-3.5".

---

### Post by amschmid on 2009-09-22
got it, thanks

---

