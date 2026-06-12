---
title: "Can only boot into terminal, please help"
date: 2010-12-27
forum: New to Ubuntu
---

### Post by germanix on 2010-12-27
So I did it again, played around and now I am stuck. I read that downloading this file:
GDM 2.32.0-0ubuntu2_i386deb helps to resolve a problem when running more than one language. As I sometimes also use german I downloaded and installed this package. When I restarted I was surprised to see that the menu was now mixed, partly in german and partly in english. The most surprising thing is I do not have the  german language even installed on my system at this time. I tried to set the language back to english system wide but all of the menus remained partly in german.
So then I decided to remove the package I had installed via synaptic (complete removal). On the reboot I could only boot into into the terminal where I am now stuck. 
I do not know who to boot up the system via the terminal and more importantly how to get the boot screen back where I can log-in as normal.
Any help will be greatly appreciated.

---

### Post by karthick87 on 2010-12-27
On booting hold down the shift key and the grub menu will appear. The Ubuntu system should be highlighted on the menu. You should press the "e" key and on the new screen navigate to the end of the line that says "quiet splash" and remove those words and replace them with "nomodeset"  without the quotes and then press ctrl + X to reboot.

---

### Post by mcduck on 2010-12-27
> **germanix said:**
> So I did it again, played around and now I am stuck. I read that downloading this file:
GDM 2.32.0-0ubuntu2_i386deb helps to resolve a problem when running more than one language. As I sometimes also use german I downloaded and installed this package. When I restarted I was surprised to see that the menu was now mixed, partly in german and partly in english. The most surprising thing is I do not have the  german language even installed on my system at this time. I tried to set the language back to english system wide but all of the menus remained partly in german.
So then I decided to remove the package I had installed via synaptic (complete removal). On the reboot I could only boot into into the terminal where I am now stuck. 
I do not know who to boot up the system via the terminal and more importantly how to get the boot screen back where I can log-in as normal.
Any help will be greatly appreciated.

So, you first replaced the existing GDM version with a new one, and then removed the new one?

That leaves you without GDM installed. Which is also why you can't get to login screen or desktop. 

Just reinstall the GDM from Ubuntu's repositories and everything should work again.

```
sudo apt-get install gdm
```

..or if you want to be sure, the ubuntu-desktop metapackage makes sure you have everyting needed for the default desktop setup to work:
```
sudo apt-get install ubuntu-desktop
```

---

### Post by germanix on 2010-12-27
> **karthick87 said:**
> On booting hold down the shift key and the grub menu will appear. The Ubuntu system should be highlighted on the menu. You should press the "e" key and on the new screen navigate to the end of the line that says "quiet splash" and remove those words and replace them with "nomodeset"  without the quotes and then press ctrl + X to reboot.

Does not work for me. Holding down the shift key whilst booting still brings me to the terminal promt

---

### Post by Hur Dur on 2010-12-27
Have you tried the startx command?

---

### Post by germanix on 2010-12-27
Hi Mcduck, thank you for your advice. GDM would not install - failed to fetch. Ubuntu desktop may well install, not sure because I aborted the install simply because I actually use the Mint-desktop. I tried using "install mint-desktop instead but no such package found. Do I now need to re-install?

---

### Post by germanix on 2010-12-27
> **Hur Dur said:**
> Have you tried the startx command?
That worked! But I am now locked in as Root? How do I change that?
Edit: So all is back to normal thanks to all of your help. I re-installed GDM from synaptic and the re-boot worked 100%.
Thank you all for your support and have a nice day.

---

### Post by mcduck on 2010-12-27
> **germanix said:**
> Hi Mcduck, thank you for your advice. GDM would not install - failed to fetch. Ubuntu desktop may well install, not sure because I aborted the install simply because I actually use the Mint-desktop. I tried using "install mint-desktop instead but no such package found. Do I now need to re-install?

what kind of network connection do you use? The problem with downloading GDM packages would most likely be related to not having a network connection... (and if you can't get gdm package, you can't get ubuntu-desktop either. It depends on gdm.)

The easiest way to connect to a network would be using a Ethernet cable (so no wireless). If it doesn't connect automatically, then try the following command:
```
sudo ifup eth0
```

...and by the way, don't forget to run "sudo apt-get update" before you try to install any package... ;)

Installing ubuntu-desktop metapackage on Mint would not be a problem. At the worst you might end with some program Mint doesn't have by default (and which you can remove afterwards) or login screen changing to default Ubuntu theme or some small thing like that which would be easy fix as well. anyway, if it was just the GDM package you removed, then simply reinstalling that one should be enough.

---

### Post by tru infini on 2011-10-20
I'm having the same troubles. I tried startx command but nothing. I also tried installing gdm (which is already the newsest version)
and ubuntu desktop (says I have held broken packages (something about unity)

---

