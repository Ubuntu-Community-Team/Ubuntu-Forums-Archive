---
title: "file deleting cron job question"
date: 2009-01-05
forum: New to Ubuntu
---

### Post by mishkin on 2009-01-05
first off server is debian etch with xfce4 and latest webmin

but i'm writing this on a ubuntu laptop and debian is simular so bear with me

I ran this once before and it did something odd (was on a different comp)

it seemed like it deleted the folders but didn't actually put the files outside the folders..... like to view it in gui it was in folders but to list in terminal rars were everywhere

It also didn't seem to decrease disk usage?

but soposidly this should work as a cron job (I can set it in webmin to run as root every  hour)

find /somefileplath/downloads/ -mtime +1 -type d -exec rm -rf {} \;   

so the above should delete all folders older than 1 day and all files within them permanently??

any suggestions ?

Oh one last thing is there a way to set it to say something like 14 hours old?

---

