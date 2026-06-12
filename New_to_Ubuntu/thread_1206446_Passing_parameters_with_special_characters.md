---
title: "Passing parameters with special characters?"
date: 2009-07-07
forum: New to Ubuntu
---

### Post by deleyd on 2009-07-07
What are the rules for passing parameters with special characters in them on the command line? Like what if your parameter has a space in it? When do you enclose a parameter in double quotes? How do you add a literal double quote to a parameter?

(I'm not even sure if this question makes sense since this is Linux, not Windows. All I know is on Linux the OS does the parsing then launches a new process handing it the individual parameters. Whereas on Windows the OS launches a new process, hands it the command line, and it's up to the new process to parse off the parameters from the command line, which means the compiler adds code to the executable to do the parsing, so the parsing rules depend on the compiler.)

---

### Post by nothingspecial on 2009-07-07
\ is the escape charcter in bash. Any character imediately after it is treated litterally and not as a special character.

See [[COLOR="Red"]here[/COLOR]]("http://www.network-theory.co.uk/docs/bashref/Quoting.html")

*******Sorry link started at wrong page - fixed now*******

---

### Post by Mornedhel on 2009-07-07
> **deleyd said:**
> What are the rules for passing parameters with special characters in them on the command line? Like what if your parameter has a space in it? When do you enclose a parameter in double quotes? How do you add a literal double quote to a parameter?

I suggest you read the bash man page, section "Quoting". I'd explain, but really the manual does it better than me.

> **deleyd said:**
> (I'm not even sure if this question makes sense since this is Linux, not Windows. All I know is on Linux the OS does the parsing then launches a new process handing it the individual parameters. Whereas on Windows the OS launches a new process, hands it the command line, and it's up to the new process to parse off the parameters from the command line, which means the compiler adds code to the executable to do the parsing, so the parsing rules depend on the compiler.)

You are almost correct. In Linux, your shell (defaults to bash) parses your command line, expanding what needs to be expanded (globs : *, ?, {}, and a few other funky things), and splitting it into words separated by spaces. (See "Quoting" to understand how to include spaces into parameters so that they are not interpreted as parameters separators. Filenames obtained through glob expansion have their spaces already escaped so you need not worry about that.)

Then it looks at the first word, assumes it's a command, and tries to launch it, passing it all the other words as arguments.

Then the command, if it actually exists, looks at its argument list and decides what to do with it. Many commands follow the GNU convention of arguments : long options (--like-this), short options (-l), the "standard input as if it were just another file" argument (-), and the "stop parsing arguments and assume the following are all filenames" argument (--). Many others do their own parsing instead of relying on GNU getopts, and some accept single letter options without any dashes at all.

But yes, overall the shell does a lot of work before handing the command its parameters.

---

