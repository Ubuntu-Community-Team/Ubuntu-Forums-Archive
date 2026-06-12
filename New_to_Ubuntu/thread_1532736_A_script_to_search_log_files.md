---
title: "A script to search log files"
date: 2010-07-16
forum: New to Ubuntu
---

### Post by phillw on 2010-07-16
Hi,

I have a lot of text log files that I want to search for "key words" to give me the file it is in, as well as the the contents of that line from within the file.

I did write and have this working but for the life of me, I cannot find the script. It was along the lines of..

for i in `ls` ;do cat $i | grep "what Im looking for" | echo $i ;done

except 
[LIST]
[*]1. it worked
2. it gave me the file-name and the text that had been found
[/LIST]

I'm just having a really bad day :-(

Thanks,

Phill.

---

### Post by jtarin on 2010-07-16
[Grep is the answer...easy to learn.]("http://www.cyberciti.biz/faq/howto-use-grep-command-in-linux-unix/")

---

### Post by phillw on 2010-07-17
> **jtarin said:**
> [Grep is the answer...easy to learn.]("http://www.cyberciti.biz/faq/howto-use-grep-command-in-linux-unix/")

I don't doubt it is, just as getting a live web-site upto level 3 (AAA) certification for Accessiblilty is dead easy.

However that was not the question I asked, I'm fairly familiar with grep - I only asked if someone who knew it, would be kind enough to answer so I could help some one out with a problem with Lubuntu, PCManFM and Windows Samba connectivity. If you can answer that, there is no need to tell me how to check my log files.

Phill.

---

### Post by bodhi.zazen on 2010-07-17
One small tip - you do not need to pipe a file to grep

cat foo.txt | grep bar - bad habit

Just grep

grep bar foo.txt  - look ma, no cat =)

What is wrong with grep ?

```
grep sshd /var/log/auth*
```Well, first the output of that command is long.

But is seems to show what you are wanting.

Lots of stuff like this:

> /var/log/auth.log.1:Jul  9 08:06:12 ufbt sshd[1823]: Connection from 119.188.7.155 port 48338
/var/log/auth.log.1:Jul  9 08:06:12 ufbt sshd[1823]: Did not receive identification string from 119.188.7.155
/var/log/auth.log.1:Jul  9 08:11:18 ufbt sshd[1826]: Connection from 119.188.7.155 port 49992
/var/log/auth.log.1:Jul  9 08:11:28 ufbt sshd[1826]: Invalid user staff from 119.188.7.155But it shows the file name and line of text as requested.

---

### Post by phillw on 2010-07-17
Thanks boss.

:popcorn:

Regards,

Phill.

---

### Post by bodhi.zazen on 2010-07-17
> **phillw said:**
> Thanks boss.

:popcorn:

Regards,

Phill.

LOL - you are most welcome.

---

### Post by jtarin on 2010-07-17
> **phillw said:**
> I don't doubt it is, just as getting a live web-site upto level 3 (AAA) certification for Accessiblilty is dead easy.

However that was not the question I asked, I'm fairly familiar with grep - I only asked if someone who knew it, would be kind enough to answer so I could help some one out with a problem with Lubuntu, PCManFM and Windows Samba connectivity. If you can answer that, there is no need to tell me how to check my log files.

Phill.I see....excuse my redundant behavior.I apologize for not giving you exactly what you needed when you wanted it.

---

