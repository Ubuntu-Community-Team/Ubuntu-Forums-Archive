---
title: "count lines,word, and characters without using wc command"
date: 2011-04-11
forum: New to Ubuntu
---

### Post by quartaela on 2011-04-11
hi there friends. i am trying to write a shell script that counts the lines,words and characters without using wc command. but i am facing with an error which is 

"read: 30: Illegal option -n
Number of lines: 0
Number of characters:
"

my code is ;
"
```
#!/bin/sh
#

filename="$1"

cline=0
#cword=0
cchar=0

if [ $# -eq 0 ]
then
echo "RUN ERROR:
    Give a filename to analyze"
exit

elif [ $# -eq 1 ]
then

while IFS= read -r -n1 c
do

if [ "$c"=="\n" ]
then
cline++

else
cchar++
fi
done < "$filename"
fi

echo "Number of lines: $cline
Number of characters: $char"
```

i can't find the solution_? so if you can help i will be very glad.

---

### Post by r-senior on 2011-04-11
Does it work if you change #!/bin/sh to #!/bin/bash?

EDIT: Oh, and next time you post code, could you enclose it in code tags so it keeps the indentation? Easiest way is to select it and then hit the # button in the posting toolbar.

---

### Post by quartaela on 2011-04-11
> **r-senior said:**
> Does it work if you change #!/bin/sh to #!/bin/bash?

EDIT: Oh, and next time you post code, could you enclose it in code tags so it keeps the indentation? Easiest way is to select it and then hit the # button in the posting toolbar.

nope it doesnt work.

---

### Post by r-senior on 2011-04-11
Same error message?

---

### Post by quartaela on 2011-04-11
"
./filecount.sh: line 24: cline++: command not found
./filecount.sh: line 24: cline++: command not found
./filecount.sh: line 24: cline++: command not found
./filecount.sh: line 24: cline++: command not found
./filecount.sh: line 24: cline++: command not found
./filecount.sh: line 24: cline++: command not found
./filecount.sh: line 24: cline++: command not found
./filecount.sh: line 24: cline++: command not found
./filecount.sh: line 24: cline++: command not found
./filecount.sh: line 24: cline++: command not found
./filecount.sh: line 24: cline++: command not found
./filecount.sh: line 24: cline++: command not found
./filecount.sh: line 24: cline++: command not found
./filecount.sh: line 24: cline++: command not found
./filecount.sh: line 24: cline++: command not found
./filecount.sh: line 24: cline++: command not found
./filecount.sh: line 24: cline++: command not found
./filecount.sh: line 24: cline++: command not found
./filecount.sh: line 24: cline++: command not found
./filecount.sh: line 24: cline++: command not found
./filecount.sh: line 24: cline++: command not found
./filecount.sh: line 24: cline++: command not found
./filecount.sh: line 24: cline++: command not found
Number of lines: 0
Number of characters: 
"
this is the output

---

### Post by r-senior on 2011-04-11
The reason your "read -n" wasn't working is that it's a bash builtin. Unfortunately /bin/sh doesn't link to /bin/bash on Ubuntu, it links to /bin/dash, which is a Debian-originated shell. This doesn't have a "-n" option to read.

See:
```

$ ls -l /bin/sh

```

So your first bug is fixed, your move ... ;)

---

### Post by 1clue on 2011-04-11
Bash doesn't know what ++ means.

cline=$cline+1

---

### Post by quartaela on 2011-04-11
i change  "#!/bin/sh" code with " #ls -l /bin/sh" but now it doesn't printing anything on the screen_? am i doing right_?. and i am new to shell programming : ).

---

### Post by r-senior on 2011-04-11
Sorry, I didn't mean you to put 'ls -l' in your script. I was just pointing out that you can see where /bin/sh is linked to by using that command in a terminal (don't type the '$', that's your prompt):

```

$ ls -l /bin/sh

```

There are a few bugs you need to work through but have a go and ask if you get stuck.

---

### Post by quartaela on 2011-04-11
> **1clue said:**
> Bash doesn't know what ++ means.

cline=$cline+1

with your advise friend it gave 

"Number of lines: 0+1+1+1+1+1+1+1+1+1+1+1+1+1+1+1+1+1+1+1+1+1+1+1
Number of characters: "

output. i know the problem is in while loop but logically there must not any problem :)

---

### Post by 1clue on 2011-04-11
That means it thinks cline is a string value rather than a numeric value.

You'll need to develop some problem solving skills on your own, and if you're tackling this sort of program it's a good time to do it.  You have some errors in your script and people are deliberately feeding you 1clue :) at a time, in hopes that you'll take the next step on your own.

I think we're willing to help, we just want you to try here.

---

### Post by quartaela on 2011-04-11
> **1clue said:**
> That means it thinks cline is a string value rather than a numeric value.

You'll need to develop some problem solving skills on your own, and if you're tackling this sort of program it's a good time to do it.  You have some errors in your script and people are deliberately feeding you 1clue :) at a time, in hopes that you'll take the next step on your own.

I think we're willing to help, we just want you to try here.

:D. well i don't want to be misunderstood of course i am trying. ok then first question what does mean IFS can you explain the code

```
 while IFS= read -r -n1 c
```

and how does it thinks cline is a string cause it doesnt have any double quotes_?.

---

### Post by 1clue on 2011-04-11
What are you using as programming reference?  Besides us, I mean?

No matter what language you use, you always need some sort of documentation.  I've been using the languages I currently use professionally for years, and I still need to hit the documentation several times a day.

Tell us what you've tried, where you looked and how what you found doesn't meet your expectations.

Give a man a fire and he will be warm for a night.
Set a man on fire and he will be warm for the rest of his life.

:D

---

### Post by quartaela on 2011-04-11
well ok generally i use my "Linux Shell Scripting Tutorial" which my lab. assistant gave. but the problem is they always give a homework which we don't have any idea about. in lecture we don't see shell programming. in lab. hours we have 2 hours for make the lab. work. after that they give a prelab work for the coming week. and the tutorial is not good in my opinion. so i try search in the internet and try to understand. and if i can't managed i write the problem here. : ).

---

### Post by quartaela on 2011-04-11
and i take the example of while statement in this link [http://www.cyberciti.biz/faq/linux-unix-read-one-character-atatime-while-loop/](http://www.cyberciti.biz/faq/linux-unix-read-one-character-atatime-while-loop/) with search "read a character from a file in bash". i know i must use the way of reading character by character method.

---

### Post by 1clue on 2011-04-11
Then get better documentation.

The reason I'm being like this is because you seem to want the forum to do your thinking for you.  That's an extremely bad habit when coding, but sometimes you just gotta ask.

Since this is for a class, you need to try harder yet.

Most languages today have some sort of developers mailing list or forum specific to the language or the IDE or whatever.  Some of those guys will rip you apart if you turn your brain off.  Those same guys might spend a day trying to figure out what the problem is if they see you've been sweating bullets.

We (and this is the collective "we" of developers who use the Internet as a resource) want to see that you did something other than copy what they said and report back.

Also, sometimes the person on the other side of the chat doesn't really know what's going on either.  The answer you get might be close but have something wrong in what they said.

Some general rules:
[LIST=1]
[*]For each language you use, set up a bookmark submenu which has language reference, forums and any other valuable resources.
[*]Put those resources in order of the best value on top.
[*]Every time you have a problem, re-read that section in the official documentation even if you're sick of looking at it.
[*]Every post you read from somebody who is helping you, question what they put in.  If you don't understand it, then study harder.  Debug that the same as you would your own code.  Before you quit looking, make sure you know what it's supposed to do.
[/LIST]

When searching on solutions, always include the name of the language, the version you're using and the basic idea of what you're trying to do or "reference" or "documentation".  Scan the whole page, and then pick something that looks similar to what you have.  Always keep an eye out for a better source of documentation, and try to read that documentation from end to end in your spare time.

For example, you might google "bash 4.1.5 documentation" and see what that brings up.  You might try to find out where the implementation you are using came from and look at the official site for documentation.

I'm a bit old school so I prefer books sometimes.

---

### Post by quartaela on 2011-04-11
well ok thanks for your advice : )

---

### Post by 1clue on 2011-04-11
> **quartaela said:**
> and i take the example of while statement in this link [http://www.cyberciti.biz/faq/linux-unix-read-one-character-atatime-while-loop/](http://www.cyberciti.biz/faq/linux-unix-read-one-character-atatime-while-loop/) with search "read a character from a file in bash". i know i must use the way of reading character by character method.

By this reference I may be wrong about bash not knowing ++, but when I tried a simple example it didn't work for me.  It could be that you and I made the same error, or it could be that the example is using some bash variant which we are not using.

That example seems to be a really cumbersome way to solve the problem, but I guess I wouldn't use bash for that type of script anyway.

I still think this is very much within the basic documentation you might find for the language, so I'm going to be a bit hard on you and make you look a bit more.

---

### Post by Vaphell on 2011-04-11
bash knows about ++ but you need (()) for integer operations
```
i=6; (( i++ )); echo $i
7
```
it's even possible to write a for loop in C style, for example:
```
for (( i=0; i<${#array[@]}; i++ ))
do
  echo \#$(( i+1 )) ${array[i]}
done
```

---

### Post by quartaela on 2011-04-13
well i made some change on my code. still it counts wrongly. i am trying to read the text file character by character  but  i recognize that it doesn't count the words. on the other hand, it adds the number of lines and words in num_lines and num_words variables. here is the code and an example of an output;

```
#!/bin/bash
#

if [ $# -eq 0 ]
then

echo "You didn't entered a filename as a parameter"
exit

elif [ $# -eq 1 ]
then
filename="$1"

num_line=0
num_word=0
num_char=0

while read -n1 char
do
if [ "char"="\n" ]
then
(( num_line++ ))

elif [ char=" "  ]
then
(( num_word++ ))

fi

(( num_char++ ))

done < "$filename"

echo "$num_line
$num_word
$num_char"

fi
```

my text file is

```
ubuntu
linux
bash
dash
kubuntu
```

and the output:

```
31
0
31

```

there are 26 characters and 5 lines. and the output gives num_lines+num_char as you can see : ). how can i fixed this _? anyway thanks for your help

---

### Post by IHeequ5i on 2011-04-13
My suggestion is to proofread your code. Carefully.

---

### Post by quartaela on 2011-04-13
i fixed some errors but i recognize that when i enter more than one word in a line it takes all spaces as a new line character_?. for example if my text file is like this :

```
ubuntu wow
linux forum
bash
dash
kubuntu
```

the output is

```
Line Number = 7
Word Number = 0
Character Number =34

```

so there are 5 lines and 2 spaces. and anyway i can't managed to count the words. and here is my code:

```
#!/bin/bash
#

cnew_line=`echo -e "\n"`
cspace=`echo -e " "`

if [ $# -eq 0 ]
then

echo "You didn't entered a filename as a parameter"
exit

elif [ $# -eq 1 ]
then
filename="$1"

num_line=0
num_word=0
num_char=0

while read -n1 char
do
if [ "$char" = "$cnew_line" ]
then
(( num_line++ ))

elif [ "$char" = "$cspace" ]
then
(( num_word++ ))

else
(( num_char++ ))

fi

done < "$filename"

echo "Line Number = $num_line
Word Number = $num_word
Character Number =$num_char"

fi
```

---

### Post by Vaphell on 2011-04-13
try ```
IFS=$'\n'
```
you will get your spaces back (bash treats all whitespaces as separators not as 'meat' by default). Also you should ++ words for newline too

---

### Post by quartaela on 2011-04-14
FINALLY! : ) it worked. but i can't understand why i increment the word number by one in the statement which i increment line number_?.

---

### Post by Vaphell on 2011-04-14
what is the difference between
```
someword someotherword
```
and ```
someword
someotherword
```?
as you see newline separates words just like space or tab (do you detect tabs?)

---

### Post by quartaela on 2011-04-14
ok i understood : ). yess i included detecting tabs option. so thanks for your help Vaphell. : )

---

