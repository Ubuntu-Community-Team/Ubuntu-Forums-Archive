---
title: "how do i extract a jar file on command line?"
date: 2010-10-02
forum: New to Ubuntu
---

### Post by nerxgas on 2010-10-02
i was given this instruction, but it doesn't work on my setup
java -jar grimwepa_X.X.jar

is there another way to do it?

---

### Post by decoherence on 2010-10-02
i believe that is a command to execute a java archive. is there some reason you want to extract its contents?

what error does it give you?

---

### Post by jtarin on 2010-10-02
> **decoherence said:**
> i believe that is a command to execute a java archive. is there some reason you want to extract its contents?

what error does it give you?THAT IS a java executable! If you have Java installed you can probably execute it from the right-click menu or open a terminal in the directory where it is and enter```
java -jar grimwepa_X.X.jar
```then hit the enter key.

---

### Post by decoherence on 2010-10-03
yes, that is the command the op is running. it would be nice to know what the instructions say and what the expected result is.

if you really want to extract the archive rather than run it, use the unzip command. jars are just zip files.

---

### Post by thelastquincy on 2010-10-03
Also does the OP have the latest jre? he/she might not even have it.

---

### Post by decoherence on 2010-10-03
> **thelastquincy said:**
> Also does the OP have the latest jre? he/she might not even have it.

That is true, Ishida-san!

---

