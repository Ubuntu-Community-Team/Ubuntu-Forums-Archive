---
title: "Problems Installing Adobe AIR"
date: 2009-05-26
forum: New to Ubuntu
---

### Post by iaskedalice09 on 2009-05-26
Hey,

Not really a beginner but seemed appropriate.

I tried installing AIR from the command line, these are the errors I got.

```

tom@jabbering-jabberwock:~/Desktop$ chmod +x AdobeAIRInstaller.bin 
tom@jabbering-jabberwock:~/Desktop$ sh AdobeAIRInstaller.bin 
AdobeAIRInstaller.bin: 1: Syntax error: "(" unexpected

```

Any insights? Thanks!

---

### Post by Mornedhel on 2009-05-26
It's a binary installer, not a shell script.

Please run ```
./AdboeAIRInstaller.bin
```

---

### Post by jose.cortes.p on 2010-01-18
Hello... I Have same issue. Tried with ./[Filename].bin and i got:
[B]bash: ./air.bin: No existe el fichero ó directorio

That's like: there's no such file or folder.

I Rename the file to air.bin for easy find. I really don't know what to do...
Thanks in advance
[/B]

---

### Post by llamabr on 2010-01-18
you need to 
```
chmod 755 file.bin
```
and then
```
./file.bin
```
in your case, it says it doesn't exist.  sometimes you'll type it wrong.  use tab completion to make sure the file exists.

---

