---
title: "Is there a way to run all scripts in a folder"
date: 2010-12-29
forum: New to Ubuntu
---

### Post by CaptainMark on 2010-12-29
If i want to run all scripts in the folder ~/Documents/scripts is there a command to do so
basically i want to be able to put this command into the start up applications section and have any script i decide to plonk in this folder run on start up.
I tried```
#!/bin/bash
bash ~/Documents/scripts/*
```but this just finds the first available bash script, runs it and stops.
Any ideas??
Thanks 
Mark

---

### Post by WRDN on 2010-12-29
Use a for loop in a shell script:

```

for f in $(ls /path/to/folder/*)
do
bash $f
done

```

---

### Post by CaptainMark on 2010-12-30
Thank you, worked perfectly, may i throw a spanner in the works and ask if anyone would know how to write this as a python3 script?

---

