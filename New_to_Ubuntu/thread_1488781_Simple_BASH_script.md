---
title: "Simple BASH script"
date: 2010-05-20
forum: New to Ubuntu
---

### Post by yanewby on 2010-05-20
I am trying to write a bash script that opens up firefox and then does some calculations and closes.  It must then leave firefox up and running, how do I do this?

#!/bin/sh

# open firefox
[COLOR="Red"]**????**[/COLOR] firefox

# do some magic
ONE=2
echo $ONE

# close but leave firefox running
exit 0

---

### Post by patchwork on 2010-05-20
try ```
firefox &
```

---

### Post by yanewby on 2010-05-20
> **patchwork said:**
> try ```
firefox &
```

I tried that but as soon as the script stops running or is closed firefox closes.  It is imperative that firefox does NOT close....

---

### Post by patchwork on 2010-05-20
Hmm, it works just fine for me.  The only difference I see between our codes is that I explicitly call bash, where you call shell.


```
#!/bin/bash

firefox &

one=1

echo $one
exit 0
```

Ouput:

```
kevin@lucid:~/Desktop$ ./test.sh 
1

```

... and firefox remains open.

---

### Post by yanewby on 2010-05-20
> **patchwork said:**
> Hmm, it works just fine for me.  The only difference I see between our codes is that I explicitly call bash, where you call shell.

... and firefox remains open.

You are correct, I was being too impatient and stopping things manually before my calculations were complete.

Thanks for the help!

---

