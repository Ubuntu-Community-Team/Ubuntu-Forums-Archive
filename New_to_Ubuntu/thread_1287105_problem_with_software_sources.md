---
title: "problem with software sources"
date: 2009-10-09
forum: New to Ubuntu
---

### Post by darkmatter247 on 2009-10-09
Hi im just going to make this short and sweet,ok well every time i open software sources ander my password it doesnt open :( help please :confused: :(

---

### Post by plucky on 2009-10-10
> **darkmatter247 said:**
> Hi im just going to make this short and sweet,ok well every time i open software sources ander my password it doesnt open :( help please :confused: :(

Open a terminal **Applications > Accessories > Terminal** and input ```
gksu software-properties-gtk
``` and see what happens.If it fails to open,post the terminal output to the forum.


OR

You could open **Synaptic Package Manager** and search for "software-properties-gtk" and re-install to see if that fixes it.


Good Luck

---

### Post by darkmatter247 on 2009-10-10
sorry with the late reply i  tried reinstalling software properties and still the same thing and heres wat the terminal gave me           
  

judson@judson-laptop:~$ gksu software-properties-gtk
  File "/usr/bin/software-properties-gtk", line 104, in <module>
    app = SoftwarePropertiesGtk(datadir=data_dir, options=options, file=file)
  File "/usr/lib/python2.6/dist-packages/softwareproperties/gtk/SoftwarePropertiesGtk.py", line 75, in __init__
    SoftwareProperties.__init__(self, options=options, datadir=datadir)
  File "/usr/lib/python2.6/dist-packages/softwareproperties/SoftwareProperties.py", line 83, in __init__
    self.reload_sourceslist()
  File "/usr/lib/python2.6/dist-packages/softwareproperties/SoftwareProperties.py", line 521, in reload_sourceslist
    self.distro.get_sources(self.sourceslist)    
  File "/usr/lib/python2.6/dist-packages/aptsources/distro.py", line 90, in get_sources
    raise NoDistroTemplateException("Error: could not find a "
aptsources.distro.NoDistroTemplateException: Error: could not find a distribution template
judson@judson-laptop:~$

---

