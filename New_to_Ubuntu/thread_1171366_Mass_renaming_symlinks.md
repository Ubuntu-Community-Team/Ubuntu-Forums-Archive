---
title: "Mass renaming symlinks"
date: 2009-05-27
forum: New to Ubuntu
---

### Post by mattgyver83 on 2009-05-27
I have over 200 symlinks in a directory.  Each say 'Link to' before the actual filename.  How can i quickly rename each of these files so that I can strip the 'Link to' text via terminal, or even a bash script?

note *These symlinks point to files outside of this particular directory*

---

### Post by Boondoklife on 2009-05-27
throw this in a script file and run it
```

#!/bin/bash

for file in *;
do
mv "$file" "`echo $file | sed 's:Link to ::'`"
done

```

Just be in the same folder.
Oh and this will name all the files in that folder. If you want to narrow it down, just play with the line "for file in *" replacing the * with your needed expression.

---

### Post by iiska on 2009-05-27
You could do that with following bash oneliner:

```
for i in "Link to"*; do mv "$i" "$(echo "$i" | sed -e "s/Link to //")"; done
```

That loops through all files which begin with phrase "Link to " and assigns filename to variable i each time. Sed command is used to substitute "Link to " with empty string. Double quotes are needed to handle spaces properly.

---

### Post by mattgyver83 on 2009-05-27
Thanks for the quick replies.  Works Flawlessly.

---

