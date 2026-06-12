---
title: "redirection &lt; &gt;, pipes | and command substitution $()"
date: 2010-12-06
forum: New to Ubuntu
---

### Post by john77eipe on 2010-12-06
Hi All,

I'm pretty confused when to use either of these 3. 

Also is it that > works from left to right, < right to left and | always from left to right?

---

### Post by asmoore82 on 2010-12-06
`>` writes *stdout* to a file
`<` pulls *stdin* from a file

`<` and `>` always have a file name to the right of them.

`|` links *stdout* on the left to *stdin* on the right.

`|` always has a program name to the right of it.

```
[COLOR="Blue"]#Right[/COLOR]
echo "Hello World" > hello.txt
echo "Hello World" | cat > hello.txt
cat hello.txt
cat < hello.txt
cat < hello.txt | cat

[COLOR="Red"]#Wrong
echo "Hello World" | hello.txt
#^attempts to load a program named "hello.txt"
echo "Hello World" > cat
#^saves a file named "cat"
echo hello.txt
#^`cat` will read from files, but not `echo`[/COLOR]

[COLOR="Blue"]#Command Sub.
#Darnit! Force `echo` to use what's in that file![/COLOR]
echo "$( cat hello.txt )"
```

---

### Post by QLee on 2010-12-06
>, outputs
<, inputs
|, pipes through whatever comes next

---

### Post by TeoBigusGeekus on 2010-12-06
>
Redirection: usually used to output a command to a file.
```
ls -la
```
will print the long format of ls in the standard output (terminal - screen).
```
ls -la>~/Desktop/list
```
instead of printing to screen, output is redirected to a file (~/Desktop/list)

<
Never used this one, but I guess it does the opposite (input a file to a command).

|
Piping - filtering: what is says exactly.
You want to find out what your hardware specs are?
```
lshw
```
You want to find out what your graphics card is? You filter the above command with grep - only the lines with the string defined in grep will be printed.
```
lshw | grep VGA
```
Do you want to save this info to a file?
```
lshw | grep VGA > ~/Desktop/graphics_card.txt
```

---

### Post by bodhi.zazen on 2010-12-06
For additional information see :

[http://tldp.org/LDP/abs/html/io-redirection.html](http://tldp.org/LDP/abs/html/io-redirection.html)

---

### Post by john77eipe on 2010-12-07
Thanks a ton guys. (Sorry for this late response :redface:)

In all examples I find that 

>, >> or < are used to redirect to a file instead of the default stdout and stdin.

So i conclude that the above redirection operators are used only with file names on it's right.

Coming to |, it's same as doing "> <" together which is not possible so we use |. And in | data flows only from left to right.


Please comment if my above understanding is correct or not.

---

### Post by sisco311 on 2010-12-07
> **bodhi.zazen said:**
> For additional information see :

[http://tldp.org/LDP/abs/html/io-redirection.html](http://tldp.org/LDP/abs/html/io-redirection.html)

I wouldn't recommend the *Advanced Bash-Scripting Guide*:


> **geirha said:**
> [SIZE="6"]BASH[/SIZE]
[http://mywiki.wooledge.org/BashGuide](http://mywiki.wooledge.org/BashGuide)
[http://wiki.bash-hackers.org/doku.php](http://wiki.bash-hackers.org/doku.php)
[http://mywiki.wooledge.org/BashFAQ](http://mywiki.wooledge.org/BashFAQ)

[SIZE="5"]What NOT to read[/SIZE]
**The Advanced Bash-Scripting Guide**
«The infamous "Advanced" Bash Scripting Guide should be avoided unless you know how to filter out the junk. It will teach you to write bugs, not scripts. In that light, the BashGuide was written: [http://mywiki.wooledge.org/BashGuide](http://mywiki.wooledge.org/BashGuide)»
**Google** 
«Google is NOT a preferred source for learning bash, because 90% of the "tutorials" and scripts out there are JUNK.»

The above two quotes are from #bash at irc.freenode.net

---

### Post by john77eipe on 2010-12-07
Thanks sisco311. I'll definitely look into it. 

> 
>, >> or < are used to redirect to a file instead of the default stdout and stdin.

So i conclude that the above redirection operators are used only with file names on it's right.

Coming to |, it's same as doing "> <" together which is not possible so we use |. And in | data flows only from left to right.

Please comment if my above understanding is correct or not.

is the above, correct?

---

### Post by bodhi.zazen on 2010-12-07
> **john77eipe said:**
> Thanks sisco311. I'll definitely look into it.

A pipe sends the output from one program to the input of another.

In general it is used to (simple) command together.

Try it:

```
cd
ls
ls | grep D
```

Do you see how the pipe took the output of ls and gave it to grep ?

If you are new to bash, I highly suggest:

[http://linuxcommand.org/](http://linuxcommand.org/)

---

