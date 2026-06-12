---
title: "add words to gedit syntax highlighting"
date: 2009-02-07
forum: New to Ubuntu
---

### Post by edpatterson on 2009-02-07
I can not find were to add reserved words to gedit. Specifically I am trying to add function names from php5.

---

### Post by jgoguen on 2009-02-07
Take a look at this post ([http://ubuntuforums.org/showpost.php?p=5426000&postcount=4](http://ubuntuforums.org/showpost.php?p=5426000&postcount=4)) and see if that helps you any.  And don't hesitate to come back if you have any other questions or if that's not clear enough :)

---

### Post by Tim Sharitt on 2009-02-07
If you want to add a new keyword for a certain language, you will need to edit the .lang file for the language in /usr/share/gtksourceview-2.0/language-specs. For php it would be /usr/share/gtksourceview-2.0/language-specs/php.lang.

---

### Post by edpatterson on 2009-02-07
> If you receive a satisfactory answerer to your question, please mark your thread solved under Thread Tools.
I must be thick, there is no 'mark as solved' under thread tools. I know it is possible since I have seen many, many threads marked [SOLVED]. I just do not know how to do it properly.

---

### Post by edpatterson on 2009-02-07
> **jgoguen said:**
> Take a look at this post ([http://ubuntuforums.org/showpost.php?p=5426000&postcount=4](http://ubuntuforums.org/showpost.php?p=5426000&postcount=4)) and see if that helps you any.  And don't hesitate to come back if you have any other questions or if that's not clear enough :)

I found the file, thanks. I was hoping for an include() kind of thing. I want to all all of various mysql|i|p statements/commands/functions tot he list. I find the colors really help with my poor typing skills.

Ed

---

### Post by jgoguen on 2009-02-07
It's not you, that's currently disabled :(

---

