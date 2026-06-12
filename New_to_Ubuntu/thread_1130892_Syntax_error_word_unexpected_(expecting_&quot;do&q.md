---
title: "Syntax error: word unexpected (expecting &quot;do&quot;)"
date: 2009-04-20
forum: New to Ubuntu
---

### Post by rohandeshmukh on 2009-04-20
Hi! i am writting a code to delete excel reports older than one day.
The code is as follows:
 
path="/home/directory/Reports"
echo "The reports older than one day are getting deleted..."
for i in `find $path/*.xls -mtime +1 -print`
do
echo "File $i is deleted"
sudo rm $i
done
echo "Deletion is completed"

When i am executing this script, it is giving me the error that 
 Syntax error: word unexpected (expecting "do")

but if i write the same code on command prompt instead of in shell script, it is getting executed properly. Please let me know where i am getting wrong.

Thanks in advance

---

### Post by leandromartinez98 on 2009-04-20
Put this in the first line of your script file:

#!/bin/sh

This sets which interpreter you are using (in this case, sh, or bash). This
may solve the problem. I cannot see anything else now.

Just for curiosity: Do you really need root privileges to delete the files? (Is the use of "sudo" necessary, it seems strange, and dangerous).

---

### Post by mister_pink on 2009-04-20
The other thing, if that doesn't solve it, is that you might need a semicolon at the end of the for line.

Also, if you post code, you can put it inside tags to make it formatted so its easier to read. Its ok here but helps for longer snippets. Just put it inside [noparse]```
 and 
```[/noparse] tags

---

### Post by rohandeshmukh on 2009-04-21
Well, even after adding #!/bin/sh, the code is giving same error. 

The code snippet is as follows:
```

#!/bin/sh
path="/home/directory/Reports"
echo "The reports older than one day are getting deleted..."
for i in `find $path/*.xls -mtime +1 -print`;
do
echo "File $i is deleted"
rm $i
done
echo "Deletion is completed"

```


The output is as follows:
$sh Reportremoval.sh
The reports older than one day are getting deleted...
Reportremoval.sh: 5: Syntax error: word unexpected (expecting "do")


Please give me some suggestion.

---

### Post by mister_pink on 2009-04-21
I think it needs more semicolons :) You can never have too many. When you type it in the shell it adds them automatically, so put them after the "echo" and "rm" lines.

Edit: It also occurred to me that this could be made much easier - find has a delete option:
```

find $path/*.xls -mtime +1 -delete

```

---

### Post by rohandeshmukh on 2009-04-21
I think the proble was associated with the permission. I changed the user name and re-executed the same script and this time it worked fine!

anyways, Thanks for your help!

---

