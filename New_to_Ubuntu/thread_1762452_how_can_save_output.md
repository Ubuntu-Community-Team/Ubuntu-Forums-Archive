---
title: "how can save output?"
date: 2011-05-19
forum: New to Ubuntu
---

### Post by Come TO love on 2011-05-19
I make shell script by use "if" statement, what should add it to 
shell script save which I enter it in output file txt?

---

### Post by compmodder26 on 2011-05-19
> **Come TO love said:**
> I make shell script by use "if" statement, what should add it to 
shell script save which I enter it in output file txt?

You use ">" or ">>" to redirect the output of your script to a file.  For example: 

```
./the_command_you_want_to_run > /tmp/test.txt
```

">" will empty the file first then write to it.
">>" will simply append the output to existing text in the file, if any is present.

---

### Post by Come TO love on 2011-05-19
> **compmodder26 said:**
> You use ">" or ">>" to redirect the output of your script to a file.  For example: 

```
./the_command_you_want_to_run > /tmp/test.txt
```">" will empty the file first then write to it.
">>" will simply append the output to existing text in the file, if any is present.


I mean
like this

echo "enter your name"
read name


# now i  when start shell script  it ask me to enter my name right?
so when i enter my name for example COME TO LOVE
i want from shell script save my name enter onther file like test.txt

how can i do that or what command must add it to get this file?

---

### Post by dcsoldschool53 on 2011-05-19
> **Come TO love said:**
> I make shell script by use "if" statement, what should add it to 
shell script save which I enter it in output file txt?

I am not sure if this is what you are talking about. If I type this command in the terminal```
cat > Save_new_text.txt
```and, press the enter key, this is a handy way to create a file without using a text editor. All output will be displayed on the screen. In order to save the output to a file, you will have to manually press the ```
CTRL + D key
``` after you have finished typing all of your information. Then, type```
gedit Save_new_text.txt
``` in the terminal, and it will open the new file that you created.

I hope this helps you.

---

### Post by compmodder26 on 2011-05-19
> **Come TO love said:**
> I mean
like this

```
echo "enter your name"
read name
```


# now i  when start shell script  it ask me to enter my name right?
so when i enter my name for example COME TO LOVE
i want from shell script save my name enter onther file like test.txt

how can i do that or what command must add it to get this file?

Ok, now I understand. Your script would look like this then:

```
echo "enter your name"
read name

echo $name > test.txt
```

---

### Post by ksprasad on 2011-05-19
>  
 
echo "enter your name"
read name
 
 
# now i when start shell script it ask me to enter my name right?
so when i enter my name for example COME TO LOVE
i want from shell script save my name enter onther file like test.txt
 
how can i do that or what command must add it to get this file?
 

 
I think this is what you are trying to do
 
```

echo "enter your name"
read name
echo $name > test.txt

```

---

