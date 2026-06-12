---
title: "How to install songbird in Lucid"
date: 2010-05-05
forum: New to Ubuntu
---

### Post by dharanitharan on 2010-05-05
Hi friends,
            I ve installed Ubuntu 10.04 a week ago.Now i want to install songbird in my lucid.I tried apt-get installation. But this package is not available in apt-get. How can i install this. I need ur help guys.


Thanks and Regards,
Dharanitharan.A

---

### Post by Didius Falco on 2010-05-05
You can get the deb file from getdeb:

[http://www.getdeb.net/updates/Ubuntu/10.04/?q=songbird](http://www.getdeb.net/updates/Ubuntu/10.04/?q=songbird)

and install it from the terminal. Put it in a folder, navigate to that folder and use this command:
```
sudo dpkg -i package_file_name.deb 
```

Alternatively, you can install it using the **GDebi Package Installer**, found in **Menu/System Tools**.

Regards,

Didius

---

