---
title: "need help - new here"
date: 2011-07-05
forum: New to Ubuntu
---

### Post by wvchinacat on 2011-07-05
Hi I am new here and NOT a computer guru - so please respond with easy to understand lingo.  I do not speak code!!  :)

I installed ubuntu (the latest version) yesterday.  I installed it side by side to my windows so that when I restart my computer I can choose which system to open.  

Yesterday Ubuntu opened great and hubby and I loved the ease of use and the speed of our computer.  Today when I booted up my computer - and chose ubuntu - it let me go all the way to putting in my password to open than stalled out on a black/translucent screen. No mouse, no ability to go anywhere.  So I just turned off my computer and tried again - the same thing happened.  So I turned off and rebooted this time in windows (which I am in right now)  I would prefer to open with ubuntu - but cannot figure out what is happening.  

Any suggestions??
Thanks

---

### Post by sanguinoso on 2011-07-05
The easiest thing for a beginner might be to just reinstall. Did you install any updates?

---

### Post by jtarin on 2011-07-05
What version of Ubuntu did you install? 
(that is computer guru code for "what is that number thingy on the thinga-majig you made that you put into the thinga-ma-bob.) :P

---

### Post by in-dust-rial on 2011-07-05
hey,

unnecessary introduction:
this or similar stuff happened so often to me.
but it was mainly my own fault :D

when you boot linux-ubuntu, the kernel starts running.

the kernel does all the operations within your operating system. 

to tell the kernel what to do there are several 'terminals'.

these terminals allow user to issue commands to the kernel. the kernel will carry out the commands. 

in the old days the terminals were text alone. maybe you already used or read about the 'shell', which is basically the same.

nowerdays one of the kernel terminals has a graphical interface with a mouse. the gui or desktop environment.




important:
if the desktop environment does not start. 
LIKE IN YOUR CASE.
you can switch to other text based terminals.
those do work even if the desktop environment is broken.

press while you are at the login screen:
[HTML]ctrl+alt+f3[/HTML]
or f1-f9
to chance terminals. on terminal 7 there is your broken desktop.

in a text terminal you can login.

now you can have a look at the log-files.
the log files keep track of what IS or WAS going on.
with
[HTML]cat /var/log/Xorg.0.log[/HTML]
you can have a look at events from the x-server. the x-server is the programm which enables graphical windows.
look for lines which begin with (EE). these mark errors.

also type 
[HTML]dmesg[/HTML]
this will show you all events of the kernel, the heart of the operating system.


maybe there is already information within these logs.

GOOD LUCK

---

### Post by in-dust-rial on 2011-07-05
if the abocve doesnt work:
if the 
[HTML]ctrl+alt+f3[/HTML]
trick does not work, - which might be a common thing in newer ubuntu versions -
you can try to boot SAFE MODE at the bootloader.
the bootloader is the first menue where you can chose to boot windows or ubuntu. there should be several entries for ubuntu. one of them should be save-mode.

in safe-mode there is no graphical desktop.
you should enter the root password.
then you are locked in as root.
now you want to change to your user account:
[HTML]su USERNAME[/HTML]
where USERNAME should be your username.

now you should be loged in not as root anymore, but as USER.
now issue the command to start the graphical desktop.
[HTML]startx[/HTML]
if this doesent work, have a look at the log-files, just as explained above.

good luck again

---

### Post by Chris Richard on 2011-07-05
At this early stage in the game (assuming you haven't had it installed for long anyway, and haven't made a ton of updates or system changes), I'm with sanguinoso. Just re-install it. 

In the future, I think you'll find that you'll get a lot more pertinent replies that are of more use to you and your specific system if you post more information about it.

"Next to Windows" doesn't really tell us much.

A list like the following helps a great deal in filtering out users answering who don't know much about the specific system you run.

For example, here's mine:

Model: Mac Pro
Operating Systems: OS X version 10.6.4, Windows XP SP 3 (Bootcamp), Ubuntu 11.04 (each installed on physically separate drives)

2 Dual-core Xeon processors
2 GB Ram
Nvidea video driver (version...)

Etc. etc...

You get the idea. The more others here know about your system, the better the chance you will eventually get the most pertinent information. I know if I see "Windows 7," that if I even bother to offer any advice, to "disclaimer" it by telling you I've never used Windows 7. Or, if I think I don't know enough about the particulars of your system, I won't waste your time with a lot of speculation about a system I'm not really familiar with.

Just some food for thought. ;)

---

### Post by akand074 on 2011-07-05
Yes is there anything you did to the system after installing during your first usage? Perhaps something came up and asked you to install drivers that could have been graphics drivers? If so the install of the graphics drivers could have possibly failed. I guess at this point it may be easiest to just reinstall and see if you are good, and if not we can go from there. But if you don't want to do that and are up for troubleshooting, we could try that assuming someone who knows enough is available (may not be me).

---

### Post by wvchinacat on 2011-07-05
> **jtarin said:**
> What version of Ubuntu did you install? 
(that is computer guru code for "what is that number thingy on the thinga-majig you made that you put into the thinga-ma-bob.) :P

It was the latest version from the ubuntu website as of yesterday 7/4/11.   I think the 11.04 version  Does that sound right?

---

### Post by wvchinacat on 2011-07-05
I am on an HP Pavilion laptop originally installed with windows vista.  The little stickers on the front say AMD turion x2
From the ubuntu website there were 3 options for downloading ubuntu.  save to flash drive, save to cd or run with windows installer with wubi.  This is what I did.  I do not understand how you can run ubuntu on a separate drive - unless you mean like a flashdrive or cd?  Is there another drive already on my computer that I could use?  sorry to sound so ignorant - computers are not my field - but windows is driving me crazy - so a friend suggested trying this out.

---

### Post by dFlyer on 2011-07-05
Did I understand you correctly, your running Wubi?

---

### Post by jtarin on 2011-07-05
That sounds right. Right off the bat I will tell you in my opinion 11.04 is one to be approached cautiously for beginners to Ubuntu if at all. I would have recommended 10.04 which has long term support or 10.10 which is very similar to 10.04. 11.04 is actually what I would call a "beta" product for a large percent of users. However having said that and if you intend on keeping this version be prepared to become a semi-guru.....or a full fledged one. Let's try this first and maybe we can get you a desktop. At the screen where you login in you have the ability to choose which desktop you want to login. Ubuntu 11.04 Natty uses Unity as default desktop environment, but this by no means the classic Gnome 2 desktop has been discarded. If you prefer this classic gnome desktop, you can do follow steps:

1.) At Ubuntu 11.04 login screen, choose login to “ubuntu classic”.

2.) Right click on “main menu”, “global menu” at top left screen and uncheck “lock to panel”, then select to “remove from panel”

3.) Right click on top panel, choose “add to panel” and then add “menu bar”.

Now you’re in Ubuntu 11.04 with classic gnome desktop!

---

### Post by jtarin on 2011-07-05
Wubi???

---

