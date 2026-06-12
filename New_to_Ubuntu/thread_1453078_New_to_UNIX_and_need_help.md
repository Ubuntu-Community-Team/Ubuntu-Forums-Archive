---
title: "New to UNIX and need help"
date: 2010-04-12
forum: New to Ubuntu
---

### Post by quista345 on 2010-04-12
[COLOR=#231F20][FONT=Arial]What is the difference between the following commands[/FONT][/COLOR]
  **[COLOR=#231F20][FONT=Arial] [/FONT][/COLOR]**
  **[COLOR=#231F20][FONT=Arial]$ [/FONT][/COLOR]**[COLOR=#231F20][FONT=Arial]cat xyz[12] **$ **cat xyz[1-2][/FONT][/COLOR][COLOR=black][FONT=Arial][/FONT][/COLOR]

---

### Post by WinterRain on 2010-04-12
Just as a heads up, this is a linux forum, not unix. There are similarities, but they are different. Enjoy.

---

### Post by Iowan on 2010-04-12
[http://tldp.org/LDP/abs/html/x16775.html](http://tldp.org/LDP/abs/html/x16775.html)
See the section on "brackets".

---

### Post by mellort on 2010-04-12
Hey quista345,

The bracket notation is part of a regular expression. Essentially, when you put anything inside [], something 'matches' that expression if it contains any of the elements inside the [].

The discrepancy between [1-2] and [12] is just syntax. For regular expressions, you can write [1-5] for [12345], and similarly for any two numbers. Similarly, you can write [a-c] for [abc].

Examples:

```
$ echo "hello" | grep [a-b]
$ echo "hello" | grep [a-e]
hello
$ echo "1234" | grep [0]
$ echo "1234" | grep [1-2]
1234
$ echo "1234" | grep [12]
1234
```

Here, I am using the command `echo`, which just prints the string you give it, and I am piping the result into a `grep`, which searches the input for the given regular expression, and prints out the lines which match the input. So in the case of matching "hello" to [a-b], there isn't any output because it doesn't match. For matching "hello" to [a-e], there is output because "hello" has an 'e' in it.

For more information, see [this link.]("http://www.panix.com/~elflord/unix/grep.html")

Cheers

---

