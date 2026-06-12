---
title: "Avast Antivirus"
date: 2009-01-18
forum: New to Ubuntu
---

### Post by Atholisto on 2009-01-18
I "installed" the Avast Antivirus Linux version.  I can't figure out how to find it, open the control panel, or even tell if it's running.  Can someone point me in the right direction?  Thanks.

---

### Post by iKonaK on 2009-01-18
As far as i know, it dosen't have a GUI; also in GNU/Linux you don't need an antivirus or antispyware or defragmenting tools, just set up your firewall with firestarter or other iptables GUI.
Try "man avast" in a terminal and look for the instructions in the output.

EDIT: The so called "control panel" is actually the "System" menu on the top gnome-bar in left; if you want to see the actual control panel, just "rightclick" click on "edit menu" and enable the "control panel" (it's under system too)
....assuming you're using a gnome desktop :)

---

### Post by Atholisto on 2009-01-18
Thanks.  I see now that it is command-line only.

---

### Post by binbash on 2009-01-18
you dont need an antivirus however you can find some tutorials at the forum's tutorial section (installation, gui etc)

---

### Post by DirtDawg on 2009-01-18
> **Atholisto said:**
> I "installed" the Avast Antivirus Linux version.  I can't figure out how to find it, open the control panel, or even tell if it's running.  Can someone point me in the right direction?  Thanks.


Avast does have a (rather nice) GUI. I assume you installed using the .deb package. I am not sure where you would find a menu entry for the GUI as I have not installed via a deb. You could try running this in a terminal:
```
avastgui
```

If that doesn't work, download the TAR GZ package instead. Once you extract it (via right-click), there will be three folders. Inside the one labeled 'bin', there is a binary file called 'avastgui.' Double-click it and choose 'run' and you should get the gui.

Hope this helps.

---

### Post by Atholisto on 2009-01-18
Running "Avastgui" in a terminal brought up the registration screen.  Once registered, I found the GUI in the folder called "Accessories".....THANK YOU!

---

### Post by cagdas on 2009-01-26
sorry for messaging here but i have a problem about avast;
that says memory allacotion error is it a fatal error that cannot fixed? 
ty!

---

### Post by DirtDawg on 2009-01-27
> **cagdas said:**
> sorry for messaging here but i have a problem about avast;
that says memory allacotion error is it a fatal error that cannot fixed? 
ty!

Ugh, that's a nasty error. You may want to consider [AVG]("http://free.avg.com/download"), which also has a Linux client and is free for personal use.

---

### Post by OrangeCrate on 2009-01-27
You could also seek some guidance, by posting any avast! concerns in their Linux forum, on the avast! forums:

[http://forum.avast.com/index.php](http://forum.avast.com/index.php)

(avast! 4 for Linux/Unix/Mac)

---

### Post by sarpulhu on 2009-01-27
Remember Ubunutu doesn't get viruses and doesn't need a virus scanner!! It's really only useful for scanning those M$ systems.

---

### Post by wyrless2002 on 2009-03-08
[CENTER]> Remember Ubunutu doesn't get viruses and doesn't need a virus scanner!! It's really only useful for scanning those M$ systems.

*Warning Highly Opinionated*[/CENTER]

<Sigh> at the risk of starting a war, that just isn't an absolute or else they wouldn't bother making a Linux version of every virus scanner, free or proprietary. I know, I know, I know. I'm for all intensive purposes, an end-user. I read every article that I come across for and against whether Linux can get virii; if one were introduced whether it would cause any harm to your home folder, your configurations, the kernel, individual applications, or your browser. I've run Ubuntu "naked" from 5.10 (the OS, not me) to 8.10 and had zero problems to date. During the same period running Spybot S & D and Avast! on the Vista and XP boxen in my home and been satisfied that they "seem to" protect from the major infections publicized. Also when they do catch something, it appears that they are capable of removing the threat. I couldn't say that of either McAfee or Norton products. If someone feels the need to run a virus scanner to be sure, Avast! is a good choice, in my opinion. It's fine to educate them on the health benefits of Linux, but to tell them not to bother is just not doing them or the community any favors. If for no other reason than to protect themselves from being a carrier and re-distributing a threat back to other OS's. If you know more about the subject than the rest of us, then answer the questions that are asked, fill in the gaps and correct mis-information. Don't drop some half true cliche and move to the next post.

---

