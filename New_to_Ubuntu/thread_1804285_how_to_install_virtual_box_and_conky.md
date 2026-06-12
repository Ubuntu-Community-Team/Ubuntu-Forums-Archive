---
title: "how to install virtual box and conky"
date: 2011-07-14
forum: New to Ubuntu
---

### Post by sravan008 on 2011-07-14
Hi guys :) , can any one tell me how to install virtual box in ubuntu 11.04 and please tell me the conky installation process also :D

---

### Post by ~!geek!~ on 2011-07-14
Did you try installing them using software center or synaptic manager. If not give it a chance. Their  searchbox works quite well. Just search for them and install them with a few clicks.

---

### Post by wolfen69 on 2011-07-14
[http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

```
sudo apt-get install conky
```

---

### Post by seawolf167 on 2011-07-14
Here is a little prettier configuration and how-to for Conky called [Conky Colors]("http://gnome-look.org/content/show.php/CONKY-colors?content=92328")

---

### Post by amjjawad on 2011-07-14
> **wolfen69 said:**
> [http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

```
sudo apt-get install conky
```

To the OP:

Don't forget to do:

> sudo apt-get update

before the above command :)

---

### Post by grahammechanical on 2011-07-14
I am in the process of installing Oneiric Ocelot 11.10 in virtualbox. So, here is a tip. You have to set the amount of RAM for the virtual machine. If you set it at more than half of the actual RAM on your computer, you get a warning that this setting will slow down the host machine. But, if you set the amount of RAM too low then you may have difficulties installing an OS into the virtual machine

I had a problem getting a live CD to run until I increased the allotted RAM and display memory allocation. Another point, you will not get Internet access unless you the network setting as Attached to NAT.

Third, you cannot write to the CD drive unless you set it to passthrough. It will not even know you have one unless you set Storage to your CD/DVD drive. It will set itself up with a virtual CD drive. Which is useful if you want to install Guess Additions. You will want to do this. It will download an iso image to the desktop of the virtual machine and the virtual CD drive reads it. Without Guess Additions installed you are limited with what you can do and how large you can make the screen.

Regards.

One more thing. When you set up a new virtual machine the wizard will let you set the OS to Linux and Ubuntu and even 64bit Ubuntu. This helps things along.

---

### Post by wildmanne39 on 2011-07-14
> **sravan008 said:**
> Hi guys :) , can any one tell me how to install virtual box in ubuntu 11.04 and please tell me the conky installation process also :D
Hi, for help on conky you should go to the conly thread.
[http://ubuntuforums.org/showthread.php?t=281865&highlight=conky](http://ubuntuforums.org/showthread.php?t=281865&highlight=conky)

Also the link that was given to you to download virtualbox you should read the documentation it will answer most of your questions and should be read before you install virtualbox and attempt to setup a vm.

---

### Post by sravan008 on 2011-07-15
Thanks for the replies guys :) 

I downloaded the virtual box through the official site but it not installing in my system. when i am giving the double click on the it says it could not opened etcc..... can any one please suggust me what i have to do now .?? and i will follow above mention process now :)

for conky i will follow above mentioned sites and i will cum bak here in very soon :)

thanks alot once again

---

### Post by grahammechanical on 2011-07-15
You say

> through the official site

was this the Ubuntu software Centre or the Virtualbox web site?

I downloaded mine from the software centre. It was in the Dash. When you first click on the icon you get a wizard to set you going.

Regards.

---

### Post by sravan008 on 2011-07-15
Finally i got the virtual box app in software center , @abv thanks buddy and can u please tell me the conky installation process. i didn't understand from the prev links :(

---

### Post by seawolf167 on 2011-07-15
> **sravan008 said:**
> Finally i got the virtual box app in software center , @abv thanks buddy and can u please tell me the conky installation process. i didn't understand from the prev links :(

Follow the instructions in any of these links.

[Official wiki]("http://wiki.conky.be/index.php?title=Conky_Wiki")

[Conky manpage]("http://conky.sourceforge.net/docs.html")

[Conky-colors setup]("http://gnome-look.org/content/show.php/CONKY-colors?content=92328")

[Ubuntu forums how to post]("http://ubuntuforums.org/showthread.php?p=6365702")

[Wikihow link]("http://www.wikihow.com/Configure-Conky")

[Older ubuntugeek howto]("http://www.ubuntugeek.com/conky-a-light-weight-system-monitor-for-ubuntu-linux-systems.html")

---

### Post by wildmanne39 on 2011-07-15
Hi, the link I gave you in my last post was so you can ask questions for conky and get a script to use, please note it will take a little setting up it is not automated.

---

### Post by sravan008 on 2011-07-18
Thanks for the links , let me check in this evening :)

---

