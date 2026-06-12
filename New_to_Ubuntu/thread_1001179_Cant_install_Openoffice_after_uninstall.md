---
title: "Cant install Openoffice after uninstall"
date: 2008-12-03
forum: New to Ubuntu
---

### Post by VitaminBB on 2008-12-03
I tried to load openoffice writer this morning and got an error, I cant remember what the error was but it kept happening when I tried to open writer.

I figured some file is hooped and decided to reinstall, this was a mistake.

I removed openoffice and most of the programs along with it, all I could find anyway and then tried to reinstall, thats when I would get this problem with synaptic ...

[IMG]http://i79.photobucket.com/albums/j121/ArghMonkey/fgfgfg.jpg[/IMG]

Now no matter how I try to do it I cant seem to install openoffice, its catch 22, if I install one little part it tells me it needs a dependency but when I go to install that dependency it gives me another dependency I originally tried to install, I need to get a chicken but for that I need an egg and for that I need a chicken and for that I need a  ....

So this is my situation ...

I even tried to install openoffice by deb file, turned out to be a huge waste of time and accomplished nothing ...

FYI I had openoffice 3 installed and openoffice repos in my source list, after uninstalling openoffice I notice in synaptic that it only gives me an option to install openoffice 2.4, odd ...

I deselected the openoffice repos and tried to install openoffice, still wont work ...

I also even deleted the home folder for openoffice, thinking that might help, no dice ...

Any ideas ?

---

### Post by RequinB4 on 2008-12-03
run

```
sudo apt-get update
```

```
sudo aptitude install openoffice.org
```

You can also get OO.o 3 manually from [http://download.openoffice.org/other.html#en-US](http://download.openoffice.org/other.html#en-US) but i would wait until the package is put back to make everything cleaner.  Ask if you need help installing

---

### Post by Simplicius on 2008-12-03
> **VitaminBB said:**
> 
FYI I had openoffice 3 installed and openoffice repos in my source list, after uninstalling openoffice I notice in synaptic that it only gives me an option to install openoffice 2.4, odd ...

VitaminBB,
I can't help you with your problem but I understand that OO 3 was removed because they found a bug that they wanted to sort out. I think they'll put OO 3 back when they are confident it is good enough.

---

### Post by binbash on 2008-12-03
you have to install the deb from official website.OO3 pkgs are removed from your repo

---

### Post by kansasnoob on 2008-12-03
What's the output of:

```
sudo apt-get -f install
```

---

### Post by evilkastel on 2008-12-03
If you really need OO you should get the debs from [www.openoffice.org](www.openoffice.org) and install them. if one asks for a dependency, seek that one and install first. There is a way to do this easier from terminal but since the dependencies for OO are so tricky i will recommend taking the time to underrstand what you are doing and installl the debs manualy. Otherwise, hold on until they get OO back in the repos.

---

### Post by kansasnoob on 2008-12-03
And what version of Ubuntu are you running?

---

### Post by thomas228 on 2008-12-03
Try the following and see if it helps
First download 00o3 from
[http://download.openoffice.org/other.html]("http://download.openoffice.org/other.html")
from the  Linux DEB colum on the English row
Now to insure all versions of openoffice are removed
 
In terminal you can remove ver 2.4 with
sudo apt-get remove openoffice*.* 

If you have already installed Openoffice 00o3 and need to remove it before reinstalling here is a rather long termianal command (just cut and paste)

sudo apt-get remove ooobasis3.0-base ooobasis3.0-binfilter ooobasis3.0-calc ooobasis3.0-core01 ooobasis3.0-core02 ooobasis3.0-core03 ooobasis3.0-core04 ooobasis3.0-core05 ooobasis3.0-core06 ooobasis3.0-core07 ooobasis3.0-draw ooobasis3.0-en-us ooobasis3.0-en-us-base ooobasis3.0-en-us-binfilter ooobasis3.0-en-us-calc ooobasis3.0-en-us-draw ooobasis3.0-en-us-help ooobasis3.0-en-us-impress ooobasis3.0-en-us-math ooobasis3.0-en-us-res ooobasis3.0-en-us-writer ooobasis3.0-gnome-integration ooobasis3.0-graphicfilter ooobasis3.0-images ooobasis3.0-impress ooobasis3.0-javafilter ooobasis3.0-kde-integration ooobasis3.0-math ooobasis3.0-onlineupdate ooobasis3.0-ooofonts ooobasis3.0-ooolinguistic ooobasis3.0-pyuno ooobasis3.0-testtool ooobasis3.0-writer ooobasis3.0-xsltfilter openoffice.org3 openoffice.org3-base openoffice.org3-calc openoffice.org3-dict-en openoffice.org3-dict-es openoffice.org3-dict-fr openoffice.org3-draw openoffice.org3-en-us openoffice.org3-impress openoffice.org3-math openoffice.org3-writer openoffice.org-ure


When this was finished I opened a terminal and did the following

tar -xvzf OOo_3.0.0_LinuxIntel_install_en-US_deb.tar.gz 
cd OOO300_m9_native_packed-1_en-US.9358 
cd DEBS 
sudo dpkg -i *.deb 
cd desktop-integration 
sudo dpkg -i openoffice.org3.0-debian-menus_3.0-9354_all.deb
 
You should have all 7 options in Applications>Office

---

### Post by thomas228 on 2008-12-03
Try the following and see if it helps
First download 00o3 from
[http://download.openoffice.org/other.html]("http://download.openoffice.org/other.html")
from the  Linux DEB colum on the English row

Now to insure all versions of openoffice are removed
 
In terminal you can remove ver 2.4 with
sudo apt-get remove openoffice*.* 

If you have already installed Openoffice 00o3 and need to remove it before reinstalling here is a rather long termianal command (just cut and paste)

sudo apt-get remove ooobasis3.0-base ooobasis3.0-binfilter ooobasis3.0-calc ooobasis3.0-core01 ooobasis3.0-core02 ooobasis3.0-core03 ooobasis3.0-core04 ooobasis3.0-core05 ooobasis3.0-core06 ooobasis3.0-core07 ooobasis3.0-draw ooobasis3.0-en-us ooobasis3.0-en-us-base ooobasis3.0-en-us-binfilter ooobasis3.0-en-us-calc ooobasis3.0-en-us-draw ooobasis3.0-en-us-help ooobasis3.0-en-us-impress ooobasis3.0-en-us-math ooobasis3.0-en-us-res ooobasis3.0-en-us-writer ooobasis3.0-gnome-integration ooobasis3.0-graphicfilter ooobasis3.0-images ooobasis3.0-impress ooobasis3.0-javafilter ooobasis3.0-kde-integration ooobasis3.0-math ooobasis3.0-onlineupdate ooobasis3.0-ooofonts ooobasis3.0-ooolinguistic ooobasis3.0-pyuno ooobasis3.0-testtool ooobasis3.0-writer ooobasis3.0-xsltfilter openoffice.org3 openoffice.org3-base openoffice.org3-calc openoffice.org3-dict-en openoffice.org3-dict-es openoffice.org3-dict-fr openoffice.org3-draw openoffice.org3-en-us openoffice.org3-impress openoffice.org3-math openoffice.org3-writer openoffice.org-ure


When this was finished I opened a terminal and did the following

tar -xvzf OOo_3.0.0_LinuxIntel_install_en-US_deb.tar.gz 
cd OOO300_m9_native_packed-1_en-US.9358 
cd DEBS 
sudo dpkg -i *.deb 
cd desktop-integration 
sudo dpkg -i openoffice.org3.0-debian-menus_3.0-9354_all.deb
 
You should have all 7 options in Applications>Office

Hope this helps

Tom

---

### Post by VitaminBB on 2008-12-03
> **RequinB4 said:**
> run

```
sudo apt-get update
```

```
sudo aptitude install openoffice.org
```

You can also get OO.o 3 manually from [http://download.openoffice.org/other.html#en-US](http://download.openoffice.org/other.html#en-US) but i would wait until the package is put back to make everything cleaner.  Ask if you need help installing

Something so simple, of course ...

Thanks for your help that did the trick :)

Thanks everyone for your help!

---

