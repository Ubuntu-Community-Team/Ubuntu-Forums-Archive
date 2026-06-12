---
title: "Direct3D / wine problem"
date: 2009-11-22
forum: New to Ubuntu
---

### Post by MrReaper on 2009-11-22
Hello :) 
First post here (although I am Linux user (Mandriva-PC, eeebuntu-NB) for over year now, so far without problems ^^ )

I'm trying to get Direct3D working in wine (Diablo II LoD to be specific).

My PC is Asus Eee 901 (Atom270, Intel 945GSE chipset).

I've been running eeebuntu base 3.0 until last week and everything went really well (no performance issues even with D3D active). Now I'm running Ubuntu 9.10 and:
1) performance dropped somehow, even using DD. Graphics seem to be the bottleneck here (I assume it's graphic driver problem, since eeebuntu worked flawlessly).
2) I'm not getting option to choose D3D in D2VidTest. Seems like graphic driver issue to me as well.

Here is some info (xorg.conf - I read it works in Karmic if manually created):

```
Section "Device"
    Identifier "Intel Corporation Mobile Integrated Graphics Controller"
    Driver "intel"
EndSection
``````
jonas@REAP:~$ glxinfo | grep render
direct rendering: Yes
OpenGL renderer string: Mesa DRI Intel(R) 945GME GEM 20090712 2009Q2 RC3 x86/MMX/SSE2
``````
jonas@REAP:~$ egrep "(GLX|DRI)" /var/log/Xorg.0.log
(==) AIGLX enabled
(II) Loading extension GLX
(II) Loading extension XFree86-DRI
(II) Loading extension DRI2
(II) intel(0): [DRI2] Setup complete
(II) intel(0): direct rendering: DRI2 Enabled
(II) AIGLX: enabled GLX_MESA_copy_sub_buffer
(II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
(II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
(II) AIGLX: Loaded and initialized /usr/lib/dri/i915_dri.so
(II) GLX: Initialized DRI2 GL provider for screen 0
```Everything looks fine to me but again, I've never dealt with graphic issues so far.

Can anyone help me please :)

If you need any more information, just hit me with command line :)

---

### Post by MrReaper on 2009-11-23
Bump :) Any ideas please?

---

### Post by MrReaper on 2009-11-23
Quick bumpie before I head to work :)

---

### Post by ankspo71 on 2009-11-23
Hi,
I'm not sure what the technical differences are between eeebuntu and Ubuntu, so I recommend that you use this advice as a last resort!!!
If the eeebuntu base is a stripped down gnome desktop... like I think it is, then you might have much better luck installing the Ubuntu mini cd OR, downloading the alternate installer ubuntu cd, and at startup press alt4 (I think) and choose the command line only installation. Either way you choose, you will then want to install your desktop.
Use this code for an example install.... 
```
sudo apt-get install gdm gnome-core network-manager synaptic jockey-gtk gdebi file-roller gnome-system-tools firefox-3.5 wine gedit
```That should get you started, and it's just the basics, but you can add anything you want to that. Here is the link to the mini Ubuntu cd [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD) . You can find the alternate install cd at any Ubuntu download mirror. 
Hope this helps,
James.

---

### Post by MrReaper on 2009-11-23
> **ankspo71 said:**
> Hi,
I'm not sure what the technical differences are between eeebuntu and Ubuntu, so I recommend that you use this advice as a last resort!!!
If the eeebuntu base is a stripped down gnome desktop... like I think it is, then you might have much better luck installing the Ubuntu mini cd OR, downloading the alternate installer ubuntu cd, and at startup press alt4 (I think) and choose the command line only installation. Either way you choose, you will then want to install your desktop.
Use this code for an example install.... 
```
sudo apt-get install gdm gnome-core network-manager synaptic jockey-gtk gdebi file-roller gnome-system-tools firefox-3.5 wine gedit
```That should get you started, and it's just the basics, but you can add anything you want to that. Here is the link to the mini Ubuntu cd [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD) . You can find the alternate install cd at any Ubuntu download mirror. 
Hope this helps,
James.

I assume you recommend this to improve performance? 
Thanks for advice, I am definitely going to try it but first I would like to solve D3D problem so that I know it's going to work afterwards. I don't want to switch back to eeebuntu but I still want to enjoy my D3D games :)

---

### Post by ankspo71 on 2009-11-24
Hi,
Yes, that is to increase performance only, as you would have no extra services or applications running in the background. This advice would only be helpful to you if the problem you are having is performance related. Sorry I couldn't be of more help. 
James

---

