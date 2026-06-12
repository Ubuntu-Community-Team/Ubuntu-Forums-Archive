---
title: "update manager not authenticated source error from server setting"
date: 2010-12-13
forum: New to Ubuntu
---

### Post by Shahram A on 2010-12-13
Experience:

After installing Ubuntu 10.10, at times the update manager failed to update, showing a dialogue box :
"requires installation of untrusted packages 
The action would require the installation of packagers from not authenticated source"
the same happened when installing applications via the Software centre.

Problem and solution:
On the software centre settings
on the update manager window -> settings button
or from the software centre -> edit -> software sources -> Ubuntu software

the download from -> drop down list - was set on server for United Kingdom
this setting was the cause of the problem
The setting was changed to Main server, thus previously problematic updates and installations went ahead without problem.

---

