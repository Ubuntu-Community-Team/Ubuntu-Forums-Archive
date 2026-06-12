---
title: "Using find in a bash script ?"
date: 2011-01-21
forum: New to Ubuntu
---

### Post by cyb3r_sn4k3 on 2011-01-21
I mostly/always use find with -iname and directory as . So I want to make a bash script to do this so how will I get the search string into the bash script? 

So here the value of x will change every time I run the script so how will I get the value of x into the script?
```

~!/bin/bash/ 
find . -iname "*x*"

```Sorry if the question is hard to understand :(

---

### Post by Dr Small on 2011-01-21
```
#!/bin/bash 
find . -iname "$1"
```

---

### Post by nothingspecial on 2011-01-21
Putting a / at the end of #! /bin/bash can cause errors.

---

### Post by cyb3r_sn4k3 on 2011-01-21
> **Dr Small said:**
> ```
#!/bin/bash/ 
find . -iname "$1"
```

Can you please explain? The script ?

---

### Post by DaithiF on 2011-01-22
theres not really much to explain, $1, $2, $3 etc. contain the values passed as arguments on the command line when you run a command.

so if you run a script like so:
```
./yourscript /home/you/somedirectory someotherparameter

```

then in your script $1 would contain the value **/home/you/somedirectory**, and $2 would contain **someotherparameter**

---

### Post by kevdog on 2011-01-22
And $0 would be the name of the script!!

---

### Post by cyb3r_sn4k3 on 2011-01-23
Thanks !!

---

### Post by Dr Small on 2011-01-23
> Putting a / at the end of #! /bin/bash can cause errors.
Yeah, I didn't mean to do that... :S

---

