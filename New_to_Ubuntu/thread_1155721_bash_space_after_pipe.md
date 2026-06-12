---
title: "bash: space after pipe"
date: 2009-05-11
forum: New to Ubuntu
---

### Post by PGScooter on 2009-05-11
Hi,

Is there a general rule between the following two codes? Are the cases where I would want to use one over the other?

```

command1|command2

```

```

command1| command2

```

```

command1 | command2

```

```

command1 |command2

```

Thank you

---

### Post by mcduck on 2009-05-11
Both work the same way, but putting spaces around the pipe makes the command more readable for us humans. Especially on longer commands and scripts.

---

### Post by Dill on 2009-05-11
As the above poster mentioned, readability is always preferred : ).

On a more theoretical note, your question got me interested in exactly how the shell treats whitespace. In general, it seems, whitespace greater than 1 character in length is ignored by the shell. Therefore, you could just as easily do 

```
finger     |            awk '{print $1}'
```

Or even...

```
finger|        awk        '{print $1}'
```

And also...

```
firefox       &
```

---

### Post by PGScooter on 2009-05-11
great! thank you both for the info.

---

