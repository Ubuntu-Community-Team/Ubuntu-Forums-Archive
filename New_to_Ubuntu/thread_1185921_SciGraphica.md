---
title: "SciGraphica"
date: 2009-06-12
forum: New to Ubuntu
---

### Post by padeco on 2009-06-12
hi there,

i was wondering if anyone has been able to install SciGraphica on Ubuntu - 8.04. if so, is there a step by step guide as to the process that was followed. i have attempted many times without any luck.

$sudo ./configure - goes very well, with no errors;

$sudo make - starts, and then the following error:

In file included from ../sg.h:28,
                 from python_config.c:15:
../../config.h:8:22: warning: missing terminating " character
In file included from python_config.c:17:
python_main.h:17:25: error: arrayobject.h: No such file or directory
In file included from python_main.h:19,
                 from python_config.c:17:
python_sheet.h:45: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;PyArrayObject&#8217;
python_config.c: In function &#8216;config_apply&#8217;:
python_config.c:239: error: label at end of compound statement
python_config.c: In function &#8216;sg_create_config_dialog&#8217;:
python_config.c:613: error: label at end of compound statement
make[3]: *** [python_config.o] Error 1
make[3]: Leaving directory `/home/.../programs/scigraphica-0.8.0/src/python'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/.../programs/scigraphica-0.8.0/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/.../programs/scigraphica-0.8.0'
make: *** [all-recursive-am] Error 2

many thanks,
padeco

---

### Post by leandromartinez98 on 2009-06-12
I can't help exactly with your problem. But we use Xmgrace and/or Qtiplot, both which are in the default ubuntu respositories and are powerful scientific graphic softwares. Particularly Qtiplot is very straightforward to use.

---

### Post by padeco on 2009-06-13
thanks leandro,

i do have Qtiplot, and it is a nice software. however, i would like to have a try of scigraphica since it has some extra resources.

cheers,
padeco

---

### Post by mdshaver on 2009-12-13
I believe scigraphica is still within the mandriva repositories so maybe you could either install Mandriva or find an .rpm and convert it to a .deb using alien.

---

