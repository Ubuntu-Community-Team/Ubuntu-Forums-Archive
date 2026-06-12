---
title: "Academic Question"
date: 2010-02-02
forum: New to Ubuntu
---

### Post by zoomiest on 2010-02-02
Just reading a chapter in a Unix text about command substitution in Bourne Shell programming, and I don't get it:

"Assign the output of *echo "Hello, world!"* command to variable *myname* variable and then display the value of *myname*. List the commands that you executed to complete your work."

So the output is: 
```
$ echo "Hello, world!"
-bash: !": event not found
```

So, if I try to assign that to the variable myname and echo it back, I get:
```
$ myname="-bash: !": event not found"
-bash: !": event not found
$ echo $myname
Allan
```

(The output "Allan" was previously assigned to the variable 'myname')

That pesky double quote in the middle must be screwing this up. Am I getting this exercise? I think I am missing something.

---

### Post by doas777 on 2010-02-02
try replacing the double quotes with single ones, and it will treat "Hellow World!" as a literal string. 

"" => executes any bash stuff within, but treats non bash stuff as strings
''  => treat as nonexecutable literal string
`` => execute teh contents.

---

