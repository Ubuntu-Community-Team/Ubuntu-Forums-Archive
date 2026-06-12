---
title: "ubuntu is too slow"
date: 2010-10-06
forum: New to Ubuntu
---

### Post by magedsoft on 2010-10-06
my desktop computer 
cpu deul core 2.7/2 M
hd 1000 GB
ram 4 G 
m.b asrok g 41 
 

why ubuntu is too slow

---

### Post by eriktheblu on 2010-10-06
Don't know. Run this in the terminal:
```
top > ~\Desktop\top.txt
```
Then open the file "top.txt" on your desktop and paste the results in a reply.

---

### Post by rockerphil on 2010-10-06
wow, i don't see how ANY system would be slow with those specs. like eriktheblu said, plz post the results of the command given, also please post the results of this command

```
free -mt
```

Phil

---

### Post by magedsoft on 2010-10-06
deadline@deadline-desktop:~$ free -mt
             total       used       free     shared    buffers     cached
Mem:          3993       3948         45          0        656       2844
-/+ buffers/cache:        446       3547
Swap:         2314          0       2314
Total:        6308       3948       2360






and 


~\Desktop\top.txt 
give nothing apper

---

### Post by oldos2er on 2010-10-06
What graphics card? Which version of Ubuntu?

---

### Post by TBABill on 2010-10-06
You are probably experiencing sluggishness due to either not using a proprietary graphics card driver or not having all necessary codecs installed (or a combination of both). Have you installed the proper driver for your card, if available, and did you install flash, java and other codecs (ubuntu-restricted-extras)?

---

### Post by carrarin on 2010-10-06
Previous poster was wrong...

Type:
```
top
```

and post output

---

### Post by bprins on 2010-10-06
> **carrarin said:**
> Previous poster was wrong...

Type:
```
top
```

and post output

mwaaaa :)

the other poster was just a little wrong. 
top > ~/Desktop/top.txt writes the top output to top.txt. He just used backslashes iso slashes.

outputting to a file in general makes sense :-)

---

