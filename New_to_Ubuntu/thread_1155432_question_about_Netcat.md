---
title: "question about Netcat"
date: 2009-05-10
forum: New to Ubuntu
---

### Post by B34ST1Y on 2009-05-10
so, i'm writing a perl script in Ubuntu, and i'm trying to output a perl variable to Netcat....the problem is, when it creates the netcat connection, it will dump the contents of the piped information only once...then it won't do it anymore.


Here's the code, its a very simple script to get the basic function of piping information to netcat. I want to be able to pipe information over and over again. Any help would be greatly appreciated! :) ```


while (1 == 1)
{

	print "yo, enter your message: \n";
	$msg = <STDIN>;
	system("dir | nc 192.168.2.108 1235");
	system("echo $msg | nc 192.168.2.108 1235");



}
    
     
		 
		 
```

---

### Post by Redache on 2009-05-10
This post should be put in the Programming Talk section of the Forum where you'll get help from Programmers.

---

### Post by B34ST1Y on 2009-05-10
sorry - this thread can be locked. ill move it over to the correct area. Sorry!

---

