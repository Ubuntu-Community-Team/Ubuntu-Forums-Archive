---
title: "Search for files containing &lt;string&gt;"
date: 2009-01-20
forum: New to Ubuntu
---

### Post by 9999999999 on 2009-01-20
Is there a standard linux command line tool that I can use to search for a file that contains <string>, or do I need to install something?

---

### Post by llamakc on 2009-01-20
The `find` command is very powerful. [http://www.linux.com/articles/55377](http://www.linux.com/articles/55377)

---

### Post by sisco311 on 2009-01-20
```
find /path/to/dir -name "*<string>*"
```
[uhelp]community/find[/uhelp]

---

### Post by 9999999999 on 2009-01-20
Could you please give me an example of using find to search for files that contain <string>? All the examples I've found made the find command seem like the locate command with more options.

---

### Post by Cypher on 2009-01-20
If you need to find a file where <string> is part of the filename, then it's 
```

find <directory> -name "*<string>*" -print

```
If you're trying to find files that contain <string> inside them, then you expand find with
```

find <dir> -exec grep '*<string>*' {} \;

```

---

### Post by blueridgedog on 2009-01-20
Or, if you are looking for a string in a file:

```
grep string /path/to/dir/*
```

---

### Post by 9999999999 on 2009-01-20
> **sisco311 said:**
> ```
find /path/to/dir -name "*<string>*"
```
[uhelp]community/find[/uhelp]


Wouldn't this just find files that contain *<string>* in the name of the file? I want to search for files that contain the <string> within the file.

---

### Post by 9999999999 on 2009-01-20
> **blueridgedog said:**
> Or, if you are looking for a string in a file:

```
grep string /path/to/dir/*
```

Yes. Thank you. I didn't realize that I could use a wildcard in the path param.

---

### Post by blueridgedog on 2009-01-20
You can also use -R to go down deeper than the directory you specify:

```
grep string /path/to/dir/* -R
```

---

