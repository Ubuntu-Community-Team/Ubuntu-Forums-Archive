---
title: "Help compiling lm-sensors"
date: 2010-02-11
forum: New to Ubuntu
---

### Post by Mark_in_Hollywood on 2010-02-11
According to the INSTALL file I d/l-d from LM-Sensors webpage [http://www.lm-sensors.org/wiki/Download](http://www.lm-sensors.org/wiki/Download), the only command necessary to compile is as follows:

Compilation
===========

At the top of the Makefile are a couple of configuration variables that
you may want to change. There's a description of what each variable does
in the Makefile itself.

Compilation is done by **`make all**'. You will get a lot of warnings about files which are not found, all ending in `.*d'. You can safely ignore this; they contain dependency information, which is regenerated on the spot.

`make install' installs the package (to /usr/local by default).


I cannot get that to run. I have extracted the tar.bz2, I have put the lm-sensors-xxxx into /usr/local/src/ and the terminal says back to me:

mark@Lexington-19-Karmic:/usr/local/src/lm_sensors-3.1.2$ sudo make all
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

Can someone point me in the right direction, please? Also, I have the AMD K10 thermal sensor.

Someone else got it to work, per this forum at:

[http://ubuntuforums.org/showthread.php?t=1371593&highlight=lm-sensors](http://ubuntuforums.org/showthread.php?t=1371593&highlight=lm-sensors)

but there is nothing of how-to.

I got this idea from a post which read:

[FONT="Arial Black"]Ah right. Sounds like there's no support for your hardware in the version of lm-sensors that's in Karmic (and probably not in the Lucid one, either)

It is supposed to be in the pipeline though.

If you're feeling game you could try downloading and compiling the latest version of lm-sensors direct from the project:

[http://www.lm-sensors.org/wiki/Download](http://www.lm-sensors.org/wiki/Download)[/FONT]

---

### Post by Mustard on 2010-02-11
Off the top of my head I'd say its looking for bison and its not installed.  If I wasnt inclined to read the instructions, I would install an application called bison using synaptic and try to compile again.

Sometimes you find there is a -dev version of an application in synaptic.  So if you find a bison-dev app in Synaptic, install that too! :)

I'd call this Mustard's Hit and Miss method of compilation. ;)

---

### Post by Mark_in_Hollywood on 2010-02-11
Call it Mustard or whatever, I installed bison, tried it again and it faile dwith the same error messages.

---

### Post by Mustard on 2010-02-11
> **Mark_in_Hollywood said:**
> Call it Mustard or whatever, I installed bison, tried it again and it faile dwith the same error messages.

Heh..well that would be the 'miss' part. :)

---

### Post by Mustard on 2010-02-11
There is also bison++ or bisonc++ in repos...I would give them a go...until you get a hit. :)

---

### Post by Anubis on 2010-03-17
You did not follow the simple directions included in the archive.

"I have put the lm-sensors-xxxx into /usr/local/src/ "<<

I don't recall the instructions telling me to extract to /usr/local so I did not. I extracted to a regular folder. Sudo make install will put the files where needed.

---

### Post by Mark_in_Hollywood on 2010-05-25
I solved the problem of having to compile a kernel module by upgrading to a more recent kernel.

[http://ubuntuforums.org/showthread.php?t=1491406](http://ubuntuforums.org/showthread.php?t=1491406)

---

