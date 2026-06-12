---
title: "tons of errors, xgl, Desktop Effects and many more."
date: 2010-12-22
forum: New to Ubuntu
---

### Post by Michael-Williams on 2010-12-22
XGL, Maradns, compiz --replace hangs, can't enable desktop effects, etc, etc, etc.

Is there a way to run a system check and fix all of this? ](*,)

The "make"command shows "nothing to make" when tyring to build/compile a program and there are halt installed packages all over the system. ](*,)

Here is one error from a half installed package:
It works, but I have to leave the Terminal window "open" ](*,)
Notice the "File or Folder not found" and "Not present" Why?
$ sudo compiz --debug
Checking for Xgl: not present.  ](*,)
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking screen 1Comparing resolution ( 1280x1024 ) to maximum 3D texture size ( 2048 ): Passed. "I put spaces here. Shows as smiley"
Checking for Software Rasterizer: Not present. 
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present.  ](*,)
/usr/bin/compiz.real (core) - Debug: Could not stat() file /home/williams/.compiz/plugins/libcore.so : No such file or directory
/usr/bin/compiz.real (core) - Debug: Could not stat() file /usr/lib/compiz/libcore.so : No such file or directory
/usr/bin/compiz.real (core) - Debug: Could not stat() file /home/williams/.compiz/plugins/libmove.so : No such file or directory
/usr/bin/compiz.real (core) - Debug: Could not stat() file /home/williams/.compiz/plugins/libresize.so : No such file or directory
/usr/bin/compiz.real (core) - Debug: Could not stat() file /home/williams/.compiz/plugins/libplace.so : No such file or directory
/usr/bin/compiz.real (core) - Debug: Could not stat() file /home/williams/.compiz/plugins/libdecoration.so : No such file or directory
/usr/bin/compiz.real (core) - Debug: Could not stat() file /home/williams/.compiz/plugins/libanimation.so : No such file or directory
/usr/bin/compiz.real (core) - Debug: Could not stat() file /home/williams/.compiz/plugins/libccp.so : No such file or directory
/usr/bin/compiz.real (core) - Debug: Could not stat() file /home/williams/.compiz/plugins/libdbus.so : No such file or directory
/usr/bin/compiz.real (core) - Debug: Could not stat() file /home/williams/.compiz/plugins/libmousepoll.so : No such file or directory
/usr/bin/compiz.real (core) - Debug: Could not stat() file /home/williams/.compiz/plugins/libgnomecompat.so : No such file or directory
/usr/bin/compiz.real (core) - Debug: Could not stat() file /home/williams/.compiz/plugins/libpng.so : No such file or directory
/usr/bin/compiz.real (core) - Debug: Could not stat() file /home/williams/.compiz/plugins/libsvg.so : No such file or directory
/usr/bin/compiz.real (core) - Debug: Could not stat() file /home/williams/.compiz/plugins/libimgjpeg.so : No such file or directory
/usr/bin/compiz.real (core) - Debug: Could not stat() file /home/williams/.compiz/plugins/libtext.so : No such file or directory
/usr/bin/compiz.real (core) - Debug: Could not stat() file /home/williams/.compiz/plugins/libcommands.so : No such file or directory
/usr/bin/compiz.real (core) - Debug: Could not stat() file /home/williams/.compiz/plugins/libneg.so : No such file or directory
/usr/bin/compiz.real (core) - Debug: Could not stat() file /home/williams/.compiz/plugins/libvideo.so : No such file or directory
/usr/bin/compiz.real (core) - Debug: Could not stat() file /home/williams/.compiz/plugins/libwall.so : No such file or directory
/usr/bin/compiz.real (core) - Debug: Could not stat() file /home/williams/.compiz/plugins/libsnap.so : No such file or directory
/usr/bin/compiz.real (core) - Debug: Could not stat() file /home/williams/.compiz/plugins/libscale.so : No such file or directory
/usr/bin/compiz.real (core) - Debug: Could not stat() file /home/williams/.compiz/plugins/libscaleaddon.so : No such file or directory
/usr/bin/compiz.real (core) - Debug: Could not stat() file /home/williams/.compiz/plugins/libexpo.so : No such file or directory
/usr/bin/compiz.real (core) - Debug: Could not stat() file /home/williams/.compiz/plugins/libstaticswitcher.so : No such file or directory
/usr/bin/compiz.real (core) - Debug: Could not stat() file /home/williams/.compiz/plugins/libregex.so : No such file or directory
/usr/bin/compiz.real (core) - Debug: Could not stat() file /home/williams/.compiz/plugins/libresizeinfo.so : No such file or directory
/usr/bin/compiz.real (core) - Debug: Could not stat() file /home/williams/.compiz/plugins/libworkarounds.so : No such file or directory
/usr/bin/compiz.real (core) - Debug: Could not stat() file /home/williams/.compiz/plugins/libezoom.so : No such file or directory
/usr/bin/compiz.real (core) - Debug: Could not stat() file /home/williams/.compiz/plugins/libvpswitch.so : No such file or directory
/usr/bin/compiz.real (core) - Debug: Could not stat() file /home/williams/.compiz/plugins/libextrawm.so : No such file or directory
/usr/bin/compiz.real (core) - Debug: Could not stat() file /home/williams/.compiz/plugins/libfade.so : No such file or directory
/usr/bin/compiz.real (core) - Debug: Could not stat() file /home/williams/.compiz/plugins/libsession.so : No such file or directory

                                                                  ](*,)

---

