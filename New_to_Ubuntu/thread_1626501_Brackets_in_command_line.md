---
title: "Brackets in command line"
date: 2010-11-20
forum: New to Ubuntu
---

### Post by wannabeterminalpro on 2010-11-20
Whenever I try to delete or open a file with brackets in it's name the terminal gives me an error:
bash: syntax error near unexpected token `('
I can't delete any files because of this. I can't access my files normally because of a problem with wine. I asked help for that here:
[http://ubuntuforums.org/showthread.php?t=1626330](http://ubuntuforums.org/showthread.php?t=1626330)
Thanks in advance!

---

### Post by whoop on 2010-11-20
put a \ in front of it...
like:

rm filewith\(init

---

### Post by SeijiSensei on 2010-11-20
You have two options.  The easiest is to put the entire filename inside single quotes like this:

```
more 'a file with spaces and [brackets]'
```

Alternatively, you can "escape" spaces and non-alphanumeric characters with a leading backslash like this:

```
more a\ file\ with\ spaces\ and\ \[brackets\]
```

I find single quotes a lot easier.

---

