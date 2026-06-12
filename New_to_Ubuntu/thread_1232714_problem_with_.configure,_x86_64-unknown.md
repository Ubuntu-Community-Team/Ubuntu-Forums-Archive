---
title: "problem with ./configure, x86_64-unknown"
date: 2009-08-05
forum: New to Ubuntu
---

### Post by Commisar Jimp on 2009-08-05
My sound recently went out, and I think it is a problem with the Esound daemon, so I'm trying to reinstall it. I tried synaptic first, but that didn't work, so I downloaded it from their website, and now I've got the directory on my desktop, but I'm having problems installing it. When I entered ./configure it ran its list of checks, but at the bottom it said this:

checking build system type... Invalid configuration `x86_64-unknown-linux-gnu': machine `x86_64-unknown' not recognized

a few lines later:

ltconfig: you must specify a host type if you use `--no-verify'
Try `ltconfig --help' for more information.

it doesn't recognize the ltconfig --help command so that didn't help, the INSTALL text that came with it mentioned that ./configure might not recognize the host system, this seems like it fits with the first error message, and that I should add the "--host=TYPE" option, but did not explain what that was, so if any one could help me with that that'd be great.

HOWEVER, (sorry this is getting so long and complex, but I'm new to this and not quite sure whats wrong) in the esound directory is a file labeled configure, one labled Makefile.in, one called Makefile.am, and several with names like install-sh and configure.in. I'm not completely sure what kind of files are made/changed when ./configure is used, so I'm not sure if one of those is the makefile and my make command isn't working working (it reads "make: *** No targets specified and no makefile found.  Stop.e is the makefile and my make command isn't working working")

This post ran much longer than I intended it to, so I'll sum up quick, either my ./configure command isn't recognizing my system and I need to use --host=TYPE, or ./configure is fine, and make can't find my make file, or something else has escaped me. Either way I'm stumped and online guides and esound readmes aren't helping. If anyone can provide me with a few nuggets of wisdom I'd me infinitly greatful.

---

### Post by Xbehave on 2009-08-06
EDIT: ignore this, i must have changed something else because i no longer need to specify the build, do you have build-essentials installed?


sorry thoughed id posted this earlier, to fix the 
```
checking build system type... Invalid configuration `x86_64-unknown-linux-gnu': machine `x86_64-unknown' not recognized
```error you just use ./configure --build=x86_64 (actually it was your host suggestion that helped me sort out that part of a problem i was having) you may want to help sort other problems you may want to attach config.log to the post so people can see the specifics.

---

### Post by arthurfragoso on 2011-12-10
It's an old thread, but I had the same problem trying to compile an old program and I found a solution. This may be useful for somebody else:

the file 'config.sub' contains the supported CPUs, if it's an old version, it wont support newer CPUs.

so, you can get the latest version of 'config.sub' from:
[http://git.savannah.gnu.org/gitweb/?p=config.git;a=blob_plain;f=config.sub;hb=HEAD](http://git.savannah.gnu.org/gitweb/?p=config.git;a=blob_plain;f=config.sub;hb=HEAD)

just copy the latest version of 'config.sub' and replace to the one that's in the folder of what you are trying to run the ./configure

good luck to anyone having the same problem ;)

---

### Post by oldos2er on 2011-12-10
Closed, necromancy.

---

