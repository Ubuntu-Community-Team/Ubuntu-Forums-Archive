---
title: "question on opening and placing .a files files"
date: 2010-08-18
forum: New to Ubuntu
---

### Post by gaurish108 on 2010-08-18
My professor gave me a code to work and experiment with but I am enable to execute it on my Ubuntu 10.04 computer. The two key library files I *dont* have on my computer are libblas.a and liblinpak.a 

Now my computer cannot open both these files. Probably I am missing some software to open such kinds of .a files? 

Also could you tell me where to place such files in the computer? I mean is there any standard folder in the Ubuntu file system where such kinds of files should be kept? 

I am a novice to programming and Ubuntu so some detail will be appreciated. :p:p

---

### Post by Bachstelze on 2010-08-18
You can install the first one from your favourite package manager (the package is [font=monospace]libblas-dev[/font]).  The second one does not seem to be packaged, if you have the .a file, copy it into [font=monospace]/usr/local/lib[/font].

---

### Post by gaurish108 on 2010-08-18
Ah thanks, a couple of more questions:

1. Are .a files compressed files? like .zip .tar.gz etc ???
How does one go about opening them? Not that I will be modifying them or anything but just curious. :lolflag:

2. Also what are the -dev files contain in the Ubuntu repository? Do       they contain all the installation files?

---

### Post by Bachstelze on 2010-08-18
> **gaurish108 said:**
> 
1. Are .a files compressed files? like .zip .tar.gz etc ???
How does one go about opening them? Not that I will be modifying them or anything but just curious. :lolflag:

The [font=monospace]file[/font] utility can tell you a bit more about a file:

```
firas@itsuki ~ % file libz.a 
libz.a: current ar archive
```

.a files are archives created with [font=monospace]ar[/font].  You can see their contents for example with [font=monospace]nm[/font]:

```
firas@itsuki ~ % nm -s libz.a 

Archive index:
adler32 in adler32.o
adler32_combine in adler32.o
adler32_combine64 in adler32.o
compressBound in compress.o
compress2 in compress.o
compress in compress.o
get_crc_table in crc32.o
crc32 in crc32.o
crc32_combine in crc32.o
crc32_combine64 in crc32.o
gzungetc in gzio.o
gzeof in gzio.o
gzdirect in gzio.o
gzclearerr in gzio.o
gzerror in gzio.o
gzclose in gzio.o
gzwrite in gzio.o
gzrewind in gzio.o
gzread in gzio.o
gzseek64 in gzio.o
gzseek in gzio.o
gzgets in gzio.o
gzgetc in gzio.o
gzsetparams in gzio.o
gzdopen in gzio.o
gzopen64 in gzio.o
gzopen in gzio.o
gztell in gzio.o
gztell64 in gzio.o
gzflush in gzio.o
gzputs in gzio.o
gzputc in gzio.o
gzprintf in gzio.o
uncompress in uncompr.o
deflateSetHeader in deflate.o
deflatePrime in deflate.o
deflateTune in deflate.o
deflateEnd in deflate.o
deflateCopy in deflate.o
deflateSetDictionary in deflate.o
deflate in deflate.o
deflateParams in deflate.o
deflateBound in deflate.o
deflateReset in deflate.o
deflateInit2_ in deflate.o
deflateInit_ in deflate.o
deflate_copyright in deflate.o
_tr_init in trees.o
_tr_stored_block in trees.o
_tr_align in trees.o
_tr_tally in trees.o
_length_code in trees.o
_dist_code in trees.o
_tr_flush_block in trees.o
zlibVersion in zutil.o
zlibCompileFlags in zutil.o
zError in zutil.o
z_errmsg in zutil.o
zcfree in zutil.o
zcalloc in zutil.o
inflateReset in inflate.o
inflatePrime in inflate.o
inflateInit2_ in inflate.o
inflateEnd in inflate.o
inflateGetHeader in inflate.o
inflateSync in inflate.o
inflateSyncPoint in inflate.o
inflateUndermine in inflate.o
inflateCopy in inflate.o
inflateSetDictionary in inflate.o
inflate in inflate.o
inflateInit_ in inflate.o
inflateBackInit_ in infback.o
inflateBackEnd in infback.o
inflateBack in infback.o
inflate_table in inftrees.o
inflate_copyright in inftrees.o
inflate_fast in inffast.o

adler32.o:
         U __moddi3
00000000 T adler32
00000290 T adler32_combine
00000360 T adler32_combine64

compress.o:
000000e0 T compress
00000020 T compress2
00000000 T compressBound
         U deflate
         U deflateEnd
         U deflateInit_

crc32.o:
00000010 T crc32
00000550 T crc32_combine
00000580 T crc32_combine64
00000310 t crc32_combine_
00000000 r crc_table
00000000 T get_crc_table

gzio.o:
00001630 t T.64
         U __errno_location
         U __fprintf_chk
         U __sprintf_chk
         U __stack_chk_fail
         U __vsnprintf_chk
00000770 t check_header
         U clearerr
         U crc32
         U deflate
         U deflateEnd
         U deflateInit2_
         U deflateParams
00000200 t destroy
         U fclose
         U fdopen
         U feof
         U ferror
         U fflush
         U fopen
         U fopen64
         U fputc
         U fread
         U free
         U fseeko
         U fseeko64
         U ftello
         U fwrite
00000710 t getLong
00000670 t get_byte
00001100 t gz_open
00000c60 t gz_seek
000000c0 T gzclearerr
000002d0 T gzclose
00000090 T gzdirect
00001570 T gzdopen
00000060 T gzeof
00000100 T gzerror
00001940 T gzflush
00001020 T gzgetc
00000fa0 T gzgets
00001610 T gzopen
000015f0 T gzopen64
00001ca0 T gzprintf
00001b80 T gzputc
00001a80 T gzputs
00000950 T gzread
000005b0 T gzrewind
00000f70 T gzseek
00000f40 T gzseek64
00001060 T gzsetparams
00001900 T gztell
00001920 T gztell64
00000000 T gzungetc
000004b0 T gzwrite
         U inflate
         U inflateEnd
         U inflateInit2_
         U inflateReset
         U malloc
         U memcpy
         U memset
         U strcat
         U strcpy
         U strerror
         U strlen
         U z_errmsg

uncompr.o:
         U inflate
         U inflateEnd
         U inflateInit_
00000000 T uncompress

deflate.o:
         U _dist_code
         U _length_code
         U _tr_align
         U _tr_flush_block
         U _tr_init
         U _tr_stored_block
         U adler32
         U compressBound
00000040 r configuration_table
         U crc32
000007a0 T deflate
00001310 T deflateBound
000001b0 T deflateCopy
000000c0 T deflateEnd
000015d0 T deflateInit2_
00001870 T deflateInit_
00001220 T deflateParams
00000030 T deflatePrime
00001440 T deflateReset
00000660 T deflateSetDictionary
00000000 T deflateSetHeader
00000070 T deflateTune
00000000 R deflate_copyright
00002510 t deflate_fast
00001ce0 t deflate_slow
00001a90 t deflate_stored
00000470 t fill_window
00000400 t flush_pending
         U memcpy
         U memset
         U z_errmsg
         U zcalloc
         U zcfree

trees.o:
00000000 R _dist_code
00000200 R _length_code
00000880 T _tr_align
00001bb0 T _tr_flush_block
00000000 T _tr_init
00000710 T _tr_stored_block
00000c20 T _tr_tally
000009a0 r base_dist
000008a0 r base_length
000007f8 r bl_order
000011a0 t build_tree
00000cc0 t compress_block
00000a20 r extra_blbits
00000920 r extra_dbits
00000820 r extra_lbits
000000e0 t send_tree
00000028 d static_bl_desc
00000014 d static_d_desc
00000780 r static_dtree
00000000 d static_l_desc
00000300 r static_ltree

zutil.o:
         U free
         U malloc
00000020 T zError
00000000 R z_errmsg
00000060 T zcalloc
00000040 T zcfree
00000010 T zlibCompileFlags
00000000 T zlibVersion

inflate.o:
         U adler32
         U crc32
000000c0 r distfix.3932
00000920 T inflate
00000510 T inflateCopy
00000220 T inflateEnd
00000280 T inflateGetHeader
00000110 T inflateInit2_
000026f0 T inflateInit_
000000b0 T inflatePrime
00000000 T inflateReset
00000810 T inflateSetDictionary
000002c0 T inflateSync
000004a0 T inflateSyncPoint
000004e0 T inflateUndermine
         U inflate_fast
         U inflate_table
00000140 r lenfix.3931
         U memcpy
00000080 r order.4000
000006a0 t updatewindow
         U zcalloc
         U zcfree

infback.o:
000000a0 r distfix.3878
00000150 T inflateBack
00000100 T inflateBackEnd
00000000 T inflateBackInit_
         U inflate_fast
         U inflate_table
00000120 r lenfix.3877
         U memcpy
00000060 r order.3899
         U zcalloc
         U zcfree

inftrees.o:
00000080 r dbase.3797
00000040 r dext.3798
00000000 R inflate_copyright
00000000 T inflate_table
00000100 r lbase.3795
000000c0 r lext.3796

inffast.o:
00000000 T inflate_fast

```

In this case, the .a file is a library (not too surprisingly, given that the filename starts with "lib"): a bunch of object files that define some functions you can use in another program.  Since those are binary object files, you don't want to modify them.

> 2. Also what are the -dev files contain in the Ubuntu repository? Do       they contain all the installation files?

Generally speaking, the -dev files are packages that only a developer would need, not a "normal" user.  In most cases, like your [font=monospace]libblas-dev[/font], they contain the files you need to develop software that uses the library in question (static library and header files).

---

