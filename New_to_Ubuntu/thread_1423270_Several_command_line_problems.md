---
title: "Several command line problems"
date: 2010-03-06
forum: New to Ubuntu
---

### Post by madmaxou on 2010-03-06
Hi,
I'm having some trouble with the command prompt for quite a long time.
 
1. What is the difference between ' and " ?
 
2. If you have something like this
 
```
./abc.sh efg   //abc is the scriptname; efg the argument
 
abc.sh:
#!/bin/sh
rm efg //not very useful example, i know
```
How do I substitute efg so that I can use the script for anything else I put in as argument?
 
3. Which command would I use to append something to the standard input?
 
4. Is there a way I can use a script without ./ ?
 
Thanks in advance,
Max

---

### Post by howlingmadhowie on 2010-03-06
> **madmaxou said:**
> Hi,
I'm having some trouble with the command prompt for quite a long time.
 
1. What is the difference between ' and " ?


try the following:
```

echo $PATH
echo "$PATH"
echo '$PATH'

```

> 
2. If you have something like this
 
```
./abc.sh efg   //abc is the scriptname; efg the argument
 
abc.sh:
#!/bin/sh
rm efg //not very useful example, i know
```
How do I substitute efg so that I can use the script for anything else I put in as argument?
 


```

#!/bin/sh
rm $1

```

> 

3. Which command would I use to append something to the standard input?

not sure what you mean here. do you mean something like:
```

echo "some text" | wc

```

> 
4. Is there a way I can use a script without ./ ?

yeah, you can drop it somewhere in your $PATH.
what a lot of people do is create a $HOME/bin directory and then add this directory to their $PATH. that way, $HOME/bin will be searched for executables.
 
> 
Thanks in advance,
Max

---

### Post by madmaxou on 2010-03-06
Cool, thx a lot

---

### Post by madmaxou on 2010-03-06
> **howlingmadhowie said:**
> try the following:
yeah, you can drop it somewhere in your $PATH.
what a lot of people do is create a $HOME/bin directory and then add this directory to their $PATH. that way, $HOME/bin will be searched for executables.
 
Sorry, I didn't understand this one, I'm quite new at ubuntu. How do I add what to where?

---

### Post by howlingmadhowie on 2010-03-06
the PATH variable contains a list of the folders the current execution environment will search for executables. HOME is the name of your home directory (probably /home/<username>).  you can modify your PATH by adding the following to /home/<username>/.bashrc
```

PATH=$HOME/bin:$PATH

```
then you have to logout and login again.

this will redeclare the PATH variable to be /home/<username>/bin added to the list of the files in the old PATH variable.

--edit--

don't forget to create a directory /home/<username>/bin ! you can put you shell scripts in there and then they will be found by the system. don't forget to make the shell scripts executable! (chmod +x <scriptname>)

---

### Post by madmaxou on 2010-03-06
> **howlingmadhowie said:**
> try the following:
not sure what you mean here. do you mean something like:
```

echo "some text" | wc

```

 
Nah, doesn't work, what I mean is something like this:
```
echo "$var"   // now append 'some text'"
```

---

### Post by Penguin Guy on 2010-03-06
For programming questions, please post in the [Development & Programming > Programming Talk]("http://ubuntuforums.org/forumdisplay.php?f=39") topic.
I would advise taking a look at [Linux Command]("http://gd.tuwien.ac.at/linuxcommand.org/") - a guide to Linux's command line for beginners.

Anyway, here's the answers to some of your questions:
[LIST=1]
[*]```

>>> x=1
>>> echo "$x"
1
>>> echo '$x'
$x

```
[*]Use [FONT="Courier New"]$0[/FONT] for the program name (a.k.a. [FONT="Courier New"]abc.sh[/FONT]), [FONT="Courier New"]$1[/FONT] for the first argument (a.k.a. [FONT="Courier New"]efg[/FONT]), and so on.
[*][FONT="Courier New"]echo "${foo}${bar}"[/FONT]
[/LIST]

---

### Post by howlingmadhowie on 2010-03-06
> **madmaxou said:**
> Nah, doesn't work, what I mean is something like this:
```
echo "$var"   // now append 'some text'"
```

i must admit, i can't think of an easy way of doing this. i'd write this:
```

echo "foo" | sed -e 's/$/bar/'

```
but there must be an easier way.

you could also try:
```

echo -n 'foo' && echo 'bar'

```

---

