---
title: "libg2c-dev for MM5 model"
date: 2009-09-22
forum: New to Ubuntu
---

### Post by ceambi on 2009-09-22
[SIZE=2]Dear All user,[/SIZE]
 
[SIZE=2]I have a problem with libg2c-dev on a newly-installed intel fortran on my ubuntu. When I compile the program of make intel in terrain.deck which required the libg2c and libg2c-dev, I have got this error. [/SIZE]
 
[SIZE=2]/home/asnor/MM5V3/NCAR_Graphic/lib/libncarg.a(fl2int.o): In function `fl2int_':[/SIZE]
[SIZE=2]fl2int.f.text+0x20): undefined reference to `gqcntn_'[/SIZE]
[SIZE=2]fl2int.f.text+0x76): undefined reference to `gqnt_'[/SIZE]
[SIZE=2]/home/asnor/MM5V3/NCAR_Graphic/lib/libncarg.a(eprin.o): In function `eprin_':[/SIZE]
[SIZE=2]eprin.f.text+0x74): undefined reference to `_gfortran_st_write'[/SIZE]
[SIZE=2]eprin.f.text+0x97): undefined reference to `_gfortran_transfer_integer'[/SIZE]
[SIZE=2]eprin.f.text+0xc5): undefined reference to `_gfortran_transfer_character'[/SIZE]
[SIZE=2]eprin.f.text+0xd3): undefined reference to `_gfortran_st_write_done'[/SIZE]
[SIZE=2]/home/asnor/MM5V3/NCAR_Graphic/lib/libncarg.a(ardbda.o): In function `ardbda_':[/SIZE]
[SIZE=2]ardbda.f.text+0x26a): undefined reference to `_gfortran_st_write'[/SIZE]
[SIZE=2]ardbda.f.text+0x287): undefined reference to `_gfortran_transfer_integer'[/SIZE]
[SIZE=2]ardbda.f.text+0x295): undefined reference to `_gfortran_st_write_done'[/SIZE]
[SIZE=2]ardbda.f.text+0x3f: undefined reference to `_gfortran_st_write'[/SIZE]
[SIZE=2]ardbda.f.text+0x415): undefined reference to `_gfortran_transfer_integer'[/SIZE]
[SIZE=2]ardbda.f.text+0x423): undefined reference to `_gfortran_st_write_done'[/SIZE]
[SIZE=2]ardbda.f.text+0x5da): undefined reference to `_gfortran_st_write'[/SIZE]
[SIZE=2]ardbda.f.text+0x5f7): undefined reference to `_gfortran_transfer_integer'[/SIZE]
[SIZE=2]ardbda.f.text+0x605): undefined reference to `_gfortran_st_write_done'[/SIZE]
[SIZE=2]/home/asnor/MM5V3/NCAR_Graphic/lib/libncarg.a(galbex.o): In function `galbex_':[/SIZE]
[SIZE=2]galbex.f.text+0xc0): undefined reference to `_gfortran_compare_string'[/SIZE]
[SIZE=2]/home/asnor/MM5V3/NCAR_Graphic/lib/libncarg.a(gaplch.o): In function `gaplch_':[/SIZE]
[SIZE=2]gaplch.f.text+0x326): undefined reference to `_gfortran_compare_string'[/SIZE]
[SIZE=2]/home/asnor/MM5V3/NCAR_Graphic/lib/libncarg.a(pcsetc.o): In function `pcsetc_':[/SIZE]
[SIZE=2]pcsetc.f.text+0x60): undefined reference to `_gfortran_compare_string'[/SIZE]
[SIZE=2]pcsetc.f.text+0x89): undefined reference to `_gfortran_compare_string'[/SIZE]
[SIZE=2]pcsetc.f.text+0xcc): undefined reference to `_gfortran_compare_string'[/SIZE]
[SIZE=2]/home/asnor/MM5V3/NCAR_Graphic/lib/libncarg.a(pcsetc.o)csetc.f.text+0xf5): more undefined references to `_gfortran_compare_string' follow[/SIZE]
[SIZE=2]/home/asnor/MM5V3/NCAR_Graphic/lib/libncarg.a(cpux.o): In function `cpux_':[/SIZE]
[SIZE=2]cpux.f.text+0x20): undefined reference to `gqcntn_'[/SIZE]
[SIZE=2]cpux.f.text+0x7e): undefined reference to `gqnt_'[/SIZE]
[SIZE=2]/home/asnor/MM5V3/NCAR_Graphic/lib/libncarg.a(cpuy.o): In function `cpuy_':[/SIZE]
[SIZE=2]cpuy.f.text+0x20): undefined reference to `gqcntn_'[/SIZE]
[SIZE=2]cpuy.f.text+0x7e): undefined reference to `gqnt_'[/SIZE]
[SIZE=2]make[1]: [terrain.exe] Error 1 (ignored)[/SIZE]
[SIZE=2]make[1]: Leaving directory `/home/asnor/MM5V3/TERRAIN/src'[/SIZE]
[SIZE=2]However, when I check, I have found that it exists on the file system.[/SIZE]
 
[SIZE=2]When am using the Synaptic Package Manager and search for libg2c but I found libg2c only not libg2c-dev. Actually, MM5 model need this two files. Due to the errors above, there are a lot of 'undefined reference' but I just copy some of them. Therefore, does anyone know how to fix this problem? Thank you in advance for your help.[/SIZE]
 
[SIZE=2]ceambi[/SIZE]

---

