---
title: "Help with .bashrc and .bash_aliases"
date: 2011-06-12
forum: New to Ubuntu
---

### Post by Neoncamouflage on 2011-06-12
In my reading around about Ubuntu and Linux I've read what I thought was enough about aliases, functions, and scripts to give me at least a basic knowledge about how to use them. Clearly, I was wrong.

Right now in my home folder I have the file .bashrc. I was planning to add the following script to it that someone mentioned being quite helpful to alphabetize a directory:
```
alias alph='cat "$1" | sort > "$1"'

```
While I was looking through the file before adding it, I noticed that it had a section suggesting I create a file named .bash_aliases to store my aliases in, instead of adding to that file. It also included what I assume to be code telling it to find that file:
```
if [ -f ~/.bash_aliases ]; then
    . ~/.bash_aliases
fi

```

So I created the .bash_aliases file using the nano text editor, and placed my script inside. However, after saving, trying my alph command simply returns me command not found.

I'll be honest, I'm completely lost as to what part of it is failing. Hoping someone here has an idea or suggestion.

---

### Post by Toz on 2011-06-12
You need to either logout/in again to re-read the .bashrc file or simply source it ala:```
. ~/.bashrc
```

---

### Post by Neoncamouflage on 2011-06-12
I logged off/on and placed the code to source it, both give me this:
```
bash: : No such file or directory
cat: : No such file or directory

```

So I'm thinking there's something wrong with my script?

---

### Post by Toz on 2011-06-12
What is it that you are trying to do with this script?

---

### Post by Neoncamouflage on 2011-06-12
I'm trying to set up a simple command "alph" that will sort through and alphabetize a file for me.

---

### Post by Toz on 2011-06-12
You can just use the sort command on the file, no need for an alias:```
sort <file>
```

Alias commands don't work with $1, that is expected after the command. ```
alias alph='sort'
alph <file>
```

You can use the $1 substitutions in functions though.```
function ssort () { 
   for i in `echo $1`; do 
   echo $i 
done | sort 
}

```

```
ssort "add multiply subtract divide"
```

Or to sort a file:```
function ssort () { for i in `cat $1`; do echo $i; done | sort;  }
```

---

### Post by Neoncamouflage on 2011-06-12
Ah, that would be why it failed then. Thanks a lot for the help.

---

