---
title: "how to get value of print command"
date: 2010-05-13
forum: New to Ubuntu
---

### Post by jaydot on 2010-05-13
hi just wanna ask is it possible for perl to get the value of a print command? for ex.

 my $result = print "hello world\n";
 print "$result\n";

why is it that the "print $result" would print a value which is 1?.. is it possible to get the result "hello world" not 1?... how do i do it?.. .how do i change my code? help please.

---

### Post by stevoo on 2010-05-13
well i dont now perl , 

but i am wondering if it is because you are doing 
a = print "something " 

perhaps it is taking the print command and checks if it is executed ? 
Try $a = "something "
and then print $a

perhaps that may do something ! 
Else you are better off asking in a perl forum , you know there are many of those around not here !

---

