---
title: "error $: command not found"
date: 2009-12-07
forum: New to Ubuntu
---

### Post by varsha upadhyaya on 2009-12-07
hi, 

#!/bin/bash

Infile=$varsha
Outfile=$varsha.caps
echo input file is $Infile
echo output file is $Outfile
$ head -n 3 varsha | tr '[a-z]' '[A-Z]'

this is my program to convert the contents of an input file from small case to upper case.
but its giving an error as
input file is
output file is .caps
./eighth.sh: line 7: $: command not found

plz tell the solution.

---

### Post by BenAshton24 on 2009-12-07
> **varsha upadhyaya said:**
> hi, 

#!/bin/bash

Infile=$varsha
Outfile=$varsha.caps
echo input file is $Infile
echo output file is $Outfile
$ head -n 3 varsha | tr '[a-z]' '[A-Z]'

this is my program to convert the contents of an input file from small case to upper case.
but its giving an error as
input file is
output file is .caps
./eighth.sh: line 7: $: command not found

plz tell the solution.

change:
```
$ head -n 3 varsha | tr '[a-z]' '[A-Z]'
```
to:
```
head -n 3 varsha | tr '[a-z]' '[A-Z]'
```

---

### Post by Some Penguin on 2009-12-07
You're not setting $varsha to anything in your script, so it is going to be empty and infile/outfile won't be very meaningful.

---

### Post by bogdan.veringioiu on 2009-12-07
Hi.
I guess what you want to do is:

```

#!/bin/bash

Infile=varsha
Outfile=varsha.caps
echo input file is $Infile
echo output file is $Outfile
head -n 3 $Infile | tr '[a-z]' '[A-Z]' > $Outfile

```

The error was coming from "$head ..."
Cheers
Bogdan

---

### Post by CaptainMark on 2009-12-07
yeah doesnt a $ at the start of a line in a script make that line invisible, anything after it essentially isnt there but its used i think for reference when making long scripts so people can make notes within the script that wont stop the script functioning

---

### Post by varsha upadhyaya on 2009-12-08
thank you . thanks a lot. it worked perfectly. take care . see ya.


:-) varsha

---

