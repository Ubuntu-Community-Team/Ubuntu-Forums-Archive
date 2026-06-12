---
title: "Terminal won't execute my Hello World python script?"
date: 2011-02-04
forum: New to Ubuntu
---

### Post by Canvasian on 2011-02-04
Hello! I just installed Ubuntu for the first time last week, and haven't had any experience with Linux at all. I've also just started learning Python, and I've just written a basic "Hello, World!" script. It runs fine in IDLE or if I run it from the terminal with "$ python Hello.py", but the text I'm learning from is saying I should be able to make it executable with "$ chmod a+x Hello.py", and that after I enter this command, I should be able to run the program with either "$ Hello.py" or "$ ./Hello.py".

"$ chmod a+x Hello.py" seems to work (or at least I don't get an error message from it), but then if I try "$ Hello.py" I get:

 "Hello.py: Command not found"

and if I type "$ ./Hello.py", I get:

 "bash: ./Hello.py: /user/bin/env: bad interpreter: No such file or directory"

When I google this topic it tells me to use "$ chmod +x Hello.py" (+x instead of a+x), but this gives me the same results. What am I doing wrong?

I figure it's a problem with what I'm entering in the terminal and not my script, which is why I thought it best to put the question here in the new user thread... but if it helps, my "Hello World!" script looks like this:


#!/user/bin/env python
print "Hello, world!"
name = raw_input("What is your name? ")
print "Hello, " + name + "!"

---

### Post by cipherboy_loc on 2011-02-04
Rather than:
```

#!/user/bin/env

```

it should be:
```

#!/usr/bin/env

```

The difference is that one is a directory (/usr), while the other does not exist.



Cipherboy

---

### Post by Canvasian on 2011-02-04
That did it, thanks a lot :)

---

### Post by cipherboy_loc on 2011-02-04
What text(book I assume?) are you using?



Cipherboy

---

### Post by Canvasian on 2011-02-05
> **cipherboy_loc said:**
> What text(book I assume?) are you using?



Cipherboy

Beginning Python From Novice to Professional (Second Edition) by Magnus Lie Hetland.

The text did have that line written correctly, I just missed my mistake, despite checking an uncountable number of times xD

---

