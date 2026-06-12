---
title: "Auto complete using Alias?"
date: 2009-07-20
forum: New to Ubuntu
---

### Post by slughappy1 on 2009-07-20
I was wondering if there is a way to have the TAB auto complete to work using an Alias? I like to use the terminal to install programs, but I don't want to have to type in 'sudo apt-get install ' every time. I know, I know. I'm lazy. I want to be able to type 'gets' or 'canhaz'. I already have alias working perfectly. I just want to have the auto complete that 'sudo apt-get install ' has.

Does that make sense?

---

### Post by Cypher on 2009-07-21
You can alias "sudo apt-get install", so in the terminal try:
```

$ alias gets="sudo apt-get install"
$ gets <package>

```
This should run the command to grab <package>. If this works, then copy the alias line above into your ~/.bash_aliases file.

---

### Post by slughappy1 on 2009-07-21
Well I know that this works```
alias gets="sudo apt-get install"

```
But it didn't do anything when I created the file ~/.bash_aliases. After reboot it says ```
bash: gets: command not found
```

Lets say I wanted to install 3dchess. I also wanted to know if there was a way to type in ```
gets 3dch[TAB]
``` and have it auto complete the package name.

---

### Post by bacardiandwatermelon on 2009-07-21
Can't you just put it in your .bashrc file?

---

### Post by slughappy1 on 2009-07-21
Yes I could just put it in .bashrc. I figured out why the .bash_aliases wasn't working. In .bashrc I had to change 
```
#if [ -f ~/.bash_aliases ]; then
#    . ~/.bash_aliases
#fi
``` to 
```
if [ -f ~/.bash_aliases ]; then
    . ~/.bash_aliases
fi
```

Now it works perfectly on every boot. 

But I am guessing since nobody has answered the other part of my question, that it is not possible to get the [TAB] auto-completion to work with it?

---

### Post by bostonaholic on 2009-07-21
> **slughappy1 said:**
> I was wondering if there is a way to have the TAB auto complete to work using an Alias? I like to use the terminal to install programs, but I don't want to have to type in 'sudo apt-get install ' every time. I know, I know. I'm lazy. I want to be able to type 'gets' or 'canhaz'. I already have alias working perfectly. I just want to have the auto complete that 'sudo apt-get install ' has.

Does that make sense?

I understand your question completely and it bugs me that I haven't found a solution yet either.  I use an alias for update/upgrade but not for install for this reason.

---

### Post by SuperSonic4 on 2009-07-21
```
if [ -f /etc/bash_completion ]; then
 . /etc/bash_completion
fi
```

I googled a code and found something about it here: [http://embraceubuntu.com/2006/01/28/turn-on-bash-smart-completion/](http://embraceubuntu.com/2006/01/28/turn-on-bash-smart-completion/)

---

### Post by sisco311 on 2009-07-21
> **slughappy1 said:**
> 
But I am guessing since nobody has answered the other part of my question, that it is not possible to get the [TAB] auto-completion to work with it?

add this to the ~/.bash_completion file:
```
_canhaz()
{
  cur=`_get_cword`
  COMPREPLY=( $( apt-cache pkgnames $cur 2> /dev/null ) )
  return 0
  
} &&
complete -F _canhaz $filenames **canhaz**

```

EDIT:
log out from bash and log back in.

EDIT2: 
replace **canhaz** with your 'apt-get install' alias.

---

### Post by bostonaholic on 2009-07-21
> **SuperSonic4 said:**
> ```
if [ -f /etc/bash_completion ]; then
 . /etc/bash_completion
fi
```

I googled a code and found something about it here: [http://embraceubuntu.com/2006/01/28/turn-on-bash-smart-completion/](http://embraceubuntu.com/2006/01/28/turn-on-bash-smart-completion/)

That doesn't work for aliases.

---

### Post by Kangarooo on 2010-12-05
> **sisco311 said:**
> add this to the ~/.bash_completion file:
```
_canhaz()
{
  cur=`_get_cword`
  COMPREPLY=( $( apt-cache pkgnames $cur 2> /dev/null ) )
  return 0
  
} &&
complete -F _canhaz $filenames **canhaz**

```

EDIT:
log out from bash and log back in.

EDIT2: 
replace **canhaz** with your 'apt-get install' alias.
Doesnt work.. It autocompletley adds filenames but not programmnames from database of repos

---

### Post by strid3r on 2012-12-19
Thanks!

---

### Post by oldos2er on 2012-12-19
Old thread closed.

---

