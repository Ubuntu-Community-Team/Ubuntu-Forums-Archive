---
title: "how to I get permanent permission to access external data partition?"
date: 2010-02-17
forum: New to Ubuntu
---

### Post by hortstu on 2010-02-17
I backed up my important files to an external hd before my last reinstall.  When I try to drag and drop them from the external to the internal data partition I get denied.

How to I get permission and keep it that way?

---

### Post by mikeyphi on 2010-02-18
> **hortstu said:**
> I backed up my important files to an external hd before my last reinstall.  When I try to drag and drop them from the external to the internal data partition I get denied.

How to I get permission and keep it that way?

1. Check name of drive within your PC.
2. open a terminal and enter:
   sudo chmod a+w nameofdrive

Edit:The above assumes you can read your external drive but can't write to the internal partition; if different please specify the exact problem!

---

### Post by hortstu on 2010-02-18
> **mikeyphi said:**
> 1. Check name of drive within your PC.
2. open a terminal and enter:
   sudo chmod a+w nameofdrive

Edit:The above assumes you can read your external drive but can't write to the internal partition; if different please specify the exact problem!

Thanks.  I think that allowed me to transfer the files.

I also tried...

```
sudo chown -R mike:mike *names of files here*
```

Not sure what actually got the job done but it is done... thanks for your help.

---

