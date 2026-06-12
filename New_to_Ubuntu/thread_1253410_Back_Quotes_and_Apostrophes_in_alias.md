---
title: "Back Quotes and Apostrophes in alias"
date: 2009-08-30
forum: New to Ubuntu
---

### Post by ner on 2009-08-30
I have added the following line to my .bash_aliases

```
alias enter_last_dir='cd `ls -ltr | grep ^d | tail -1 | gawk -F" "  '{print $8}'`'
```

that line is supposed to enter the last modified directory. It is working well when only this part is used: 
```
cd `ls -ltr | grep ^d | tail -1 | gawk -F" "  '{print $8}'`
```

With the alias however it results in the following error message each time I open bash, "bash: alias: }`: not found"

This has something to do with the back quotes and apostrophes used there. I tried several combinations, but couldn't figure out the correct way to do this

---

### Post by DaithiF on 2009-08-30
alias enter_last_dir=**[COLOR=Red]'[/COLOR]**cd `ls -ltr | grep ^d | tail -1 | gawk -F" " **[COLOR=Red] '[/COLOR]**{print $8}'`'

the opening and closing quotes to the alias command are the ones highlighted in red above -- leaving the {print $8}'`' part hanging off the end giving an error.
this would work:
```
alias enter_last_dir="cd `ls -ltr | grep ^d | tail -1 | awk -F ' ' '{print $8}'`"
```**BUT**, i'm not sure this is what you really want :)
This will execute the ls -ltr command at the time the alias is being defined.  If you inspect the alias you have created after the fact it will look something like:
alias enter_last_dir='cd tmp'  or some such, where tmp was the most recently modified subdirectory to the one you were in when you defined the alias.

If you then run the alias in any other directory you'll just get an error because there is likely no tmp (or whatever) subdirectory there.

what you really want is a bash function which will run the ls command each time you invoke the function, so something like:
```
function enter_last_dir() {
   cd $(ls -ltr | grep ^d | tail -1 | awk '{print $8}')
}

```hope this helps
d

---

### Post by ner on 2009-08-30
Great,

 thanks a lot!

---

