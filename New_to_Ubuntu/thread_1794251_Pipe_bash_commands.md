---
title: "Pipe bash commands"
date: 2011-06-30
forum: New to Ubuntu
---

### Post by H3110! on 2011-06-30
Hey guys,

I have a SQL script which is creating 2 databases, and 1 user and all necessary privileges (using GRANT).

I then have a bash script ./add_db -n <name> -p <prefix> which will do some processing and then at the end I wish to replace some strings within the SQL document, then execute it.

```
CMD="cat ${SH_DIR_SRC}sql.add_db | sed s/__HOST__/${DOMAIN_HOST}/g | sed s/__PFX__/${PREFIX}/g | sed s/__PWD__/${PASSWORD}/g"
eval ${CMD}

CMD="mysql -usqladm -p'**' < ${SH_DIR_SRC}sql.add_db"
eval ${CMD}
```

The last 2 lines do not process correctly (obviously since the values are not correctly replaced) How can this be done?

Thanks!

---

### Post by TeoBigusGeekus on 2011-06-30
Can you give us an error message to see where the expansion fails?

---

### Post by H3110! on 2011-06-30
I've solved the problem now, by using a temp file! Why I overlooked this was beyond me.

```
echo "Starting installation..."
cat ${SH_DIR_SRC}sql.add_db | sed s/__HOST__/${DATABASE}/g | sed s/__PFX__/${PREFIX}/g | sed s/__PWD__/${PASSWORD}/g > /tmp/${DATABASE}.sql.tmp

echo "Installing databases..."
mysql -uroot -p'**' < /tmp/${DATABASE}.sql.tmp

echo "Clearing temporary files..."
rm -fr /tmp/${DATABASE}.sql.tmp
```

However there is a little issue, using "mysql -uroot -p'**' < /tmp/${DATABASE}.sql.tmp"  How do i kill this connection afterwards?

---

