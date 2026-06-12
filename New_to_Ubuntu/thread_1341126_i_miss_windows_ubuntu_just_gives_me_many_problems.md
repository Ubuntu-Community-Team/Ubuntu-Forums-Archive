---
title: "i miss windows ubuntu just gives me many problems"
date: 2009-11-29
forum: New to Ubuntu
---

### Post by milmekos on 2009-11-29
i installed ubuntu a few weeks ago and so far it was good, until my friend and i decided to endeavor into creating an online radio station, we wanna make it big and i have contact with many spanish rock celebrities to help me get this going, either wayi wanted to install shoutcast on my ubuntu computer and after doing all steps of the compilation one by one, i couldnt get it done, it was just sending me errors, i cant seem to be able to compilate any program

then i found icecast on the synaptic package manager and even after installing, i cant find the program anywhere, can someone help me out?

---

### Post by mikeac72 on 2009-11-29
Install Wine.
[http://www.winehq.org/download/deb](http://www.winehq.org/download/deb)
Install Shoutcast for Windows.
Try it now.

---

### Post by howefield on 2009-11-29
> **milmekos said:**
> then i found icecast on the synaptic package manager and even after installing, i cant find the program anywhere, can someone help me out?

[http://www.howtoforge.com/linux_webradio_with_icecast2_ices2](http://www.howtoforge.com/linux_webradio_with_icecast2_ices2)

---

### Post by jrrader on 2009-11-29
NM, someone beat me to it.

---

### Post by milmekos on 2009-11-29
> **howefield said:**
> [http://www.howtoforge.com/linux_webradio_with_icecast2_ices2](http://www.howtoforge.com/linux_webradio_with_icecast2_ices2)
when i tried installing according to the instructions on the website this was the result 
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?




  installed wine early in the am and the programs didnt show in wine's menu so i dunno whatta hell

---

### Post by howefield on 2009-11-29
> **milmekos said:**
> when i tried installing according to the instructions on the website this was the result

You said you had it installed already, just skip the install steps on that tutorial.

(The reason you can't find it after installing is that it doesn't have a graphical interface to launch, you launch from the terminal).

---

### Post by milmekos on 2009-11-29
> **howefield said:**
> You said you had it installed already, just skip the install steps on that tutorial.

(The reason you can't find it after installing is that it doesn't have a graphical interface to launch, you launch from the terminal).
icecast2 daemon disabled - read /etc/default/icecast2.



i guess i have to go back to windows :(

---

### Post by Mark Phelps on 2009-11-29
> **mikeac72 said:**
> Install Wine.
[http://www.winehq.org/download/deb](http://www.winehq.org/download/deb)
Install Shoutcast for Windows.
Try it now.

Have you even bothered to check the Win HQ app database to see if shoutcase is supported?

I did, and there's no mention of it.

---

### Post by jrrader on 2009-11-29
> **Mark Phelps said:**
> Have you even bothered to check the Win HQ app database to see if shoutcase is supported?

I did, and there's no mention of it.

Some people shout "Wine" whenever they hear "Windows" apparently.  Wine doesn't work for most Windows applications and is far from the best option for Linux users when there are usually native applications that will do the job better.

---

### Post by milmekos on 2009-11-29
thanks everyone :(

---

### Post by halitech on 2009-11-29
there is nothing to compile to run the shoutcast server, you download it, extract it to where you want, edit the sc_serv.conf file to have the info you want (mainly passwords and port) and then run it by opening a terminal and running ./sc_serv sc_serv.conf

now, getting the SHOUTcast Radio DSP for Unix/Linux/MAC OSX part working in linux is a bit harder and I've never gotten it to work myself but it's supposed to work.

---

