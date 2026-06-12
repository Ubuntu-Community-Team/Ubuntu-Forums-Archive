---
title: "Youtube etc. performance with 9.10 very poor"
date: 2009-11-02
forum: New to Ubuntu
---

### Post by TygerTung on 2009-11-02
I have just done a fresh install of 9.10 and the performance while trying to watch online videos like youtube is very poor.

The frame rate is very low and it is very jerky. What could cause this? It went fine on 9.04 and it works fine on windows.

My computer is reasonably powerful with P4 3.2GHz with 1.5 Gigabyte of ram.

I don't know why it should be doing this!

---

### Post by Zzl1xndd on 2009-11-02
Likely a silly question on my part, but after the fresh install your did reinstall your Video drivers right? (Providing your are using an ATI or Nvidia card)

---

### Post by TygerTung on 2009-11-02
No, I didn't, it usually seems to do it automatically.

I have a ATI 9600 Pro or similar.

How do I go about installing a driver?

---

### Post by Zzl1xndd on 2009-11-02
It would normally be listed under System > Administraton > Hardware

---

### Post by TygerTung on 2009-11-02
The only one which seems similar to the one you mention is 'Hardware Drivers' and I went into that, and it whizzed for a bit searching for drivers and then when you go into it, it says 'No proprietary drivers are in use in this system'

Maybe my video card is too ancient to be able to get drivers anymore in these late model ubuntu's

---

### Post by soapytheclown on 2009-11-02
Are you running 64bit? it seems that on 64bit running the flashnonfree from the repository is pretty pathetic - there should be a tutorial somewhere to install 64bit if this is the case for you.

---

### Post by philinux on 2009-11-02
> **TygerTung said:**
> I have just done a fresh install of 9.10 and the performance while trying to watch online videos like youtube is very poor.

The frame rate is very low and it is very jerky. What could cause this? It went fine on 9.04 and it works fine on windows.

My computer is reasonably powerful with P4 3.2GHz with 1.5 Gigabyte of ram.

I don't know why it should be doing this!

If you're running 64 bit then see below.

Interesting benchmark.
[http://www.tuxradar.com/content/ubun...bit-benchmarks](http://www.tuxradar.com/content/ubun...bit-benchmarks)

Search synaptic and remove all other flash.

1. get the plug in from adobe. [http://get.adobe.com/flashplayer/thankyou/?installer=Flash_Player_10_for_Linux_(.tar.gz](http://get.adobe.com/flashplayer/thankyou/?installer=Flash_Player_10_for_Linux_(.tar.gz)) and save to Desktop.

2. Right click the archive and choose extract here.

3. copy the file libflashplayer.so to ~/.mozilla/plugins
You will have to first create the plugins folder.

---

### Post by TygerTung on 2009-11-02
Nah it's only 32 bit.

I'll try changing the flash player though, see what happens.

---

### Post by philinux on 2009-11-02
> **TygerTung said:**
> Nah it's only 32 bit.

I'll try changing the flash player though, see what happens.

The only flash player worth installing is probably the one you've got. flashplugin-nonfree

Have a look in firefox. Type this in adddress bar ```
about:plugins
```

Post back what it says about flash.

---

### Post by kevinman on 2009-11-05
Hi, 

I got the same problem. My Ubuntu version is 9.10 with all updates installed and my nvidia driver version is 190.42.

My flash plugin version is 

[IMG]http://img30.imageshack.us/img30/2403/flashrg.png[/IMG]
[http://img30.imageshack.us/img30/2403/flashrg.png](http://img30.imageshack.us/img30/2403/flashrg.png)

It's not only youtube, the performance of other video playbacks are also not satisfying no matter what video player is used. I don't have this kind of problems under windows.

---

### Post by philinux on 2009-11-05
Right click on top or bottom panel. Select CPU frequency scaling. Once added left click it and choose performance. Now try flash.

---

