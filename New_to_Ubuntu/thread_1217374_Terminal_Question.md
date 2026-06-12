---
title: "Terminal Question"
date: 2009-07-19
forum: New to Ubuntu
---

### Post by /usr/sbin on 2009-07-19
I have been playing around with the termin using the alias command but when i close the terminal the alias commands are not remembered. I heard somewhere about saving them in a text file. Is this possible? 

Thanks Adam

---

### Post by m_duck on 2009-07-19
In your home folder you can put your aliases in the .bashrc hidden file. I think you can put them in another file and refer to that file from .bashrc but I cannot remember how. Once you have added an alias to .bashrc, to make it work in the current session, you will need to execute the following```
source .bashrc
```

---

### Post by /usr/sbin on 2009-07-19
Thanks, what code would i use to put them in the file. I cannot remeber the exact command for alias.

---

### Post by m_duck on 2009-07-19
To open the file for editing, either use```
nano ~/.bashrc
```or```
gedit ~/.bashrc
```For cli editing/gui editing respectively. Within the file, aliases take the following format```
alias nameofalias='command to execute'
```So to have the word *update* execute *sudo apt-get update* the alias would be```
alias update='sudo apt-get update'
```

---

### Post by /usr/sbin on 2009-07-19
Thank you m_duck

---

