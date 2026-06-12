---
title: "Running Deb Packages"
date: 2009-05-16
forum: New to Ubuntu
---

### Post by GRelEM on 2009-05-16
I am new to linux (I am running Kubuntu) and am trying to figure out how to run openoffice3 which I have installed using dpkg. However, I did not install the "openoffice.org3.1-debian-menus_3.1-9393_all.deb" file since it would install the menu's which conflict with my current openoffice 2.4 (which I would like to keep along side of 3). So, I am wondering, how do I run an installed debian package without running it from the K-Menu.

It is properly installed as verified by:

```
jonathan@Computer:~/Desktop/OOO310_m11_native_packed-4_en-US.9399/DEBS$ dpkg --get-selections 'openoffice*'
openoffice.org                                  install
openoffice.org-base                             install
openoffice.org-base-core                        install
openoffice.org-calc                             install
openoffice.org-common                           install
openoffice.org-core                             install
openoffice.org-debian-menus                     install
openoffice.org-draw                             install
openoffice.org-filter-binfilter                 install
openoffice.org-filter-mobiledev                 install
openoffice.org-help-en-gb                       install
openoffice.org-help-en-us                       install
openoffice.org-hyphenation                      install
openoffice.org-impress                          install
openoffice.org-java-common                      install
openoffice.org-kde                              install
openoffice.org-l10n-common                      install
openoffice.org-l10n-en-gb                       install
openoffice.org-l10n-en-za                       install
openoffice.org-math                             install
openoffice.org-officebean                       install
openoffice.org-style-crystal                    install
openoffice.org-style-human                      install
openoffice.org-thesaurus-en-au                  install
openoffice.org-thesaurus-en-us                  install
openoffice.org-ure                              install
openoffice.org-writer                           install
openoffice.org-writer2latex                     install
openoffice.org3                                 install
openoffice.org3-base                            install
openoffice.org3-calc                            install
openoffice.org3-dict-en                         install
openoffice.org3-dict-es                         install
openoffice.org3-dict-fr                         install
openoffice.org3-draw                            install
openoffice.org3-en-us                           install
openoffice.org3-impress                         install
openoffice.org3-math                            install
openoffice.org3-writer                          install
```So, it seems that openoffice.org3 is installed (since it is there at the bottom of the list), but how do I run it?

Thanks.

---

### Post by taurus on 2009-05-16
See if it can find the new OpenOffice.

```
whereis ooffice
```

---

### Post by GRelEM on 2009-05-16
```
jonathan@Computer:/bin$ whereis ooffice
ooffice: /usr/bin/ooffice /usr/share/man/man1/ooffice.1.gz

```

However, it seems to have found openoffice 2.4 since that is what starts up when I open that ooffice file.

---

### Post by taurus on 2009-05-16
What's the output of this command?

```
sudo find / -name ooffice -print
```

---

### Post by sandyd on 2009-05-16
Openoffice Writer
```

openoffice.org3 -writer %U

```

Openoffice Calc (Spreadhseet)
```

openoffice.org3 -calc %U

```

Openoffice Impress
```

openoffice.org3 -impress %U

```

Openoffice Math
```

openoffice.org3 -math %U

```

Openoffice Draw
```

openoffice.org3 -draw %U

```

Openoffice Base
```

openoffice.org3 -base %U

```

Why don't you just use the PPA and completely remove openoffice 2.4. Its much easier....

---

### Post by GRelEM on 2009-05-17
Thanks.
Those commands i.e.:
```
 
openoffice.org3 -writer %U

``` don't seem to work unless I actually install the menu deb file.
So, what I ended up doing was what you suggested: removed the old version of open office and installed the new. Everything works well now.

---

