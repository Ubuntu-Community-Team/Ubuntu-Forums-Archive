---
title: "How to zip into a restricted folder"
date: 2011-03-25
forum: New to Ubuntu
---

### Post by Johnsen9000 on 2011-03-25
I am trying to unzip or just move a plugin into my rythmbox folder, but I can't get it to work. Simply copy-paste wont do since it's a restricted folder. I have looked around to get a How to: but no go.
 I have tried;
 [PHP]sudo tar xvfz albumartsearch_0.2.tar.gz /usr/lib/rhythmbox/plugins/[/PHP] but it doesn't work
 and then I try  
 [PHP]unzip -d /usr/lib/rhythmbox/plugins /home/espen/albumartsearch_0.2.tar.gz[/PHP] but it can't find albumartsearch_0.2.tar.gz
 what am I doing wrong?

---

### Post by dniMretsaM on 2011-03-25
Did you cd to the location of the plugin file? If you didn't, that could explain why it can't find the file.

---

### Post by gmargo on 2011-03-25
> 
 [PHP]sudo tar xvfz albumartsearch_0.2.tar.gz /usr/lib/rhythmbox/plugins/[/PHP]

To change the extraction directory, use the **-C** tar option.

```

sudo tar xvfz albumartsearch_0.2.tar.gz [COLOR=Red]-C[/COLOR] /usr/lib/rhythmbox/plugins/

```

---

### Post by Johnsen9000 on 2011-03-25
> **gmargo said:**
> To change the extraction directory, use the **-C** tar option.

```

sudo tar xvfz albumartsearch_0.2.tar.gz [COLOR=Red]-C[/COLOR] /usr/lib/rhythmbox/plugins/

```

Thanks. that worked. But for future references, what did the -c do and, in another context, when do i need it?

---

### Post by piquat on 2011-03-26
From:

```
man tar
``````
-C, --directory DIR
           change to directory DIR
```It appears that it allows tar to CD from where the archive is sitting to where you want to extract it to.

I'm betting that if you had moved it to that DIR to begin with it would have worked without the -C.

---

### Post by Joeb454 on 2011-03-26
> **piquat said:**
> 
I'm betting that if you had moved it to that DIR to begin with it would have worked without the -C.

It would :) by default, tar works in the current directory unless you tell it otherwise.

---

