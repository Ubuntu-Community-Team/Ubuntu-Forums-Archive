---
title: "Uninstall and shortcut question"
date: 2011-08-16
forum: New to Ubuntu
---

### Post by jyerabutar on 2011-08-16
Hello, 1st post YAY !

I've just converted to ubuntu and have been reading my head off, there're some questions I can't seem to get my head around.

1. My question is when a program gets installed ( from the apt-get command ) for all users i see it goes to >> /usr/bin/(here)

and i assume it keeps the path somewhere (may be a config file) so we could properly uninstall it using the 
apt-get uninstall command.

Is this correct?

Also is there a list somewhere that tells the system where that executables are?  
for exp. typing "firefox" will launch the FF browser. I know that we could add PATHS to programs that we compile and run ourselves but i don't quite under stand this.

2. Another question is what about programs that we configure, make and install ourselves? We can locate where we want it to be installed but to properly remove it do we just rm the directory?

Thanks !
Jack

---

### Post by Shake 'n' Bake on 2011-08-16
To uninstall run
```

sudo apt-get remove [softwarehere]

```

Or to remove configuration files as well, do this

```

sudo apt-get purge [softwarehere]

```

I have found that, unless I'm missing something, Synaptic is the only way to *completely* remove something.

I'm not 100% on this, but I do not think there is a concrete list of executables anywhere.  Usually, the software comes with something of an add-on to the command line.

---

### Post by jyerabutar on 2011-08-16
thanks for the quick answer

maybe because i am coming from a windows base architechtire where programs get installed into their own folders except for libraries and some other stuff.

but how is it possible to keep track of every file? where they should belong?

---

### Post by jtarin on 2011-08-16
In Linux and therefore Ubuntu the system has what is called "[Environment Variables]("https://help.ubuntu.com/community/EnvironmentVariables")"....this should answer some of you questions.

For [Debian Package Management]("http://wiki.debian.org/PackageManagement?action=show&redirect=CategoryPackageManagement") of which Ubuntu uses.....

---

### Post by jtarin on 2011-08-16
> **jyerabutar said:**
> thanks for the quick answer

maybe because i am coming from a windows base architechtire where programs get installed into their own folders except for libraries and some other stuff.

but how is it possible to keep track of every file? where they should belong?You have documentation and several excellent tools for searching and locating non-standard packages or left-over configs. I agree with using Synaptics.

---

