---
title: "possible to use grub-md5-crypt in a script?"
date: 2009-01-18
forum: New to Ubuntu
---

### Post by ptn107 on 2009-01-18
I would like the script to take a users password as input (something like 'read -p "Password: " PASSWORD') and be able to pass it to 'grub-md5-crypt' to create the md5 hash that can then be inserted to /boot/grub/menu.lst  Is this possible?  I can't get it to work.

---

### Post by cshabazian on 2009-03-19
Two ways.  The easiest is to use openssl:

openssl passwd -1 $1

Otherwise, if you cat /sbin/grub-md5-crypt, you will see that it's simply a bash script that does the following:

# Run the grub shell.
$grub_shell --batch --device-map=/dev/null <<EOF \
    | grep "^Encrypted: " | sed 's/^Encrypted: //'
md5crypt
$password
quit
EOF

---

