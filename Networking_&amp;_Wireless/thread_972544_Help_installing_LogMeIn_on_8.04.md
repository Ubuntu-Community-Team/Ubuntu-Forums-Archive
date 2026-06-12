---
title: "Help installing LogMeIn on 8.04"
date: 2008-11-05
forum: Networking &amp; Wireless
---

### Post by Excedio on 2008-11-05
Hey Everyone,

Can someone please explain to me how to install LogMeIn on ubuntu 8.04? I already downloaded the tarball and extracted the files already, but i don't really know what to do from there.

I tried the README file, and i'm sure that it's pretty easy to follow for someone who could even be called an intermediate user of the terminal and using commands, but I'm pretty new, and don't know how to use the commands.

The files are in /home/excedio/Downloads/hamachi-0.9.9.9-20-lnx i(if that helps).

Here are the steps it says to follow, please tell me exactly what i should be typing when doing these steps:

Quick Start

	Run 'make install' and then 'tuncfg' from under the root account

	Run 'hamachi-init' to generate crypto identity (any account).

	Run 'hamachi start' to launch Hamachi daemon.

	Run 'hamachi login' to put the daemon online and to create an account.

	Run 'hamachi join <network>' to join the network.

	Run 'hamachi go-online <network>' to go online in the network.

	Run 'hamachi list' to list network members and their status.

---

### Post by Excedio on 2008-11-06
Please guys...does anyone use LogMeIn?


Can someone suggest another easy to use free(beer) alternative? Oh and if alternative...how to I get and install it?

Thanks Everyone.

---

### Post by CommieTechie on 2008-11-15
Ok well no guarantee I can help, as I haven't been on ubuntu very long myself, but if you just need to know what to do to install / run it, its fairly simple.


first you'll need to open a terminal: Accessories > Terminal

you said you untarred the files to a directory, so next change to the directory you untarred it to. in terminal type

```
cd '/home/excedio/Downloads/hamachi-0.9.9.9-20-lnx'
```

next, to install it type 

```
sudo make install
``` it will ask for your root password

after its installed (it shouldn't take long) type

```
sudo tuncfg
``` to start the tuncfg daemon. You'll have to do this every time you boot your computer before you can use hamachi.

after that, its easiest to use one of the GUIs that you can find online. one example that is fairly simple is [http://hamachi-gui.sourceforge.net/]("http://hamachi-gui.sourceforge.net/")

its much like the windows GUI for hamachi, and fairly straightforward. 

remember everytime you boot your computer you'll have to run ```
sudo tuncfg
``` from the terminal before you can use hamachi.

Hopefully that actually helped :/

---

### Post by Excedio on 2008-11-18
Your help is much appreciated. After talking to a co-worker of mine (my personal Linux Guru) he redirected me to a program from a company called No Machine.

I am now running NX Server on my home PC and am running NX Client on my laptop (100% Linux user now). The NX programs were a breeze for me to download and install, getting access to my PC from outside of my home network took some doing and alot of pestering of my Guru, but it finally works.

I like NX better than LogMeIn at this point. Easy to use, easy to setup, and in my opinion it more secure since it runs through ssh and not through LogMeIn's website.

Thanks again though, I may just install it anyway to try it out. :)

---

### Post by Mr_JMM on 2008-11-19
Glad you found an alternative.

For future benefit:

[http://www.howtoforge.com/configure-remote-access-to-your-ubuntu-desktop]("http://www.howtoforge.com/configure-remote-access-to-your-ubuntu-desktop")

---

