---
title: "'&gt;' symbol at Terminal"
date: 2011-08-14
forum: New to Ubuntu
---

### Post by avnd on 2011-08-14
Hello!

Quite a number of times, I follow instructions to do something in  Linux. These instructions often involve using the terminal.

More than once, when I type some command that was instructed (I don't remember the commands exactly) I end up with the terminal showing a new line beginning with '>' ('greater than' symbol) and the cursor blinking right next to it. It's not the usual 'user@machine:' prompt. 

I would like to know what that means. I don't mind a link explaining it. I read a few pages about the terminal for beginners but none of them explain it.

I would also like to know the proper way to get out of it.

Thanks!

---

### Post by mcduck on 2011-08-14
That's indicating that whatever command you typed wasn't complete, and it's still waiting for you to type the rest of it.

Most likely that would be a result from mistyping the command you tried to run, or perhaps following instructions from a web site with a layout that splits long commands into several lines (while you should of course type a single command into a single line on a terminal).

You can just finish whatever command you were trying to run and press enter to complete it, or hit Ctrl-C to cancel everything and return back to the command prompt.

---

### Post by AlphaLexman on 2011-08-14
> **avnd said:**
> It's not the usual 'user@machine:' prompt. 

I would like to know what that means.
Your USUAL _primary_ prompt is a variable named '**$PS1**'
Your _secondary_ prompt is named '**$PS2**' and it's default setting is the '**>**' character.

As stated above it really just means the command interpreter is waiting for a required closing statement to a command.

An example would be...
```
if [ $a = b ]; then
    echo 'a equals b'
[COLOR="Red"]fi[/COLOR]
```
The '[COLOR="red"]fi[/COLOR]' is the closing statement.

---

### Post by avnd on 2011-08-14
@ McDuck & AlphaLexman: Thank you for your replies.

---

