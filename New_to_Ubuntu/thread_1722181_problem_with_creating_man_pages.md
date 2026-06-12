---
title: "problem with creating man pages"
date: 2011-04-05
forum: New to Ubuntu
---

### Post by ardent on 2011-04-05
So I wanted to created a manual page for my qt program, and I followed this tutorial:
[http://linux.omnipotent.net/article.php?article_id=12493&page=2](http://linux.omnipotent.net/article.php?article_id=12493&page=2)

Basically it said the general steps to take:
1. Use VI editor to create the man page with the proper formatting.
2. Use the "Groff -Tascii -man _file_.1" command 
3. Make a backup and compress the file
4. Put the compressed man page in the /usr/share/man/man1 dir

So I did all of that, and got the " man myprogram" to work. But it still has the .PP, .B, and .I options showing on the page. See attached.

How do I get rid of them from showing up? And for that matter, the formatting doesn't seem to consistently work (e.g .B doesn't bold only the immediate word after).

Should I give up all hope?:confused:

---

