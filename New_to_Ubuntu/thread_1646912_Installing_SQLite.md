---
title: "Installing SQLite"
date: 2010-12-16
forum: New to Ubuntu
---

### Post by bohboh on 2010-12-16
I need to install sqlite so have been trying the following command on etchy.

sudo apt-get install php5-sqlite

I keep getting 404 errors from the repos in sources.list. It is a non standard sources.list setup by the hosting company. Firstly, how do i know which repos to add to my sources.list?

---

### Post by sanderd17 on 2010-12-16
etchy isn't supported anymore, the repo's for etchy are offline. You need to upgrade.

---

### Post by oldfred on 2010-12-16
Are you sure you do not have SQLite. It is part of python as standard now and Uubntu has to have python to run.

fred@fred-LucidDT:~$ whereis sqlite
sqlite: /usr/include/sqlite.h

---

### Post by bohboh on 2010-12-16
My bad, i just found out that I have in fact debian 4.0.
(this is a setup supplied to me and now i am being left in the dark a bit)
Am i right in saying that these forums wont be of any help as its ubuntu?
doing a whereis returns nothing.

---

