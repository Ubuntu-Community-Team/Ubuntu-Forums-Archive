---
title: "Flash won't install &quot;Error: ....... libcurl3&quot;"
date: 2009-04-24
forum: New to Ubuntu
---

### Post by Tj218 on 2009-04-24
Having trouble installing Flash on  9.04

When I open the .deb file I get the following error message:

"Error: Dependency is not satisfiable: libcurl3"

Any thoughts?

Thanks

---

### Post by sonu 1807 on 2009-04-24
Just go to Menu --> Add/Remove --> In show tab select all applications --> Search ubuntu restricted extras --> select it and then hit apply change. It would be done

---

### Post by Bakon Jarser on 2009-04-24
You could install libcurl3 and then try the .deb

```
sudo apt-get install libcurl3
```

or you could install the version of flash in the repositories.

```
sudo apt-get install flashplugin-nonfree
```
`

---

