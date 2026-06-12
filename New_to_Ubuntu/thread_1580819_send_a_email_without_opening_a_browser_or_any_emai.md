---
title: "send a email without opening a browser or any email client"
date: 2010-09-23
forum: New to Ubuntu
---

### Post by vj.patcher on 2010-09-23
[COLOR=#000000][FONT=Times New Roman][FONT=arial]how to send a email without opening a browser or any email client.
[/FONT][/FONT][/COLOR]

---

### Post by gzarkadas on 2010-09-23
You can use the `mail' program (type `man mail' in a terminal window to see options and related info). Example usage:

```

< [message-body-file] mail -s [your-message-subject] [to-address]

``````

{ cat << EOF
put your multi-line message
inside those EOF markers;
last EOF must be alone, hence the {} 
to allow piping to mail
EOF
} | mail -s [your-message-subject] [to-address]

``````

echo -e 'This is another way
to send multiline messages' | mail -s [your-message-subject] [to-address]
 
```

---

### Post by jacob.david on 2010-09-24
you can install the sendmail utility (sudo apt-get install sendmail).
This is a very good utility to send mails. Check the manual pages for more options.

---

