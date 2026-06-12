---
title: "How to check installed softwares on terminal"
date: 2011-03-15
forum: New to Ubuntu
---

### Post by xptional on 2011-03-15
Hi :), 

     How can i check my whole list of  installed softwares in heaps of installations ? 

Will this code remove all the softwares or some particular ```
sudo apt-get autoremove
```

what is difference between these commands, using  ```
sudo apt-get remove
sudo apt-get autoremove
```

Thanks !

---

### Post by mcduck on 2011-03-15
I didn't really understand your first question.

Anyway:

"apt-get remove *somepackage*" uninstalls a single package.

"apt-get autoremove *somepackage*" uninstalls a single package, and other packages that might have been installed as dependencies for that specific package.

"apt-get autoremove" uninstalls any packages that were installed as dependencies and aren't needed any more.

("apt-get remove" would do nothing at all. You ened to tell it what to remove... ;))

...and no, none of those will uninstall all software. There would be little sense in having such command. Formatting your hard drive would work better if you wanted to remove *everything*. :)

Edit: did you mean in your first question that you want to know how to list all installed packages? In that case, "*dpkg -l*" should do the trick.

---

### Post by col48 on 2011-03-15
Hi xceptional

This text is copied from the manual pages for apt-get
```
man apt-get

```
```
      remove
           remove is identical to install except that packages are removed
           instead of installed. Note the removing a package leaves its
           configuration files in system. If a plus sign is appended to the
           package name (with no intervening space), the identified package
           will be installed instead of removed.

```
```
       purge
           purge is identical to remove except that packages are removed and
           purged (any configuration files are deleted too).

```
```
       autoremove
           autoremove is used to remove packages that were automatically
           installed to satisfy dependencies for some package and that are no
           more needed.

```

In each case you would specify the specific package.  Many packages require other packages ("dependencies") to be installed with them in order to run.  I find most of these dependency package names do not reveal what the packages are for.

In order to get a complete list of installed packages, use
```
dpkg --get-selections > list-file

```which will put a list in list-file.

---

### Post by xptional on 2011-03-15
I thank you both, 

I get the answer that i need, now i am not fear of autoremove command and I also learned how to see the installed package list. 

Thanks again. 

NahkNarmi

---

