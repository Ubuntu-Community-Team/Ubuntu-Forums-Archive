---
title: "Why won't my scripts execute?"
date: 2009-06-04
forum: New to Ubuntu
---

### Post by Miljet on 2009-06-04
I am beginning to learn python and creating simple scripts listed  in the tutorial. However I cannot get them to execute by entering the script name.

The first line of the script is : "#!usr/bin/python" (without the quotes).
I used "chmod +x name_of_script" to make it executable.
The permissions are now -rwxr-xr-x.

If I type 
```
python module1.py
```
it will run.
But if I type
```
module1.py
```
I get the following error
```
bash: module1.py: command not found
```

I know that I am probably missing something incredibly simply, but I just can't see it.

By the way, I just tried a shell script and am having the same problem with it. Shell script first line is "#!/bin/bash".
It will run with "bash name_of_script" but not just by entering "name_of_script".

---

### Post by Celauran on 2009-06-04
This is probably a typo in the post and not the script, but check that the shebang line reads #!/usr/bin/python, and not #!usr/bin/python. "#!/usr/bin/env python" (without quotes) is even better.

That aside, run the script like so:

```
./module1.py
```

---

### Post by gamblor01 on 2009-06-04
Yeah it doesn't seem like ./ makes any sense but it does.  Here's a good article about it:

[http://www.linfo.org/dot_slash.html](http://www.linfo.org/dot_slash.html)

---

### Post by Miljet on 2009-06-04
That was it! I had read that before, but had forgotten about it. And of course, the book I am using didn't say anything about using "./"
Thanks for the quick replies.

---

### Post by patrickpatrick on 2009-06-05
I am new to programming/ubuntu and have only been able to run scripts by 
typing: python '/path/to/myfile.py'   in terminal     My programs will not run with out the quotes around the file path.  Is there a better way?   Can't seem to make anything from chmod +x command either.  AnyHelpAppreciated

---

### Post by Celauran on 2009-06-05
> **patrickpatrick said:**
> I am new to programming/ubuntu and have only been able to run scripts by 
typing: python '/path/to/myfile.py'   in terminal     My programs will not run with out the quotes around the file path.  Is there a better way?   Can't seem to make anything from chmod +x command either.  AnyHelpAppreciated

You only need to specify python before the script if you haven't specified it in the script. Start your scripts with the following line:

```
#!/usr/bin/env python
```

and you'll be able to run them as ./scriptName

For chmod, I've always preferred using numeric values

---

### Post by The Cog on 2009-06-05
You can mke the file executable using nautilus if you prefer - right-click the file and choose Properties. On the Permissions tab, check the Execute box.

As Celauran says, the **first line** of the script should be:
```
#!/usr/bin/env python
```

Once I'm happy they work, I like to remove the .py extension, but I leave it on there while editing because the editor then knows how to do syntax higlighting.

---

### Post by Wobblybob on 2009-06-05
> **patrickpatrick said:**
> I am new to programming/ubuntu and have only been able to run scripts by 
typing: python '/path/to/myfile.py'   in terminal     My programs will not run with out the quotes around the file path.  Is there a better way?   Can't seem to make anything from chmod +x command either.  AnyHelpAppreciated

to use the chmod open a Terminal and navigate to the same directory that your script is in and then type in chmod +x yourscriptname or just right click the file, go to properties and tick the allow as executable option.
If you are in the same directory as the script you wish to run, then ./yourscriptname will work if not then you would have to specify the full path unless you place the script in say /home/yourname/bin and then add it to the system PATH

echo $PATH
which will give you something like as your current PATH;

/usr/local/sbin:/usr/local/bin:/usr/sbin
then add your own by typing,
PATH=$PATH:/home/yourname/bin

---

### Post by Tibuda on 2009-06-05
You have to prefix it with ./
```
./myscript.py
```

---

