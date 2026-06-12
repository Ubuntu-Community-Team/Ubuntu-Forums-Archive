---
title: "Cannot connect to internet (AT&amp;T Wireless) Sierra 875U"
date: 2011-05-31
forum: New to Ubuntu
---

### Post by Elwood_R on 2011-05-31
Hi folks,

I'm brand new to Linux, but I successfully installed Ubuntu 11.04 64bit alongside my XP HE SP3 installation, but I can't for the life of me connect to the internet in Ubuntu. I'd really like to get into Ubuntu, but this issue is causing me not to be able to enjoy it the way I ought to.

I found this thread:

[at&t with aircard 875u on 10.04]("http://ubuntuforums.org/showthread.php?t=1480759&highlight=875u")

And I tried to set up my connection the way the screenshot pdc posted indicated, but still no joy. My aircard, however, is recognized by Ubuntu.

I don't have any other way of connecting to the internet, no dsl or cable out in the boonies where I live, but I get 3G service most of the time in XP and that's how I'm able to post this message here.

Not trying to get sympathy, but I'm in quite a bit of physical pain almost all  the time (peripheral neuropathy) and it causes me not to have the patience I used to have and  I'd appreciate any help you may provide.

I don't even know how to open a command prompt in Ubuntu so please explain things step by step for me. I am fairly proficient with Windows tho'.

Thanks again.

---

### Post by Mariane on 2011-06-01
Sorry, I know only one way of fixing that kind of problems and that is to add software via a cable connection. I realise this is not what you wanted to hear but as no-one else answered... 

Find a network cable and a socket to plug it in. Then you can try two programs, wicd and wifi-radar. 

To open the command prompt:
If you have KDE it is in "Applications/System/Terminal" (or "Applications/System/Konsole"). In Gnome it is in the "System" menu. 

Then you type the following one line at a time, after you press "enter" and give your password you have to wait for it to finish before typing the second line. 

```

sudo apt-get install wifi-radar
sudo apt-get install wicd

```

To launch wifi-radar you type:
```

sudo wifi-radar

```

To launch wicd you type (one line at a time):
```

wicd
wicd-client

```

If the prompt does not reappear in the terminal window (the prompt looks like yourname@yourname:~$ ) you can leave this terminal window opened. 

wicd draws a little icon representing 2 computers (bottom right in KDE, I thing top right in Gnome). You can click on it to start detecting wifi. 

Mariane

---

