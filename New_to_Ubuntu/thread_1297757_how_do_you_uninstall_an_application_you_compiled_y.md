---
title: "how do you uninstall an application you compiled yourself?"
date: 2009-10-22
forum: New to Ubuntu
---

### Post by jarongg on 2009-10-22
it's not coming up in either add/remove or synaptic. thanks in advance.

---

### Post by NCLI on 2009-10-22
EDIT: Nvm.

---

### Post by Jaraxle on 2009-10-22
Try this:

cd into the directory you compiled the application
type 'make uninstall'
press enter

This will only work if there is an uninstall script that was provided with the program. If not, you may have to manually remove the directory.

---

### Post by mcduck on 2009-10-22
> **jarongg said:**
> it's not coming up in either add/remove or synaptic. thanks in advance.

If you compiled it yourself you only options are to use the uninstall script that (hopefully) came with the source code. If there isn't one, you'll just need to remove all the files manually.

If you want programs you compile from source code to appear in package management tools you need to use Checkinstall to convert the compiled program into a .deb package and then install that, instead of installing the compiled stuff directly. To use Checkinstall you'd replace the "sudo make install" in the install process with "sudo checkinstall". (Checkinstall isn't installed by default, and .deb packages created with Checkinstall shouldn't be distributed since they don't contain all the information a proper .deb package does, so they don't always work correctly on other systems than the one where you did the compiling.)

---

### Post by OpenGuard on 2009-10-22
Take a look at [checkinstall]("http://www.asic-linux.com.mx/%7Eizto/checkinstall/") - #1 tool to get before you start doing stuff like this ( installing from source ).

---

### Post by Hospadar on 2009-10-22
I use checkinstall too.  replace 'make install' with checkinstall, it will examine where the make install script put new files, and make a .deb package (Which can be removed in synaptic) that does the same thing.

---

