---
title: "View djvu files using Okular"
date: 2011-05-19
forum: New to Ubuntu
---

### Post by LittleGyko on 2011-05-19
Is it possible to view djvu files using okular. I had tried to install some packages the previous time I tried to do this. Instead, I ended up installing djview4. 

If I open a djvu file with okular I get the error "cannot find plugin"

I use ubuntu 10.04

Thanks.

---

### Post by compmodder26 on 2011-05-19
You say you installed extra packages.  Was one of those "okular-extra-backends"?  According to the package details, that should allow you to view djvu formats.

---

### Post by LittleGyko on 2011-05-19
Thanks. I managed to install okular-extra-backends and it works fine now.

---

### Post by compmodder26 on 2011-05-19
You're welcome!

---

### Post by LittleGyko on 2011-05-19
I added a new repository to my /etc/apt/sources.list by using 

"sudo gedit /etc/apt/sources.list"

After this do I need to compile this file or will it work automatically.

---

### Post by compmodder26 on 2011-05-19
do "sudo apt-get update", then all the packages of that repository should be available for you to download.

---

### Post by LittleGyko on 2011-05-19
Thanks again. Installing Okular-extra... didn't work with apt-get even though I had added the repository. I installed it using Synaptic. So I was just wondering what I had missed!

---

