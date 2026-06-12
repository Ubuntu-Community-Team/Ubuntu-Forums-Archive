---
title: "Gem install rubygame fails"
date: 2010-05-29
forum: New to Ubuntu
---

### Post by trigsenior on 2010-05-29
Trying to install rubygame with gem , but get this error 

```
@-laptop:~$ sudo gem install rubygame
[sudo] password for @: 

Building native extensions.  This could take a while...
ERROR:  Error installing rubygame:
	ERROR: Failed to build gem native extension.

rake RUBYARCHDIR=/var/lib/gems/1.8/gems/ffi-0.6.3/lib RUBYLIBDIR=/var/lib/gems/1.8/gems/ffi-0.6.3/lib
sh: rake: not found


Gem files will remain installed in /var/lib/gems/1.8/gems/ffi-0.6.3 for inspection.
Results logged to /var/lib/gems/1.8/gems/ffi-0.6.3/gen/gem_make.out

```


Here are gems i already have

```


gem list --local 

*** LOCAL GEMS ***

anise (0.4.0)
autumn (3.1.11)
daemons (1.0.10)
english (0.6.0, 0.5.0)
facets (2.8.4, 2.8.1)
language (0.6.0)
rake (0.8.7)
sribi (3.2.10)


```

Gem and ruby version

```

Gem version 1.3.1
ruby 1.8.7 (2008-08-11 patchlevel 72) [i486-linux]*

```

---

### Post by jas1290 on 2010-06-24
bump for similar problem

---

### Post by JeremyA on 2010-12-08
Try the page at [http://www.ubuntuupdates.org/ppa/pratikmsinha_ruby_1.9.2](http://www.ubuntuupdates.org/ppa/pratikmsinha_ruby_1.9.2)
 -- that's a version of ruby that SHOULD work with rubygame.

Good luck!

---

