---
title: "Help pls: Newbie Install &amp; won't upgrade &amp; other choppy problems"
date: 2009-12-02
forum: New to Ubuntu
---

### Post by collards on 2009-12-02
Hi all & help please,

I want to use Ubuntu & want to get rid of my Windows and can't afford a new computer right now so I hope these problems can be fixed:

I have tried to be as detailed as possible:

-- I double-booted Ubuntu alongside W98SE; but  I could not get updates-- not enough disk space.
--the installed program acted as slow & choppy as it did when I tried it just using the disk.
--the desktop opened with a black square in the center
--when I typed text or tried to delete or highlight it was slow and choppy and patchy and left bits or fragments of text images as I was working.
--internet searching was slow and choppy.  
-tried to open a couple of programs--terminal & system monitor-- and they opened to a blank white square.  others I tried opened ok.

Using GParted, I shrunk Windows to allocate more space and increased the Ubuntu partition to 12.22 G & Linux-swap to 580.44M  

It took several hours because I changed the sizes a few times before applying...& didn't think to undo some of the steps.   

When it was done there was a message on the pending window that said " completed with 12 warnings"  I can't find out what the warnings meant because there was no detail;  & thought maybe it was because the screensaver went gray many times. 

Now the same problems above remain plus:

--when I tried to Update Manager>install updates it opened to a white square and the screen darkened and froze.  I had to use the power to shut down & start up again.   the same thing happened when I opened computer janitor--froze.

--then when I tried to enter the Ubuntu forum the screen turned grey, - then darker grey-then back to white in a wave on the screen from bottom to top and did this several times. 

while I was trying to create this thread thi first time,  the forum pages went blank-except for the menu buttons--i tried from other work spaces--same thing--then I tried to go to my yahoo mail and it worked.  I tried a couple more times and was able to log back into Ubuntu forum.

Any help????   don't want to give up on Ubutu.


I have 512M RAM   & 700mhz

collards

---

### Post by zkriesse on 2009-12-02
Hmmm...sounds as if either the pc is too slow or not enough space. In any case I would have you check out Xubuntu. It's an Ubuntu derivative that is MUCH smaller and lighter. It was built for the sole purpose of usability on older & slower systems. The link for it is, [Xubuntu.org]("http://www.xubuntu.org/") Hope this helps you. Don't give up hope yet!

---

### Post by gmjs on 2009-12-02
The amount of RAM available sounds good, but perhaps the processor and graphics card are letting things down a little.

You might like to try the lighter XFCE Desktop environment instead of GNOME, either by installing [Xubuntu]("http://www.xubuntu.org") instead, or installing XFCE within your current installation with the following at the terminal:

```
sudo aptitude install xfce4
```

Perhaps try the LiveCD for Xubuntu first.

If you're still no better off, perhaps an earlier version would suit the machine better (e.g. 8.04).

Other than that, you might have to give up Ubuntu in favour of a much lighter distribution (perhaps Puppy Linux or DSL).

Hope this helps,

Graham


EDIT: Sorry for the almost double post Zachk18, you were quicker than me!

---

### Post by zkriesse on 2009-12-02
It's cool man...glad you posted!

---

### Post by collards on 2009-12-02
> **gmjs said:**
> The amount of RAM available sounds good, but perhaps the processor and graphics card are letting things down a little.

You might like to try the lighter XFCE Desktop environment instead of GNOME, either by installing [Xubuntu]("http://www.xubuntu.org") instead, or installing XFCE within your current installation with the following at the terminal:

```
sudo aptitude install xfce4
```Perhaps try the LiveCD for Xubuntu first.

If you're still no better off, perhaps an earlier version would suit the machine better (e.g. 8.04).

Other than that, you might have to give up Ubuntu in favour of a much lighter distribution (perhaps Puppy Linux or DSL).

Hope this helps,

Graham


EDIT: Sorry for the almost double post Zachk18, you were quicker than me!

Thank you & Zachk18 !!

I have heard of Xubuntu.  Is this a place where you can tell me the basic difference between the two -- in terms of how xubuntu may perform & any program or features difference.

Thanks,
Collards

---

### Post by Drakkenkill on 2009-12-02
i have a similar problem but i cant use synaptic package manager goes to a blank window with a darkened background everytime i try to download a program terminal as well and all videos are far from smooth no matter if it;s you tube or google videos ect  my OS is Ubuntu 9.10 265mb ram 20 gb quantum fireball intel graphics controller pentium 3

---

### Post by gmjs on 2009-12-02
> **collards said:**
> Is this a place where you can tell me the basic difference between the two -- in terms of how xubuntu may perform & any program or features difference.

It's **very** similar.  The main thing I've noticed is that Xubuntu doesn't have OpenOffice installed by default--it includes AbiWord and Gnumeric for word processing and spreasheets.  Of course, you can still add this later if you want to (**sudo aptitude install openoffice.org3**).

Also, it uses a different default file browser--it's still good to use though (reminds me of the Mac OS 'Finder') Exaile instead of Rhythmbox Music player, a slightly different image preview app and the F-Spot photo organiser isn't installed by default (again, easily installed with **sudo aptitude install f-spot**).

I'm a little disappointed about the default text editor's lack of syntax highlighting ;).

Other than that, it's pretty much Ubuntu!

---

### Post by gmjs on 2009-12-02
> **Drakkenkill said:**
> i cant use synaptic package manager goes to a blank window with a darkened background everytime i try to download

Yes, Ubuntu 'greys out' a window when it thinks it has crashed by turning it greyscale.

It sounds like a very similar issue, although perhaps more due to the lower amount of RAM.  Again, Xubuntu sounds like a better choice for your PC specification.  I have known increasing the amount of swap space improving a similar situation to this one in the past, but I'd still favour the Xubuntu approach.

Hope this helps,

Graham

---

### Post by collards on 2009-12-02
> **Drakkenkill said:**
> i have a similar problem but i cant use synaptic package manager goes to a blank window with a darkened background everytime i try to download a program terminal as well and all videos are far from smooth no matter if it;s you tube or google videos ect  my OS is Ubuntu 9.10 265mb ram 20 gb quantum fireball intel graphics controller pentium 3

Thanks for responding.

Where in Ubuntu can I look up my hardware profiles.   I did that in Windows but didn't take notes for everything--I'd like to look up my graphic card or anything else you all may suggest.   

I am also in Wikipedia looking up Xubuntu.   

Any Xubuntu experience to share anyone?

Thanks,
Collards

---

### Post by gmjs on 2009-12-02
> **collards said:**
> 
Where in Ubuntu can I look up my hardware profiles.

You can list the PC's hardware at the terminal with the following command:

```
lshw
```

(it's short for 'list hardware')

You might find more useful information in the PCI devices list:

```
lspci
```

For information about the graphics card only, try:

```
lspci | grep VGA
```

Hope that helps.

---

### Post by ajgreeny on 2009-12-02
You could also try installing the minimal install CD and adding the lxde desktop.  It is blazingly fast and attractive, though not as configurable as gnome or xfce, but I tried it a while ago and really liked it as an alternative desktop.

I think there was a ubuntu derivative available with the lxde desktop, but can't remember what it was called; do a search yourself and you may be able to find something.

OK, here we go, a quich search found these:-
**Ubuntu variants with LXDE pre-installed**

 If you are installing Ubuntu + LXDE on a new machine, there are some existing Ubuntu-based distros using LXDE. Maybe you can try them first. 
 
[LIST]
[*][WattOS]("http://www.planetwatt.com/") - Designed for older and low power computers (we make new ones screaming fast also :) ).
[*][MoonOS]("http://www.moonos.co.cc/") - an operating system featuring art.
[*][PUD GNU/Linux LXDE version]("http://distrowatch.com/?newsid=04826") - Lightweight and small Ubuntu-based installable live CD featuring LXDE.
[*][U-lite]("http://u-lite.org/?q=node/2") - A member of [Ubuntu Derivative Team]("https://wiki.ubuntu.com/DerivativeTeam/Derivatives") featuring LXDE.
[*] [Masonux]("http://wiki.lxde.org/en/Masonux")[[1]]("http://sites.google.com/site/masonux/home") - Ubuntu remix featuring LXDE that includes Firefox, Pidgin, Ubuntu's normal networking applet, and Synaptic package manager preinstalled.
[*][BoomBuntu]("http://boombuntu.wordpress.com/") - An extra light & super fast distribution based on Ubuntu & LXDE!
[/LIST]

---

### Post by collards on 2009-12-02
> **gmjs said:**
> You can list the PC's hardware at the terminal with the following command:

```
lshw
```(it's short for 'list hardware')

You might find more useful information in the PCI devices list:

```
lspci
```For information about the graphics card only, try:

```
lspci | grep VGA
```Hope that helps.


Thank you  gjms an all,

Okay, now here is where my newbieness is showing.  First the terminal only gives me a blank screen so I can't use that ---I guess.

and how do I use code follow your advice.

---

### Post by collards on 2009-12-02
> **ajgreeny said:**
> You could also try installing the minimal install CD and adding the lxde desktop.  It is blazingly fast and attractive, though not as configurable as gnome or xfce, but I tried it a while ago and really liked it as an alternative desktop.

I think there was a ubuntu derivative available with the lxde desktop, but can't remember what it was called; do a search yourself and you may be able to find something.

OK, here we go, a quich search found these:-
**Ubuntu variants with LXDE pre-installed**

 If you are installing Ubuntu + LXDE on a new machine, there are some existing Ubuntu-based distros using LXDE. Maybe you can try them first. 
 
[LIST]
[*][WattOS]("http://www.planetwatt.com/") - Designed for older and low power computers (we make new ones screaming fast also :) ).
[*][MoonOS]("http://www.moonos.co.cc/") - an operating system featuring art.
[*][PUD GNU/Linux LXDE version]("http://distrowatch.com/?newsid=04826") - Lightweight and small Ubuntu-based installable live CD featuring LXDE.
[*][U-lite]("http://u-lite.org/?q=node/2") - A member of [Ubuntu Derivative Team]("https://wiki.ubuntu.com/DerivativeTeam/Derivatives") featuring LXDE.
[*] [Masonux]("http://wiki.lxde.org/en/Masonux")[[1]]("http://sites.google.com/site/masonux/home") - Ubuntu remix featuring LXDE that includes Firefox, Pidgin, Ubuntu's normal networking applet, and Synaptic package manager preinstalled.
[*][BoomBuntu]("http://boombuntu.wordpress.com/") - An extra light & super fast distribution based on Ubuntu & LXDE!
[/LIST]



Thanks for all this advice, ajgreeny & all. I read about LXDE in Wikopedia I will do  more search

-- but honestly feel a little overwhelmed with probably good options --that I don't know how to choose between.  Any suggestions?

Again:  512MB RAM    700mhz celeron processor   (don't know graphic card--shouldn't  I use that info too?)

I am on my way to work soon, so if I don't respond, I  will revisit this info again later.

thank you thankyou

---

### Post by gmjs on 2009-12-02
> **collards said:**
> ...the terminal only gives me a blank screen so ...
how do I use code follow your advice.

Press Ctrl+Alt+F1 and log in to use a terminal-only virtual console.  You can run the commands simply by typing them out as shown.  Output is printed to the screen by default (aka Standard Output or STDOUT), but you could save it to a file like this:

```
lspci > /home/username/my-pci-devices.txt
```

or pipe to the program 'more' so you can read a page at a time:

```
lspci | more
```
[B]
You return to the graphical virtual console by pressing Ctrl+Alt+F7[/B].

---

### Post by collards on 2009-12-02
> **gmjs said:**
> You can list the PC's hardware at the terminal with the following command:

```
lshw
```(it's short for 'list hardware')

You might find more useful information in the PCI devices list:

```
lspci
```For information about the graphics card only, try:

```
lspci | grep VGA
```Hope that helps.


maybe my brain is getting fried.....I can't find the PCI devices list.

I am off to work now & will check for your response from work or later.

[U]
Thanks Everyone!!!!!!!![/U]
:KS

---

### Post by gmjs on 2009-12-03
> **collards said:**
> I can't find the PCI devices list.

It should just list it.  Here's the output on my machine following the 'lspci | grep vga' command:

```
01:00.0 VGA compatible controller: ATI Technologies Inc Mobilitiy Radeon HD 3600 Series

```

Is it just showing another terminal prompt (user@machine:~$) then?

---

### Post by collards on 2009-12-03
> **gmjs said:**
> It should just list it.  Here's the output on my machine following the 'lspci | grep vga' command:

```
01:00.0 VGA compatible controller: ATI Technologies Inc Mobilitiy Radeon HD 3600 Series

```Is it just showing another terminal prompt (user@machine:~$) then?


Thanks for checking back.

I'll have to get to another computer & printer to print out all this info & directions so I can re-read & review & use what i am able to.     This computer is so slow now to work with...

Please answer the following if possible.  I've numbered them to help my tired brain.

1. It seems based on all the feedback & advice I've received that the problems that I've described would be due to not enough memory for the Gnome desktop and I shoule try  XFCE or LXDE desktop instead or or just switch from Ubuntu in general and use Xubuntu instead?     So I shouldn't be concerned about the warnings after GParted was finished?

2. Is it easy to just change desktops for now?  just so I can have something -until I can get an Xubuntu CD? How do I do the minimal install? --or how do I remove Gnome & install XFCE or LXDE?

3.Also, again,  I have not been able to get updates using Update Manager--so I haven't even tried to get any downloads--plug'ins or anything.  can I do any of this?

4. I am in another workspace getting ready to order Xubuntu CD--it looks like only 9.10 is available.....any feedback about that?

This is a great community of helpers...thank you

---

### Post by gmjs on 2009-12-03
> **collards said:**
> Is it easy to just change desktops for now?  just so I can have something

You should be able to install Xfce as follows (all commands are case sensitive):
[LIST=1]
[*]Boot your Ubuntu system to get to the login screen.
[*]Press **Ctrl+Alt+F1** on the keyboard to open tty1.
[*]Log in with your username and password (don't worry that the password doesn't show when you type).
[*]At the prompt, type the following and press **Return**:
```
sudo aptitude install xfce4
```

(You'll also need to type your password again.)


[*]When asked 'Do you want to continue?', type **Y** and press **Return**.

The download is approximately 25MB and will use about 80MB when installed.


[*]When installation has finished (it'll read 'Writing extended state information... Done') type the following to restart your PC:
```
sudo init 6
```

Let Ubuntu boot back to the login screen.


[*]Select your name from the login box (I'm assuming you're running Ubuntu 9.10) **but don't log in yet!**
[*]At the bottom of the screen there's a drop-down list box for you to choose which '**Session**' you want.  Select:

```
Xfce Session
```

before entering your password and logging in.

[/LIST]

If that has worked, you should have a slightly speedier setup.  GDM will remember your session choice, so there's no need to specify Xfce next time.


> **collards said:**
> 
I am in another workspace getting ready to order Xubuntu CD--it looks like only 9.10 is available.....any feedback about that?

D'you know I'm not sure!  I don't think Canonical do older versions of Xubuntu, but you may find them elsewhere on the net (I don't know one I'd recommend though).  Is your connection definitely too slow to download it, or do you not have a CD burner?


> **collards said:**
> So I shouldn't be concerned about the warnings after GParted was finished?
I'm sure I've ignored one or two GParted warnings in the past.  Of course, we always back up our data before partitioning anyway ;).

I hope you see an improvement.

Graham

---

### Post by kansasnoob on 2009-12-03
> **ajgreeny said:**
> You could also try installing the minimal install CD and adding the lxde desktop.  It is blazingly fast and attractive, though not as configurable as gnome or xfce, but I tried it a while ago and really liked it as an alternative desktop.

I think there was a ubuntu derivative available with the lxde desktop, but can't remember what it was called; do a search yourself and you may be able to find something.

OK, here we go, a quich search found these:-
**Ubuntu variants with LXDE pre-installed**

 If you are installing Ubuntu + LXDE on a new machine, there are some existing Ubuntu-based distros using LXDE. Maybe you can try them first. 
 
[LIST]
[*][WattOS]("http://www.planetwatt.com/") - Designed for older and low power computers (we make new ones screaming fast also :) ).
[*][MoonOS]("http://www.moonos.co.cc/") - an operating system featuring art.
[*][PUD GNU/Linux LXDE version]("http://distrowatch.com/?newsid=04826") - Lightweight and small Ubuntu-based installable live CD featuring LXDE.
[*][U-lite]("http://u-lite.org/?q=node/2") - A member of [Ubuntu Derivative Team]("https://wiki.ubuntu.com/DerivativeTeam/Derivatives") featuring LXDE.
[*] [Masonux]("http://wiki.lxde.org/en/Masonux")[[1]]("http://sites.google.com/site/masonux/home") - Ubuntu remix featuring LXDE that includes Firefox, Pidgin, Ubuntu's normal networking applet, and Synaptic package manager preinstalled.
[*][BoomBuntu]("http://boombuntu.wordpress.com/") - An extra light & super fast distribution based on Ubuntu & LXDE!
[/LIST]

+1!

I was going to suggest U-lite.

An actual Lubuntu is in the works I believe.

---

### Post by collards on 2009-12-03
Thanks Graham, K, & all,

I will re read this all again later  after work and try to print it out.  I know I will have some more questions.

Collards

---

