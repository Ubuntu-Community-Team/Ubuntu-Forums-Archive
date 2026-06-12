---
title: "How do I combine two files?"
date: 2011-07-02
forum: New to Ubuntu
---

### Post by jayi on 2011-07-02
Hi, I have two text files with some text, they are called "file1" and "file2". I wanted to learn how I can use the command line to combine these two files and so I read about "man cat" which explains that "cat - concatenate files and print on the standard output".

So this was my attempt at first:

```

cat file1 file2

```The result was, neither file1 nor file2 was modified, but the result was shown to me in my terminal with the text from file1, a line break, and then the text from file2. This was not exactly what I was trying to do, so I had a few questions:

1) How do I modify file1 only, so that the text of file2 is added to the end of file1?
2) How do I not modify either file, but create a new file called file3 that has file1's text, and then file2's text right after?
3) How do I get rid of the line break or replace it with some custom text? For example, file1 text, and then "Below this point is the text originally from file2".
4) Is there a good guide to learn about how to do more complicated tasks to manipulate files with the command line? For example, if I want to only grab lines that begin with the character # from file1 concatenate that with the full text from file2 and output the result to file3 or something similar.

Thank you.

---

### Post by jtarin on 2011-07-02
I don't have a line break here.....post a pic of what the difficulty is.

In a terminal 'man grep' is something to look at for your #4.

[Google]("http://www.google.com/webhp?hl=en&tab=nw#hl=en&xhr=t&q=bash+combine+2+files+into+a+third&cp=33&pf=p&sclient=psy&site=webhp&source=hp&aq=f&aqi=&aql=&oq=bash+combine+2+files+into+a+third&pbx=1&bav=on.2,or.r_gc.r_pw.&fp=deb24ccd75812d3e&biw=1440&bih=720")

---

### Post by sam_delta on 2011-07-02
you can redirect the output of any command to a file using the operator ">", most of my answers will be based on that.

> **jayi said:**
> 
1) How do I modify file1 only, so that the text of file2 is added to the end of file1?

I believe this cant be done with 1 cat comand. you could do something like this tho
```
cat file1 file2 > output
mv output file1
```


> **jayi said:**
> 
2) How do I not modify either file, but create a new file called file3 that has file1's text, and then file2's text right after?


just redirect the output to another file
```
cat file1 file2 > outputfile
```


> **jayi said:**
> 
3) How do I get rid of the line break or replace it with some custom text? For example, file1 text, and then "Below this point is the text originally from file2".

Note that cat does not add an empty line when concatenating files, your first file must end in with an empty line.
with cat you can only supress REPEATED empty lines with -s switch
```
cat file1 file2 -s > outputfile
```

you can also pass the ouput from cat to another program which can take care of the empty lines. To do this, you use whats called a 'pipe' |. In this following example, we execute cat and pass the output to another program called sed which takes cares of the empty lines.
```
cat file1 file2 | sed '/^ *$/d'
```

remember you can always redirect the output to a file with a '>' even when we have pipes. Example ```
cat file1 file2 | sed '/^ *$/d' > output file
```

note that sed can du much more than just removing empty lines, sed is a powerful inline text editor, it can also acomplish the task you mention of replacing text.

> **jayi said:**
> 
4) Is there a good guide to learn about how to do more complicated tasks to manipulate files with the command line? For example, if I want to only grab lines that begin with the character # from file1 concatenate that with the full text from file2 and output the result to file3 or something similar.


there are many guides on manipulating files, just google the tools (cat, sed, awk, head, tail, paste, grep... )

any questions, let us know

sam

---

### Post by jayi on 2011-07-02
> **jtarin said:**
> I don't have a line break here.....post a pic of what the difficulty is.

In a terminal 'man grep' is something to look at for your #4.

[Google]("http://www.google.com/webhp?hl=en&tab=nw#hl=en&xhr=t&q=bash+combine+2+files+into+a+third&cp=33&pf=p&sclient=psy&site=webhp&source=hp&aq=f&aqi=&aql=&oq=bash+combine+2+files+into+a+third&pbx=1&bav=on.2,or.r_gc.r_pw.&fp=deb24ccd75812d3e&biw=1440&bih=720")

I see, I think it was because gedit automatically added a newline to the end of my file. I tried with a different text editor and now there is no newline.

> **sam_delta said:**
> you can redirect the output of any command to a  file using the operator ">", most of my answers will be based on  that.

...


Ah, I see. Thank you sam for the answer. I didn't realize the tasks I wanted to do required so much knowledge.

Since I know the names of the tools that I must google I can also figure out many things now. Thank you. :)

---

### Post by sam_delta on 2011-07-02
no problem, feel free to ask me if you find yourself needing help.
I had a very good set of PDF's explaining those tools and making examples with them, i just cant find them. If i find them, ill let you know

sam

---

### Post by hakermania on 2011-07-02
Another one-command-no-temp-files way:
```

alex@MaD-pc:~$ cat file1
1
alex@MaD-pc:~$ cat file2
2
alex@MaD-pc:~$ echo "Appending file1 to file2..."; _**cat file1 >> file2**_
Appending file1 to file2...
alex@MaD-pc:~$ cat file2
2
1
alex@MaD-pc:~$

```

---

