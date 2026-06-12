---
title: "Trouble Installing Firefox 3.5 in Jaunty"
date: 2009-06-30
forum: New to Ubuntu
---

### Post by Spooky5 on 2009-06-30
I followed the instructions in this [link]("http://www.blogsdna.com/3824/how-to-download-install-firefox-35-on-ubuntu-904-linux.htm"). Since Firefox is already installed I skipped to #3 like the instructions said but Firefox is still showing up as version 3.0.11. What did I do wrong? :confused:

---

### Post by bekind2thenoob on 2009-06-30
don't skip any steps and it should work fine

use method 1 btw

---

### Post by zeroseven0183 on 2009-06-30
Following the instructions per number did not work for me either.

---

### Post by Spooky5 on 2009-06-30
I went back and started with step one. When I paste the line in the terminal and hit enter it says "bash: /etc/apt/sources.list: Permission denied." :-k

---

### Post by zeroseven0183 on 2009-06-30
Yup. And even if adding the lines to my /etc/apt/sources.list it didn't work.
I wonder if I miss something. The instructions were not very clear.

---

### Post by Gary.M on 2009-06-30
Try installing swiftfox instead... it installs alongside and uses your firefox settings and is v3.5

[http://getswiftfox.com/](http://getswiftfox.com/)

---

### Post by zeroseven0183 on 2009-06-30
And like what I've said, I missed something. I was able to download the Firefox 3.5 following the instructions from the link Spooky5 provided. However, when I tried to open it using Terminal, typing:

```
firefox-3.5
```

It started transferring the settings and then it opens the new version.

Now I know. It's time for me to modify my shortcuts. Welcome to Firefox 3.5!

---

### Post by Spooky5 on 2009-06-30
> **zeroseven0183 said:**
> And like what I've said, I missed something. I was able to download the Firefox 3.5 following the instructions from the link Spooky5 provided. However, when I tried to open it using Terminal, typing:

```
firefox-3.5
```

It started transferring the settings and then it opens the new version.

Now I know. It's time for me to modify my shortcuts. Welcome to Firefox 3.5!

That worked! Thanks! :)

---

### Post by Spooky5 on 2009-06-30
How do get my menu shortcut to open 3.5? It still opens the 3.0.11 version.

---

### Post by ~sHyLoCk~ on 2009-06-30
> **Spooky5 said:**
> I went back and started with step one. When I paste the line in the terminal and hit enter it says "bash: /etc/apt/sources.list: Permission denied." :-k

You have to use ```
sudo gedit /etc/apt/sources.list
```

---

### Post by robert shearer on 2009-06-30
> **Spooky5 said:**
> How do get my menu shortcut to open 3.5? It still opens the 3.0.11 version.

Make a new shortcut for 3-5 then you can open either.

this post will walk you through it....
[http://ubuntuforums.org/showthread.php?t=533265](http://ubuntuforums.org/showthread.php?t=533265)

---

### Post by tijmz on 2009-07-01
The instructions from the OP are not complete. If you want to follow them, you should start by using:

```
sudo su
```

However, this is not to be advised, as it lets you run as root. Moreover, just copy/pasting the echo commands from the instructions will mess up your sources.list. 

It's probably better to replace step 1 with a manual addition to your repository list (there's a button that allows you to do so in Synaptic Package Manager: Settings->Repositories->Third Party Software):

```
deb http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu jaunty main
deb-src http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu jaunty main
```

If you do this and follow up with steps 2 and 3 from the instructions, things should work.

Note that you might get an error from Synaptic telling you he can't reload the repositories - this is the thing that is fixed by step 2 :)

---

### Post by jose187 on 2009-07-01
I followed all the steps and it installed Minefield instead of updating my FF 3.0

Is this what should happen?

---

### Post by hgergo on 2009-07-02
Warning with that instructions from that site you will instal 3.5.1 its an alpha build for the next update.

and you must remove the ' sign befor deb and after the line end from there is the error :)

---

### Post by winotree on 2009-07-02
I was initially disappointed that Firefox may not be upgraded in my new install of Xubuntu 9.04 until I found this link  [http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox)  which did everything I wanted including setting up a connection in my menus -- it just worked.  :-)

---

### Post by colau on 2009-08-15
Easiest way to install firefox-3.5!
[psychocats]("http://www.psychocats.net/ubuntu/firefox")

---

