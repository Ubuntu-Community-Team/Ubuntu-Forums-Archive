---
title: "Quick Scripting Question"
date: 2011-01-27
forum: New to Ubuntu
---

### Post by YouEatLard on 2011-01-27
**SOLVED**
 
[CENTER]**[SIZE=4]SOLVED[/SIZE]**[/CENTER]
 
I'm writing a quick script to start a few servers on demand but for some reason it's not working.
 
Code:
```
/etc/init.d/ssh start
/etc/init.d/webmin start
/etc/init.d/mysql start
/etc/init.d/apache2 start

```
Output:
```
Usage: /etc/init.d/ssh {start|stop|reload|force-reload|restart|try-restart|status}.
Usage: /etc/init.d/webmin { start | stop | restart }
Usage: /UNIONFS/etc/init.d/mysql start|stop|restart|reload|force-reload|status
Usage: /etc/init.d/apache2 {start|stop|graceful-stop|restart|reload|force-reload|start-htcacheclean|stop-htcacheclean|status}
```
 
Why does it not see the 'start'?

---

### Post by kevdog on 2011-01-27
post your entire script.

---

### Post by YouEatLard on 2011-01-27
Thats all I have in there.

---

### Post by AlphaLexman on 2011-01-27
You need a [shebang]("http://en.wikipedia.org/wiki/Shebang_(Unix)") on the first line to start a script.
```
#!/bin/bash
```

---

### Post by YouEatLard on 2011-01-27
Tried that.  Same results.

---

### Post by AlphaLexman on 2011-01-27
Can you start | stop | restart from the command line?

---

### Post by YouEatLard on 2011-01-27
Yes, running the commands individually, from terminal works fine.

---

### Post by AlphaLexman on 2011-01-27
Are you running them from the command line as 'sudo' or as your username? You would need to run the script as sudo also.

---

### Post by YouEatLard on 2011-01-27
The script is has been tried with sudo and root.  It will be run with root permissions in the end product.

---

### Post by asmoore82 on 2011-01-27
Was your script created or edited with a DOS text editor?

Check these and compare the results:
```
file <your_script>
cat <your_script>
cat -A <your_script>
```

---

### Post by YouEatLard on 2011-01-27
It's all done with vi.
 
The results from above:
 
```

# file knoppix.sh
knoppix.sh: Bourne-Again shell script text executable
 
# cat knoppix.sh
#!/bin/bash
/etc/init.d/ssh start
/etc/init.d/webmin start
/etc/init.d/mysql start
/etc/init.d/apache2 start
 
# cat -A knoppix.sh
#!/bin/bash^M$
/etc/init.d/ssh start^M$
/etc/init.d/webmin start^M$
/etc/init.d/mysql start^M$
/etc/init.d/apache2 start^M$
^M$

```

---

### Post by asmoore82 on 2011-01-27
Yep, you've got a script with DOS newlines (see [http://en.wikipedia.org/wiki/CRLF](http://en.wikipedia.org/wiki/CRLF)).

That's why all those ^M's show up when you `cat -A`.
vi doesn't create these files by default but if you open one
for editing, vi will go with the flow.

Strip out the extraneous Carriage Returns (0x0d) like this:
```
mv knoppix.sh knoppix.sh.CRLF
cat knoppix.sh.CRLF | tr -d '\r' > knoppix.sh
```

---

### Post by AlphaLexman on 2011-01-27
@asmoore82: Good Catch!

---

### Post by YouEatLard on 2011-01-27
[CENTER][SIZE=4]**SOLVED**[/SIZE][/CENTER]
 
> **asmoore82 said:**
> Yep, you've got a script with DOS newlines (see [http://en.wikipedia.org/wiki/CRLF](http://en.wikipedia.org/wiki/CRLF)).
 
That's why all those ^M's show up when you `cat -A`.
vi doesn't create these files by default but if you open one
for editing, vi will go with the flow.
 
Strip out the extraneous Carriage Returns (0x0d) like this:
```
mv knoppix.sh knoppix.sh.CRLF
cat knoppix.sh.CRLF | tr -d '\r' > knoppix.sh
```
 
 
[COLOR=black][FONT=Verdana]:PExcellent catch. That was the issue. [/FONT][/COLOR]

[FONT=Verdana][COLOR=black]Thank you all for taking the time. [/COLOR][/FONT]
 
[COLOR=black][FONT=Verdana]Asmoore82, I'll be jumping over to Knoppix forums to post this as I doubt I'm the first to run into it. I'll be sure to quote you.[/FONT][/COLOR]
Oh yeah, and thanks btw. I now understand why FTP programs have options to transfer files as ASCII or binary.

---

