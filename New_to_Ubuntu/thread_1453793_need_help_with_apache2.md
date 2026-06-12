---
title: "need help with apache2"
date: 2010-04-13
forum: New to Ubuntu
---

### Post by hvtino87 on 2010-04-13
i am having trouble getting my web page to display in apache2. all i am looking for is when i type in my ip address it displays my document and not the default. i made a little simple html in open office that has my name and was trying to replace it with the default but cant seem to get it to work. i have put my document in the /var/www folder and deleted the index.html so that mine was the only document there but it still does not display it.

---

### Post by undecim on 2010-04-13
When you go to view the document, does it give you a file list?

If so, you need to either rename the document to index.html or set the DirectoryIndex directive in apache2.conf

---

### Post by hvtino87 on 2010-04-13
worked like a charm. thanks

---

### Post by Iowan on 2010-04-13
Wow, that was quick...
[[SOLVED]]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")?

---

