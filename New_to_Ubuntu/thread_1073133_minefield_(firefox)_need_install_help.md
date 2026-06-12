---
title: "minefield (firefox) need install help"
date: 2009-02-18
forum: New to Ubuntu
---

### Post by ghostofzuul on 2009-02-18
Hello,

I'm trying to install the latest version of minefield (aka firefox)and I downloaded the file and unarchived it and have it on my desktop however the binary doesn't seem to be working so i can't install it...

any ideas? 

thanks...

---

### Post by ashwinhgtx on 2009-02-18
I don't think you need to install it as such. You just need to untar it and then click the shell script named firefox in the folder. It should launch Minefield.
Make the shell script executable by changing it in the properties dialog which you get by right clicking it in Nautilus. You can also use chmod to do it but i am not sure of the exact command format.

---

### Post by ghostofzuul on 2009-02-18
> **ashwinhgtx said:**
> I don't think you need to install it as such. You just need to untar it and then click the shell script named firefox in the folder. It should launch Minefield.
Make the shell script executable by changing it in the properties dialog which you get by right clicking it in Nautilus. You can also use chmod to do it but i am not sure of the exact command format.

i tried that but it didn't work... i installed firefox completely... and reinstalled it... now i can't launch firefox at all... 

either version. it acts like it's trying to start but it just quits... major problem that.

---

### Post by ashwinhgtx on 2009-02-18
Try purging the config files after uninstalling firefox. Then reinstall it. See if it makes any difference.

---

### Post by ghostofzuul on 2009-02-18
> **ashwinhgtx said:**
> Try purging the config files after uninstalling firefox. Then reinstall it. See if it makes any difference.

i'm pretty new to ubuntu/linux so how would i go about purging the config files? 

i've downloaded the file again to try and reinstall... this is the file i'm using...

[http://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-trunk/firefox-3.2a1pre.en-US.linux-x86_64.tar.bz2](http://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-trunk/firefox-3.2a1pre.en-US.linux-x86_64.tar.bz2)

thanks for your help...

---

### Post by ashwinhgtx on 2009-02-18
Is your original Firefox 3.0 installation working properly? I suggested purging the files if you were planning to reinstall firefox 3.0.

sudo apt-get --purge remove firefox

I got it from here.
[http://www.debian.org/doc/manuals/apt-howto/ch-apt-get.en.html#s-remove](http://www.debian.org/doc/manuals/apt-howto/ch-apt-get.en.html#s-remove)

Then reinstall firefox using sudo apt-get install firefox

You can do all this in Synaptic also. I don't remember the exact options as i"m on Kubuntu and am using Adept now.
Don't remove firefox 3.0 if it is working fine.

I'm not sure why the 3.2a binary is not working properly. I just tested out 3.1b2 and it works smoothly on my machine.

---

### Post by ghostofzuul on 2009-02-18
> **ashwinhgtx said:**
> Is your original Firefox 3.0 installation working properly? I suggested purging the files if you were planning to reinstall firefox 3.0.

sudo apt-get --purge remove firefox

I got it from here.
[http://www.debian.org/doc/manuals/apt-howto/ch-apt-get.en.html#s-remove](http://www.debian.org/doc/manuals/apt-howto/ch-apt-get.en.html#s-remove)

Then reinstall firefox using sudo apt-get install firefox

You can do all this in Synaptic also. I don't remember the exact options as i"m on Kubuntu and am using Adept now.
Don't remove firefox 3.0 if it is working fine.

I'm not sure why the 3.2a binary is not working properly. I just tested out 3.1b2 and it works smoothly on my machine.



sorry for the confusion... i tried to install the 3.2 binary and it didn't work. after i tried to do that install (described here: [http://www.debianadmin.com/install-firefox30a1-in-ubuntu-and-list-of-addons.html](http://www.debianadmin.com/install-firefox30a1-in-ubuntu-and-list-of-addons.html)) my regular 3.0 (that installed with ubuntu) stopped working... 

so now i'm trying to reinstall firefox b/c it's not on there at all... if i can, i'd like to install the version of minefield i originally set out to install... not sure if that's clearer now...

thanks again...

---

### Post by ghostofzuul on 2009-02-18
it says package firefox not removed because not installed. however if i go to synaptic package manager it shows it installed there...

now i'm really confused.

---

### Post by ghostofzuul on 2009-02-18
> **ghostofzuul said:**
> it says package firefox not removed because not installed. however if i go to synaptic package manager it shows it installed there...

now i'm really confused.

nevermind this... shouldhave been firefox-3.0.

removed successfully. now will try to reinstall.

---

### Post by ashwinhgtx on 2009-02-18
> **ghostofzuul said:**
> sorry for the confusion... i tried to install the 3.2 binary and it didn't work. after i tried to do that install (described here: [http://www.debianadmin.com/install-firefox30a1-in-ubuntu-and-list-of-addons.html](http://www.debianadmin.com/install-firefox30a1-in-ubuntu-and-list-of-addons.html)) my regular 3.0 (that installed with ubuntu) stopped working... 

so now i'm trying to reinstall firefox b/c it's not on there at all... if i can, i'd like to install the version of minefield i originally set out to install... not sure if that's clearer now...

thanks again...

Those instructions are for installing FF 3.0a1 not 3.2a1

---

### Post by ghostofzuul on 2009-02-18
> **ashwinhgtx said:**
> Those instructions are for installing FF 3.0a1 not 3.2a1

i have the 3.2a1 folder on the desktop. when i click on it i can see all of the firefox files in there. i right click on the file marked "firefox" and then select "run" and nothing happens. i also tried to "run" the file labeled "mozilla-run.sh" and that didn't work either. 

perhaps i'm trying to open or install the wrong file?

---

### Post by ghostofzuul on 2009-02-18
> **ashwinhgtx said:**
> Those instructions are for installing FF 3.0a1 not 3.2a1

duh. was trying to install the 64 bit version by accident. 

carless mistake. 

i have it running now. but i have 2 questions.

1. obviously the folder shouldn't be on my desktop, where the proper place to put the firefox folder in the filesystem?

2. how do i make an icon or have it in the "applications" tab?

thanks!

---

### Post by ghostofzuul on 2009-02-18
solved


i just  moved the firefox folder into the HOME folder and it works fine. 

found the icon for minefield in firefox>icons and created application using the application creator and then changed the icons in the properties of the newly created app shortcut.

---

### Post by ashwinhgtx on 2009-02-18
Glad to know that you sorted out your problems yourself. I think you should mark this thread as solved now.

---

### Post by SunnyRabbiera on 2009-02-18
Yeh but why use the beta minefeild as opposed to the stable?
The latest stable is firefox 3.0.6

---

### Post by ghostofzuul on 2009-02-18
> **ashwinhgtx said:**
> Glad to know that you sorted out your problems yourself. I think you should mark this thread as solved now.

I haven't been able to mark threads solved. when i got to thread tools that's not an option...

---

### Post by ghostofzuul on 2009-02-18
> **SunnyRabbiera said:**
> Yeh but why use the beta minefeild as opposed to the stable?
The latest stable is firefox 3.0.6

i've used minefield on my mac for years as i find it to be faster and more java friendly than firefox. i don't mind a few bugs here and there i'd rather have a faster more up-to-date browser...

i wish it was supported through package manager but it has it's own update feature so i'll just have to remember to do it manually...

---

### Post by Sealbhach on 2009-02-18
> **SunnyRabbiera said:**
> Yeh but why use the beta minefeild as opposed to the stable?
The latest stable is firefox 3.0.6

It's a lot faster, it's got a new gecko engine or something.

PS> make sure you install the Add-On "Nightly Tester Tools". It allows you to force compatibility of your Add-Ons so that you can use them.

.

---

### Post by ghostofzuul on 2009-02-19
> **Sealbhach said:**
> It's a lot faster, it's got a new gecko engine or something.

PS> make sure you install the Add-On "Nightly Tester Tools". It allows you to force compatibility of your Add-Ons so that you can use them.

.

thanks for the tip!

---

### Post by Hugo Bio on 2009-03-13
I managed to install minefield correctly, but it overrides my firefox installation. Can't i use both?

---

