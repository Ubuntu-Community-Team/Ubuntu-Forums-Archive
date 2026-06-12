---
title: "Syntax Highlighting Command?"
date: 2009-06-05
forum: New to Ubuntu
---

### Post by ubuntuforums on 2009-06-05
Hi,
I'm trying to find out what this command is. A friend told me that you can export your code from vim into a syntax highlighted html page. He said this can also be done from the terminal, but he doesn't remember how. He said it's something like: '2html /dir/code.php' and it will output that code in html with syntax highlighting.

Does anyone know how to do this? This would be very helpful for me. Thanks.

---

### Post by Volt9000 on 2009-06-05
Did a quick search and found code2html, sounds like what you're looking for.

```

sudo apt-get install code2html

```

It's a separate program, however.

---

### Post by ubuntuforums on 2009-06-05
That looks interesting, I'll try it. Thank you.

---

### Post by ubuntuforums on 2009-06-06
I tried it out, it's what I want, unfortunately it doesn't support as many languages as I want. One of the most important ones for me is PHP, it isn't supported.

---

### Post by ad_267 on 2009-06-06
The highlight and source-highlight packages look like they might be what you're after. I'm not sure which one would be best, but source-highlight specifically mentions PHP support. "apt-cache search" is a useful tool. (Or synaptic)

---

### Post by Alias1407 on 2009-06-06
You might also try...

```
cat <path to file> | ccze
```

---

### Post by andrew.46 on 2009-06-06
Hi ubuntuforums,

> **ubuntuforums said:**
> I'm trying to find out what this command is. A friend told me that you can export your code from vim into a syntax highlighted html page. He said this can also be done from the terminal, but he doesn't remember how. He said it's something like: '2html /dir/code.php' and it will output that code in html with syntax highlighting.

Perhaps the command you are after is:

```
:TOhtml
```

typed from within vim. I have not experimented too much with this but it seems to work well enough for basic files.

All the best,

Andrew

---

