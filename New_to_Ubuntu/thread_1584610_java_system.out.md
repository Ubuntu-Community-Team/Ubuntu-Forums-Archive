---
title: "java system.out"
date: 2010-09-29
forum: New to Ubuntu
---

### Post by navaneethan on 2010-09-29
In java you know System.out.println("");

In this sentence System is a class

out is a object

println is the method

How it is possible that Class.object.method() can you explain plz?

i have got from net that out is a static reference but i don't understand!!

---

### Post by DaithiF on 2010-09-29
Hi,
so I assume that you're ok generally with object.method(), right?  And that its the System part thats troubling you here?

A variable is a reference to an object.  Variables can be class variables or instance variables.  Class variables belong (as the name implies) to a Class.  All instances of this class share a single copy of this variable, and it is possible to access the variable directly via the Class without having to instantiate any instances of that class.  In java declaring a variable with the static keyword achieves this.

Instance variables on the other hand, are specific to an instance of a class.  Each instance has its own separate copy of the variable.

If you look up the javadocs for the System ([http://download.oracle.com/javase/1.4.2/docs/api/java/lang/System.html#out](http://download.oracle.com/javase/1.4.2/docs/api/java/lang/System.html#out)) class you'll see the definition of the out variable as:
```
static PrintStream out
```
which makes it a class variable of the System class.  And thus you can do System.out.println() etc.

---

### Post by navaneethan on 2010-09-29
yeah fine,

System is class which consists static instance variable(out),ok

How we can call a method using the static instance variable ?

System.out---> fine
out.println() this part again troubling

out is just a instance variable then How it would call println()?

generally object.methodname() usually does but here it varies?can you justify?

---

### Post by DaithiF on 2010-09-29
> **navaneethan said:**
> yeah fine,

System is class which consists static instance variable(out),ok

How we can call a method using the static instance variable ?

System.out---> fine
out.println() this part again troubling

out is just a instance variable then How it would call println()?

generally object.methodname() usually does but here it varies?can you justify?

why?  an object is an object is an object.  the fact that it is 'static' here is only relevant to its relationship to a parent Class, but the object itself is no different from any other (non-static) object, you can call its methods just the same.

---

