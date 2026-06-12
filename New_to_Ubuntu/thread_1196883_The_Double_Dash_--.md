---
title: "The Double Dash --"
date: 2009-06-25
forum: New to Ubuntu
---

### Post by GaretJax on 2009-06-25
I see lots of command lines that mix single dashes with double dashes.  This confuses me coming from a Windows environment.  What is significant about the double dash and how could I intuitively know when to use it in place of its smaller cousin?

---

### Post by Mornedhel on 2009-06-25
GNU-style options can traditionally be written in long style (--option) or short style (-o). This is a convention that not all programs enforce. Those that rely on getopt to parse their command line arguments do ; those that do their own parsing don't.

As a side note, - alone means "standard input" and -- alone means "the following are not to be considered options even if they look like it".

For instance, cat :

```
cat --show-tabs somefile
cat -T somefile
```

are equivalent.

```
cat -
```

expects standard input from keyboard instead of a file, and

```
cat -- -T
```

prints the contents of a file called -T, where cat -T would just wait for you to do something since it parses -T as an option instead of a file name.

Basically, use long options because they're easier to remember than short options, and use short options because they're faster to type than long options.

---

### Post by GaretJax on 2009-06-26
Interesting.  Okay I think that clears up some of the mess.  I will remember this as I go forward.  Thanks.

---

### Post by juanoleso on 2009-06-26
another thing is "--help" can be used with a lot of programs to have them output their options.  so for instance:

```

vlc --help

```

and then the man pages may also have more information when using CLI programs:

```

man vlc

```

---

### Post by Sealbhach on 2009-06-26
One command I have to use sometimes because I have 64-bit Ubuntu is:

sudo dpkg -i --force architecture name_of_package_1.0.deb

So the -i tells dpkg that I want it to install the .deb package, and the --force architecture tells it to ignore the fact that I dont have a 32-bit system.

So I sort of interpreted it as

-i    tells dpkg the action it I want it to perform
--force architecture    tells dpkg some more information it needs to perform the action (or I select this option from various options)

another command that's similar:

sudo dpkg -r --purge packagename

Please correct me if I have this all wrong...

---

### Post by Mornedhel on 2009-06-26
-i is the short version of --install, and -r is the short version of --remove. --purge can also be shortened to -P.

In many cases (at least when conforming to getopt style options) you can concatenate short options :

ls lists files ;
ls -l lists files with details ;
ls -a lists files including hidden files ;
ls -al and ls -la list files with details including hidden files.

---

