---
title: "Problem with Low Graphics Mode?"
date: 2011-05-28
forum: New to Ubuntu
---

### Post by WebHome on 2011-05-28
To all newbie include me, here are some code to solve your problem if you encounter "Low graphics Mode" 

Code:

lspci | grep VGA

If it is a nVidia 6xxx or above (otherwise you must use Nouveau).

Code:

sudo apt-get install --reinstall nvidia-current

sudo nvidia-xconfig

Restart !
enjoy ubuntu!

---

