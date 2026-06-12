---
title: "shopt"
date: 2010-10-16
forum: New to Ubuntu
---

### Post by Hippytaff on 2010-10-16
sorry...one last question (for the time being) :-)

after adding aliases to .bashrc I get this when the terminal first opens. Prompts for password and then

```

sudo: shopt: command not found

```

had a search and can't find why this is happening...only added aliases which work fine

---

### Post by SadisticCheeto on 2010-10-16
Edit the .bashrc to use shopt without sudo.

---

### Post by Hippytaff on 2010-10-16
I don't think it's set up to ask for sudo?

```

# append to the history file, don't overwrite it
shopt -s histappend

```

---

### Post by SadisticCheeto on 2010-10-16
What aliases were added in?

---

### Post by sisco311 on 2010-10-16
Are you sure?

What's the output of:
```
alias
```?

---

### Post by Hippytaff on 2010-10-16
```

# my aliases

# upgrade
alias upgd='sudo apt-get update && sudo apt-get upgrade'

#sudo
alias !='sudo'

#install
alias get='sudo apt-get install'

#uninstall
alias chuck='sudo apt-get remove'

```

---

### Post by Hippytaff on 2010-10-16
> **sisco311 said:**
> Are you sure?

What's the output of:
```
alias
```?

output

```

alias !='sudo'
alias alert='notify-send --urgency=low -i "$([ $? = 0 ] && echo terminal || echo error)" "$(history|tail -n1|sed -e '\''s/^\s*[0-9]\+\s*//;s/[;&|]\s*alert$//'\'')"'
alias chuck='sudo apt-get remove'
alias egrep='egrep --color=auto'
alias fgrep='fgrep --color=auto'
alias get='sudo apt-get install'
alias grep='grep --color=auto'
alias l='ls -CF'
alias la='ls -A'
alias ll='ls -alF'
alias ls='ls --color=auto'
alias upgd='sudo apt-get update && sudo apt-get upgrade'

```

---

### Post by SadisticCheeto on 2010-10-16
The problem is with alias !='sudo'. != is a comparison operator which means 'does not equal'. You should change that alias to something else.

---

### Post by Hippytaff on 2010-10-16
> **SadisticCheeto said:**
> The problem is with alias !='sudo'. != is a comparison operator which means 'does not equal'. You should change that alias to something else.

Excellent - Thankyou

---

### Post by sisco311 on 2010-10-16
> **SadisticCheeto said:**
> The problem is with alias !='sudo'. != is a comparison operator which means 'does not equal'. You should change that alias to something else.

Nope, that's a valid alias.

OP: Search the initialization & startup files for shopt:
```
grep shopt /etc/profile /etc/bash.bashrc ~/.bash_profile ~/.bashrc
```

---

### Post by SadisticCheeto on 2010-10-16
I put it in my own .bashrc and reproduced the error, so it was the problem either way.

---

### Post by Hippytaff on 2010-10-16
> **sisco311 said:**
> Nope, that's a valid alias.

OP: Search the initialization & startup files for shopt:
```
grep shopt /etc/profile /etc/bash.bashrc ~/.bash_profile ~/.bashrc
```

removing ! alias did work - heres the output for shopt

```

/etc/bash.bashrc:shopt -s checkwinsize
/etc/bash.bashrc:#if [ -f /etc/bash_completion ] && ! shopt -oq posix; then
grep: /home/hippytaff/.bash_profile: No such file or directory
/home/hippytaff/.bashrc:shopt -s histappend
/home/hippytaff/.bashrc:shopt -s checkwinsize
/home/hippytaff/.bashrc:if [ -f /etc/bash_completion ] && ! shopt -oq posix; then

```

---

### Post by sisco311 on 2010-10-16
> **SadisticCheeto said:**
> I put it in my own .bashrc and reproduced the error, so it was the problem either way.

Still, !='sudo' is a valid alias. =)

By default ~/.bashrc contains the following entry:
```
if [ -f /etc/bash_completion ] && ! shopt -oq posix; then
    . /etc/bash_completion
fi

```

If you put the alias before this entry, **! shopt -oq posix** is interpreted as **sudo shopt -oq posix**. 

In the above entry ! is used as a logical negation.
example:
```
[sisco@acme ~]$ shopt -oq posix
[sisco@acme ~]$ echo $?
1
[sisco@acme ~]$ ! shopt -oq posix
[sisco@acme ~]$ echo $?
0

```

---

### Post by Hippytaff on 2010-10-16
> **sisco311 said:**
> Still, !='sudo' is a valid alias. =)

By default ~/.bashrc contains the following entry:
```
if [ -f /etc/bash_completion ] && ! shopt -oq posix; then
    . /etc/bash_completion
fi

```If you put the alias before this entry, **! shopt -oq posix** is interpreted as **sudo shopt -oq posix**. 

In the above entry ! is used as a logical negation.
example:
```
[sisco@acme ~]$ shopt -oq posix
[sisco@acme ~]$ echo $?
1
[sisco@acme ~]$ ! shopt -oq posix
[sisco@acme ~]$ echo $?
0

```

ah..that makes sense...thanks for the explanation :-)

---

