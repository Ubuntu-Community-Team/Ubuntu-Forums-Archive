---
title: "Veetle plugin crashed Firefox and Chrome. I can't even open them. Please help."
date: 2010-06-27
forum: New to Ubuntu
---

### Post by dummiebeginner on 2010-06-27
Hi,

I installed the plugin of Veetle (to watch online TV) and right after doing it my ChromePlus crashed and when I try to open it again it just opens for a second and gets closed again immediately.

And exactly the same happens in Firefox, so I cannot even try to unistall it from the Firefox plugins section.

Opera is working though.

I followed the instructions that I found in a blog that people posting feedback said it was working. I did this:

1- I dowloaded this file from the Veetle site: veetle-0.9.17-linux-install.download

2- Run this in Terminal from the folder where I had the file:

```
chmod 777 veetle-0.9.17-linux-install.download
```

3- Then this: 

```
./veetle-0.9.17-linux-install.download
```

4- Then I accepted the license and apparently installed it properly.

And then the disaster and crash came.

I am using Ubuntu 10.04 32-bits and just installed it fresh today and was working well.

Can somebody help, please?

Thanks

---

### Post by lovinglinux on 2010-06-27
Post the result of the command below:

```
ls /usr/lib/mozilla/plugins
```

---

### Post by dummiebeginner on 2010-06-27
Thanks for your answer.

yo@sam:~$ ls /usr/lib/mozilla/plugins
flashplugin-alternative.so             libtotem-gmp-plugin.so
libjavaplugin.so                       libtotem-mully-plugin.so
librhythmbox-itms-detection-plugin.so  libtotem-narrowspace-plugin.so
libtotem-cone-plugin.so
yo@sam:~$ 

I removed Firefox but it doesnt change anything.

Thanks again.

---

### Post by lovinglinux on 2010-06-27
> **dummiebeginner said:**
> Thanks for your answer.

yo@sam:~$ ls /usr/lib/mozilla/plugins
flashplugin-alternative.so             libtotem-gmp-plugin.so
libjavaplugin.so                       libtotem-mully-plugin.so
librhythmbox-itms-detection-plugin.so  libtotem-narrowspace-plugin.so
libtotem-cone-plugin.so
yo@sam:~$ 

I removed Firefox but it doesnt change anything.

Thanks again.

Post the output of:

```
locate veetle*.so
```

The site from where you installed the plugin should have instructions on how to remove it.

---

### Post by lovinglinux on 2010-06-27
Please provide the link to the site with the instructions on how to install veetle. I'm going to install it here to discover how to remove it.

---

### Post by dummiebeginner on 2010-06-27
Thanks again.

yo@sam:~$ locate veetle*.so
yo@sam:~$ 

The blog from which I followed the instructions is this:

[http://preview.tinyurl.com/236lwln](http://preview.tinyurl.com/236lwln)

And in the Veetle site and forum I couldn't find any how-to uninstall in Linux.

[http://forums.veetle.com/forums/](http://forums.veetle.com/forums/)

[http://www.veetle.com/index.php/download](http://www.veetle.com/index.php/download)

Thanks.

---

### Post by lovinglinux on 2010-06-27
> **dummiebeginner said:**
> Thanks again.

yo@sam:~$ locate veetle*.so
yo@sam:~$ 

The blog from which I followed the instructions is this:

[http://tiny.cc/36r7p](http://tiny.cc/36r7p)

And in the Veetle site and forum I couldn't find any how-to uninstall in Linux.

[http://forums.veetle.com/forums/](http://forums.veetle.com/forums/)

[http://www.veetle.com/index.php/download](http://www.veetle.com/index.php/download)

Thanks.

I will do this after Argentina x Mexico :)

---

### Post by lovinglinux on 2010-06-27
Post the output of:

```
locate libveetle-broadcast-plugin.so
locate libveetle-core-plugin.so
locate libveetle-player-plugin.so
```

---

### Post by dummiebeginner on 2010-06-27
> **lovinglinux said:**
> I will do this after Argentina x Mexico :)

Lol :biggrin: Unfortunately Argentina won.

I gave up. I am reinstalling. As usual. Many things started not to work, such as the wifi and many more. Total gradual crash.

I still wonder why they say that Linux is so good. I have to reinstall it all the time and spend more time fixing things and searching and reading solutions on the internet than using the computer.

Really, Linux is pure crap, it is bug after bug and crash after crash.

Lovinglinux? Hatinglinux!

Go Brazil ;)

---

### Post by lovinglinux on 2010-06-27
> **dummiebeginner said:**
> Lol :biggrin: Unfortunately Argentina won.

I gave up. I am reinstalling. As usual. Many things started not to work, such as the wifi and many more. Total gradual crash.

I still wonder why they say that Linux is so good. I have to reinstall it all the time and spend more time fixing things and searching and reading solutions on the internet than using the computer.

Really, Linux is pure crap, it is bug after bug and crash after crash.

Lovinglinux? Hatinglinux!

Go Brazil ;)

Sorry to read that. For me is a lot better than Windows. Anyway, I would recommend not trying Veetle again.

---

### Post by Codemagnet on 2011-04-09
Evening all, well, at least its evening where I am.

Sorry to start this old thread back up again but I am having the exact same problem as the original thread starter.  I'll have to install opera seeing as it is not affected by this problem according to sir dummiebeginner.

I really dont want to have to reinstall ubuntu, i have done that in the past but I want to learn more about using the system and a clean install doesnt teach much.  Does anyone know how to remove this dreaded plugin??

I will run the commands mentioned above shortly and give the output, Im typing this on my old laptop at the moment as I cant use any of my browsers.

Ta

---

### Post by Codemagnet on 2011-04-09
Managed to solve it.  While reinstalling it, i noticed files were installed to /home/user/.mozilla/plugins and /home/user/.veetle_vlc, where user is the name of the user account.  The folders in question are hidden so I had to show hidden files first.  The of course I deleted everything to do with veetle, and firefox is working again :).

---

