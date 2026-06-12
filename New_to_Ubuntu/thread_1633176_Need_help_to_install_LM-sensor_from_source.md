---
title: "Need help to install LM-sensor from source"
date: 2010-11-28
forum: New to Ubuntu
---

### Post by Mobidoy on 2010-11-28
My laptop is fairly new and, it does not look like that the version of lm-sensors that is installed from the repo detects my cpu core temp sensors so, I am trying to install the latest version from source.

I have downloaded and extracted the latest version then I follow an old post here: 

1- in a terminal window, I cd to lm_sensors-3.2.0 directory
2- I do a sudo make user
but I get numerous errors... 

```
Makefile:175: lib/data.ld: No such file or directory
Makefile:175: lib/general.ld: No such file or directory
Makefile:175: lib/error.ld: No such file or directory
Makefile:175: lib/access.ld: No such file or directory
Makefile:175: lib/init.ld: No such file or directory
Makefile:175: lib/sysfs.ld: No such file or directory
Makefile:175: lib/conf-parse.ld: No such file or directory
Makefile:175: lib/conf-lex.ld: No such file or directory
Makefile:175: lib/data.ad: No such file or directory
Makefile:175: lib/general.ad: No such file or directory
Makefile:175: lib/error.ad: No such file or directory
Makefile:175: lib/access.ad: No such file or directory
Makefile:175: lib/init.ad: No such file or directory
Makefile:175: lib/sysfs.ad: No such file or directory
Makefile:175: lib/conf-parse.ad: No such file or directory
Makefile:175: lib/conf-lex.ad: No such file or directory
Makefile:175: prog/sensors/main.rd: No such file or directory
Makefile:175: prog/sensors/chips.rd: No such file or directory
Makefile:175: prog/dump/util.rd: No such file or directory
Makefile:175: prog/dump/isadump.rd: No such file or directory
Makefile:175: prog/dump/isaset.rd: No such file or directory
Makefile:175: prog/dump/superio.rd: No such file or directory
gcc -M -MG -DETCDIR="\"/etc\"" -I.  -Wall -O2 -Wstrict-prototypes -Wshadow -Wpointer-arith -Wcast-qual -Wcast-align -Wwrite-strings -Wnested-externs -Winline -W -Wmissing-prototypes -Wundef  prog/dump/superio.c | \
	sed -e 's@^\(.*\)\.o:@prog/dump/superio.rd prog/dump/superio.ro: Makefile '`dirname prog/dump/superio.rd`/Module.mk' @' > prog/dump/superio.rd
gcc -M -MG -DETCDIR="\"/etc\"" -I.  -Wall -O2 -Wstrict-prototypes -Wshadow -Wpointer-arith -Wcast-qual -Wcast-align -Wwrite-strings -Wnested-externs -Winline -W -Wmissing-prototypes -Wundef  prog/dump/isaset.c | \
	sed -e 's@^\(.*\)\.o:@prog/dump/isaset.rd prog/dump/isaset.ro: Makefile '`dirname prog/dump/isaset.rd`/Module.mk' @' > prog/dump/isaset.rd
gcc -M -MG -DETCDIR="\"/etc\"" -I.  -Wall -O2 -Wstrict-prototypes -Wshadow -Wpointer-arith -Wcast-qual -Wcast-align -Wwrite-strings -Wnested-externs -Winline -W -Wmissing-prototypes -Wundef  prog/dump/isadump.c | \
	sed -e 's@^\(.*\)\.o:@prog/dump/isadump.rd prog/dump/isadump.ro: Makefile '`dirname prog/dump/isadump.rd`/Module.mk' @' > prog/dump/isadump.rd
gcc -M -MG -DETCDIR="\"/etc\"" -I.  -Wall -O2 -Wstrict-prototypes -Wshadow -Wpointer-arith -Wcast-qual -Wcast-align -Wwrite-strings -Wnested-externs -Winline -W -Wmissing-prototypes -Wundef  prog/dump/util.c | \
	sed -e 's@^\(.*\)\.o:@prog/dump/util.rd prog/dump/util.ro: Makefile '`dirname prog/dump/util.rd`/Module.mk' @' > prog/dump/util.rd
gcc -M -MG -DETCDIR="\"/etc\"" -I.  -Wall -O2 -Wstrict-prototypes -Wshadow -Wpointer-arith -Wcast-qual -Wcast-align -Wwrite-strings -Wnested-externs -Winline -W -Wmissing-prototypes -Wundef  prog/sensors/chips.c | \
	sed -e 's@^\(.*\)\.o:@prog/sensors/chips.rd prog/sensors/chips.ro: Makefile '`dirname prog/sensors/chips.rd`/Module.mk' @' > prog/sensors/chips.rd
gcc -M -MG -DETCDIR="\"/etc\"" -I.  -Wall -O2 -Wstrict-prototypes -Wshadow -Wpointer-arith -Wcast-qual -Wcast-align -Wwrite-strings -Wnested-externs -Winline -W -Wmissing-prototypes -Wundef  prog/sensors/main.c | \
	sed -e 's@^\(.*\)\.o:@prog/sensors/main.rd prog/sensors/main.ro: Makefile '`dirname prog/sensors/main.rd`/Module.mk' @' > prog/sensors/main.rd
bison -p sensors_yy -d lib/conf-parse.y -o lib/conf-parse.c
make: bison: Command not found
make: *** [lib/conf-parse.c] Error 127

``` 

What do I do wrong ?

---

### Post by bananas4370 on 2010-11-29
> **Mobidoy said:**
> My laptop is fairly new and, it does not look like that the version of lm-sensors that is installed from the repo detects my cpu core temp sensors so, I am trying to install the latest version from source.

What do I do wrong ?

According to the INSTALL file, you only need to issue

```
make all
```

and

```
sudo make install
```

to install. 

The README file also says this

[I]You will get a lot of warnings about files which are not found, all ending in `.*d'. You can safely ignore this; they contain dependency information, which is regenerated on the
spot.

[/I]That explains the error you are getting at the beginning of compilation.
Cheers
Patrick

---

### Post by budde on 2011-02-06
You need to install the bison package (sudo apt-get install bison) and that should get you through it.

If you look at the INSTALL file it also says:
"
Dependencies
============

Build-time dependencies:
* GNU make
* gcc
* bison
* flex
* rrd header files (optional, for sensord)"

This means you need bison to compile it.

Good luck.

---

### Post by Paqman on 2011-02-06
> **Mobidoy said:**
> My laptop is fairly new and, it does not look like that the version of lm-sensors that is installed from the repo detects my cpu core temp sensors so, I am trying to install the latest version from source.


Just to back up a step, did you run:
```
sudo sensors-detect
```
in a terminal after installing it?

---

### Post by perspectoff on 2011-02-06
If my memory serves me correctly, lm-sensors is not used by the Linux kernel at all.

Lm-sensors these days is an add on (I don't even think it's in the main repositories -- it's in the universe repositories).

If you are installing it to influence the way the kernel monitors temperature sensors, this might not work.

---

