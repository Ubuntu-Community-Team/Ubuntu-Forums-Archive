---
title: "Rythmbox Extraction Problem"
date: 2009-06-05
forum: New to Ubuntu
---

### Post by brenan on 2009-06-05
When I try to extract the files from a CD onto my hard drive, it works most of the time, but if for any reason the extraction is interrupted (I accidentally exit of Rythmbox or something) I can never get the file that it was burning at the time on my computer. For example, say I was extracting the 2nd of 3 songs when I closed Rythmbox. I'll then open it up again hit extract, say not to overwrite the 1st song and tell it to overwrite the 2nd. It would give me a "could not open resource for writing" error and then burn the 3rd song perfectly, leaving the 2nd uncompleted.

---

### Post by Cypher on 2009-06-05
Hm..I suppose the "solution" could be to not close Rhythmbox until it's done it's job. Miminize it or switch to a different desktop so you don't accidently close it.

Or, you could always manually delete the partially copied file and then have Rhythmbox restart..

---

### Post by brenan on 2009-06-05
Ok deleting the file worked. I could have sworn that I had tried that. ](*,)

---

### Post by Cypher on 2009-06-05
The only thing I can think of is that when you did accidently close Rhthmbox, it was doing the extraction in a thread/process which hadn't gotten the message to close/die yet, so when you tried to delete the file, it was still owned..

---

