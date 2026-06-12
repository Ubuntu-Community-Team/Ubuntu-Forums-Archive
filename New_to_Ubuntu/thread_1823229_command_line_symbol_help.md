---
title: "command line symbol help"
date: 2011-08-11
forum: New to Ubuntu
---

### Post by twistedrealm on 2011-08-11
hey guys, im new here. i just installed Ubuntu and i love it. However i still have a lot to learn. I was hoping somebody could explain to me what certain symbols mean in the terminal

like in: 
[SIZE=-1]find / -perm +6000 -type f`; do ls -aFl **$i** >> suids; done [/SIZE]

and 
[FONT=monospace]
[/FONT]find / -local -type f \( -perm -4000 -o -perm -2000 \) -exec ls -ld '{}' \**;**


I've also seen the and (&&) sign. what does this all mean? especially the forward slash \, the &&, '{}' \**; and $**

i know that >> means output to a file, so i assume << is read from a file correct?

thanks any help is welcome.

---

### Post by Johnb0y on 2011-08-11
could try:
[http://www.tuxfiles.org/linuxhelp/shell.html](http://www.tuxfiles.org/linuxhelp/shell.html)

[http://en.wikibooks.org/wiki/Linux_For_Newbies/Command_Line](http://en.wikibooks.org/wiki/Linux_For_Newbies/Command_Line)

p.s. bit "winded" but : [http://tldp.org/HOWTO/Text-Terminal-HOWTO.html](http://tldp.org/HOWTO/Text-Terminal-HOWTO.html)

---

### Post by zealibib slaughter on 2011-08-11
have a look at linuxcommand.org

---

### Post by AlphaLexman on 2011-08-11
> **twistedrealm said:**
> find / -perm +6000 -type f`; do ls -aFl **$i** >> suids; done 

and 
find / -local -type f \( -perm -4000 -o -perm -2000 \) -exec ls -ld '{}' \**;**
```
The '**$i**' is a variable name,
the '**;**'  is a command separator,
the '**\**'  escapes the next character,
the '**&&**' is a literal 'this **and** that' construct.
```

---

### Post by twistedrealm on 2011-08-11
> **AlphaLexman said:**
> ```
The '**$i**' is a variable name,
the '**;**'  is a command separator,
the '**\**'  escapes the next character,
the '**&&**' is a literal 'this **and** that' construct.
```


thanks for the help guys, ill check out those links

quick question, if \ escapes the next character, then why use brackets at all in this instance:
find / -local -type f \( -perm -4000 -o -perm -2000 \) -exec ls -ld '{}' \[B];

[/B] wouldnt "find / -local -type f -perm -4000 -o -2000 -exec ls -ld '{}' \**;** " achieve the same result since the \ is canceling out both brackets? 

and why put the ; at the end, if there is no other commands on the same line? its almost like people are deliberately trying to confuse noobs.

---

### Post by AlphaLexman on 2011-08-11
> **twistedrealm said:**
> quick question, if \ escapes the next character, then why use brackets at all in this instance:
find / -local -type f \( -perm -4000 -o -perm -2000 \) -exec ls -ld '{}' \[B];

[/B] wouldnt "find / -local -type f -perm -4000 -o -2000 -exec ls -ld '{}' \**;** " achieve the same result since the \ is canceling out both brackets? 

and why put the ; at the end, if there is no other commands on the same line?
They all have a purpose... escaping a character is NOT deleting it, but giving it a different meaning, the '-exec' option needs to separate each result of find, so it needs the ';'

---

### Post by cgroza on 2011-08-11
Going through a bash tutorial should answer all those questions. It really does not hurt knowing a little bash, helps automating your tasks a little.

---

