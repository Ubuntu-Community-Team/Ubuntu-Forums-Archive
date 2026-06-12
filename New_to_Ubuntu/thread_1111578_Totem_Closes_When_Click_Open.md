---
title: "Totem Closes When Click Open"
date: 2009-03-30
forum: New to Ubuntu
---

### Post by Tumpster on 2009-03-30
So I had a few troubles with my hard drive the a chk disk took care of but now since returning to Ubuntu everything runs fine EXCEPT Totem. It opens and play files just fine when I double clicked it in my folders. But when I click open in Totem it just crashes without warning. I ran it in the terminal and get "Segmentation Fault". I have since removed all of it and reloaded it to no success. Anyone have any ideas? Thanks! :)

---

### Post by spiderbatdad on 2009-03-30
This is hard to diagnose...some library missing possibly. Debugging can be tricky too. There are quite a few tutorials for attempting to debug:
You might start by running "totem --debug" or installing totem-dbg from synaptic and running valgrind or other debugging app. You'll need to do some research to fix this I think. Also search launchpad for similar reports.

---

### Post by dr.silly on 2009-03-30
you may want to try just reinstalling totem

---

### Post by Tumpster on 2009-03-30
> **dr.silly said:**
> you may want to try just reinstalling totem

Please see end of first post. Thanks for the help so far!

---

### Post by Tumpster on 2009-03-30
> **spiderbatdad said:**
> This is hard to diagnose...some library missing possibly. Debugging can be tricky too. There are quite a few tutorials for attempting to debug:
You might start by running "totem --debug" or installing totem-dbg from synaptic and running valgrind or other debugging app. You'll need to do some research to fix this I think. Also search launchpad for similar reports.


Ran valgrind
==7838==    by 0x4D28C18: (within /lib/tls/i686/cmov/libdl-2.7.so)
==7838==    by 0x400D5C5: (within /lib/ld-2.7.so)
==7838==    by 0x4D292BB: (within /lib/tls/i686/cmov/libdl-2.7.so)
==7838==    by 0x4D28B50: dlopen (in /lib/tls/i686/cmov/libdl-2.7.so)
==7838==    by 0x4C4E5FB: g_module_open (in /usr/lib/libgmodule-2.0.so.0.1600.6)
==7838==    by 0x471FEB7: (within /usr/lib/libgtk-x11-2.0.so.0.1200.9)
==7838==    by 0x471EE66: (within /usr/lib/libgtk-x11-2.0.so.0.1200.9)
==7838==    by 0x47B9A31: (within /usr/lib/libgtk-x11-2.0.so.0.1200.9)
==7838==  Address 0x697ed74 is 20 bytes inside a block of size 22 alloc'd
==7838==    at 0x4022AB8: malloc (vg_replace_malloc.c:207)
==7838==    by 0x4C90CEC: g_malloc (in /usr/lib/libglib-2.0.so.0.1600.6)
==7838==    by 0x4CA9638: g_strdup (in /usr/lib/libglib-2.0.so.0.1600.6)
==7838==    by 0x4C4E92D: g_module_open (in /usr/lib/libgmodule-2.0.so.0.1600.6)
==7838==    by 0x471FEB7: (within /usr/lib/libgtk-x11-2.0.so.0.1200.9)
==7838==    by 0x471EE66: (within /usr/lib/libgtk-x11-2.0.so.0.1200.9)
==7838==    by 0x47B9A31: (within /usr/lib/libgtk-x11-2.0.so.0.1200.9)
==7838==    by 0x4C21A07: g_object_newv (in /usr/lib/libgobject-2.0.so.0.1600.6)
==7838==    by 0x4C225C5: g_object_new_valist (in /usr/lib/libgobject-2.0.so.0.1600.6)
==7838==    by 0x4C226CF: g_object_new (in /usr/lib/libgobject-2.0.so.0.1600.6)
==7838==    by 0x47A9F47: (within /usr/lib/libgtk-x11-2.0.so.0.1200.9)
==7838==    by 0x47BEE1B: (within /usr/lib/libgtk-x11-2.0.so.0.1200.9)
==7838== 
==7838== Invalid read of size 4
==7838==    at 0x40151F9: (within /lib/ld-2.7.so)
==7838==    by 0x4011533: (within /lib/ld-2.7.so)
==7838==    by 0x400D5C5: (within /lib/ld-2.7.so)
==7838==    by 0x4010F4D: (within /lib/ld-2.7.so)
==7838==    by 0x4D28C18: (within /lib/tls/i686/cmov/libdl-2.7.so)
==7838==    by 0x400D5C5: (within /lib/ld-2.7.so)
==7838==    by 0x4D292BB: (within /lib/tls/i686/cmov/libdl-2.7.so)
==7838==    by 0x4D28B50: dlopen (in /lib/tls/i686/cmov/libdl-2.7.so)
==7838==    by 0x4C4E5FB: g_module_open (in /usr/lib/libgmodule-2.0.so.0.1600.6)
==7838==    by 0x471FEB7: (within /usr/lib/libgtk-x11-2.0.so.0.1200.9)
==7838==    by 0x471EE66: (within /usr/lib/libgtk-x11-2.0.so.0.1200.9)
==7838==    by 0x47B9A31: (within /usr/lib/libgtk-x11-2.0.so.0.1200.9)
==7838==  Address 0x697ed74 is 20 bytes inside a block of size 22 alloc'd
==7838==    at 0x4022AB8: malloc (vg_replace_malloc.c:207)
==7838==    by 0x4C90CEC: g_malloc (in /usr/lib/libglib-2.0.so.0.1600.6)
==7838==    by 0x4CA9638: g_strdup (in /usr/lib/libglib-2.0.so.0.1600.6)
==7838==    by 0x4C4E92D: g_module_open (in /usr/lib/libgmodule-2.0.so.0.1600.6)
==7838==    by 0x471FEB7: (within /usr/lib/libgtk-x11-2.0.so.0.1200.9)
==7838==    by 0x471EE66: (within /usr/lib/libgtk-x11-2.0.so.0.1200.9)
==7838==    by 0x47B9A31: (within /usr/lib/libgtk-x11-2.0.so.0.1200.9)
==7838==    by 0x4C21A07: g_object_newv (in /usr/lib/libgobject-2.0.so.0.1600.6)
==7838==    by 0x4C225C5: g_object_new_valist (in /usr/lib/libgobject-2.0.so.0.1600.6)
==7838==    by 0x4C226CF: g_object_new (in /usr/lib/libgobject-2.0.so.0.1600.6)
==7838==    by 0x47A9F47: (within /usr/lib/libgtk-x11-2.0.so.0.1200.9)
==7838==    by 0x47BEE1B: (within /usr/lib/libgtk-x11-2.0.so.0.1200.9)
==7838== 
==7838== Invalid read of size 1
==7838==    at 0x402380A: index (mc_replace_strmem.c:160)
==7838==    by 0x47A9D3B: (within /usr/lib/libgtk-x11-2.0.so.0.1200.9)
==7838==    by 0x47AC439: (within /usr/lib/libgtk-x11-2.0.so.0.1200.9)
==7838==    by 0x47B3E4E: (within /usr/lib/libgtk-x11-2.0.so.0.1200.9)
==7838==    by 0x47B5183: (within /usr/lib/libgtk-x11-2.0.so.0.1200.9)
==7838==    by 0x4C22B02: g_object_set_property (in /usr/lib/libgobject-2.0.so.0.1600.6)
==7838==    by 0x47BEDA3: (within /usr/lib/libgtk-x11-2.0.so.0.1200.9)
==7838==    by 0x4C22B02: g_object_set_property (in /usr/lib/libgobject-2.0.so.0.1600.6)
==7838==    by 0x47BB736: (within /usr/lib/libgtk-x11-2.0.so.0.1200.9)
==7838==    by 0x4C20C25: g_object_set_valist (in /usr/lib/libgobject-2.0.so.0.1600.6)
==7838==    by 0x4C211E5: g_object_set (in /usr/lib/libgobject-2.0.so.0.1600.6)
==7838==    by 0x47A4720: gtk_file_chooser_set_local_only (in /usr/lib/libgtk-x11-2.0.so.0.1200.9)
==7838==  Address 0x3 is not stack'd, malloc'd or (recently) free'd
==7838== 
==7838== Process terminating with default action of signal 11 (SIGSEGV)
==7838==  Access not within mapped region at address 0x3
==7838==    at 0x402380A: index (mc_replace_strmem.c:160)
==7838==    by 0x47A9D3B: (within /usr/lib/libgtk-x11-2.0.so.0.1200.9)
==7838==    by 0x47AC439: (within /usr/lib/libgtk-x11-2.0.so.0.1200.9)
==7838==    by 0x47B3E4E: (within /usr/lib/libgtk-x11-2.0.so.0.1200.9)
==7838==    by 0x47B5183: (within /usr/lib/libgtk-x11-2.0.so.0.1200.9)
==7838==    by 0x4C22B02: g_object_set_property (in /usr/lib/libgobject-2.0.so.0.1600.6)
==7838==    by 0x47BEDA3: (within /usr/lib/libgtk-x11-2.0.so.0.1200.9)
==7838==    by 0x4C22B02: g_object_set_property (in /usr/lib/libgobject-2.0.so.0.1600.6)
==7838==    by 0x47BB736: (within /usr/lib/libgtk-x11-2.0.so.0.1200.9)
==7838==    by 0x4C20C25: g_object_set_valist (in /usr/lib/libgobject-2.0.so.0.1600.6)
==7838==    by 0x4C211E5: g_object_set (in /usr/lib/libgobject-2.0.so.0.1600.6)
==7838==    by 0x47A4720: gtk_file_chooser_set_local_only (in /usr/lib/libgtk-x11-2.0.so.0.1200.9)
==7838== 
==7838== ERROR SUMMARY: 377 errors from 36 contexts (suppressed: 491 from 2)
==7838== malloc/free: in use at exit: 9,980,641 bytes in 70,594 blocks.
==7838== malloc/free: 331,588 allocs, 260,994 frees, 87,802,898 bytes allocated.
==7838== For counts of detected errors, rerun with: -v
==7838== searching for pointers to 70,594 not-freed blocks.
==7838== checked 27,936,576 bytes.
==7838== 
==7838== LEAK SUMMARY:
==7838==    definitely lost: 38,959 bytes in 1,415 blocks.
==7838==      possibly lost: 387,577 bytes in 1,372 blocks.
==7838==    still reachable: 9,554,105 bytes in 67,807 blocks.
==7838==         suppressed: 0 bytes in 0 blocks.
==7838== Rerun with --leak-check=full to see details of leaked memory.

---

### Post by Tumpster on 2009-04-01
Any ideas folks? Thanks

---

