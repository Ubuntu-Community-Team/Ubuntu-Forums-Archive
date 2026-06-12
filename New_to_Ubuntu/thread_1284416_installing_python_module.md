---
title: "installing python module"
date: 2009-10-06
forum: New to Ubuntu
---

### Post by filifunk on 2009-10-06
I've downloaded scikits.timeseries, and I'm trying to install it.  This is my first time downloading something out of the synaptic manager.  I've run the setup python script and this is what I get:

```


Tasks:
  i       - Show python/platform/machine information
  ie      - Show environment information
  c       - Show C compilers information
  c<name> - Set C compiler (current:None)
  f       - Show Fortran compilers information
  f<name> - Set Fortran compiler (current:None)
  e       - Edit proposed sys.argv[1:].

Task aliases:
  0         - Configure
  1         - Build
  2         - Install
  2<prefix> - Install with prefix.
  3         - Inplace build
  4         - Source distribution
  5         - Binary distribution

Proposed sys.argv = ['setup.py', 'build']
    
Choose a task (^D to quit, Enter to continue with setup):


```

When I choose install, nothing happens, it just shows this on the bottom:

Proposed sys.argv = ['setup.py', 'install']

I figured maybe I should just use 

```


run setup.py install


``` 

and I get an error message

```


SystemExit: error in scikits.timeseries setup command: Distribution contains no modules or packages for namespace package 'scikits'
WARNING: Failure executing file: <setup.py>

```

Any tips on how to install this?  I'm kind of a newbie to linux.  I'm used to just double clicking on something and it installs lol.  Thanks eveyrone

---

### Post by wojox on 2009-10-08
What happens when you choose:

```
1         - Build
```

---

