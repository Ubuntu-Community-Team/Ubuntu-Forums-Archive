---
title: "command alias"
date: 2010-11-27
forum: New to Ubuntu
---

### Post by Unewbeginner on 2010-11-27
Hello everyone, I'm pretty new to Ubuntu and want to have some shell commands to make my work easier. Basically I hope to have a short cut like this:
```
goto nameabc123456
```

and then I go to the directory 
```
./name/abc/123/456/
```

How could I get this work? Do I need to write some python scripts?
Any suggestions are welcome!

---

### Post by asmoore82 on 2010-11-27
The TAB key is your best friend: [http://en.wikipedia.org/wiki/Command_line_completion](http://en.wikipedia.org/wiki/Command_line_completion)

---

### Post by Unewbeginner on 2010-11-27
Sorry I might not make it very clear. It's for our daily work and the directories is much deeper than I wrote. Just imagine it's something like:

```
/name/test/xxx/year/month/day/version/abc/123/456
```

So I need to make it as easy as possible.

---

### Post by bodhi.zazen on 2010-11-28
Add an alias to ~/.bashrc

The syntax is 

alias shortcut = command

I advise you use the full path to most commands, but cd is "built in"

```
alias foo='cd /full/path/to/directory'
```

change "foo" and the path as needed.

---

### Post by Unewbeginner on 2010-11-28
Our file system have thousands of the code in this style. So I have to have a function like command that I get quick path change when I input "goto name123456" "goto name 254157" "goto name521516" etc.

---

### Post by bodhi.zazen on 2010-11-28
> **Unewbeginner said:**
> Our file system have thousands of the code in this style. So I have to have a function like command that I get quick path change when I input "goto name123456" "goto name 254157" "goto name521516" etc.

Then you shall have to write a script to do that for you. Without knowing your thousands of directories it would be guess work for us to start something like this for you.

[http://linuxcommand.org/](http://linuxcommand.org/)

---

### Post by asmoore82 on 2010-11-28
For specifying a full path, it can't get any faster than tab completion.
Tab completion also guarantees no typos.

---

### Post by Unewbeginner on 2010-11-28
> **bodhi.zazen said:**
> Then you shall have to write a script to do that for you. Without knowing your thousands of directories it would be guess work for us to start something like this for you.

[http://linuxcommand.org/](http://linuxcommand.org/)

Our system is for multiple users, and then has a level related to user names(like Mike, Tom, Kate, etc). And the system has some codes for detail information, a 3-character code (for example "abc", "exj", "tsr", etc". 
Then two sets of numbers (each has 3 digits). You could call it test codes.
Then some individual folders for the test results (pic for all pictures, sim for all simulations, etc).

Below are some examples for our folders.
```
/Projects/tsr/job/mike/012/531/sim
/Projects/ace/job/tom/423/151/pic
```

I want to develop a shortcut for this:
when mike inputs the command below on his machine, then he gets to the first directory above.
```
sim tsr012531
```

when tom inputs the command below on his machine, then he gets to the second directory above.
```
pic ace423151
```

Hope it makes things clear:)

---

### Post by brishu on 2010-11-28
echo "anyName(){cd /thing/one/$1/awesome/$2/$3;}" | tee -a ~/.bashrc
(also, what the code after the | does is copy the code between the "" into the .bashrc file (which is where you store your aliases and extra functions))

doing that will go to /thing/one/my/awesome/code/isAwesome if you type on
anyName my code isAwesome

BUT, keep in mind, they NEED to be separated by space.

also going with your example if I wanted tom to go to: /Projects/ace/job/tom/423/151/pic when he typed in: pic ace 423 151
"goToFolder(){cd /Projects/$2/job/$USER/$3/$4/$1;}"

Although I will however say that it really is much easier to specify a full path via Tab-completion.

---

### Post by DaithiF on 2010-11-28
a bash function like this may give you a start:
```
function pic() {
    input=$1
    first=${input:0:3}
    remaining=${input:3}
    trailing_path=""
    while true
    do
        [[ ${#remaining} -le 0 ]] && break
        trailing_path="${trailing_path}${remaining:0:3}/"
        remaining=${remaining:3}
    done
    requested_dir="$first/job/$USER/${trailing_path}pic"
    cd $requested_dir
}

```

---

### Post by Unewbeginner on 2010-11-28
If I don't want to separate the code, do I need to use python script for this?

> **brishu said:**
> echo "anyName(){cd /thing/one/$1/awesome/$2/$3;}" | tee -a ~/.bashrc
(also, what the code after the | does is copy the code between the "" into the .bashrc file (which is where you store your aliases and extra functions))

doing that will go to /thing/one/my/awesome/code/isAwesome if you type on
anyName my code isAwesome

BUT, keep in mind, they NEED to be separated by space.

also going with your example if I wanted tom to go to: /Projects/ace/job/tom/423/151/pic when he typed in: pic ace 423 151
"goToFolder(){cd /Projects/$2/job/$USER/$3/$4/$1;}"

Although I will however say that it really is much easier to specify a full path via Tab-completion.

---

### Post by theozzlives on 2010-11-28
A regular BASH script should suffice, but I agree using the full path is easier.

---

### Post by DaithiF on 2010-11-29
update to my earlier post -- adding a couple of aliases for sim and pic to a generic function which does the work of figuring out the directories

add to .bashrc:
```
alias sim="quickdir sim "
alias pic="quickdir pic "
function quickdir() {
    lastdir=$1
    input=$2
    first=${input:0:3}
    remaining=${input:3}
    trailing_path=""
    while true
    do
        [[ ${#remaining} -le 0 ]] && break
        trailing_path="${trailing_path}${remaining:0:3}/"
        remaining=${remaining:3}
    done
    requested_dir="$first/job/$USER/${trailing_path}${lastdir}"
    echo $requested_dir
    cd $requested_dir
}

```

usage:
```
sim tsr012531

```
```
pic ace423151
```

---

