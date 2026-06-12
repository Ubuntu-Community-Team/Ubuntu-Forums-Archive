---
title: "How to apply a patch to xournal"
date: 2011-07-27
forum: New to Ubuntu
---

### Post by Koyotuma on 2011-07-27
I am having some trouble applying revision 7 of the insert image patch for xournal. I am using Natty Narwhal. My main problem is I am not sure where to apply the patch using the patch -p1 < Filename.patch  there seem to be various xournal files in different places.  Below is the result of trying the patch in /usr/bin   

isaac@isaac-ThinkPad-X60-Tablet:/usr/bin$ sudo patch -p1 < xournal-0.4.5-sjg-image-rev7.patch
[sudo] password for isaac: 
patching file README.image
patching file src/Makefile.am
Hunk #1 FAILED at 12.
1 out of 1 hunk FAILED -- saving rejects to file src/Makefile.am.rej
patching file src/Makefile.in
Hunk #1 FAILED at 1.
Hunk #2 FAILED at 46.
Hunk #3 FAILED at 154.
Hunk #4 FAILED at 219.
Hunk #5 FAILED at 311.
Hunk #6 FAILED at 340.
Hunk #7 FAILED at 365.
7 out of 7 hunks FAILED -- saving rejects to file src/Makefile.in.rej
patching file src/TODO
Hunk #1 FAILED at 138.
1 out of 1 hunk FAILED -- saving rejects to file src/TODO.rej
patching file src/main.c
Hunk #1 FAILED at 287.
1 out of 1 hunk FAILED -- saving rejects to file src/main.c.rej
patching file src/xo-callbacks.c
Hunk #1 FAILED at 452.
Hunk #2 FAILED at 666.
Hunk #3 FAILED at 824.
Hunk #4 FAILED at 946.
Hunk #5 FAILED at 958.
Hunk #6 FAILED at 969.
Hunk #7 FAILED at 980.
Hunk #8 FAILED at 1539.
Hunk #9 FAILED at 1585.
Hunk #10 FAILED at 1747.
Hunk #11 FAILED at 2321.
Hunk #12 FAILED at 2407.
Hunk #13 FAILED at 2487.
Hunk #14 FAILED at 2665.
Hunk #15 FAILED at 3340.
15 out of 15 hunks FAILED -- saving rejects to file src/xo-callbacks.c.rej
patching file src/xo-callbacks.h
Hunk #1 FAILED at 211.
1 out of 1 hunk FAILED -- saving rejects to file src/xo-callbacks.h.rej
patching file src/xo-clipboard.c
patching file src/xo-clipboard.h
patching file src/xo-file.c
Hunk #1 FAILED at 25.
Hunk #2 FAILED at 68.
Hunk #3 FAILED at 199.
Hunk #4 FAILED at 575.
Hunk #5 FAILED at 610.
Hunk #6 FAILED at 647.
Hunk #7 FAILED at 716.
Hunk #8 FAILED at 737.
Hunk #9 FAILED at 823.
Hunk #10 FAILED at 1338.
10 out of 10 hunks FAILED -- saving rejects to file src/xo-file.c.rej
patching file src/xo-image.c
patching file src/xo-image.h
patching file src/xo-interface.c
Hunk #1 FAILED at 36.
Hunk #2 FAILED at 53.
Hunk #3 FAILED at 81.
Hunk #4 FAILED at 131.
Hunk #5 FAILED at 153.
Hunk #6 FAILED at 196.
Hunk #7 FAILED at 289.
Hunk #8 FAILED at 368.
Hunk #9 FAILED at 437.
Hunk #10 FAILED at 577.
Hunk #11 FAILED at 597.
Hunk #12 FAILED at 808.
Hunk #13 FAILED at 940.
Hunk #14 FAILED at 1141.
Hunk #15 FAILED at 1588.
Hunk #16 FAILED at 1669.
Hunk #17 FAILED at 1694.
Hunk #18 FAILED at 1707.
Hunk #19 FAILED at 1720.
Hunk #20 FAILED at 1747.
Hunk #21 FAILED at 1759.
Hunk #22 FAILED at 1771.
Hunk #23 FAILED at 1783.
Hunk #24 FAILED at 1795.
Hunk #25 FAILED at 1807.
Hunk #26 FAILED at 1819.
Hunk #27 FAILED at 1831.
Hunk #28 FAILED at 1843.
Hunk #29 FAILED at 1855.
Hunk #30 FAILED at 1867.
Hunk #31 FAILED at 2426.
Hunk #32 FAILED at 2513.
Hunk #33 FAILED at 2530.
Hunk #34 FAILED at 2557.
Hunk #35 FAILED at 2605.
Hunk #36 FAILED at 2626.
Hunk #37 FAILED at 2664.
Hunk #38 FAILED at 2750.
Hunk #39 FAILED at 2860.
Hunk #40 FAILED at 2869.
Hunk #41 FAILED at 2951.
41 out of 41 hunks FAILED -- saving rejects to file src/xo-interface.c.rej
patching file src/xo-misc.c
Hunk #1 FAILED at 17.
Hunk #2 FAILED at 90.
Hunk #3 FAILED at 142.
Hunk #4 FAILED at 218.
Hunk #5 FAILED at 302.
Hunk #6 FAILED at 350.
Hunk #7 FAILED at 440.
Hunk #8 FAILED at 458.
Hunk #9 FAILED at 474.
Hunk #10 FAILED at 513.
Hunk #11 FAILED at 861.
Hunk #12 FAILED at 1377.
Hunk #13 FAILED at 1716.
Hunk #14 FAILED at 1799.
14 out of 14 hunks FAILED -- saving rejects to file src/xo-misc.c.rej
patching file src/xo-misc.h
Hunk #1 FAILED at 2.
Hunk #2 FAILED at 20.
2 out of 2 hunks FAILED -- saving rejects to file src/xo-misc.h.rej
patching file src/xo-paint.c
Hunk #1 FAILED at 879.
1 out of 1 hunk FAILED -- saving rejects to file src/xo-paint.c.rej
patching file src/xo-paint.h
Hunk #1 FAILED at 22.
1 out of 1 hunk FAILED -- saving rejects to file src/xo-paint.h.rej
patching file src/xo-print.c
Hunk #1 FAILED at 772.
Hunk #2 FAILED at 1006.
Hunk #3 FAILED at 1034.
Hunk #4 FAILED at 1161.
Hunk #5 FAILED at 1187.
Hunk #6 FAILED at 1198.
Hunk #7 FAILED at 1267.
Hunk #8 FAILED at 1323.
Hunk #9 FAILED at 1343.
Hunk #10 FAILED at 1357.
Hunk #11 FAILED at 1476.
Hunk #12 FAILED at 1487.
Hunk #13 FAILED at 1509.
Hunk #14 FAILED at 1548.
14 out of 14 hunks FAILED -- saving rejects to file src/xo-print.c.rej
patching file src/xo-print.h
Hunk #1 FAILED at 45.
1 out of 1 hunk FAILED -- saving rejects to file src/xo-print.h.rej
patching file src/xournal.h
Hunk #1 FAILED at 17.
Hunk #2 FAILED at 120.
Hunk #3 FAILED at 150.
Hunk #4 FAILED at 178.
Hunk #5 FAILED at 251.
Hunk #6 FAILED at 300.
6 out of 6 hunks FAILED -- saving rejects to file src/xournal.h.rej

any help would be greatly appriciated 
Many Thanks

---

### Post by Favux on 2011-07-27
Hi Koyotuma,

Welcome to Ubuntu forums!

I'm not sure but are you applying the patch to the source code?  It sounds like you are attempting to apply the patch to the already compiled binaries in /usr/bin and that won't work.

You need to download the source code or if it is in a git repository clone the repository and apply the patch to the uncompressed source code.  You just change directory in a terminal into the source code folder.  Then assuming you've copied the patch into the folder use the command you show.  Otherwise make sure you have the full directory path to the patch.

Once the patch is applied then you can compile Xournal and install it.

---

### Post by Koyotuma on 2011-10-20
Thanks Favux, that worked much better, at least until after I had applied the patch. Now when I try to compile xournal all goes well until:  checking pkg-config is at least version 0.9.0... yes checking for PACKAGE... no configure: error: Package requirements (gtk+-2.0 >= 2.10.0 libgnomecanvas-2.0 >= 2.4.0 poppler-glib >= 0.5.4) were not met:  No package 'gtk+-2.0' found No package 'libgnomecanvas-2.0' found No package 'poppler-glib' found  Consider adjusting the PKG_CONFIG_PATH environment variable if you installed software in a non-standard prefix.  Alternatively, you may set the environment variables PACKAGE_CFLAGS and PACKAGE_LIBS to avoid the need to call pkg-config. See the pkg-config man page for more details.  I am not sure what to make of this, or for that matter how to get and install these packages it talks of.  Many Thanks  PS I am using 11.10

---

### Post by Favux on 2011-10-20
Hi Koyotuma,

I can explain:
> No package 'gtk+-2.0' found
I think.  Oneiric (11.10) is the first release to use Gtk 3.0.  Natty still used Gtk 2.x.  Presumambly the other two are related libraries.  I suspect you now need a newer version than revision 7 of the Insert Image patch for Xournal.  I gather that Oneiric's Xournal still doesn't have that patch?

---

