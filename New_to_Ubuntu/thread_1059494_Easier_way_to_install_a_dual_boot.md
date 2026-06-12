---
title: "Easier way to install a dual boot"
date: 2009-02-03
forum: New to Ubuntu
---

### Post by HittingSmoke on 2009-02-03
I need a Windows install to install apps on my Windows Mobile phone. I looked at the instructions for setting up a dual boot with Linux installed as the first OS and fixing GRUB after using a Live CD.

There's got to be some easier way to do this that I'm missing. I tried the directions [here]("http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm") but the error that I got doesn't match up with the article. When I select my NTFS partition it tells me I need to format my Ubuntu root partition to install the boot manager. Is there maybe some program like nLite that I can run in Vbox to build a Windows install that is friendly with a dual boot setup? I'm pissed off enough as it is that I have to dual boot to get my phone to work right...

---

### Post by sandyd on 2009-02-03
have you tried this? (yes, i have windows mobile too)

install activesync in wine.
THEN install the app

the app will drop the cab file somewhere, go hunting for it in ~/.wine. Once you find it , just transfer the cab to windows mobile device. 

you can also try cabextract (but with limited results)

p.s. (active sync doesn't run in WINE, its just so you can get the cab)

---

### Post by HittingSmoke on 2009-02-03
> **carlee said:**
> have you tried this? (yes, i have windows mobile too)

install activesync in wine.
THEN install the app

the app will drop the cab file somewhere, go hunting for it in ~/.wine. Once you find it , just transfer the cab to windows mobile device. 

you can also try cabextract (but with limited results)

p.s. (active sync doesn't run in WINE, its just so you can get the cab)

Well installing apps via ActiveSync isnt the only thing I'm refering to. I like to use cooked ROMs and the like on my phone. It may or may not be possible to run these under WINE to flash my phone, but I sure as hell am not going to risk bricking my phone to try it.

---

