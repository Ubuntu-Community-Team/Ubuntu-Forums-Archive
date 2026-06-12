---
title: "Possible to use existing install as a repository?"
date: 2009-06-05
forum: New to Ubuntu
---

### Post by Thumbert on 2009-06-05
Hi,

I have no internet access at home but snuck a pc into work where I installed most of the software I wanted for my new 9.04 installation by using add/remove. I have another computer at home I want to install Ubuntu on, if I network them is it possible to use the "fully loaded" PC as a repository of sorts for the other PC?

Thanks for any help.

---

### Post by mike555 on 2009-06-05
There is a app for that, I haven't tried it but it sounds good ... [http://keryxproject.org/](http://keryxproject.org/)   or you might try "aptOnCd " .

---

### Post by Thumbert on 2009-06-05
Thanks mike555,

I'll give "aptOnCd" a try. Since Linux doesn't have a registry(?) is it possible to just copy application folders across?

---

### Post by ajgreeny on 2009-06-05
No you can't simply copy application folders across, as many lib files will probably also be needed, and not actually i that folder.  I agree that aptoncd is the way to go, but you can also copy the packages themselves in /var/apt/cache/archives from the old to the new machine, omitting the **partial** folder and the **lock** file from the files when you copy across.  You will need to do the copying as root, so either use the terminal **sudo cp** command or use nautilus as root (with care or you could damage your system) by using the command ```
gksudo nautilus
``` when you copy the files to the new machine.

Aptoncd does this all for you so is probably the best way.  You don't even have to burn a CD if you don't want to, you can just use the iso file that aptoncd makes and move it on a usb flash drive to the new machine, and then use aptoncd on that to restore the iso file.

---

### Post by clive littlewood on 2009-06-05
Hi

Perhaps try the USB startup disc option in the admin menu ?

Clive

---

### Post by ayenack on 2009-06-05
There's a few way to do this. Have a look at this [tutorial]("http://taufanlubis.wordpress.com/2007/08/15/how-to-make-local-repository-in-ubuntu/"). I did something very similar to this on my home network once.

If you follow this guide you can then use your laptop as the repo and keep it update every month in work. Then when at home you can keep your desktop up to date. Both need to be running the same version of Ubuntu.

[COLOR="Red"]**Just a quick warning make sure you know what you're doing before trying this as you can totally destroy your system if it doesn't work or if you mess it up somehow.**[/COLOR]

[http://taufanlubis.wordpress.com/2007/08/15/how-to-make-local-repository-in-ubuntu/](http://taufanlubis.wordpress.com/2007/08/15/how-to-make-local-repository-in-ubuntu/)

---

### Post by Thumbert on 2009-06-05
Think I have enough info to do what I intended - aptOnCd looks the simplest and safest option, although using ayenack's suggested tutorial is probably closer to what I originally intended - and I think will allow me to keep an updated directory.

Thanks for the info all.

---

