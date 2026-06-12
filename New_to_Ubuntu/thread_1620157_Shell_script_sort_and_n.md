---
title: "Shell script sort and \n"
date: 2010-11-12
forum: New to Ubuntu
---

### Post by kubkub on 2010-11-12
I have 2 problems...

The first one is regarding newline. When I type in 

echo "Hello World"
echo "\nByeWorld!"

The result is:
Hello World
\nByeWorld!

The awkward thing is, the exact code in another computer with Ubuntu gives me:
Hello World

Bye World!

 I don't understand, can someone help me fix this? Why is it not working?


My second problem is with shell script. I need to sort command-line arguments in ascending order, I've tried the sort -n command but it's not working. How do you sort arguments in shell? :confused:

---

### Post by rampageoberon on 2010-11-12
> **kubkub said:**
> I have 2 problems...

The first one is regarding newline. When I type in 

echo "Hello World"
echo "\nByeWorld!"

The result is:
Hello World
\nByeWorld!

The awkward thing is, the exact code in another computer with Ubuntu gives me:
Hello World

Bye World!

 I don't understand, can someone help me fix this? Why is it not working?


Try ```
echo -e "\nByeWorld"!
```

Also, please explain more what you mean by sort command line arguments?

---

### Post by kubkub on 2010-11-12
Thanks rampageoberon, it worked, but I don't understand why it happens for one computer and not the other... :/
Anyways, I figured out my problem with argument, it works differently for each type of shells you use.

---

