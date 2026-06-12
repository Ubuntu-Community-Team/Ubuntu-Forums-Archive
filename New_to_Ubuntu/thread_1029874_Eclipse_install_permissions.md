---
title: "Eclipse install permissions"
date: 2009-01-03
forum: New to Ubuntu
---

### Post by NongA_TongE on 2009-01-03
Greetings,  I'm running Hardy 64bit.  I've installed eclipse via the synaptic package manager and am now trying to install the WTP plugins from the Callisto Discovery site.  Unfortunately, I get the following errors:
>   Unable to complete action for feature "Visual Editor" due to errors.
  Unable to complete action for feature "Java EMF Model" due to errors.
    Unable to create file "/usr/lib/eclipse/plugins/org.eclipse.jem.beaninfo_1.2.0.v20060918_M.jar1231034140897.tmp". [/usr/lib/eclipse/plugins/org.eclipse.jem.beaninfo_1.2.0.v20060918_M.jar1231034140897.tmp (Permission denied)]
    Unable to create file "/usr/lib/eclipse/plugins/org.eclipse.jem.beaninfo_1.2.0.v20060918_M.jar1231034140897.tmp". [/usr/lib/eclipse/plugins/org.eclipse.jem.beaninfo_1.2.0.v20060918_M.jar1231034140897.tmp (Permission denied)]
  Unable to complete action for feature "Java EMF Model" due to errors.
    Unable to create file "/usr/lib/eclipse/plugins/org.eclipse.jem.beaninfo_1.2.0.v20060918_M.jar1231034140897.tmp". [/usr/lib/eclipse/plugins/org.eclipse.jem.beaninfo_1.2.0.v20060918_M.jar1231034140897.tmp (Permission denied)]
    Unable to create file "/usr/lib/eclipse/plugins/org.eclipse.jem.beaninfo_1.2.0.v20060918_M.jar1231034140897.tmp". [/usr/lib/eclipse/plugins/org.eclipse.jem.beaninfo_1.2.0.v20060918_M.jar1231034140897.tmp (Permission denied)]
  Unable to create file "/usr/lib/eclipse/plugins/org.eclipse.jem.beaninfo_1.2.0.v20060918_M.jar1231034140897.tmp". [/usr/lib/eclipse/plugins/org.eclipse.jem.beaninfo_1.2.0.v20060918_M.jar1231034140897.tmp (Permission denied)]

I believe that these are due to permissions.  If I were running this from the terminal, I could just sudo,  but I don't know how to update eclipse from the terminal and I don't know what additional permissions to grant myself to allow the install,     
Please help :)

---

### Post by Helios1276 on 2009-01-03
sudo apt-get update && sudo apt-get upgrade ?

---

### Post by NongA_TongE on 2009-01-03
Thanks for that,  does that string just update and upgrade anything installed?  the terminal says that the command takes no parameters, so how do I specify the specific eclipse plugins I'm looking for?

---

### Post by Helios1276 on 2009-01-03
Im not quite sure, have you tried to update at all? does it not solve your problem?

---

