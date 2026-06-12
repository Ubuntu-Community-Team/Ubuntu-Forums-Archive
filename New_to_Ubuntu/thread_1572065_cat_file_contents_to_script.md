---
title: "cat file contents to script"
date: 2010-09-10
forum: New to Ubuntu
---

### Post by Jloser on 2010-09-10
If I type:
./googlevoice.pl -c sms -p 123456789 This is the text message

I get a text message sent to my phone.  I want to script the content of the message, so how do I get the contents of a file as the message?  I tried:

cat message.txt | ./googlevoice.pl -c sms -p 123456789

but nothing happens.  What simple thing am I doing wrong?

---

### Post by spjackson on 2010-09-10
```

./googlevoice.pl -c sms -p 123456789 $(cat message.txt)

```

---

