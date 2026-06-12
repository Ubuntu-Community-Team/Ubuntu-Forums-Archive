---
title: "Compiling IceCat (help needed please!)"
date: 2008-12-08
forum: New to Ubuntu
---

### Post by unknownwarrior33 on 2008-12-08
Hey everyone.  So, I'm trying to build IceCat from the source, and I have a bit of a problem.  I have all the correct libraries installed, but I still get this error when I try to compile using make (after config):

```
jsinterp.o: file not recognized: File truncated
collect2: ld returned 1 exit status
make[3]: *** [libmozjs.so] Error 1
make[3]: Leaving directory `/home/jake/icecat/js/src'
make[2]: *** [libs_tier_js] Error 2
make[2]: Leaving directory `/home/jake/icecat'
make[1]: *** [tier_js] Error 2
make[1]: Leaving directory `/home/jake/icecat'
make: *** [default] Error 2

```

---

### Post by snova on 2008-12-08
Can you provide a little more context please? I'm not sure what this error means, but it would be useful to know what led up to this error.

Running make again should repeat the error.

---

### Post by unknownwarrior33 on 2008-12-08
I think the problem started here:

```
make[3]: Entering directory `/home/jake/icecat/js/src'
rm -f libmozjs.so
gcc  -Wall -W -Wno-unused -Wpointer-arith -Wcast-align -W -Wno-long-long -pedantic -fno-strict-aliasing -pthread -pipe  -DNDEBUG -DTRIMMED -pipe -O2 -fPIC -shared -Wl,-z,defs -Wl,-h,libmozjs.so -o libmozjs.so  jsapi.o jsarena.o jsarray.o jsatom.o jsbool.o jscntxt.o jsdate.o jsdbgapi.o jsdhash.o jsdtoa.o jsemit.o jsexn.o jsfun.o jsgc.o jshash.o jsinterp.o jsinvoke.o jsiter.o jslock.o jslog2.o jslong.o jsmath.o jsnum.o jsobj.o jsopcode.o jsparse.o jsprf.o jsregexp.o jsscan.o jsscope.o jsscript.o jsstr.o jsutil.o jsxdrapi.o jsxml.o prmjtime.o     -lpthread  -Wl,-rpath-link,../../dist/bin   -lm -ldl -L../../dist/lib -lplds4 -lplc4 -lnspr4 -lpthread -ldl -ldl -lm
jsinterp.o: file not recognized: File truncated
collect2: ld returned 1 exit status
make[3]: *** [libmozjs.so] Error 1
make[3]: Leaving directory `/home/jake/icecat/js/src'
make[2]: *** [libs_tier_js] Error 2
make[2]: Leaving directory `/home/jake/icecat'
make[1]: *** [tier_js] Error 2
make[1]: Leaving directory `/home/jake/icecat'
make: *** [default] Error 2

```

---

### Post by phidia on 2008-12-08
There is a deb file [here]("http://www.mail-archive.com/info-gnu@gnu.org/msg00555.html").

---

### Post by snova on 2008-12-08
Try removing the object file in question (jsinterp.o) and run make again, see what happens.

---

### Post by unknownwarrior33 on 2008-12-08
Using the .deb I got it installed OK, but now the problem is that I can't get any plugins or add-ons working.  I found a way to make a link to gnash, but when I try to make the link it tells me the plugins folder doesn't exist.  Is there a different place I need to put it?  Add-ons are another problem; are add-ons from the mozilla database supposed to work?

At this point I think I'm just going to stick with the unbranded browser, but I may keep trying if there is a relatively easy way to do it.  Thanks for your help.

---

### Post by phidia on 2008-12-08
There is a wiki guide on Ice Cat [here]("http://www.linuxconfig.org/GNU_IceCat"). You might also look into swiftweasel and/or [this thread]("http://ubuntuforums.org/showthread.php?t=822129").

---

