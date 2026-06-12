---
title: "Initialize shell variable from mysql query"
date: 2009-08-07
forum: New to Ubuntu
---

### Post by Mauler5858 on 2009-08-07
Im trying to initialize a shell variable from a result of a mysql query.  Any idea where i am going wrong here?

```

set $isSuffix = `echo $(mysql DBASENAME -uUSER -pQUERY -e "SELECT NAME1 from TABLE where recordId = 2;")`


```

---

### Post by decoherence on 2009-08-07
> **Mauler5858 said:**
> Im trying to initialize a shell variable from a result of a mysql query.  Any idea where i am going wrong here?

```

set $isSuffix = `echo $(mysql DBASENAME -uUSER -pQUERY -e "SELECT NAME1 from TABLE where recordId = 2;")`


```

```
isSuffix=`echo $(mysql DBASENAME -uUSER -pQUERY -e "SELECT NAME1 from TABLE where recordId = 2;")`
```

or

```
export isSuffix=`echo $(mysql DBASENAME -uUSER -pQUERY -e "SELECT NAME1 from TABLE where recordId = 2;")`
```

if you're spawning child processes that need to see $isSuffix

no need for set, also you don't generally use the dollar sign on the right-hand side of the assignment (otherwise you'd be assigning it to the name contained within the variable.... not sure if that even works!)

---

### Post by unutbu on 2009-08-07
```
isSuffix = $(mysql -u USER -pPASSWORD -D DATABASE -Bse "SELECT NAME1 from TABLE where recordId = 2;")
```

-B tells mysql to run in "batch" mode
-s tells mysql to run in "silent" mode
-e tells mysql to execute the following statement

Substitute appropriate values for USER, PASSWORD and DATABASE
Note that there must not be a space between -p and the PASSWORD.

---

### Post by Mauler5858 on 2009-08-07
> **unutbu said:**
> ```
isSuffix = $(mysql -u USER -pPASSWORD -D DATABASE -Bse "SELECT NAME1 from TABLE where recordId = 2;")
```

-B tells mysql to run in "batch" mode
-s tells mysql to run in "silent" mode
-e tells mysql to execute the following statement

Substitute appropriate values for USER, PASSWORD and DATABASE
Note that there must not be a space between -p and the PASSWORD.

That did it!  Thanks.

---

