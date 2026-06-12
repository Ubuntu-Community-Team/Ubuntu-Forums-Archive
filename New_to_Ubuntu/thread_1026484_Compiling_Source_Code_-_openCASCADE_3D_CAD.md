---
title: "Compiling Source Code - openCASCADE 3D CAD"
date: 2008-12-31
forum: New to Ubuntu
---

### Post by Roger Allott on 2008-12-31
I've been hunting around for a good 3D CAD package and having looked at their website, I think [openCASCADE]("http://www.opencascade.org") might be suitable for me.

However, I'm a bit confused as to how to go about installing it, and what I need to install.

I prefer to install all my software via Synaptic. There are 5 packages on Synaptic from the Multiverse repository, but none of them seem to be the main program. The packages are:
[LIST][*]opencascade-doc
[*]opencascade-examples
[*]opencascade-tools
[*]libopencascade-dev
[*]libopencascade6.2[/LIST]

All those seem to be support files, not the program itself, and they also seem to reference version 6.2 of openCASCADE.

The openCASCADE website offers version 6.3, but only as source code (.tgz) for local compiling. I've never compiled an application before, so could someone walk me through how I do it?

Also, would it be worthwhile getting Synaptic to install the version 6.2 stuff from Multiverse, or would that cause a conflict?

---

### Post by Sealbhach on 2008-12-31
The main stages in compiling are:

```
sudo apt-get install build-essential
```

Extract the tar.gz

cd into the folder it creates

```
./configure
```

```
make 
```

```
make install
```

There may be more dependencies you need specific to this software, you can also specify options to compile for different CPUs and stuff.

There's a very good tutorial here

[http://www.linuxformat.co.uk/wiki/index.php/Compiling_Made_Easy](http://www.linuxformat.co.uk/wiki/index.php/Compiling_Made_Easy)

which you can follow and it will show you most of the issues that come up.


.

---

### Post by cb951303 on 2008-12-31
open cascade is not a CAD. it's a library.

---

### Post by Roger Allott on 2009-01-01
> **Sealbhach said:**
> The main stages in compiling are:

```
sudo apt-get install build-essential
```

Extract the tar.gz

OK, done that.

> **Sealbhach said:**
> cd into the folder it creates

No problem.

> **Sealbhach said:**
> ```
./configure
```

```
make 
```

```
make install
```

It's THAT easy???? No need for sudo?? No need for suffixes or for me to identify which files to configure, make or install?

> **Sealbhach said:**
> There may be more dependencies you need specific to this software, you can also specify options to compile for different CPUs and stuff.

I'd expect the process will identify which dependency packages I need, and I should be able to get them via Synaptic, I suppose.

> **Sealbhach said:**
> There's a very good tutorial here

[http://www.linuxformat.co.uk/wiki/index.php/Compiling_Made_Easy](http://www.linuxformat.co.uk/wiki/index.php/Compiling_Made_Easy)

which you can follow and it will show you most of the issues that come up.

Thanks. Yes, I've read that tutorial. Still got a few uncertainties though. For example, the tutorial says to run:
```
./configure --help
```

What's the benefit of adding the '--help' suffix?

---

