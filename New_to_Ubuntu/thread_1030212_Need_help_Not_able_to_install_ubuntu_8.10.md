---
title: "Need help: Not able to install ubuntu 8.10"
date: 2009-01-04
forum: New to Ubuntu
---

### Post by Mejborg on 2009-01-04
Hi! 

I have deleted windows xp on my computer, downloaded ubuntu 8.10, burned it on a CD, tjecked if the CD is allright (in the booting menu) - and it is allright it says.

My problem: When I try to install ubuntu (following the documentation site), choosing 'guided - use whole disk for ubuntu' in the partioning part, it installs the livecd mode (or what you call it) instead of the real version.. And then it says (around that): "crash: Sorry, the program 'Ubiquits' closed unexpectedly'.

What's wrong?

My laptop is an around 3 years old Acer Travelmate 2400, and I used to run Windows XP, it worked without problem, but kind of slow though - why I wanted to change.. 

Thanks in advance!

Mads Mejborg Borup

---

### Post by rolnics on 2009-01-04
If my search is correct then you will probably not be able to run Ubuntu properly, because you only have 256mb ram. You might be able to install a minimal desktop or another version of Ubuntu like Xubuntu which need less amounts of ram.

But don't lose hope, I managed to install Ubuntu on a Dell with only 256mb ram. 

How fast did you burn the iso?

---

### Post by Peter09 on 2009-01-04
I'm a little bit muddled here.

When you boot from the LiveCD you should get a running Ubuntu system - which is based from the CD. (Do you get that?)

You then select the install option, which should then go to the partitioner as you described.(After a few set up questions).

If the install is failing after that then we need to understand a bit more about where the failure is.

How much RAM is on your system?

Edit - Two posts with the same thoughts re RAM - guess you got there just before me :-)

---

### Post by kelean on 2009-01-04
One problem might be that you do not have enough memory to install using the livecd.  I think you need at least 384 or 512 megs of ram to install using the livecd.

You might be better off using the alternative install disk.

---

### Post by kwacka on 2009-01-04
Download/Burn the alternative install CD - this is designed for use with boxes using 256 MB or less; the graphicall install of the LiveCD needs  more than 256 BM

After installation Ubuntu will run on the machine but, as mentioned, Xubuntu will be quicker.

---

### Post by fela on 2009-01-04
I would only run Ubuntu with at least 768MB RAM (even 512MB isn't much for a full blown GNOME installation IMHO). Try Xubuntu, it'll be much more responsive.

---

### Post by Peter09 on 2009-01-04
I run a laptop with 512Mb and no problems. I have 2 Desktops both with 2Gb. In terms of responsiveness, not a great deal of difference - where the difference lies in in capacity - i.e Virtualised machines etc. do not compromise the basic stuff.

---

### Post by fela on 2009-01-04
> **Peter09 said:**
> I run a laptop with 512Mb and no problems. I have 2 Desktops both with 2Gb. In terms of responsiveness, not a great deal of difference - where the difference lies in in capacity - i.e Virtualised machines etc. do not compromise the basic stuff.

OK. Maybe I just run alot of programs at once!

---

### Post by Mejborg on 2009-01-04
Thanks alot for the quick answers. 

RoInics: I have 1 GB ram, so it should not be a problem. I burned the iso with 'standard speed' i guess, think it was 10x though (i did not adjust anything, i just clicked burn - hope you know what i mean).

Peter 09: I booted from the CD on which i have burned down the iso file. Then in the menu I choosed 'install ubuntu' (NOT the 'try ubuntu without changing anything..). Then I go through the steps (keyboard, time aso.) And then in the partioning part i choosed the 'guide - everything ubuntu'. Then i finished the last steps and clicked 'install'. And then it begins to install.. I seems like, though, that it does not run through the whole instalation (it goes from 'deleting.. 5%' strait to 'installing'. And then (when it is finished) its only in livecdmode (where I can see the installing-icon aso.) And then i can see the message in the notification area: 'crash, the program ubiquits closed unexpectedly'

Hope it helps!

---

### Post by Peter09 on 2009-01-04
When you are in the liveCD O/S open a terminal

Applications->Accesories->Terminal
and run the application 

```
gparted
```

You can try to delete all the existing partitions on your drive. See what happens.

If you succeed try the install again.

---

### Post by kelean on 2009-01-04
Try burning at the slowest speed.

---

### Post by PeeZz on 2009-01-04
Did you took the cd out after the installation was done?

Maybe you can try deleting your partitions first..

---

### Post by Mejborg on 2009-01-04
From the problem report:

Title: 'ubiquity crashed with AttributeError in configure (..)

Package: 'i386'

PythonArgs: '['/usr/lib/ubiquity/binubiquity'... only']' (something like that

---

### Post by Mejborg on 2009-01-04
Peter: I try your suggestion, write back when im done with it

Kelean: Maybe i burned in high speed (im not sure), but ubuntu says the cd allright after cdtjeck - so guess it will not help?

PeZz: I did not take the cd out after i was done - i could not. It said: error (and something more i cannot remember). I try deleting my partions now (as Peter explained - write back afterwards

Thanks again!

---

### Post by Mejborg on 2009-01-04
Hi again. 

I did NOT succeed in deleting any partions. When typing 'gparted' in terminal, this message occurs: "Root privileges are required for running GParted"

So: What should i do now? 

Is burning a new cd in slower speed worth trying at all, when ubuntu says my cd is OK in cdtjeck?

---

### Post by rolnics on 2009-01-04
> **Peter09 said:**
> 

```
gparted
```



Do as Peter said in his earlier post but add sudo in front of gparted so it looks like this: - 

```
sudo gparted
```

And also it might be wise to redo your ISO of Ubuntu and burn it a 4x and not higher.

---

### Post by sadaruwan12 on 2009-01-04
Hi,

I think it might be some thing to do with your optical disk drive any way try to follow this guide this will show you step by step of installing Ubuntu this guide is for Ubuntu v8.04 but don't worry 'cos installing the OS is not much different on the newer version too. Before doing a clean installation when you're at the partition dialog go to manual then delete all the partitions you see then create new partitions then try to install it. If it doesn't work try to download the alternate installer and try that also remember when you're burning a CD try to burn it on slower speed like 8x or 16x don't go for the default speed 'cos that setting is the highest speed your optical driver can burn a CD/DVD so alter the speed.

Installation guide :- [Ubuntu installation]("http://news.softpedia.com/news/Installing-Ubuntu-8-04-LTS-84314.shtml")

Alternate installation CD :- [Ubuntu Text based installer download list]("http://www.ubuntu.com/getubuntu/downloadmirrors#mirrors")

\\:D/

---

