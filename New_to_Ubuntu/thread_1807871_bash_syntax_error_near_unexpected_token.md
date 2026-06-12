---
title: "bash: syntax error near unexpected token"
date: 2011-07-19
forum: New to Ubuntu
---

### Post by margaux on 2011-07-19
Hi,

I'm trying to upload a library packaged called GenABEL, which I have installed in its own directory. I keep getting this bash: syntax error message though. Any ideas?

This is the code I'm using:

library (GenABLE)

and the error message I get:
bash: syntax error near unexpected token 'GenABLE'

I'm running this from within:
/home/Documents/R/GenABLE

so as far as I know I'm in the right directory.

Thanks

---

### Post by MG&amp;TL on 2011-07-19
I don't have a clue about what you are doing, but usually if you are doing something with a directory, you start from one level up from the directory, i.e. 'R' in your case. Otherwise (correct me if I'm wrong) bash looks for the directory name in the directory, where assumably there is nothing called GenAble in the directory. Just a thought.

---

### Post by AlphaLexman on 2011-07-19
> **margaux said:**
> bash: syntax error near unexpected token ...
That error usually means you are missing a closing construct statement ...

[LIST]
[*]do without done
[*]case without esac
[*]if without fi
[*]'{' without '}'
[/LIST]

---

### Post by gmargo on 2011-07-19
> **margaux said:**
> 
This is the code I'm using:

library (GenABLE)

and the error message I get:
bash: syntax error near unexpected token 'GenABLE'


To pass arguments to a command or shell function, do not use parentheses.  Just list the arguments after the command name:
```

library GenABLE

```

---

