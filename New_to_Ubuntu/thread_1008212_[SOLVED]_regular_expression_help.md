---
title: "[SOLVED] regular expression help"
date: 2008-12-11
forum: New to Ubuntu
---

### Post by uioreanu on 2008-12-11
Hello,

I am a beginner in what regular expressions are concerned. What I want is to replace a string into a html file with another string. The string to be replaced is here

[HTML]<td><a href="mailto:info@abc.net" class="topmenu">Email</a></td>[/HTML]

and it should be replaced with:

[HTML]<td><a href="contact.php" class="topmenu">Contact</a></td>[/HTML]

so basically the href and the link text should be changed. I have tried using sed, who I call using this syntax:

sed -e 's/string_to_replace/string_to_replace/g' file.html

Thing is that I'm stuck in the search for the proper regular expression. Can any of you regexp gurus help me?

Thanks!
Calin

---

### Post by karlr42 on 2008-12-11
Why have you marked the thread as solved?
I would use a perl script like:
```
#!/usr/bin/perl
my $replacement = "<td><a href=\"contact.php\"class=\"topmenu\">Contact</a></td>"
open(FILE, +>file.html) or die($!); #change to match your file
foreach(<FILE>){
       if(/mailto/){
             $_ =~ s/.*/$replacement/;
        }
}
close(FILE) or die($!);
```
Note I'm a bit rusty on perl, and there are probably much, much better ways of doing this.

---

### Post by rrashkin on 2008-12-11
or in Python:
```
f=open(<your filename>)
for s1 in f:
  if (s1.find("mailto:")>0 and s1.find("Email")>0):
     s1=s1.replace('mailto:info@abc.net','contact.php')
     s1=s1.replace('Email','Contact')
f.close()
```

---

### Post by glennric on 2008-12-11
Or in Bash:
```
#!/bin/bash
sed -i -e 's/<td><a href="mailto:info@abc\.net" class="topmenu">Email<\/a><\/td>/<td><a href="contact.php" class="topmenu">Contact<\/a><\/td>/' test.html
```

---

