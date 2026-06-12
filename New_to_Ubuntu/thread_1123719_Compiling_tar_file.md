---
title: "Compiling tar file"
date: 2009-04-12
forum: New to Ubuntu
---

### Post by pitchdiesel on 2009-04-12
I'm trying to compile a tar file and here's my output:

g++ -I./src/ -c src/config.cpp -o obj/config.o -O3 -DDATABASE_MYSQL -DDATABASE_SQLITE -I"/usr/include/mysql/"
g++ -I./src/ -c src/database.cpp -o obj/database.o -O3 -DDATABASE_MYSQL -DDATABASE_SQLITE -I"/usr/include/mysql/"
In file included from src/database.cpp:2:
src/database.hpp:11:19: error: mysql.h: No such file or directory
src/database.hpp:14:21: error: sqlite3.h: No such file or directory
In file included from src/database.hpp:10,
                 from src/database.cpp:2:
src/socket.hpp: In member function ‘void Server< <template-parameter-1-1> >::Bind(IPAddress, uint16_t)’:
src/socket.hpp:354: error: there are no arguments to ‘memset’ that depend on a template parameter, so a declaration of ‘memset’ must be available
src/socket.hpp:354: error: (if you use ‘-fpermissive’, G++ will accept your code, but allowing the use of an undeclared name is deprecated)
In file included from src/database.cpp:2:
src/database.hpp: At global scope:
src/database.hpp:107: error: ISO C++ forbids declaration of ‘MYSQL’ with no type
src/database.hpp:107: error: expected ‘;’ before ‘*’ token
src/database.hpp:110: error: ISO C++ forbids declaration of ‘sqlite3’ with no type
src/database.hpp:110: error: expected ‘;’ before ‘*’ token
src/database.cpp: In member function ‘void Database::Connect(Database::Engine, std::string, std::string, std::string, std::string)’:
src/database.cpp:73: error: ‘class Database’ has no member named ‘mysql_handle’
src/database.cpp:73: error: ‘mysql_init’ was not declared in this scope
src/database.cpp:75: error: ‘class Database’ has no member named ‘mysql_handle’
src/database.cpp:75: error: ‘mysql_error’ was not declared in this scope
src/database.cpp:77: error: ‘class Database’ has no member named ‘mysql_handle’
src/database.cpp:77: error: ‘mysql_real_connect’ was not declared in this scope
src/database.cpp:77: error: ‘class Database’ has no member named ‘mysql_handle’
src/database.cpp:79: error: ‘class Database’ has no member named ‘mysql_handle’
src/database.cpp:79: error: ‘mysql_error’ was not declared in this scope
src/database.cpp:81: error: ‘class Database’ has no member named ‘mysql_handle’
src/database.cpp:81: error: ‘mysql_select_db’ was not declared in this scope
src/database.cpp:83: error: ‘class Database’ has no member named ‘mysql_handle’
src/database.cpp:83: error: ‘mysql_error’ was not declared in this scope
src/database.cpp:90: error: ‘class Database’ has no member named ‘sqlite_handle’
src/database.cpp:90: error: ‘sqlite3_open’ was not declared in this scope
src/database.cpp:90: error: ‘SQLITE_OK’ was not declared in this scope
src/database.cpp: In member function ‘Database_Result Database::Query(const char*, ...)’:
src/database.cpp:128: error: ‘class Database’ has no member named ‘mysql_handle’
src/database.cpp:128: error: ‘mysql_real_escape_string’ was not declared in this scope
src/database.cpp:136: error: ‘sqlite3_mprintf’ was not declared in this scope
src/database.cpp:138: error: ‘sqlite3_free’ was not declared in this scope
src/database.cpp:157: error: ‘MYSQL_RES’ was not declared in this scope
src/database.cpp:157: error: ‘mresult’ was not declared in this scope
src/database.cpp:158: error: ‘MYSQL_FIELD’ was not declared in this scope
src/database.cpp:158: error: ‘fields’ was not declared in this scope
src/database.cpp:161: error: ‘class Database’ has no member named ‘mysql_handle’
src/database.cpp:161: error: ‘mysql_real_query’ was not declared in this scope
src/database.cpp:163: error: ‘class Database’ has no member named ‘mysql_handle’
src/database.cpp:163: error: ‘mysql_error’ was not declared in this scope
src/database.cpp:166: error: ‘class Database’ has no member named ‘mysql_handle’
src/database.cpp:166: error: ‘mysql_field_count’ was not declared in this scope
src/database.cpp:168: error: ‘class Database’ has no member named ‘mysql_handle’
src/database.cpp:168: error: ‘mysql_store_result’ was not declared in this scope
src/database.cpp:172: error: ‘class Database’ has no member named ‘mysql_handle’
src/database.cpp:172: error: ‘mysql_affected_rows’ was not declared in this scope
src/database.cpp:177: error: ‘class Database’ has no member named ‘mysql_handle’
src/database.cpp:177: error: ‘mysql_error’ was not declared in this scope
src/database.cpp:181: error: ‘mysql_fetch_fields’ was not declared in this scope
src/database.cpp:183: error: ‘MYSQL_ROW’ was not declared in this scope
src/database.cpp:183: error: expected `;' before ‘row’
src/database.cpp:183: error: ‘row’ was not declared in this scope
src/database.cpp:183: error: ‘mysql_fetch_row’ was not declared in this scope
src/database.cpp:189: error: ‘IS_NUM’ was not declared in this scope
src/database.cpp:216: error: ‘mysql_free_result’ was not declared in this scope
src/database.cpp:223: error: ‘class Database’ has no member named ‘sqlite_handle’
src/database.cpp:223: error: ‘sqlite3_exec’ was not declared in this scope
src/database.cpp:223: error: ‘SQLITE_OK’ was not declared in this scope
src/database.cpp:225: error: ‘class Database’ has no member named ‘sqlite_handle’
src/database.cpp:225: error: ‘sqlite3_errmsg’ was not declared in this scope
make: *** [obj/database.o] Error 1


Not all that great at this stuff so I'm a little lost... Any help is greatly appreciated!

---

### Post by benj1 on 2009-04-12
have you extracted the tar file?

```
tar -xf file.tar
```

---

### Post by lavinog on 2009-04-12
What command did you use to compile?

---

### Post by llamabr on 2009-04-12
A .tar file isn't something you typically compile.

What is this file for, what's it called, and what did you do to it?

---

