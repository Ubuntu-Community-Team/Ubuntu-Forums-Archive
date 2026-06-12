---
title: "Noob help with sed"
date: 2010-06-01
forum: New to Ubuntu
---

### Post by sdredwingsfan on 2010-06-01
I'm trying to take 4 lines of text from multiple files and output to one text file.  So far I have...

```
sed -n '14P;21P;144P;245P' *.txt > log.txt
```
But, after i run it I get the results but they just overwrite from 1 of the text files.  Instead, I need to append the search for each *.txt file.

I'm only using sed because this part was the easiest to figure out so far. If you have an easier method i'm all ears.  thanks for the help!

---

### Post by Ozymandias_117 on 2010-06-01
> **sdredwingsfan said:**
> I'm trying to take 4 lines of text from multiple files and output to one text file.  So far I have...

```
sed -n '14P;21P;144P;245P' *.txt > log.txt
```
But, after i run it I get the results but they just overwrite from 1 of the text files.  Instead, I need to append the search for each *.txt file.

I'm only using sed because this part was the easiest to figure out so far. If you have an easier method i'm all ears.  thanks for the help!

```
sed -n '14P;21P;144P;245P' *.txt >> log.txt
```

---

### Post by tom.swartz07 on 2010-06-01
> **Ozymandias_117 said:**
> ```
sed -n '14P;21P;144P;245P' *.txt >> log.txt
```

I know what this means, but the OP might not. Please explain the commands that you post. :)

---

### Post by Ozymandias_117 on 2010-06-01
All he asked was how to make it append to a text file rather than overwrite it, he had everything except for the >>. I assumed since that was the only thing that was changed he could figure out what it did.

---

### Post by sdredwingsfan on 2010-06-01
> **Ozymandias_117 said:**
> ```
sed -n '14P;21P;144P;245P' *.txt >> log.txt
```

Thanks!, I gave this a shot but the output only contained one result.  Is it possible that the problem is with the sed cmd?

---

### Post by Ozymandias_117 on 2010-06-01
The >> will make it append. If you expected more output and didn't receive it, I would suspect sed.

---

### Post by tom.swartz07 on 2010-06-01
> **Ozymandias_117 said:**
> All he asked was how to make it append to a text file rather than overwrite it, he had everything except for the >>. I assumed since that was the only thing that was changed he could figure out what it did.

alrighty! I know, I know.

Its just that others who may not know about it might use this thread for help.

Think of it as completeness of knowledge.

---

### Post by DaithiF on 2010-06-02
Hi,
when you pass multiple input files to sed, it will treat them as one overall (concatenated) stream, so the line numbers you are operating on are not per-file, but instead line numbers of the whole stream.

To operate on files individually do it in a loop instead:
```
for i in *.txt
do
sed -n '14P;21P;144P;245P' "$i" >> log.txt
done

```

---

