---
title: "Graphics card update"
date: 2009-11-26
forum: New to Ubuntu
---

### Post by judith_sw on 2009-11-26
Hi,

I've had all sorts of problems with the graphics card on my HP2133 (Via Chrome9). In another thread I explained how I would like to use BBC iPlayer, but while sound was OK, playback was jumpy and out of sync with sound. I have now installed Ubuntu 9.04, replacing 9,10 as there seems to be better support for the graphics card. I have applied the VGA fix successfully. 

I have now downloaded to desktop the following 2 graphics card updates, but have no idea how to install them! I was advised this afternoon that they should be .tar files rather than the .tgz files that I had downloaded - now renamed.

Please could someone explain in easy steps how to install them - iPlayer is still very slow andout of sync with the sound.

/home/judith/Desktop/5.74.33.86a-u904-50937.tar
/home/judith/Desktop/5.74.33.86a-u904-50937.tar

Thank you!!!

---

### Post by sandyd on 2009-11-26
> **judith_sw said:**
> Hi,

I've had all sorts of problems with the graphics card on my HP2133 (Via Chrome9). In another thread I explained how I would like to use BBC iPlayer, but while sound was OK, playback was jumpy and out of sync with sound. I have now installed Ubuntu 9.04, replacing 9,10 as there seems to be better support for the graphics card. I have applied the VGA fix successfully. 

I have now downloaded to desktop the following 2 graphics card updates, but have no idea how to install them! I was advised this afternoon that they should be .tar files rather than the .tgz files that I had downloaded - now renamed.

Please could someone explain in easy steps how to install them - iPlayer is still very slow andout of sync with the sound.

/home/judith/Desktop/5.74.33.86a-u904-50937.tar
/home/judith/Desktop/5.74.33.86a-u904-50937.tar

Thank you!!!
write down these instructions before continueing
Press ALT+F1, then login
```

sudo killall kdm
sudo killall gdm
cd ~/Desktop
tar xvf /home/judith/Desktop/5.74.33.86a-u904-50937.tar
cd 5.7*
./configure
make
sudo make install

```

---

### Post by judith_sw on 2009-11-27
Hi,

Thought that was going to be it, but ... This is the output I received - the file seems to be recognised, it's the installation that seems to be problematic:


judith@judith-laptop:~$ cd ~/Desktop
judith@judith-laptop:~/Desktop$ tar xvf /home/judith/Desktop/5.74.33.86a-u904-50937.tar
5.74.33.86a-u904-50937/
5.74.33.86a-u904-50937/xorg.conf
5.74.33.86a-u904-50937/vuninstall
5.74.33.86a-u904-50937/vinstall
5.74.33.86a-u904-50937/DRM_Code/
5.74.33.86a-u904-50937/DRM_Code/unichrome_2.6.27/
5.74.33.86a-u904-50937/DRM_Code/unichrome_2.6.27/via_drv.h
5.74.33.86a-u904-50937/DRM_Code/unichrome_2.6.27/via_video.c
5.74.33.86a-u904-50937/DRM_Code/unichrome_2.6.27/via_3d_reg.h
5.74.33.86a-u904-50937/DRM_Code/unichrome_2.6.27/via_map.c
5.74.33.86a-u904-50937/DRM_Code/unichrome_2.6.27/README.txt
5.74.33.86a-u904-50937/DRM_Code/unichrome_2.6.27/via_drm.h
5.74.33.86a-u904-50937/DRM_Code/unichrome_2.6.27/via_dma.c
5.74.33.86a-u904-50937/DRM_Code/unichrome_2.6.27/via_mm.c
5.74.33.86a-u904-50937/DRM_Code/unichrome_2.6.27/via_dmablit.h
5.74.33.86a-u904-50937/DRM_Code/unichrome_2.6.27/via_drv.c
5.74.33.86a-u904-50937/DRM_Code/unichrome_2.6.27/via_dmablit.c
5.74.33.86a-u904-50937/DRM_Code/unichrome_2.6.27/via_verifier.h
5.74.33.86a-u904-50937/DRM_Code/unichrome_2.6.27/Makefile
5.74.33.86a-u904-50937/DRM_Code/unichrome_2.6.27/via_verifier.c
5.74.33.86a-u904-50937/DRM_Code/unichrome_2.6.27/via_irq.c
5.74.33.86a-u904-50937/DRM_Code/chrome9_2.6.27_28/
5.74.33.86a-u904-50937/DRM_Code/chrome9_2.6.27_28/via_chrome9_dma.c
5.74.33.86a-u904-50937/DRM_Code/chrome9_2.6.27_28/via_chrome9_verifier.c
5.74.33.86a-u904-50937/DRM_Code/chrome9_2.6.27_28/via_chrome9_verifier.h
5.74.33.86a-u904-50937/DRM_Code/chrome9_2.6.27_28/via_chrome9_drv.c
5.74.33.86a-u904-50937/DRM_Code/chrome9_2.6.27_28/via_chrome9_drm.h
5.74.33.86a-u904-50937/DRM_Code/chrome9_2.6.27_28/via_chrome9_mm.c
5.74.33.86a-u904-50937/DRM_Code/chrome9_2.6.27_28/via_chrome9_drv.h
5.74.33.86a-u904-50937/DRM_Code/chrome9_2.6.27_28/via_chrome9_mm.h
5.74.33.86a-u904-50937/DRM_Code/chrome9_2.6.27_28/Makefile
5.74.33.86a-u904-50937/DRM_Code/chrome9_2.6.27_28/via_chrome9_3d_reg.h
5.74.33.86a-u904-50937/DRM_Code/chrome9_2.6.27_28/via_chrome9_drm.c
5.74.33.86a-u904-50937/DRM_Code/chrome9_2.6.27_28/via_chrome9_dma.h
5.74.33.86a-u904-50937/bin/
5.74.33.86a-u904-50937/bin/via_drv.so
5.74.33.86a-u904-50937/bin/libGL.so.1.2.via_unichrome
5.74.33.86a-u904-50937/bin/via_unichrome_dri.so
5.74.33.86a-u904-50937/bin/via_chrome9.ko
5.74.33.86a-u904-50937/bin/libGL.so.1.2.via_chrome9
5.74.33.86a-u904-50937/bin/via.ko
5.74.33.86a-u904-50937/bin/via_chrome9_dri.so
5.74.33.86a-u904-50937/Release_notes
judith@judith-laptop:~/Desktop$ cd 5.7*
judith@judith-laptop:~/Desktop/5.74.33.86a-u904-50937$ ./configure
bash: ./configure: No such file or directory
judith@judith-laptop:~/Desktop/5.74.33.86a-u904-50937$ make
make: *** No targets specified and no makefile found. Stop.
judith@judith-laptop:~/Desktop/5.74.33.86a-u904-50937$ sudo make install
[sudo] password for judith: 
make: *** No rule to make target `install'. Stop.

Is there something I've missed out here?

Thank you!

---

