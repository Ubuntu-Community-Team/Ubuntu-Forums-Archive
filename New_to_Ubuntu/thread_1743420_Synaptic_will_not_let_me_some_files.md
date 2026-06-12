---
title: "Synaptic will not let me some files"
date: 2011-04-29
forum: New to Ubuntu
---

### Post by captgadget on 2011-04-29
I have: not installed(resid config) and when I mark them for removal it will not let me remove them. The apply check mark never turns green. How can I remove these?

---

### Post by gandaran on 2011-04-29
> **captgadget said:**
> I have: not installed(resid config) and when I mark them for removal it will not let me remove them. The apply check mark never turns green. How can I remove these?
you have marked them for _complete removal_?

---

### Post by hocvol1 on 2011-04-29
> **captgadget said:**
> I have: not installed(resid config) and when I mark them for removal it will not let me remove them. The apply check mark never turns green. How can I remove these?

I am having the same problem.  I have a list of approx 30 residual configs after upgrade 10.10 to 11.04 which I mark for removal and then find the "apply" is greyed out.

---

### Post by captgadget on 2011-04-29
Yes, my problem would be the same as hocvol1 - problem showed up the upgrade.

---

### Post by yetiman64 on 2011-04-29
I can confirm that Synaptic won't let me remove residual configuration files in 11.04 (when the setting "mark for complete removal" is chosen, the apply arrow stays grayed out). 

OP, consider checking out launchpad.net for bugs related to Synaptic, or if you can't find one maybe consider listing a new one there, if this is causing you problems.

A workaround is to mark the packages you want removed completely and also tick something for install, all the changes will be implemented including the removal of the old config files. 

Then whenever you uninstall a package use Synaptic and choose the complete removal option first, it seems as if once a package is removed Synaptic can no longer handle removal of config files by themselves.

Note: my install is a fresh install not an upgrade. Would be worth checking out launchpad if you don't like doing workarounds.

**Edit**: or if you use the terminal to uninstall use "sudo apt-get purge <package-name>" rather than using "sudo apt-get remove <package-name>, using the purge option will remove the config files and you won't get caught out in Synaptic with hard to remove left over config files.

**Edit2**: From launchpad.net [[COLOR=Blue]--LINK--[/COLOR]]("https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/763893"), the problem has already been reported. I would suggest anyone this affects register with launchpad, then login and click the link "Does this bug also affect you ?" at the top of the page and click the answer "Yes it does".

---

### Post by solitaire on 2011-04-30
Temp workaround:
Mark something for install, reinstall or removal (or wait for an update) This will activate the "tick"
Then you can select the residual configs and they will be removed.

---

