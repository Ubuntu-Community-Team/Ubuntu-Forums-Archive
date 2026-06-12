---
title: "Elegant way to test a variable if a number with SH / DASH ?"
date: 2011-06-26
forum: New to Ubuntu
---

### Post by honeybear on 2011-06-26
Hello, 

I found several solutions with this but those are not POSIX any longer. 

[http://stackoverflow.com/questions/806906/how-do-i-test-if-a-variable-is-a-number-in-bash](http://stackoverflow.com/questions/806906/how-do-i-test-if-a-variable-is-a-number-in-bash)

The simplest way would be: 
```
   #!/bin/sh
   if [ $var ???? ] ; then 
          echo number
   else
          echo not_number
   fi
```

---

### Post by Bachstelze on 2011-06-26
You can use tr to delete all digits, then test whether the resulting string is empty:

```
firas@wakaba ~ % cat test.sh 
#!/bin/dash

if [ $(echo $1 | tr -d '[:digit:]') ]; then
    echo "Not a number"
else
    echo "Number"
fi

firas@wakaba ~ % ./test.sh foo   
Not a number
firas@wakaba ~ % ./test.sh 1    
Number
firas@wakaba ~ % ./test.sh 12345
Number

```

Note: [ is a shortcut for test, so man test is your friend here. :)

---

### Post by Bachstelze on 2011-06-26
Actually tr is not POSIX, you can do the same thing with sed (I'll leave it as an exercise :p).

---

### Post by honeybear on 2011-06-27
> **Bachstelze said:**
> You can use tr to delete all digits, then test whether the resulting string is empty:

```
firas@wakaba ~ % cat test.sh 
#!/bin/dash

if [ $(echo $1 | tr -d '[:digit:]') ]; then
    echo "Not a number"
else
    echo "Number"
fi

firas@wakaba ~ % ./test.sh foo   
Not a number
firas@wakaba ~ % ./test.sh 1    
Number
firas@wakaba ~ % ./test.sh 12345
Number

```

Note: [ is a shortcut for test, so man test is your friend here. :)

thanks that's indeed in fact the most elegant method I could see. Simple, beautiful & 100% efficient

---

### Post by sisco311 on 2011-06-27
[http://mywiki.wooledge.org/BashFAQ/054](http://mywiki.wooledge.org/BashFAQ/054)

---

