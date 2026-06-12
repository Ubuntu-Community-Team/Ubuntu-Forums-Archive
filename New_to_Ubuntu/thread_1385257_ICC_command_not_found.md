---
title: "ICC: command not found"
date: 2010-01-19
forum: New to Ubuntu
---

### Post by mister_playboy on 2010-01-19
I have the Intel C++ Compiler installed, but I get this error of "icc:command not found".  I've gathered that I can fix this by editing .bashrc, but I am unclear on the lines to add.  Any help?

It's installed to /opt/intel/Compiler/11.0/083/bin/intel64

Trying to use it to compile Firefox, and this is the last hurdle (I hope). ;)

---

### Post by sisco311 on 2010-01-19
You have to use the full path to the application (/opt/intel/Compiler/11.0/083/bin/intel64) or add the /opt/intel/Compiler/11.0/083/bin/ directory to your PATH environment variable.

Append the ~/.bashrc file with: 
```

if [ -d "/opt/intel/Compiler/11.0/083/bin" ] ; then
    PATH="/opt/intel/Compiler/11.0/083/bin:$PATH"
fi

```
then run:
```
. ~/.bashrc
```

---

### Post by mister_playboy on 2010-01-19
> **sisco311 said:**
> You have to use the full path to the application (/opt/intel/Compiler/11.0/083/bin/intel64) or add the /opt/intel/Compiler/11.0/083/bin/ directory to your PATH environment variable.

Append the ~/.bashrc file with: 
```

if [ -d "/opt/intel/Compiler/11.0/083/bin" ] ; then
    PATH="/opt/intel/Compiler/11.0/083/bin:$PATH"
fi

```
then run:
```
. ~/.bashrc
```

```

if [ -d "/opt/intel/Compiler/11.0/083/bin/intel64" ] ; then
    PATH="/opt/intel/Compiler/11.0/083/bin/intel64:$PATH"
fi

``` ;)

That solved it!  Thank you very much.

---

### Post by FRKiran on 2012-12-08
Excuse me! But how can we find the address that we should use in the pass?

---

### Post by howefield on 2012-12-08
Old thread back to sleep.

Please feel free to start a fresh one.

---

