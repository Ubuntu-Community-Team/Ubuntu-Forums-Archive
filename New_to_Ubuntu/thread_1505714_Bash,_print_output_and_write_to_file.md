---
title: "Bash, print output and write to file?"
date: 2010-06-09
forum: New to Ubuntu
---

### Post by enternet21 on 2010-06-09
I have a question:

When I log in to bash, i have my .profile set up to print `fortune` before the prompt, just something I enjoy. However, i would like it if it would also print the same message to file, eg. "~/Documents/The Wisdom of Fortune.txt"

relevant lines of .profile:
     echo;fortune;echo

Is it possible to double the output?

Thanks.

---

### Post by Brandon Williams on 2010-06-09
```
echo
fortune | tee ~/Documents/The Wisdom of Fortune.txt
echo
```

The command tee sends stdin to both stdout and the specified file.

---

### Post by sisco311 on 2010-06-09
Hi and welcome to the forums!

Try someting like:
```
fortune | tee path/to/file
```
If you want to append the file:
```
fortune | tee -a path/to/file
```

To redirect the echo commands as well write a function:
```
function fort
{
  echo
  fortune
  echo
}

fort | tee path/to/file
```

---

### Post by enternet21 on 2010-06-09
Thanks to all of you, esp. for the quick replies.

This was exactly what I was looking for.

---

