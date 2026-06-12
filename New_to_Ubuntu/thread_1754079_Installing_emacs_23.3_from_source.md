---
title: "Installing emacs 23.3 from source"
date: 2011-05-09
forum: New to Ubuntu
---

### Post by _Fury_ on 2011-05-09
I have been trying to install emacs 23.3 using the tar.gz file instead of using apt-get install. I have run the configure script and that seems to have worked, however when I run make after that I keep getting this result:

"gcc -Demacs -DHAVE_CONFIG_H  -I. -I~/Downloads/emacs-23.3/src -D_BSD_SOURCE     -g -O2 -Wdeclaration-after-statement -Wno-pointer-sign   -MMD -MF deps/.d -Wl,-znocombreloc   prefix-args.o -o prefix-args
gcc -nostdlib `./prefix-args -Xlinker  -z nocombreloc` -Wl,-znocombreloc   -o temacs pre-crt0.o /usr/lib/crt1.o /usr/lib/crti.o dispnew.o frame.o scroll.o xdisp.o menu.o xmenu.o window.o charset.o coding.o category.o ccl.o character.o chartab.o cm.o term.o terminal.o xfaces.o xterm.o xfns.o xselect.o xrdb.o fontset.o xsmfns.o fringe.o image.o xsettings.o xgselect.o   emacs.o keyboard.o macros.o keymap.o sysdep.o buffer.o filelock.o insdel.o marker.o minibuf.o fileio.o dired.o filemode.o cmds.o casetab.o casefiddle.o indent.o search.o regex.o undo.o alloc.o data.o doc.o editfns.o callint.o eval.o floatfns.o fns.o font.o print.o lread.o syntax.o unexelf.o bytecode.o process.o callproc.o region-cache.o sound.o atimer.o doprnt.o strftime.o intervals.o textprop.o composite.o md5.o    xfont.o termcap.o tparam.o lastfile.o   vm-limit.o     ../oldXMenu/libXMenu11.a   -lSM -lICE -ltiff -ljpeg -lpng -lz -lm -lgif -lXpm -lX11       -L/usr/lib/1 -linux-gnu -lfontconfig  -lm -lgcc -lc -lgcc /usr/lib/crtn.o 
/usr/bin/ld: cannot find -linux-gnu
collect2: ld returned 1 exit status
make[1]: *** [temacs] Error 1"

I have read through the problems info that was provided and I don't think it addresses this. I haven't had much luck with googling this either. I found a directory called 'linux-gnu' in /usr/bin/ but I don't know if this is what it is looking for or how to tell it to look there if it is. I also tried a sudo apt-get install 'linux-gnu' and that gave me something called 'type-handling' but it didn't fix the problem. I'm running on 11.04.

---

### Post by calimocho on 2011-05-18
I was able to build it without trouble.  I see from your user pane you're on 11.04 and I'm still on 10.10.  Here's the summary from the config script... maybe it will show some clues?  Also, in the link line at the bottom of your post, all the libraries are includeed as -lblahlib but -linux-gnu looks like it would include a library called 'inux-gnu'.  Just a thought.

Configured for `i686-pc-linux-gnu'.

  What operating system and machine description files should Emacs use?
        `s/gnu-linux.h' and `m/intel386.h'
  What compiler should emacs be built with?               gcc -g -O2 -Wdeclaration-after-statement -Wno-pointer-sign
  Should Emacs use the GNU version of malloc?             yes
      (Using Doug Lea's new malloc from the GNU C Library.)
  Should Emacs use a relocating allocator for buffers?    yes
  Should Emacs use mmap(2) for buffer allocation?         no
  What window system should Emacs use?                    x11
  What toolkit should Emacs use?                          none
  Where do we find X Windows header files?                Standard dirs
  Where do we find X Windows libraries?                   Standard dirs
  Does Emacs use -lXaw3d?                                 no
  Does Emacs use -lXpm?                                   yes
  Does Emacs use -ljpeg?                                  yes
  Does Emacs use -ltiff?                                  yes
  Does Emacs use a gif library?                           yes -lgif
  Does Emacs use -lpng?                                   yes
  Does Emacs use -lrsvg-2?                                no
  Does Emacs use -lgpm?                                   no
  Does Emacs use -ldbus?                                  no
  Does Emacs use -lgconf?                                 no
  Does Emacs use -lfreetype?                              no
  Does Emacs use -lm17n-flt?                              no
  Does Emacs use -lotf?                                   no
  Does Emacs use -lxft?                                   no
  Does Emacs use toolkit scroll bars?                     no

---

