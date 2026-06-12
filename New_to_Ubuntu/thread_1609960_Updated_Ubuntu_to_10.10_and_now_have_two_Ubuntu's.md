---
title: "Updated Ubuntu to 10.10 and now have two Ubuntu's"
date: 2010-10-31
forum: New to Ubuntu
---

### Post by Chooch Train on 2010-10-31
[FONT=Times New Roman][SIZE=3]This is my first time on a form so if I did not respond back I'm having difficulty locating and the use of the form. I'm a fairly new user to Ubuntu and love it. Would like more information on donating now that I've gotten several members of my family to use it and I just feel that that is the right thing to do because I use it so much now. My nephew uses nothing but Ubuntu. I would also like to use nothing but Ubuntu but I like using a speech to text program on Windows 7 called DragonDictate. The support and help out there on the web for Ubuntu issues for new users has been nothing but spectacular. My particular problem that I am having now needs some explanation. I have recently upgraded my Ubuntu to 10.10. Now when I shut off my computer and start up my computer I have 2 Ubuntu selections like I am dual booting to separate OSs. Both of the Ubuntu's are running 10.10.  Both of the Ubuntu's have my information associated with. However one of the Ubuntu's I call the bizarro Ubuntu does not have to correct theme and is really slow and uses a lot of memory or it does not have a lot of memory allocated to it. My first instinct was to uninstall the bizarro Ubuntu but I was wondering if there is a simpler fix and would that do damage to the other Ubuntu? Thank you for your time.[/SIZE][/FONT]

---

### Post by Kyluke on 2010-10-31
Hey, have you tried ubuntu tweak?
[http://launchpad.net/ubuntu-tweak/0.5.x/0.5.7/+download/ubuntu-tweak_0.5.7-1_all.deb](http://launchpad.net/ubuntu-tweak/0.5.x/0.5.7/+download/ubuntu-tweak_0.5.7-1_all.deb)

In this you can remove the unnecessary kernel and files  using the package cleaner tab.

---

### Post by coffeecat on 2010-10-31
You do not have two Ubuntus. The two entries you see in the grub menu  are for two versions of the kernel, that is all. Since you have done an  upgrade to 10.10, I guess the older kernel will be the 10.04 one. Are  the two "Ubuntus" 2.6.32-* and 2.6.35-*? The 2.6.32 is from 10.04 and  2.6.35 is for 10.10.

You will find that when the 10.10 kernel is upgraded from 2.6.35-22 to  2.6.35-23 (possibly -24 - they sometimes skip a minor number) you'll  have menu entries for both. The old kernel is never removed  automatically. This is because on rare occasions the newer version of  the kernel fails with some hardware combinations, so you still have a  working kernel to boot into. In this case the 10.04 kernel is clearly  problematic so it should be OK to uninstall it. But most people like to  keep the immediately previous kernel for just in case.

By the way, please use the default forum font for the main text in posts - it is more readable.

---

### Post by GabrielYYZ on 2010-10-31
maybe his 10.04 kernel was the generic one and the 10.10 kernel is PAE? 

i say this because when i installed 10.04 the connection didn't work during installation, so the kernel defaulted to generic but when i upgraded 10.10 my connection was working and i got the PAE. i didn't have the "ubuntu dual booting" problem chooch train has though, so i don't know.

---

### Post by Chooch Train on 2010-11-01
[FONT=Times New Roman][SIZE=3][FONT=Verdana]Hey thank you guys so much. Sorry it took so long to get back I hope that I haven't broken some kind of unspoken rule. I checked out everything that you guys were talking about and all of your information was fantastic. What else can I expect from Ubuntu users. Now the decision is whether to delete the old. I think the information about leaving the old kernel just in case is sound advice. Thanks again you guys, you guys are the HEAT.[/FONT]
[/SIZE][/FONT]

---

