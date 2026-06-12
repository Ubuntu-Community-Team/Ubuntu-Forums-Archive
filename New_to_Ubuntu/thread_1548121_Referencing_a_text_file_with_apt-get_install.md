---
title: "Referencing a text file with apt-get install"
date: 2010-08-07
forum: New to Ubuntu
---

### Post by zer010 on 2010-08-07
I have seen this somewhere, but I can't seem to find it anywhere. 
If I keep a list of apps to be installed in a text file, what is the format of the list (app1, app2 or app1 app2) and how do I reference to it when I use apt-get install....?
It would be a useful command to know, as well as helping me to understand more about using input/output at the CLI. Thanks!

---

### Post by Zeike on 2010-08-07
if you just put them into a file separated by spaces this works:

'cat package-list | xargs sudo apt-get install '

---

### Post by zer010 on 2010-08-07
Sorry, could you be a little more specific, or not so specific? What part of that is the "filename"?  What is xargs?

---

### Post by Zeike on 2010-08-07
> **zer010 said:**
> Sorry, could you be a little more specific, or not so specific? What part of that is the "filename"?  What is xargs?

'package-list' is the name of the file with the packages, separated by spaces:

like this:
```
irssi nmap ubuntu-desktop blah
```

xargs allows you to "build and execute command lines from standard input".  see 'man xargs'

Essentially what is happening here is:
'cat package-list': you're printing the contents of the file package-list to the standard output
' | ': this is a pipe, it sends the standard output from the previous command to the standard input of the next.
'xargs sudo apt-get install ': xargs takes the standard input, and adds it on to the following command (sudo apt-get install) as arguments.

So if your file looks like my example above, this command would be like typing 'sudo apt-get install irssi nmap ubuntu-desktop blah'

---

### Post by zer010 on 2010-08-07
Cool! Thanks very much! I never heard of xargs. To the manual, I go!

---

### Post by Using Debian on 2011-08-05
Excellent, just wanted to say thanks, I tried the same and "xargs" was the missing segment, worked liked a charm.

I also added "-y" to assume yes to all questions asked:

cat **[COLOR=Blue]list-of-packages[/COLOR]**.txt | xargs sudo apt-get install -y

Hope that helps someone to avoid confirming what they are **sure** they want to install

---

