---
title: "How do I fix broken packages?"
date: 2010-09-11
forum: New to Ubuntu
---

### Post by Suzanne42 on 2010-09-11
I am trying to upgrade my Ubuntu to 10.04, I jus realised I can't upgrade most likely bcose there are broken packages. What steps should I take to fix broken packages?I tried the fix option under Synaptic but that's no use, it does no fixing bcse the same error-"Fix broken packages" comes after selecting that.

---

### Post by MrWES on 2010-09-11
> **Suzanne42 said:**
> I am trying to upgrade my Ubuntu to 10.04, I jus realised I can't upgrade most likely bcose there are broken packages. What steps should I take to fix broken packages?I tried the fix option under Synaptic but that's no use, it does no fixing bcse the same error-"Fix broken packages" comes after selecting that.

From a terminal window:

```
sudo dpkg --configure -a
```

then

```
sudo apt-get install -f
```

You can read more on package management [here]("https://help.ubuntu.com/community/SynapticHowto")

---

### Post by hhlp on 2010-09-11
How to fix broken packages

 'Broken packages' are packages that have unsatisfied dependencies. If broken packages are detected, Synaptic will not allow any further changes to the system until all broken packages have been fixed.

    * To fix broken packages
          o Choose Edit > Fix Broken Packages from the menu.
          o Choose Apply Marked Changes from the Edit menu or press Ctrl + P.
          o Confirm the summary of changes and click Apply. 

If that does not help, then please follow this procedure:

[https://help.ubuntu.com/community/PackageManagerTroubleshootingProcedure]("https://help.ubuntu.com/community/PackageManagerTroubleshootingProcedure")

---

### Post by JohnHeikkila on 2010-09-11
Or try reinstalling the packages if none of the above helps.
sudo apt-get install --reinstall *package name*

---

### Post by Suzanne42 on 2010-09-11
I tried the procedure in the link suggested by hhlp. It worked fine initially but hung @ the last command. I waited a long while for the process to proceed before restarting the comp. Now, I presume broken packages have been fixed. I wanted to fix them bcose I wanted to upgrade to Ubuntu 10.04 but m still waiting for upgrade to complete, the error broken packages no longer pop up but the upgrade process is stuck @ the getting new packages option.

---

