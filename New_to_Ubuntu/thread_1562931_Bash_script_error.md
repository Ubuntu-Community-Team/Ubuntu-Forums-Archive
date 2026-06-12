---
title: "Bash script error"
date: 2010-08-28
forum: New to Ubuntu
---

### Post by gzipper on 2010-08-28
Hello.
Setting up a Mantis/Svn environment. Trying to make Mantis to talk to svn with a script. Im getting a 
```
./post-commit: 62: Syntax error: redirection unexpected

```
error
post-commit looks like 
```

#!/bin/bash
---snip---
REPOS="$1"
REV="$2"
svnlook=/usr/bin/svnlook
auth=$($svnlook author -r $REV $REPOS)
dt=$($svnlook date -r $REV $REPOS)
changed=$($svnlook changed -r $REV $REPOS)
log=$($svnlook log -r $REV $REPOS)
n=$'\n'
echo "Running /usr/bin/php -q /var/www/mantis/scripts/checkin.php <<< Changeset [${REV}] by $auth, $dt$n$log$n$changed"
/usr/bin/php -q /var/www/mantis/scripts/checkin.php <<< "echo -e Changeset [${REV}] by $auth, $dt$n$log$n$changed"

```
Bash version is
```
GNU bash, version 4.1.5(1)-release (i486-pc-linux-gnu)

```
What's wrong with the
```
/usr/bin/php -q /var/www/mantis/scripts/checkin.php <<< "echo -e Changeset [${REV}] by $auth, $dt$n$log$n$changed"
```
line?

---

### Post by Spice Weasel on 2010-08-28
Shouldn't it be:

> 
echo -e "Changeset [${REV}] by $auth, $dt$n$log$n$changed"


?

---

### Post by gzipper on 2010-08-28
Thanks for the reply.
Originally it was:
```
/usr/bin/php -q /var/www/mantis/scripts/checkin.php <<< "Changeset [${REV}] by $auth, $dt$n$log$n$changed"
```

echo -e inside or outside the "" didn't matter.
It's supposed to work. Got it from a guide.

---

### Post by AlphaLexman on 2010-08-28
I don't know anything about it, but I think you should do some homework on the 'changeset' command. :cool:

---

