---
title: "Now what? --wireless continue to trouble me!"
date: 2007-01-26
forum: Networking &amp; Wireless
---

### Post by hopestorm on 2007-01-26
Wireless worked before, after I accidentally upgrade to Feisty, wireless is gone.
I did what I was advised in this forum (/bow):
 
(1) downloaded the right linux-reistricted-modules, no help
(2) set up ndiswrapper using product CD. 
     $ndiswrapper -l
          Installed ndis drivers:
          airplus driver present, hardware present.

     $iwconfig
          lo        no wireless extensions.
          eth0      no wireless extensions.
          wlan0     no wireless extensions.
(3) run wifi-radar.
       lo        Interface doesn't support scanning.
       eth0      Interface doesn't support scanning.
       wlan0     Interface doesn't support scanning.
       lo        no wireless extensions.
       eth0      no wireless extensions.
      wlan0     no wireless extensions.

Now what else can I try? 
Remove feisty? if it's possible, I would do it, but how?

---

### Post by lhtown on 2007-01-27
Wow, an accidental upgrade to Fiesty... and I couldn't get it to work when I TRIED.

Fiesty is still pretty early in the game. If you hang on, it may start working.

I don't know of any real way to downgrade reliably. You should just reinstall your system. Trying to downgrade would, in my opinion likely leave you with a lot of problems that would take some time to work through and maybe even an unusable system in which case you would have to reinstall anyway.

If you are prone to accidental upgrades, you might try installing your operating system in a separate partition from your home directory so that you can reinstall without having to repopulate your home directory.

---

