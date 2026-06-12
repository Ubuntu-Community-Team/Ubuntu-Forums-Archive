---
title: "Help in compiling shntool 3.0.10 in 64-bit"
date: 2010-05-03
forum: New to Ubuntu
---

### Post by roddersg on 2010-05-03
I have just moved to 64-bit 10.04 and need shntool 3.0.10 ([http://etree.org/shnutils/shntool/](http://etree.org/shnutils/shntool/)) to be recompiled.  I was running the 32-bit in 9.10.

here's my results:
**./configure**
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
..
(the rest is ok, ready to build)

**make **
Making all in man
make[1]: Entering directory `/home/rodney/Downloads/shntool-3.0.10/man'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/rodney/Downloads/shntool-3.0.10/man'
Making all in src
make[1]: Entering directory `/home/rodney/Downloads/shntool-3.0.10/src'
gcc -DHAVE_CONFIG_H -I. -I../include  -I../include  -I../include -g -O2 -MT glue_modes.o -MD -MP -MF .deps/glue_modes.Tpo -c -o glue_modes.o glue_modes.c
mv -f .deps/glue_modes.Tpo .deps/glue_modes.Po
gcc -DHAVE_CONFIG_H -I. -I../include  -I../include  -I../include -g -O2 -MT glue_formats.o -MD -MP -MF .deps/glue_formats.Tpo -c -o glue_formats.o glue_formats.c
mv -f .deps/glue_formats.Tpo .deps/glue_formats.Po
gcc -I../include -g -O2   -o shntool core_convert.o core_fileio.o core_format.o core_mode.o core_module.o core_output.o core_shntool.o core_wave.o glue_modes.o glue_formats.o mode_len.o mode_fix.o mode_hash.o mode_pad.o mode_join.o mode_split.o mode_cat.o mode_cmp.o mode_cue.o mode_conv.o mode_info.o mode_strip.o mode_gen.o mode_trim.o  format_wav.o format_aiff.o format_shn.o format_flac.o format_ape.o format_alac.o format_tak.o format_ofr.o format_tta.o format_als.o format_wv.o format_lpac.o format_la.o format_mkw.o format_bonk.o format_kxs.o format_cust.o format_term.o format_null.o  
make[1]: Leaving directory `/home/rodney/Downloads/shntool-3.0.10/src'
make[1]: Entering directory `/home/rodney/Downloads/shntool-3.0.10'

any ideas on how to fix this?
(NB. Ubuntu provides 3.0.08 but can't use this because I need the -F option).

Thanks

Rodders

---

### Post by ibuclaw on 2010-05-03
Looks like it compiled successfully mate.
What happens when you run:
```
./src/shntool
```

Regards

---

### Post by ibuclaw on 2010-05-03
PS:

Did you clean the build directory before recompiling?
```
make distclean
```

Then run the configure and make steps again.
```
./configure && make
```

Regards
Iain

---

