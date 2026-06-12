---
title: "bash: renaming all files with replacing space by &quot;_&quot; ?"
date: 2010-12-12
forum: New to Ubuntu
---

### Post by honeybear on 2010-12-12
Hello,

some issues, I can make it, but someone maybe has that that works well already? 

I couldnt find on google

---

### Post by AlphaLexman on 2010-12-12
Here is the script I use:
```
#!/bin/bash

find . -print | while read FILENAME
	do 

		rename -v 's/ /_/g' "$FILENAME"

	done

```
Just make it executable and run it!

---

### Post by isosi on 2011-02-26
If the file name last char is " " the rename program is not working.

Example the script will work with raplacing
"name name" -> "name_name"
but will not work with
"name name " -> "name_name_"

---

### Post by sisco311 on 2011-02-26
```
rename 's/ /_/**g**' *\ *
```
should do the trick. Note the **g** option, which means *replace all instances*.

If you don't want to use the rename command, in bash, you can do something like:
```

cd path/to/dir
for file in *\ *; do
  mv --backup=numbered -- "$file" "${file// /_}"
done

```

or recursively:
```

while IFS= read -rd '' file; do
  filename="${file##*/}"
  dirname="${file%/*}"
  mv --backup=numbered -- "$file" "${dirname}/${filename// /_}"
done < <(find path/to/dir -depth -name '*\ *' -print0)

```

---

### Post by elizdaavis on 2011-02-26
I tried this coding, but still not successful

---

