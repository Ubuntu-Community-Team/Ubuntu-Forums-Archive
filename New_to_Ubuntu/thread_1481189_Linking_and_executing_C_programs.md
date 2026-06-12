---
title: "Linking and executing C programs"
date: 2010-05-12
forum: New to Ubuntu
---

### Post by SteelCore on 2010-05-12
I'm trying to run C programs on Lucid. To compile I enter the following code
```
gcc progname.c
```
this produces an 'a.out' file in the same directory.
how do I link and execute this program?
thanks

---

### Post by muteXe on 2010-05-12
```

./a.out

```

in the folder where the a.out file is.

---

### Post by WRDN on 2010-05-12
Typically when you compile, you also want to output to a different binary, with the "-o" switch:

```
gcc my_program.c -o my_progam_binary
```

Then run it:

```
./my_program_binary
```

---

