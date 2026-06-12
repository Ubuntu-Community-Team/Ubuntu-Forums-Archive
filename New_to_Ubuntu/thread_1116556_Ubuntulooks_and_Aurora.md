---
title: "Ubuntulooks and Aurora"
date: 2009-04-05
forum: New to Ubuntu
---

### Post by JoshuaSB on 2009-04-05
Hello Everyone,

I installed Ubuntu the other day and have been playing around with it for the past week +. Anyways, I like to think I am fairly intelligent but for the life of me I just cannot seem to figure out this issue.

First, I was looking for some themes and found some very nice looking ones, most noticeably LUX and Slickness Black. Both however take Ubuntulooks and Aurora GTK engines...

However, when I follow the instructions on Ubuntulooks and try to put the file in /usr/lib/gtk-2.0/2.*.*/engines using the terminal gtsu or sudo Nautilus  command it still says I do not have enough priviledges to transfer the files into the root directory...

I attempted to open another gtsu nautilus window to navigate to the desktop, however it doesn't show anything or allow me to select the files to move from nautilus to nautilus.

Basically to recap, I am trying to move files into the protected root directory, but for some reason Sudo/gtsu nautilus command doesn't give me the privileges to move them...

Hopefully one of you can assist me. 
Thanks guys.

---

### Post by tarps87 on 2009-04-06
I think this is what you are looking for:
[http://packages.ubuntu.com/intrepid/gtk2-engines-ubuntulooks](http://packages.ubuntu.com/intrepid/gtk2-engines-ubuntulooks)
It is in the repository so you can install it using
```
sudo apt-get install gtk2-engines-ubuntulooks
```


I would suggest using the the on in the repository.
This command will copy the themes to the correct location if the untar'd folder is on your desktop and the folder is called ubuntulookspack
```
sudo cp -r ~/Desktop/ubuntulookspack/usr/share/themes/* /usr/share/themes/
```

---

