---
title: "using mySQL in the terminal - show results"
date: 2009-11-22
forum: New to Ubuntu
---

### Post by jingleheimer76 on 2009-11-22
I really tried to find this on my own . . . 

New to linux, new to using the terminal.

How do I display mySQL query results when using the terminal?

I log onto my server and open mySQL and my table without problems. Now I just need to be able to see some of my query results.

I type:

select * from [some_table_name]

it looks like the query executes but where do can I see all the good data?

---

### Post by cariboo on 2009-11-28
I'm not much of a mysql guru, but whe I run a query like yours I get the following result:

```
select * from pma_history
    -> ;
+----+----------+--------------------+-----------------+---------------------+---------------------------------+
| id | username | db                 | table           | timevalue           | sqlquery                        |
+----+----------+--------------------+-----------------+---------------------+---------------------------------+
|  1 | root     | mysql              | user            | 2009-11-22 22:47:52 | SELECT * FROM `user`            | 
|  2 | root     | information_schema | USER_PRIVILEGES | 2009-11-22 22:48:24 | SELECT * FROM `USER_PRIVILEGES` | 
|  3 | root     | information_schema | VIEWS           | 2009-11-22 22:48:34 | SELECT * FROM `VIEWS`           | 
|  4 | root     | phpmyadmin         | pma_pdf_pages   | 2009-11-22 22:48:49 | SELECT * FROM `pma_pdf_pages`   | 
+----+----------+--------------------+-----------------+---------------------+---------------------------------+
4 rows in set (0.01 sec)
```

---

### Post by gdonwallace on 2009-11-29
I use the MySQL front end gui from the repo's and it works like a charm.  You might try installing that.  Do a search in synaptic package manager for MySQL and it will show the app.  Once installed, point it to your MySQL database and you should be fine.

Not sure why it wont display anything for you.  That seems very odd.  The only thing I can think of is that the table was created in a windows environment.  But with my limited experience in doing those types of things, that seems like it should not be a problem.  As the table properties and layouts would be the same.

---

### Post by jingleheimer76 on 2009-11-29
Thanks you two. It was actually my failure to include the ";" at the end of my command. 

Let the mocking begin. I deserve it.

---

### Post by The Cog on 2009-11-29
If you're anything like me, you'll still forget the ; occasionally even years from now. But next time, and every time thereafter, you will know why you didn't get an answer. You'll still do it though.

---

