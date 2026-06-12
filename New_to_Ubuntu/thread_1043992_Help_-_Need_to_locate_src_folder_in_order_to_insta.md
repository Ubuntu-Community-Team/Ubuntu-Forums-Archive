---
title: "Help - Need to locate /src/ folder in order to install -intel patch"
date: 2009-01-19
forum: New to Ubuntu
---

### Post by suncoolsu on 2009-01-19
Hi All,
I have a 1535 dell studio with AUO LCD. There was a bug in xserver-xorg-video-intel which resulted in WSoD. 

Well! the good news is that it has been solved and the patch has been released. [http://launchpadlibrarian.net/21219729/104_i830-vbt-timing-hack.patch](http://launchpadlibrarian.net/21219729/104_i830-vbt-timing-hack.patch)
this is the bug link: [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/297245](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/297245)

> diff -Nurp patched/src/i830_bios.c working/src/i830_bios.c
--- patched/src/i830_bios.c	2009-01-14 12:36:59.000000000 -0800
+++ working/src/i830_bios.c	2009-01-14 12:40:10.000000000 -0800
@@ -221,13 +221,13 @@ i830_bios_get_panel_mode(ScrnInfoPtr pSc
 		_H_SYNC_OFF(timing_ptr);
 	    fixed_mode->HSyncEnd   = fixed_mode->HSyncStart +
 		_H_SYNC_WIDTH(timing_ptr);
-	    fixed_mode->HTotal     = fixed_mode->HDisplay +
+	    fixed_mode->HTotal     = fixed_mode->HSyncEnd +
 	        _H_BLANK(timing_ptr);
 	    fixed_mode->VSyncStart = fixed_mode->VDisplay +
 		_V_SYNC_OFF(timing_ptr);
 	    fixed_mode->VSyncEnd   = fixed_mode->VSyncStart +
 		_V_SYNC_WIDTH(timing_ptr);
-	    fixed_mode->VTotal     = fixed_mode->VDisplay +
+	    fixed_mode->VTotal     = fixed_mode->VSyncEnd +
 	        _V_BLANK(timing_ptr);
 	    fixed_mode->Clock      = _PIXEL_CLOCK(timing_ptr) / 1000;
 	    fixed_mode->type       = M_T_PREFERRED;


I can understand that - means remove and + means add the lines to the file i830_bias.c file in /src/ directory. But i dont know where to see the **SRC** directory. (find -name command doesn't work for me :-( )

I downloaded the fresh xf86-video-intel-2.6.0 (2008Q4 release) from the [www.intellinuxgraphics.org](www.intellinuxgraphics.org). I could see the i830_bias.c file in the src folder after i extracted the tar file.

Can any one tell me where to locate the src file from the already installed xserver-xorg-video-intel. And it would be great if someone can tell me how to install this patch cuz I have spent a lot of time on it and haven't been able to install it successfully.

It would be a great help if i could enjoy the pleasures of my graphics card now :D. I thanks all u guys for ur help

thx
b.

---

### Post by iaculallad on 2009-01-19
Try /usr/src path.

---

### Post by suncoolsu on 2009-01-19
I also that and tried .. but in the /usr/src directory i can only see

> linux-headers-2.6.24-16          linux-headers-2.6.24-23
linux-headers-2.6.24-16-generic  linux-headers-2.6.24-23-generic


directories. When i do find -name "i830_bias.c" - I dont get anything.

If possible can anyone also help me how to install this patch - I would be greatful.

thx
B.

---

### Post by suncoolsu on 2009-01-19
Ok - i tried installing the intel drivers (latest Q4) on my laptop with hardy. I checked the i830_bios.c file in src folder and it has already been fixed. This is what I did.

I downloaded the fresh xf86-video-intel-2.6.0 (2008Q4 release) from the Intel Linux Graphics ([http://intellinuxgraphics.org/index.html](http://intellinuxgraphics.org/index.html)). I could see the i830_bias.c file in the src folder after i extracted the tar file. I tried to install the -intel drivers.

I went to the folder xf86-video-intel-2.6.0 and tried to configure by -

~/xf86-video-intel-2.6.0$ ./configure

At the very end I get this error. (Everything else was fine)

> checking for XORG... configure: error: Packge requirements (xorg-server xproto fontsproto ) were not met:

No package 'xorg-server' found
No package 'xproto' found
No package 'fontsproto' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables XORG_CFLAGS
and XORG_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

How do i install these packages? or what do i need to do to solve this problem?

Pls help :-(( :confused:

thx
B.

---

### Post by theteju on 2009-02-07
Hello Sir,

I am having the exact same problem and kind of stuck where your last post says.
I have dell 1420 inspiron with intel 965 chipset and want to install latest intel driver but having same no packges error with ./configure command.

If you have found the solution already please reply asap.

Thank you.

---

### Post by holodad on 2009-03-20
Try to perform a:
* sudo apt-get build-dep xserver-xorg-video-intel.

That will bring you all the dependencies of the intel driver included xserv-xorg and fontsproto.
Then: sudo ./configure 

However, i' go much further but still having a issue with libdrm version...
Hope to find something

---

### Post by holodad on 2009-03-20
Ok got it!!

For those you get the same error as me, please install libdrm before with this instructions:

    * git clone git://anongit.freedesktop.org/git/mesa/drm
    * cd drm
    * ./autogen.sh
    * ./configure –prefix=/usr/local/xorg
    * make
    * sudo make install

---

