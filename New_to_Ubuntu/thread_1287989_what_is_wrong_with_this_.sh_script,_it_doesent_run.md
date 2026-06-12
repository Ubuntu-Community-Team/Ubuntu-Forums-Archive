---
title: "what is wrong with this .sh script?, it doesent run each command."
date: 2009-10-10
forum: New to Ubuntu
---

### Post by cosmoshell on 2009-10-10
sed -i "s/\<hat\>/kite/g" *.php && sed -i "s/\<happy\>/movie/g" *.php && sed -i "s/\<love_ksnal\>/movjj_random/g" *.php

---

### Post by NoaHall on 2009-10-10
Try this instead

```

#! /bin/bash
sed -i "s/\<hat\>/kite/g" *.php
sed -i "s/\<happy\>/movie/g" *.php
sed -i "s/\<love_ksnal\>/movjj_random/g" *.php

```

---

### Post by cosmoshell on 2009-10-10
> **NoaHall said:**
> Try this instead

```

#! /bin/bash
sed -i "s/\<hat\>/kite/g" *.php
sed -i "s/\<happy\>/movie/g" *.php
sed -i "s/\<love_ksnal\>/movjj_random/g" *.php

```

ty

---

### Post by lloyd_b on 2009-10-10
To clarify, "&&" is a logical operator.  It executes the second command if (and *only* if) the first command returns a value of 0.

If you just want to string multiple commands on a single line, separate them with semicolons:```
sed -i "s/\<hat\>/kite/g" *.php ; sed -i "s/\<happy\>/movie/g" *.php ; sed -i "s/\<love_ksnal\>/movjj_random/g" *.php

```

Lloyd B.

---

### Post by lswb on 2009-10-10
FYI you can use the -e option to sed to make a single invocation run more than one edit:

```

$ echo example |sed -e 's/x/X/' -e 's/a/A/' -e 's/e/E/g'
EXAmplE

$ # separating statements with semicolon also works but is not well documented
$ # and may not be portable to different versions of sed

echo example |sed  's/x/X/; s/a/A/; s/e/E/g'
EXAmplE


```

---

