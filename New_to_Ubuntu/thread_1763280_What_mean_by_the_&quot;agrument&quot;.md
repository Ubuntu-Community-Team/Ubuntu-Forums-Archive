---
title: "What mean by the &quot;agrument&quot; ?"
date: 2011-05-20
forum: New to Ubuntu
---

### Post by Come TO love on 2011-05-20
Write a script that Takes exactly one argument, a directory name.


can anyone clean for me?

---

### Post by frankbooth on 2011-05-20
In this context, I believe the argument is your input and in this case the input is a directory.

You should ask your teacher instead, this forum isn't intended for homework assignments ;).

---

### Post by Come TO love on 2011-05-20
> **frankbooth said:**
> In this context, I believe the argument is your input and in this case the input is a directory.

You should ask your teacher instead, this forum isn't intended for homework assignments ;).

thanks for you bost but this not home work my love and  Iam not student   I  try just lean write script, If i am a student need not ask what mean argument ;)

---

### Post by Anuovis on 2011-05-20
*Arguments* in shell are additional parameters you give to *commands*. Some *commands* work without *argument*s but a lot of them don't.

E.g.
**cd ~/Music**
"cd" is a command that opens a directory, "~/Music" is an argument that points to the location you want to open.

**ls**
A plain command "ls" to list files

**ls -a**
A command "ls" with an argument "-a" that shows hidden files as well.

---

### Post by Come TO love on 2011-05-20
> **Anuovis said:**
> *Arguments* in shell are additional parameters you give to *commands*. Some *commands* work without *argument*s but a lot of them don't.

E.g.
**cd ~/Music**
"cd" is a command that opens a directory, "~/Music" is an argument that points to the location you want to open.

**ls**
A plain command "ls" to list files

**ls -a**
A command "ls" with an argument "-a" that shows hidden files as well.

thanks my freind Anuovis

can you give me e.g for this "Write a script that Takes exactly one argument, a directory name."
by use termanal

$ vi  argument

cd ~/Music



is right?

---

### Post by Petrolea on 2011-05-20
> **Come TO love said:**
> thanks my freind Anuovis

can you give me e.g for this "Write a script that Takes exactly one argument, a directory name."
by use termanal

$ vi  argument

cd ~/Music



is right?

I'm not sure if I correctly understood your question but if you're writing Bash scripts, you would do this:

```
./script_name "/home/example"
```

In your code, you refer to the argument by its number, $1 for example -> in this case the first and the only argument would be "/home/example" (script reads it without quotes of course).

Script example:
```
echo $1
```

would return the value of first argument.

Hope this helped :)

---

### Post by Come TO love on 2011-05-20
> **Petrolea said:**
> I'm not sure if I correctly understood your question but if you're writing Bash scripts, you would do this:

```
./script_name "/home/example"
```In your code, you refer to the argument by its number, $1 for example -> in this case the first and the only argument would be "/home/example" (script reads it without quotes of course).

Script example:
```
echo $1
```would return the value of first argument.

Hope this helped :)

blz can you clean more i am not understaand](*,)

---

### Post by blind2314 on 2011-05-20
> **Come TO love said:**
> blz can you clean more i am not understaand](*,)
 
 
I'm unsure what's not clear about it...
 
And for the record, this does sound suspiciously like something you should be doing on your own.
 
He wrote a "script" that echo's the first argument given to it (the only argument in this case).
 
Open up a new file, write the command, and then save it/execute it.
 
```
vi myscript
echo $1

```
 
Then make it executable and run it.
 
```
chmod 755 myscript
./myscript "hey"
```
 
It should return the word "hey" in your terminal..or whatever else you decide to type there.

---

### Post by Petrolea on 2011-05-20
> **blind2314 said:**
> I'm unsure what's not clear about it...
 
And for the record, this does sound suspiciously like something you should be doing on your own.
 
He wrote a "script" that echo's the first argument given to it (the only argument in this case).
 
Open up a new file, write the command, and then save it/execute it.
 
```
vi myscript
echo $1

```
 
Then make it executable and run it.
 
```
chmod 755 myscript
./myscript "hey"
```
 
It should return the word "hey" in your terminal..or whatever else you decide to type there.

If you aren't really into terminal stuff you can always use other editors like gedit, which is installed by default (assuming you use Ubuntu). Just make sure to make it executable or it won't get executed. 
The post I quoted explains it well - I'm just referring to the part with 'vi'.

---

