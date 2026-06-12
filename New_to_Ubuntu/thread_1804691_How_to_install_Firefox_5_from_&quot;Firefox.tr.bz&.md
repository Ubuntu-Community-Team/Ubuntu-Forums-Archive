---
title: "How to install Firefox 5 from &quot;Firefox.tr.bz&quot; in ubuntu 11.04?"
date: 2011-07-15
forum: New to Ubuntu
---

### Post by Prathmesh01 on 2011-07-15
I' am new to ubuntu. I downloaded Firefox.tar.bz and just wondering how to install it on my Ubuntu 11.04. Please Help me.

---

### Post by drpjkurian on 2011-07-15
Firefox 5 is already there in natty repository. Therefore
use the command```
$ sudo apt-get update
``` and
```
$ sudo apt-get upgrade
```
Or you can also use Update manager to update

---

### Post by raja.genupula on 2011-07-15
open terminal
[B]tar -jxvf filename  
cd filename
./firefox [/B]

       if **./firefox** not done

  then just untar it & look for **./configure**
                                  if it success then do **make** after that **sudo make install**

---

### Post by coffeecat on 2011-07-15
@Prathmesh01, Firefox comes pre-installed in Ubuntu 11.04. If you update your system, you will get Firefox 5. You don't need to install it from a tarball. Or are you running Kubuntu?

---

### Post by lovinglinux on 2011-07-15
See [Firefox 4, 5 & Beyond Mega Thread]("http://ubuntuforums.org/showthread.php?t=1712247").

---

### Post by Prathmesh01 on 2011-07-15
Im using Ubuntu not Kubuntu.
firefox 4 is pre installed i wanna upgrade it to firefox 5.0.1
for ./firefox i get:

bash: ./firefox: Is a directory

for ./configure i get:

bash: ./configure: No such file or directory

---

### Post by aktiwers on 2011-07-15
If you just want to test drive it, you can simply double-click the Firefox file inside the Firefox folder you just extracted from the tar.gz and pick run from terminal.

---

### Post by lovinglinux on 2011-07-15
> **Prathmesh01 said:**
> Im using Ubuntu not Kubuntu.
firefox 4 is pre installed i wanna upgrade it to firefox 5.0.1
for ./firefox i get:

bash: ./firefox: Is a directory

for ./configure i get:

bash: ./configure: No such file or directory

Please ignore those instructions. They are for compiling source code and don't even work with Firefox source code.

Just extract the tar.bz to your home directory and and click the firefox file inside it to start Firefox. For more information, including how to make plugins work, see the Manual installation method at [http://www.webgapps.org/tutorials/firefox/general/installing-other-versions](http://www.webgapps.org/tutorials/firefox/general/installing-other-versions)

BTW, I don't know why you are downloading a tar.bz, you can just update your system to get Firefox 5 on Ubuntu 11.04. There are already two other replies saying that. Execute the commands below on a terminal.

```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by leeconne on 2011-07-17
Why can I not install firefox "5.0.1" from the software center. Downloading from the firefox website removes the menu integration etc. I have a similar problem trying to get the new transmission which I cannot even get from their website.

---

### Post by lovinglinux on 2011-07-17
> **leeconne said:**
> Why can I not install firefox "5.0.1" from the software center. Downloading from the firefox website removes the menu integration etc. I have a similar problem trying to get the new transmission which I cannot even get from their website.

Firefox 5 is only available from official repositories if you are using Ubuntu 11.04 Natty Narwhal. You can get it via regular upgrade through the Update Manager. If you are specifically tying to get Firefox 5.0.1 and not 5.0, then you will have to wait until that version is available in the repositories. It shouldn't take long.

If you are using an older version of Ubuntu then see [Firefox 4, 5 & Beyond Mega Thread]("http://ubuntuforums.org/showthread.php?t=1712247"). You will find explanations there about why you can't get it from the repositories and instructions on how to get it.

---

### Post by alphacrucis2 on 2011-07-17
Is it possible that the mirrors the op is using are out of date?

---

### Post by lovinglinux on 2011-07-17
> **alphacrucis2 said:**
> Is it possible that the mirrors the op is using are out of date?

Yes, it is possible. However, since it looks like the OP is a new user, then most likely he has the main repo in the settings. Unless of course he has an older version of Ubuntu.

---

### Post by CommuneOfLoon on 2011-07-26
> **lovinglinux said:**
> See [Firefox 4, 5 & Beyond Mega Thread]("http://ubuntuforums.org/showthread.php?t=1712247").

Thanks!

---

### Post by lovinglinux on 2011-07-26
> **CommuneOfLoon said:**
> Thanks!

You are welcome.

---

