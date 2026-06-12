---
title: "Zotac Geforce Gt 220 does not load."
date: 2011-02-08
forum: New to Ubuntu
---

### Post by Unimatrix1982 on 2011-02-08
Help ! Am I in the right forum ? 

I am brand new to Ubuntu. I just intallled it last night and  everything works fine. I just installed a new card : Zotac GeForce Gt  220 PCI to have an HMI output. I removed my old card (which was PCI as  well) and inserted this one. Now when I turn on my computer, I get the  first screen where it gives me the option to acess bios, then a black  screen, then it asks me for my Ubuntu login and password... It took a  couple of minutes to figure out that my login was my computer name. When  I enter both correctly it tells me : Help at help.ubuntu.com then gives  me the option to enter command after the following line television@television: (television being the name of my computer).

---

### Post by Tyggna on 2011-02-08
This is going to help you solve the problem--but it's going to be more information than you probably were expecting.

What you see when it asks for your username and password is the terminal.  This is what Linux really looks like--everything you've seen in linux before was just a pretty "store front."   This terminal is where everything happens--and where you can do everything.

So, with your new card, it seems like it is either not loading the driver properly, or it simply isn't configured.  

If you had an Nvidia card in there before, then there's a good chance it's the latter option.

Once you login and get to the prompt, try typing in:

```
sudo nvidia-xconfig
```

If you had a similar Nvidia card in your system before, there's a good chance that'll fix it.  You can test by typing in:

```
sudo init 3 &&
```

If that works, then you ought to be able to reboot and have it work fine.

If not, then you need a few more commands:

```
apt-get install nvidia-glx nvidia-common nvidia-kernel-common nvidia-settings
```
Installs the driver and settings control for your card.  
From there, repeat the above steps and then let me know how it goes.

---

### Post by Unimatrix1982 on 2011-02-08
It was an Nvidia I will try that tonight thanks !

---

### Post by Unimatrix1982 on 2011-02-08
My old card va a Geforce 8600gts. I tried the commands and they don't work...

---

### Post by losintikfos on 2011-06-17
Hello,

Did you manage to get your Zotac Geforce Gt220 to work?

---

