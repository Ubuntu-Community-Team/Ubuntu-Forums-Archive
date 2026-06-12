---
title: "CLI Help- Adding a line to the top of every file"
date: 2009-10-21
forum: New to Ubuntu
---

### Post by Warpnow on 2009-10-21
I need to add #!/usr/local/bin/php to the top of every php file and #!/usr/local/bin/perl to the top of every perl file...there are, however, hundreds of files...

Anyone know how I can do this via the command line? I know its possible, just can't seem to figure out how.

---

### Post by diesch on 2009-10-21
```
find . -name \*.php -exec  sed -i -e'1i#!/usr/local/bin/php' "{}"  \;
```

---

### Post by Bachstelze on 2009-10-21
```
for i in *.php; do mv $i $i.orig; echo "#!/usr/local/bin/php" > $i; cat $i.orig >> $i; rm $i.orig; done
```

---

