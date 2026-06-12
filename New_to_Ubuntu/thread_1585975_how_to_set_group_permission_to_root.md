---
title: "how to set group permission to root"
date: 2010-10-01
forum: New to Ubuntu
---

### Post by begtognen on 2010-10-01
Is there a simple terminal command that allows me to set the group permission for one file to "root" and "read only"?

Background: I'm attempting to create my own Kate syntax highlighting file. I've taken the syntax.template file that's included with Kate, and edited it, saved it as "tyr.xml".

Kate crashes when I try to open a TYR file, and I'm pretty sure it's because the permissions for all of the OTHER .xml files in the syntax directory are set to "root" and "read only", while the permissions for *my* file are set to my name and "read only".

Thanks so much for any help you can give.

---

### Post by s3MA00RRNY on 2010-10-01
sudo chmod g=r <filename>
sudo chown root:root <filename>

---

### Post by begtognen on 2010-10-01
Thanks so much!

---

