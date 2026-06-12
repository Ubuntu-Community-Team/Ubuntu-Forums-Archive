---
title: "Problems with DVDs and WMV"
date: 2009-04-08
forum: New to Ubuntu
---

### Post by Ejene on 2009-04-08
I'm running Ubuntu 8.10 on a Compaq Presario V6000. I have the restricted medibuntu repositories, and my nvidia card is up to date. 

However, since I reinstalled ubuntu 8.10, my dvds haven't worked and I can't get wmv files to play. They all worked under 8.10 before, but now I can't figure out what I haven't done to let them work. They don't work under vlc or mplayer, either. 
With DVDs, Totem tells me "Error Occured Could not read from source" vlc starts to respond and then stops and mplayer plays some garbled video. 

With WMVs, Totem tells me there is a problem with encryption/decryption, vlc is garbled video, and mplayer is garbled video and sound.

Any ideas? I'm at a loss for what else to download.

---

### Post by LowSky on 2009-04-08
libdvdcss will play dvd's
w32codecs for codec support

get both from here

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by fooman on 2009-04-08
probably just need to install the ubuntu-restricted-extras package....that should get you all the codecs you need.

open a terminal (applications > accessories > terminal) and type or copy/paste the following:

```
sudo apt-get install ubuntu-restricted-extras
```then press enter.

hope that helps.

---

### Post by Ejene on 2009-04-08
Thanks for the help, but I've already installed those. I ran all of it again, just in case, but it all still doesn't work.

---

### Post by unc0nn3ct3d on 2011-02-26
I'm running into this problem, I have all of the restricted extra's installed, w64 codecs and libdvdcss2.  But I'm still seeing a garbled image when I try to play


Gnome Mplayer gives me this error message: Failed to open VDPAU backend libvdpau_nvidia.so: cannot open shared object file: No such file or directory

Movie Player gives me this error message: The stream is encrypted and decryption is not supported.

this problem is only with wmv files, all else work fine, I'm running an AMD E350 with an ATI 6130.

I'm seeing the following error messages a lot:

[wmav2 @ 0x7f2a2cd79020]overflow in spectral RLE, ignoring?,?% 0 0 
[wmav2 @ 0x7f2a2cd79020]overflow in spectral RLE, ignoring
[wmv3 @ 0x7f2a2cd79020]Bits overconsumption: 29166 > 291600.5% 340 0 
[wmv3 @ 0x7f2a2cd79020]concealing 318 DC, 318 AC, 318 MV errors

---

### Post by Perfect Storm on 2011-02-26
> Gnome Mplayer gives me this error message: Failed to open VDPAU backend libvdpau_nvidia.so: cannot open shared object file: No such file or directory


Install: libvdpau1 and vdpau-va-driver

---

### Post by unc0nn3ct3d on 2011-02-28
thanks, I had the first installed but not the second.. I will give it a go again and see if it works.. thanks again

---

