---
title: "Ignoring case in table names"
date: 2011-04-18
forum: New to Ubuntu
---

### Post by atulmittal_mds on 2011-04-18
Hello All,


I m using ubuntu first time and i have some mysql scripts that i have to run with eclipse but issue that came in front of me is that the scripts were wriiten in windows and as now  i m using it with linux it says some of the tables not found just becuase of case sensitive..
so can anyone suggest me how to com over this issue without changing case-letters from scripts as it would consume a lot of time..



cheers
Atul

---

### Post by cavh on 2011-04-18
I think you should ask this question in a MySQL forum as it's a MySQL issue rather than a generic Ubuntu issue. The MySQL forums are at [http://forums.mysql.com/]("http://forums.mysql.com/").

If you do ask in a MySQL forum, please mark this thread as SOLVED.

---

### Post by rajanikaruturi on 2011-10-04
This depends on lower_case_table_names system variable in mysql.

```
mysql> SHOW GLOBAL VARIABLES LIKE 'lower_case_table_names';
```

If set to 0, table names are stored as specified and comparisons are case sensitive. If set to 1, table names are stored in lowercase on disk and comparisons are not case sensitive. If set to 2, table names are stored as given but compared in lowercase.

The default value is 0 on unix, 1 on windows and 2 on mac.


You can change this by specifying the option while starting mysqld  (--lower-case-table-names=2 )

more about it here 
[http://dev.mysql.com/doc/refman/5.0/en/server-system-variables.html#sysvar_lower_case_table_names](http://dev.mysql.com/doc/refman/5.0/en/server-system-variables.html#sysvar_lower_case_table_names)
[http://dev.mysql.com/doc/refman/5.0/en/identifier-case-sensitivity.html](http://dev.mysql.com/doc/refman/5.0/en/identifier-case-sensitivity.html)

---

