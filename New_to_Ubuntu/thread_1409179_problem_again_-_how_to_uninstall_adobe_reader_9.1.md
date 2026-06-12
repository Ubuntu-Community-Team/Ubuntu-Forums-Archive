---
title: "problem again - how to uninstall adobe reader 9.1"
date: 2010-02-17
forum: New to Ubuntu
---

### Post by smokystone on 2010-02-17
Hi, I have installed the .bin file downloaded from adobe website, but I don't know how to uninstall it, because I can't remove it from package manager. 

Anyone knows how to remove it?

Thanks

---

### Post by smokystone on 2010-02-17
or maybe I have to remove the adobe reader manually, but I don't know what files or folders I need to remove. I don't want remove some other important files or folders.

Anyone knows how to do it?

---

### Post by smokystone on 2010-02-17
:D, I have found the solution. Actually there is an uninstall file in the Adobe folder where is as this:

/opt/Adobe/Reader9/bin

Finally, another problem is google chrome still cannot open pdf in web. I have checked the about:plugins, and all reader plugins are opened. I have tried many ways to figure out how to fix, but still doesn't work.

Does anyone know how to fix it?

Should I post a new thread?

---

### Post by madnag4u on 2012-02-23
> **smokystone said:**
> :D, I have found the solution. Actually there is an uninstall file in the Adobe folder where is as this:

/opt/Adobe/Reader9/bin

Finally, another problem is google chrome still cannot open pdf in web. I have checked the about:plugins, and all reader plugins are opened. I have tried many ways to figure out how to fix, but still doesn't work.

Does anyone know how to fix it?

Should I post a new thread?

Thanks for the info! I didn't know about the uninstall script. Ran the script as root. Worked like a charm :)

---

### Post by yayosry on 2013-01-10
> **smokystone said:**
> :D, I have found the solution. Actually there is an uninstall file in the Adobe folder where is as this:

/opt/Adobe/Reader9/bin

Finally, another problem is google chrome still cannot open pdf in web. I have checked the about:plugins, and all reader plugins are opened. I have tried many ways to figure out how to fix, but still doesn't work.

Does anyone know how to fix it?

Should I post a new thread?
thanks for the info, for the novs like me:

this procedure didt work for me  clicking on uninstall file, it needs  root permition to uninstall  

cd /opt/Adobe/Reader9/bin
sudo ./UNISNTALL

regards

---

