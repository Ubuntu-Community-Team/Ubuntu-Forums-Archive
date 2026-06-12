---
title: "Shell commmand options"
date: 2009-09-27
forum: New to Ubuntu
---

### Post by SteelCore on 2009-09-27
I noticed that the options after Shell commands come with either one or two dashes.  I also read somewhere that 2 dashes are only for GNU not Bash commands. Is there a difference between them? any links that could explain the issue further?
Thanx

---

### Post by zeroseven0183 on 2009-09-27
I noticed that also.

Single-dash as a prefix supports only single-character options.
Double-dash is or the long option name.

Here are some sites I've found:
[http://www.manpagez.com/man/1/getopt/](http://www.manpagez.com/man/1/getopt/)
[http://stackoverflow.com/questions/402377/using-getopts-in-bash-shell-script-to-get-long-and-short-command-line-options](http://stackoverflow.com/questions/402377/using-getopts-in-bash-shell-script-to-get-long-and-short-command-line-options)


Still learning shell commands at [http://linuxcommand.org](http://linuxcommand.org)

---

### Post by mcduck on 2009-09-27
Single dash is used for shorthand version of the option, while double dash is for the long version.

For example, "dpkg --install *package*" versus "dpkg -i *package*".

Note that when using the short options you can still combine many options together, like "ls -al" to list all files in current directory using the long list format. If you use long optiosn you need to use each one separately.

(And  don't know what article you might have read, but either you or the author have misunderstood something.. There is no such thing as "GNU commands", and the syntax is part of the POSIX standard and also the standard used by GNU project.)

---

### Post by SteelCore on 2009-09-27
I'm actually reading "Introduction to Linux" by Machtelt Garrels. Obviously I misunderstood the material on p. 22 of the last edition (1.27), section 2.2.2 General remarks. But I must say that I didn't find the wording as clear as I did with your (mcduck) answer. Thanks for the help.

---

