---
title: "bash condition"
date: 2010-10-20
forum: New to Ubuntu
---

### Post by Hippytaff on 2010-10-20
with the if condition, how can you say

if user input = y
then
command
else
exit

basically, how does the script take a user input and then use it to satisfy -or not- an if condition.

my head hurts

---

### Post by amauk on 2010-10-20
```
#!/bin/bash

echo "Enter 'y' or 'n'"

# waits for user to enter some text
# and stores the text in a variable
# named INPUT
read INPUT

if [ "$INPUT" == "y" ]; then
    echo "You typed 'y'"
elif [ "$INPUT" == "n" ]; then
    echo "You typed 'n'"
else
    echo "You can't read"
fi
```

---

### Post by Hippytaff on 2010-10-20
Sweet...I was missing the 
```

]; then

```

Thankyou :-D

---

