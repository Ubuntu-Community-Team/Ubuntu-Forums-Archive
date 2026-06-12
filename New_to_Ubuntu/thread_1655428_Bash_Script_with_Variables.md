---
title: "Bash Script with Variables?"
date: 2010-12-29
forum: New to Ubuntu
---

### Post by Chrissd on 2010-12-29
Hi all,

Can someone tell me if it's possible to create a bash script with variables?

What I'd like it to do is: encrypt a varible file (gpg -c filename) then delete the file I've just encrypted (shred -u filename)

---

### Post by bluefrog on 2010-12-29
add a function to .bashrc for example

function encrypt ()
{
gpg -c $1
rm $1
}


save and exit any terminal you have running.
launch a terminal and run

encrypt path/of/file/filename

---

### Post by Chrissd on 2010-12-29
That's even better than what I had planned!

Thanks very much!

---

