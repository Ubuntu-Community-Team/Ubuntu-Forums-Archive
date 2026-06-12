---
title: "Some programs run and some dont in terminal, what?!?!?!?!"
date: 2009-05-09
forum: New to Ubuntu
---

### Post by harrye123 on 2009-05-09
Hey friends just a very newbie question as I am getting the basics in the bash shell.

I have the terminal on, and say I do a
cat blahblah
echo hi
ctrl D

then I do an ls and I see that it doesnt have x permission and I have to do a chmod, what? Why? do I have to sudo every single command.

Whats more disconcerting is that some progs run fine with nor probs say this one
#!/bin/bash

# Arithmetic tests.
# The (( ... )) construct evaluates and tests 
# numerical expressions.
# Exit status opposite from [ ... ] construct!

(( 0 ))
echo "Exit status of \"(( 0 ))\" is $?." # 1
(( 1 ))
echo "Exit status of \"(( 1 ))\" is $?." # 0
(( 5 > 4 )) # true
echo "Exit status of \"(( 5 > 4 ))\" is $?." # 0
(( 5 > 9 )) # false

And some just don't like the simple one blahblah I wrote above, or this one:
#!/bin/bash

a=100.19
b=$(echo "scale=3; $a/100" | bc)

echo b = $b # b = 1.001

#perform inequality tests
A=0.04
B=0.03
let "comp=`echo $A-$B\>0 | bc`"
echo $comp      # 1

let "comp=`echo $B-$A\>0 | bc`"
echo $comp      # 0


Where I get instead a bash: /.filename: No such file or directory

I am very, very perplexed, thanks to any good soul who wants to takle these....
(btw why do I always have to put a #!/bin/bash in every prog?)

---

### Post by sgosnell on 2009-05-09
You don't **have** to put a #!/bin/bash in every script (not program, that's something different), although it's usual.  It tells the OS what shell to use for the terminal session.  

By default, Linux runs only programs and scripts that are in folders in the path. If you want to run something in your current folder, you have to tell it to look there, and that's what ./ (not /.) does.  It tells the OS that the command is in the current folder.  You can either use ./, or you can give the full path to the folder.  ./ is shorter and quicker.

[This page](http://www.linux-tutorial.info/modules.php?name=MContent&pageid=224) is a Linux tutorial which should help you a lot, and give you much more information than you will get here or on any other forum.

---

### Post by spiderbatdad on 2009-05-09
well you dont have to use sudo to edit or change permissions of files you own in your home directory. The rest is the ubuntu security model...might as well get used to it, if you plan to use ubuntu. Of course there are ways around the security model, but the forum does not support any of these.
Problems with not finding files is due to not specifying complete path to file or executable not in $PATH.
run ```
echo $PATH
```To add a directory to path, export it in your .bashrc or create a directory called bin in your home directory...I believe, if bin is created, it is automgically added to path...as outlined in your .bashrc.

---

### Post by harrye123 on 2009-05-09
Wow, guys, thanks for the great replies, I am very novice and some things can seem like mountains :) but I really want to be over and done with windows and migrate.

May I also ask to anyone who wants to reply what these expressions mean
`echo $2 | grep - > dev/null` 
I understand the | pipe and the > redirection but what is the - before the > and the dev/null 

also what is ! -d and ! -e, I know the ! not equal but what is the -d or -e as in if [ ! -d $parameter]

thanks.

---

### Post by harrye123 on 2009-05-10
Hey guys anyone have any ideas for this novice?:(

---

### Post by sgosnell on 2009-05-10
Have you read the tutorial I linked for you?

---

