---
title: "Classpath problem using JUnit 4.7"
date: 2009-10-28
forum: New to Ubuntu
---

### Post by McMurry on 2009-10-28
Hello,

I have installed JUnit 4.7 following the install instructions at

[http://junit.sourceforge.net/doc/faq/faq.htm#started_2](http://junit.sourceforge.net/doc/faq/faq.htm#started_2)

with $JUNIT_HOME = /home/mcmurry/java/junit4.7

When going to the install direcory I can execute the suggested test after setup

java org.junit.runner.JUnitCore org.junit.tests.AllTests

this runs JUnit and all tests succeed.

My CLASSPATH variable includes

/home/mcmurry/java/junit4.7/ and /home/mcmurry/java/junit4.7/junit-4.7.jar

In a SimpleTest class I have the following two import statements

import junit.org.*;
import junit.org.Assert.*;

When I try to compile SimpleTest.java I get the message

"test/SimpleTest.java:2: package junit.org does not exist
import junit.org.*;
^
test/SimpleTest.java:3: package junit.org does not exist
import static junit.org.Assert.*;"
                       ^
I have searched this error message on Google and it seems that is a simple issue relating to the CLASSPATH variable, but I can not work out what else I need to add to CLASSPATH.

In $JUNIT_HOME there is among other things a junit and an org folder. However, there is no org folder inside the folder junit. Shouldnt class C in packaga x.y.z be located in a x/y/z ??

---

### Post by bogdan.veringioiu on 2009-10-28
Hi.
Could you please invert your imports?

```
import junit.org.*;
import junit.org.Assert.*;
```

It looks to me that you got them wrong:

Try:

```
import org.junit.*;
import org.junit.assert.*;
```

Cheers.
Bogdan

---

