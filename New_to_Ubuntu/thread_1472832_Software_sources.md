---
title: "Software sources"
date: 2010-05-04
forum: New to Ubuntu
---

### Post by saltynut on 2010-05-04
Hello Im a complete newbie to this so forgive me if i come off ignorant but I am trying to install Adobe falsh player and reader downloaded but tells me it needs something to open it so I read to do this I need to go to System>Admin >Software Sources...but when i click on software sources it doesnt open any help would be galdly appreciated.....Rob

---

### Post by barney385 on 2010-05-04
These you can activate in your software sources:
The repository components are: 

[LIST]
[*]**Main** - Officially supported software. 
[*]**Restricted**  - Supported software that is not available under a completely free  license. 
[*]**Universe** - Community maintained  software, i.e. not officially supported software. 
[*]**Multiverse**  - Software that is not free.  
[/LIST]
Then follow the instructions and add: [http://www.medibuntu.org/](http://www.medibuntu.org/)

See if that helps.

---

### Post by saltynut on 2010-05-04
Maybe im not following but when I click on software sources nothing happens.

---

### Post by barney385 on 2010-05-04
System>Administration>Software Sources

This is where you're going right?

---

### Post by saltynut on 2010-05-04
yes thats where im going i sign in as admin but when i click on sotware sources it doesnt open

---

### Post by barney385 on 2010-05-04
Try this thread:

[http://ubuntuforums.org/showthread.php?t=1469825&highlight=terminal+software+sources](http://ubuntuforums.org/showthread.php?t=1469825&highlight=terminal+software+sources)

---

### Post by saltynut on 2010-05-04
that all refers me to open the software sources which wont work

---

### Post by saltynut on 2010-05-04
let me add to this as I am discovering that now i can only open 2 or 3 of the programs under admistration some act like they are going to open then they just dissappear.

---

### Post by oldos2er on 2010-05-04
Can you run **gksu software-properties-gtk** in a terminal, and post the output here?

---

### Post by Jetro on 2010-11-03
Since this applies to me as well, I'll post here.

```
gksu software-properties-gtk
Traceback (most recent call last):  File "/usr/bin/software-properties-gtk", line 113, in <module>
    app = SoftwarePropertiesGtk(datadir=data_dir, options=options, file=file)
  File "/usr/lib/python2.6/dist-packages/softwareproperties/gtk/SoftwarePropertiesGtk.py", line 87, in __init__
    SoftwareProperties.__init__(self, options=options, datadir=datadir)
  File "/usr/lib/python2.6/dist-packages/softwareproperties/SoftwareProperties.py", line 90, in __init__
    self.reload_sourceslist()
  File "/usr/lib/python2.6/dist-packages/softwareproperties/SoftwareProperties.py", line 538, in reload_sourceslist
    self.distro.get_sources(self.sourceslist)    
  File "/usr/lib/python2.6/dist-packages/aptsources/distro.py", line 90, in get_sources
    raise NoDistroTemplateException("Error: could not find a "
aptsources.distro.NoDistroTemplateException: Error: could not find a distribution template
```

It is Ubuntu 10.04, by the way.

Neither *Repositories*, from Synaptic Package Manager, or *Ubuntu Software Center* will open, either.

---

