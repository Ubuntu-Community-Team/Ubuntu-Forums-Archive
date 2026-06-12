---
title: "Script question"
date: 2010-07-11
forum: New to Ubuntu
---

### Post by mike628 on 2010-07-11
This works:
[/] # cd ./mnt/ext/opt/mysql/bin
[/mnt/ext/opt/mysql/bin] # ./mysql -u root -padmin
 
The script:
[~] # cat ./Mysql
cd /mnt/ext/opt/mysql/bin
./mysql -u root -padmin
 
When I run it I get a permission denied, even if I comment the ./mysql ....

---

### Post by john newbuntu on 2010-07-11
One small thing I notice is "cd ./mnt" vs "cd /mnt".  Check that first.
The next is to have the executable bit set on the Mysql script (chmod 755 ./Mysql).

---

### Post by mike628 on 2010-07-11
Nice!! Thanks

---

