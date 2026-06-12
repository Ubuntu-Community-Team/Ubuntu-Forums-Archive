---
title: "Adobe flash wont install"
date: 2010-02-26
forum: New to Ubuntu
---

### Post by coubury on 2010-02-26
Adobe flash wont install for me

I try - 

ubuntu@ubuntu:~$  sudo apt-get install flashplugin-nonfree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package flashplugin-nonfree
ubuntu@ubuntu:~$ 


Anyone help?

---

### Post by linuxman94 on 2010-02-26
What version of Ubuntu are you using?

---

### Post by coubury on 2010-02-26
THe latest one 9.10

---

### Post by zachHH on 2010-02-26
Did you install Ubuntu recently? If so, try updating the system (System -> Administration ->Update Manager). Once that is finished, try again and the flash plugin should be available.

---

### Post by lrcaballero on 2010-02-26
Try doing it through their website........just click on agree and install now. And see if it works for you...

[http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)

Luis

---

### Post by Kakers on 2010-02-26
check your repositories to make sure you have multiverse I believe it is the run the following commands 

```
[INDENT]sudo apt-get update
 sudo apt-get install adobe-flashplugin
[/INDENT]
```

---

### Post by linuxman94 on 2010-02-26
The easiest way to install flash player is through the ubuntu software center (Applications -> Ubuntu Software Center). Just search for flash and it will come up.

---

### Post by coubury on 2010-02-26
> **Kakers said:**
> check your repositories to make sure you have multiverse I believe it is the run the following commands 

```
[INDENT]sudo apt-get update
 sudo apt-get install adobe-flashplugin
[/INDENT]
```

Tried this and im getting the same error.


lrcaballero. I also tried that and it never worked.

---

### Post by coubury on 2010-02-26
> **linuxman94 said:**
> The easiest way to install flash player is through the ubuntu software center (Applications -> Ubuntu Software Center). Just search for flash and it will come up.

THis worked

Cheers :p

---

### Post by linuxman94 on 2010-02-26
Glad I could help.:guitar:

---

### Post by lrcaballero on 2010-02-26
Below you will find 2 links, 1st one is a video on how to and 2nd is a link to medibuntu repositories. Hope this can help. By the way in my previous comment did you tried .deb for Ubuntu 8.04+????

[http://www.youtube.com/watch?v=NT7urt5UcQg&feature=related](http://www.youtube.com/watch?v=NT7urt5UcQg&feature=related)

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

Luis

---

### Post by coubury on 2010-02-26
> **coubury said:**
> THis worked

Cheers :p

actually it didn't.

IT looked like it was going to install, 50%, then my pc froze, I had to reboot and then when i go into the Ubuntu Software centre, the the option to install the flash player again isn't there. :S

---

### Post by sandyd on 2010-02-26
> **coubury said:**
> actually it didn't.

IT looked like it was going to install, 50%, then my pc froze, I had to reboot and then when i go into the Ubuntu Software centre, the the option to install the flash player again isn't there. :S

using 64 bit or 32 bit ubuntu?

32 bit.
This will DEFINATELY work if its 32 bit.
```

wget -c http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_10_linux.tar.gz
tar xvfz install_flash_player*
sudo mv libflashplayer.so /usr/lib/mozilla/plugins/

```

if your using 64-bit ubuntu, see sig.

---

### Post by coubury on 2010-02-26
> **carlee said:**
> using 64 bit or 32 bit ubuntu?

32 bit.
This will DEFINATELY work if its 32 bit.
```

wget -c http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_10_linux.tar.gz
tar xvfz install_flash_player*
sudo mv libflashplayer.so /usr/lib/mozilla/plugins/

```

if your using 64-bit ubuntu, see sig.

Nah 32. I followed the guide and it seemed to install fine even moving the .so to the plugin folder.

But when i go on to youtube no videos show up.

---

### Post by coubury on 2010-02-26
:(

---

### Post by sandyd on 2010-02-26
alright.
By now, I **think** you have multiple versions of flash installed.... which is not a good thing....

see sig, click the remove flash button.
then try steps above again...

---

