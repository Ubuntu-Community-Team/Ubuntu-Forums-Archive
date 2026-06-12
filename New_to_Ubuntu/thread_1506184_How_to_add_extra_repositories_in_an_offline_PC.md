---
title: "How to add extra repositories in an offline PC?"
date: 2010-06-10
forum: New to Ubuntu
---

### Post by maqtanim on 2010-06-10
As the title says. Do anyone know, how to add extra repositories (as an example, say, Medibuntu) in a PC which does not have any Internet connection? Is it possible to add one?

---

### Post by Elfy on 2010-06-10
You can edit the sources list - ```
gksudo gedit /etc/apt/sources.list
``` , you can add them in Software Sources - Sys - Admin - Software Sources, you can add them if you have a ppawith ```
sudo add-apt-repository ppa:namefromppa
```

Without an internet connection though you will not be able to update them.

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

---

### Post by maqtanim on 2010-06-10
Actually for updating or downloading software/software list, I can use [keryx]("http://keryxproject.org/"), but keryx can't add extra repositories. some times some repo need authentication, if the pc is in offline how can I complete the authentication?

---

### Post by Elfy on 2010-06-10
Try adding the necessary and running keryx then - no idea if it will work though I'm afraid. 

You could also look into apt-offline [http://www.debian-administration.org/article/Offline_Package_Management_for_APT](http://www.debian-administration.org/article/Offline_Package_Management_for_APT)

---

### Post by EXCiD3 on 2010-06-10
Keryx can add repositories, including PPAs. You just have to use the repository format that starts with "deb". If you look at the PPA page and click "Technical details about this PPA" you will find that format. 

For example on my personal PPA: [https://launchpad.net/~excid3/+archive/ppa](https://launchpad.net/~excid3/+archive/ppa)
```
deb http://ppa.launchpad.net/excid3/ppa/ubuntu lucid main 
deb-src http://ppa.launchpad.net/excid3/ppa/ubuntu lucid main 
```

Also, as long as you know trust which repositories you are using, you can ignore the authentication (since you already trust it by visiting their website and checking it out for yourself, etc).

---

### Post by maqtanim on 2010-06-12
@[EXCiD3]("http://ubuntuforums.org/member.php?u=289809")
Thanks a lot... I didnot know about that!

---

### Post by EXCiD3 on 2010-06-12
Yep, no problem. :)

Let me know if you need any help with it, I'm working it quite a lot this summer until school starts again.

---

