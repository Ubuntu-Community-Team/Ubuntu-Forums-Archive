---
title: "Songbird error"
date: 2009-06-25
forum: New to Ubuntu
---

### Post by Elep.Repu on 2009-06-25
Downloaded from standard site (getdeb did not work, not did whatever other sites I found providing deb files.)

```
aji@aij-dtp:~/Songbird$ 
aji@aij-dtp:~/Songbird$ sudo chown aji /home/aji/Songbird/*
[sudo] password for aji: 
aji@aij-dtp:~/Songbird$ sudo chmod 755 -R /home/aji/Songbird/songbird
aji@aij-dtp:~/Songbird$ ./songbird
*** glibc detected *** ././songbird-bin: free(): invalid pointer: 0x00007fb015339070 ***
======= Backtrace: =========
/lib/libc.so.6[0x7fb03acfecb8]
/lib/libc.so.6(cfree+0x76)[0x7fb03ad01276]
/usr/lib/libvisual-0.4.so.0(visual_mem_free+0xe)[0x7fb0119e84ce]
/usr/lib/libvisual-0.4.so.0[0x7fb0119e1646]
/usr/lib/libvisual-0.4.so.0(visual_plugin_get_list+0x48)[0x7fb0119e17d8]
/usr/lib/libvisual-0.4.so.0(visual_init+0x243)[0x7fb0119ee703]
/usr/lib64/gstreamer-0.10/libgstlibvisual.so[0x7fb011c0fcb1]
/home/aji/Songbird/lib/libgstreamer-0.10.so[0x7fb02529a383]
/home/aji/Songbird/lib/libgstreamer-0.10.so(gst_plugin_load_file+0x98c)[0x7fb02529af7d]
/home/aji/Songbird/lib/libgstreamer-0.10.so[0x7fb0252a69fb]
/home/aji/Songbird/lib/libgstreamer-0.10.so(gst_registry_scan_path+0x11f)[0x7fb0252a6b7e]
/home/aji/Songbird/lib/libgstreamer-0.10.so[0x7fb02525259b]
/home/aji/Songbird/lib/libgstreamer-0.10.so[0x7fb025252a09]
/home/aji/Songbird/lib/libgstreamer-0.10.so[0x7fb025252fd7]
/home/aji/Songbird/lib/libgstreamer-0.10.so[0x7fb025253568]
/usr/lib/libglib-2.0.so.0(g_option_context_parse+0x540)[0x7fb037050020]
/home/aji/Songbird/lib/libgstreamer-0.10.so(gst_init_check+0xd6)[0x7fb025251936]
/home/aji/Songbird/lib/libgstreamer-0.10.so(gst_init+0x29)[0x7fb025251a23]
/home/aji/Songbird/lib/sbGStreamerMediacore.so(_ZN18sbGStreamerService4InitEv+0xacc)[0x7fb022eceb04]
/home/aji/Songbird/lib/sbGStreamerMediacore.so[0x7fb022ed65e5]
/home/aji/Songbird/xulrunner/libxul.so[0x7fb038b9659f]
/home/aji/Songbird/xulrunner/libxul.so[0x7fb038b960e9]
/home/aji/Songbird/lib/sbGStreamerMediacore.so[0x7fb022ee492b]
/home/aji/Songbird/lib/sbGStreamerMediacore.so[0x7fb022ee4958]
/home/aji/Songbird/lib/sbGStreamerMediacore.so[0x7fb022ee4140]
/home/aji/Songbird/lib/sbGStreamerMediacore.so[0x7fb022ed502e]
/home/aji/Songbird/lib/sbGStreamerMediacore.so(_ZN27sbGStreamerMediacoreFactory4InitEv+0x4b)[0x7fb022ed5601]
/home/aji/Songbird/lib/sbGStreamerMediacore.so[0x7fb022ed6555]
/home/aji/Songbird/xulrunner/libxul.so[0x7fb038b9659f]
/home/aji/Songbird/components/sbMediacoreManager.so[0x7fb02840e613]
/home/aji/Songbird/components/sbMediacoreManager.so[0x7fb02840e650]
/home/aji/Songbird/components/sbMediacoreManager.so[0x7fb02840df32]
/home/aji/Songbird/components/sbMediacoreManager.so(_ZN8nsCOMPtrI19sbIMediacoreFactoryEC1ERK15nsCOMPtr_helper+0x1c)[0x7fb0283f9154]
/home/aji/Songbird/components/sbMediacoreManager.so(_ZN18sbMediacoreManager4InitEv+0x1ff)[0x7fb0283f6729]
/home/aji/Songbird/components/sbMediacoreManager.so[0x7fb0283f6b17]
/home/aji/Songbird/xulrunner/libxul.so[0x7fb038b76eba]
/home/aji/Songbird/xulrunner/libxul.so[0x7fb038b7738c]
/home/aji/Songbird/xulrunner/libxul.so[0x7fb038447f86]
/home/aji/Songbird/xulrunner/libxul.so(XRE_main+0x177d)[0x7fb038445c57]
././songbird-bin[0x401417]
/lib/libc.so.6(__libc_start_main+0xe6)[0x7fb03aca55a6]
././songbird-bin[0x401009]
======= Memory map: ========
00400000-00408000 r-xp 00000000 08:11 14434807                           /home/aji/Songbird/songbird-bin
00608000-00609000 rw-p 00008000 08:11 14434807                           /home/aji/Songbird/songbird-bin
00728000-00749000 rw-p 00728000 00:00 0                                  [heap]
7fb00ff7a000-7fb00ff7b000 r-xp 00000000 08:11 5005691                    /usr/lib/tls/libnvidia-tls.so.180.44
7fb00ff7b000-7fb01007b000 ---p 00001000 08:11 5005691                    /usr/lib/tls/libnvidia-tls.so.180.44
7fb01007b000-7fb01007c000 rw-p 00001000 08:11 5005691                    /usr/lib/tls/libnvidia-tls.so.180.44
7fb0119cf000-7fb011a0c000 r-xp 00000000 08:11 4811219                    /usr/lib/libvisual-0.4.so.0.0.0
7fb011a0c000-7fb011c0b000 ---p 0003d000 08:11 4811219                    /usr/lib/libvisual-0.4.so.0.0.0
7fb011c0b000-7fb011c0c000 r--p 0003c000 08:11 4811219                    /usr/lib/libvisual-0.4.so.0.0.0
7fb011c0c000-7fb011c0d000 rw-p 0003d000 08:11 4811219                    /usr/lib/libvisual-0.4.so.0.0.0
7fb011c0d000-7fb011c13000 r-xp 00000000 08:11 4104242                    /usr/lib/gstreamer-0.10/libgstlibvisual.so
7fb011c13000-7fb011e12000 ---p 00006000 08:11 4104242                    /usr/lib/gstreamer-0.10/libgstlibvisual.so
7fb011e12000-7fb011e13000 r--p 00005000 08:11 4104242                    /usr/lib/gstreamer-0.10/libgstlibvisual.so
7fb011e13000-7fb011e14000 rw-p 00006000 08:11 4104242                    /usr/lib/gstreamer-0.10/libgstlibvisual.so
7fb011e14000-7fb011e30000 r-xp 00000000 08:11 12476650                   /usr/lib/libdca.so.0.0.0
7fb011e30000-7fb01202f000 ---p 0001c000 08:11 12476650                   /usr/lib/libdca.so.0.0.0
7fb01202f000-7fb012030000 r--p 0001b000 08:11 12476650                   /usr/lib/libdca.so.0.0.0
7fb012030000-7fb01203d000 rw-p 0001c000 08:11 12476650                   /usr/lib/libdca.so.0.0.0
7fb01203d000-7fb012042000 r-xp 00000000 08:11 4825598                    /usr/lib/gstreamer-0.10/libgstdtsdec.so
7fb012042000-7fb012241000 ---p 00005000 08:11 4825598                    /usr/lib/gstreamer-0.10/libgstdtsdec.so
7fb012241000-7fb012242000 r--p 00004000 08:11 4825598                    /usr/lib/gstreamer-0.10/libgstdtsdec.so
7fb012242000-7fb012243000 rw-p 00005000 08:11 4825598                    /usr/lib/gstreamer-0.10/libgstdtsdec.so
7fb012243000-7fb012246000 r-xp 00000000 08:11 4825646                    /usr/lib/gstreamer-0.10/libgstvalve.so
7fb012246000-7fb012445000 ---p 00003000 08:11 4825646                    /usr/lib/gstreamer-0.10/libgstvalve.so
7fb012445000-7fb012446000 r--p 00002000 08:11 4825646                    /usr/lib/gstreamer-0.10/libgstvalve.so
7fb012446000-7fb012447000 rw-p 00003000 08:11 4825646                    /usr/lib/gstreamer-0.10/libgstvalve.so
7fb012447000-7fb01244e000 r-xp 00000000 08:11 4825586                    /usr/lib/gstreamer-0.10/libgstautoconvert.so
7fb01244e000-7fb01264e000 ---p 00007000 08:11 4825586                    /usr/lib/gstreamer-0.10/libgstautoconvert.so
7fb01264e000-7fb01264f000 r--p 00007000 08:11 4825586                    /usr/lib/gstreamer-0.10/libgstautoconvert.so
7fb01264f000-7fb012650000 rw-p 00008000 08:11 4825586                    /usr/lib/gstreamer-0.10/libgstautoconvert.so
7fb012650000-7fb012663000 r-xp 00000000 08:11 4825625                    /usr/lib/gstreamer-0.10/libgstnsf.so
7fb012663000-7fb012862000 ---p 00013000 08:11 4825625                    /usr/lib/gstreamer-0.10/libgstnsf.so
7fb012862000-7fb012863000 r--p 00012000 08:11 4825625                    /usr/lib/gstreamer-0.10/libgstnsf.so
7fb012863000-7fb012864000 rw-p 00013000 08:11 4825625                    /usr/lib/gstreamer-0.10/libgstnsf.so
7fb012864000-7fb01286d000 rw-p 7fb012864000 00:00 0 
7fb01286d000-7fb01287e000 r-xp 00000000 08:11 4811217                    /usr/lib/libv4lconvert.so.0
7fb01287e000-7fb012a7e000 ---p 00011000 08:11 4811217                    /usr/lib/libv4lconvert.so.0
7fb012a7e000-7fb012a7f000 r--p 00011000 08:11 4811217                    /usr/lib/libv4lconvert.so.0
7fb012a7f000-7fb012a80000 rw-p 00012000 08:11 4811217                    /usr/lib/libv4lconvert.so.0
7fb012a80000-7fb012ad0000 rw-p 7fb012a80000 00:00 0 
7fb012ad0000-7fb012ad6000 r-xp 00000000 08:11 4811216                    /usr/lib/libv4l2.so.0
7fb012ad6000-7fb012cd5000 ---p 00006000 08:11 4811216                    /usr/lib/libv4l2.so.0
7fb012cd5000-7fb012cd6000 r--p 00005000 08:11 4811216                    /usr/lib/libv4l2.so.0
7fb012cd6000-7fb012cda000 rw-p 00006000 08:11 4811216                    /usr/lib/libv4l2.so.0
7fb012cda000-7fb012cf0000 r-xp 00000000 08:11 4825547                    /usr/lib/gstreamer-0.10/libgstvideo4linux2.so
7fb012cf0000-7fb012eef000 ---p 00016000 08:11 4825547                    /usr/lib/gstreamer-0.10/libgstvideo4linux2.so
7fb012eef000-7fb012ef0000 r--p 00015000 08:11 4825547                    /usr/lib/gstreamer-0.10/libgstvideo4linux2.so
7fb012ef0000-7fb012ef1000 rw-p 00016000 08:11 4825547                    /usr/lib/gstreamer-0.10/libgstvideo4linux2.so
7fb012ef1000-7fb012f8a000 r-xp 00000000 08:11 4811141                    /usr/lib/libsmbios.so.2.1.0
7fb012f8a000-7fb013189000 ---p 00099000 08:11 4811141                    /usr/lib/libsmbios.so.2.1.0
7fb013189000-7fb013191000 r--p 00098000 08:11 4811141                    /usr/lib/libsmbios.so.2.1.0
7fb013191000-7fb013192000 rw-p 000a0000 08:11 4811141                    /usr/lib/libsmbios.so.2.1.0
7fb013192000-7fb0131a2000 r-xp 00000000 08:11 4810660                    /usr/lib/libhal.so.1.0.0
7fb0131a2000-7fb0133a1000 ---p 00010000 08:11 4810660                    /usr/lib/libhal.so.1.0.0
7fb0133a1000-7fb0133a2000 r--p 0000f000 08:11 4810660                    /usr/lib/libhal.so.1.0.0
7fb0133a2000-7fb0133a3000 rw-p 00010000 08:11 4810660                    /usr/lib/libhal.so.1.0.0
7fb0133a3000-7fb0133a8000 r-xp 00000000 08:11 4825522                    /usr/lib/gstreamer-0.10/libgsthalelements.so
7fb0133a8000-7fb0135a7000 ---p 00005000 08:11 4825522                    /usr/lib/gstreamer-0.10/libgsthalelements.soCould not initialize GStreamer: Error re-scanning registry , child terminated by signal
aji@aij-dtp:~/Songbird$ 

```Ubuntu 9.04 x64

I got directions from this site, for the above code;
[http://www.jonathanmoeller.com/screed/?p=907](http://www.jonathanmoeller.com/screed/?p=907)

---

### Post by skyjacker on 2009-06-25
Use this site   [http://www.getdeb.net/release.php?id=4214](http://www.getdeb.net/release.php?id=4214).  It uses the deb installer package. I used it with no problem... Good Luck

---

### Post by Elep.Repu on 2009-06-26
> **skyjacker said:**
> Use this site   [http://www.getdeb.net/release.php?id=4214](http://www.getdeb.net/release.php?id=4214).  It uses the deb installer package. I used it with no problem... Good Luck


My (repeated) installation/uninstallation from the getdeb package resulted in a nonworking program. I tried this originally.

I just ended up installing an earlier one (For Hardy). I'm on Jaunty.
Of course the release i was able to install is no longer supported (but oh well, better then trying to use their nonworking *newer* deb file.)

---

### Post by billgoldberg on 2009-06-26
Use Banshee instead.

Songbird is a horrible app.

---

### Post by n0_mad on 2009-06-27
no, banshee is horrible, even library browser has only 2 columns and it cant filter artists by yearm and i dont know how to enable lyrics fetching in banshee when songbird offers this plugin  on first page in plugin reps, and progress bar is too short.

---

### Post by Greenwidth on 2009-06-27
@Elep.Repu

I had that problem when trying out the beta, after removing libvisual plugins it worked fine.

```
sudo apt-get remove libvisual-0.4-plugins
```

---

### Post by Jimmerz28 on 2009-06-27
Songbird won't start up for me either, but when I try to 

```
sudo apt-get remove libvisual-0.4-plugins
```

I get:
[HTML]...
Certificate was added to keystore
  added certificate mozilla/WellsSecure_Public_Root_Certificate_Authority.crt
failed.
dpkg: error processing ca-certificates-java (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 ca-certificates-java
E: Sub-process /usr/bin/dpkg returned an error code (1)[/HTML]

Any ideas?

---

### Post by Elep.Repu on 2009-06-28
Looks like it's an **NVIDIA **problem. Seeing as how I *own* an Nvidia card, the removal of *libvisual-0.4-plugins *worked for me.

I installed from getdeb,
removed the above plugins, then it worked.

Ty; 
[Greenwidth]("http://ubuntuforums.org/member.php?u=628497")

---

