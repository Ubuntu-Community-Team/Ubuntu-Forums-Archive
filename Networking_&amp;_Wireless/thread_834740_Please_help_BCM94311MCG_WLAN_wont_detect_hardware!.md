---
title: "Please help BCM94311MCG WLAN wont detect hardware!"
date: 2008-06-19
forum: Networking &amp; Wireless
---

### Post by Lifeis on 2008-06-19
I have installed Ndiswrapper through the add programs function in Ubuntu, and downloaded the drivers for my card from Ndiswrappers website. And first time I got it working perfectly, found my network, and connected. However, after I shutdown my laptop, then booted up again, it wouldnt connect. So I checked the network manager, and wireless wasnt listed. So I checked Ndiswrapper and it said 'Hardware Present: No' or something along those lines.
So I reinstalled Ubuntu from scratch and started again. And the same thing happened. Im cabled in by ethernet at the moment but I really need wireless sorted out.
Im new to Linux, so some help from you guys would be awesome.
Iv read up as much as I can, and followed guides on this forum, but nothing works. So please help dudes.
Thanks for your time,
Craig.
P.S. My card is: Broadcom Corp. BCM94311MCG wLAN mini-PCI (rev 02)

---

### Post by molotov00 on 2008-06-19
> So I checked Ndiswrapper and it said 'Hardware Present: No'

That's pretty vague. It's hard to help with information like that. What do you mean you checked ndiswrapper?

However, if it works then doesn't work the only explanation to me is that the drivers aren't being loaded at startup. What tutorial did you read to get ndiswrapper set up? Do you recall typing 'blacklist ...' along the way? That step would tell Ubuntu not to try loading drivers for your card and leave ndiswrapper to do it.

Please be a little more specific.

---

### Post by Lifeis on 2008-06-19
Oh and also, im running Ubuntu 8.04 Hardy Heron. Fresh download just a few days ago. And fully updated the day it was installed. So the OS is all good. And apart from the networking issues, im loving it. Specialy the compiz effects. Absolutely awesome.
Anyways, help me out if you can friends.

---

### Post by Lifeis on 2008-06-19
Okay, il try my best to explain.
I added Ndiswrapper, and like the GUI version (I dunno if they are all GUI) and downloaded the driver from there website.
I didnt use the terminal at all, other than to determine what the card was. And I read a tutorial on how to find that out. Since then iv tried to do what it says on the Ndiswrapper website and unload module ssb and bcm43xx.
I ran the command to unload it, and bcm43xx worked okay, but ssb was 'in use'
Im confused because of the fact that it did work perfectly once, but then never again. Plus its listed as a card that works on Ndiswrappers list.
Sorry for being vague im a total noob man.
Thanks for tryin to help me out.
Also you said 'if it works'
well it doesnt work now. It just did once. Now when I located the inf file and click install it just says:
Hardware Present: No

Whereas last time it said Yes and detected the router.
Its a strange one.

---

### Post by molotov00 on 2008-06-19
Let me explain a bit about now ndiswrapper works:

If there's no linux driver for your hardware (in this case, wireless network chip) then it won't function correctly under linux. So you need to disable linux from trying to use its own driver. Then you use ndiswrapper, which is a program that takes a windows driver and 'wraps' it so that it works under linux.

What I suspect has happened is that there is a driver conflict. Essentially, ndiswrapper and the os are fighting over the hardware, each wanting to use their own driver.

If you can find a link to the tutorial you used, that will be helpful.

---

### Post by Lifeis on 2008-06-19
Thanks again man. I will find the link and post tomorrow. Cause its late here and im at work in 5 hours =(
But I shall post tomorrow. Thanks alot for helping me out, I didnt even realise Linux could be trying to use its own driver, I didnt even know linux came with wireless card drivers installed.
Thanks man, and il post again tomorrow

---

### Post by Ayuthia on 2008-06-19
Here is a link that might help you get it set up with NDISwrapper.  The original poster has the same card.

[http://ubuntuforums.org/showthread.php?t=769990](http://ubuntuforums.org/showthread.php?t=769990)

---

### Post by Lifeis on 2008-06-20
Hey Guys,
Thanks for the responses.
Just booted the laptop up there and my Ndiswrapper says: 'Hardwae Present: Yes'
Which I asume is a good sign.
Iv got these screen shots of whats happening though.
It wont let me unlock the network manager, to configure the wireless card etc.
[ATTACH]74804[/ATTACH]

[ATTACH]74805[/ATTACH]

[ATTACH]74806[/ATTACH]

[ATTACH]74807[/ATTACH]

Dunno how this forum works but hopefully you can see them, and see my problem. Its just so messed up cause I had it connected wirelessly to my router perfectly for hours. And it had an even better signal stregnth than windows. Its wierd. Il read that tutorial, but im scared to touch my setup cause Ndiswrapper is detecting the hardware as you can hopefully see in the screenshot.

Thanks for all your help buddys.
This is an awesome friendly community. Unlike Microsoft 2 dollars a minute pakistani help-line!
Thanks Guys!

---

### Post by Ayuthia on 2008-06-20
Well, if you were able to connect once before and you can't right now, it kind of points towards a module conflict.  Can you open up the Terminal and post the results of:
```
lsmod|grep -i -e bcm43xx -e b43 -e ssb -e wl -e ndiswrapper
lshw -C network
cat /etc/modprobe.d/blacklist*|grep -i -e bcm43xx -e b43 -e ssb -e wl -e ndiswrapper
cat /etc/modules|grep -i -e bcm43xx -e b43 -e ssb -e wl -e ndiswrapper
```
The first command will tell us what modules are loaded.  The second command will tell us what driver is being used.  The third will tell us what modules are not supposed to load.  The fourth will tell us what we want to have load.

Here is a command to try to see if you can get connected.  It is a temporary command that will only last for the current session:
```
sudo modprobe -r b43 b43legacy ssb bcm43xx wl ndiswrapper
sudo depmod -ae
sudo modprobe ndiswrapper
```
The first command is the module remover.  We will take out all the possible modules for your card.  The next command will rebuild the module dependencies.  The last command will load the ndiswrapper module.

---

### Post by Lifeis on 2008-06-20
Just got a connection there after setting a root password, in the users and groups options, then switched user, tried root but it wouldnt let me. So I logged in, in my account 'ubuntu' and it connected! But im scared to turn the system off cause last time it wouldnt ever connect again. Is there a way I can get it to just connect like this every time it boots like Microshit Windoze does?
Thanks for the help though man, im getting there! Please just try and help me to get this permanent, and il be ubuntu forever and always! (I was gonna anyway, but Its a pain running a 15 meter ethernet to a router all the time lol)
Thanks buddy!
See ---->       [ATTACH]74809[/ATTACH]

---

### Post by Lifeis on 2008-06-20
If someone has time please help me out. Im running on a wireless connection right now. Ethernet cable is meters away from the laptop.
The signal is great, speed is great, everything is perfect. But this is what happened before, and then the next day when I booted up, Ndiswrapper said: 'Hardware Present: No' 
And there was no connection at all. No mention of even a wireless card in the network manager.
Im scared if I shutdown this will happen again.
And the thing is, i haven't done anything special to get the wireless up and running, so I probably couldn't do it again. Well not quickly anyway. If you read my previous posts then you'll see what I mean, and view the screenshots I took to show you guys.
I figured it would help you see what my situation is.
Help out if you can guys. But im very greatful for your help so far. Iv came miles from when I was using windows. If I can just get this wireless to connect at login, then il never turn back. Il even run my office on Ubuntu. I dont know if you can get AutoCAD for Linux, but thats all we really need crucially. And this is so much more fun, easy to use, and an all together better computer experience.

Thanks guys, help if you can.
Cheers!:)

---

### Post by Lifeis on 2008-06-20
Im afraid I have to go sleep now. Its almost 2AM,
So im gonna have to just risk the shutdown and pray it connects tommorrow. But im sure it wont, however never say never.
Thanks guys, il bump the thread for more help if it doesnt connect tommorrow.
Thanks again.
-Laters
Craig.

---

### Post by Ayuthia on 2008-06-20
You can try this:
```
echo -e '#Hardy ssb/ndiswrapper workaround, added' `date` '\ninstall ndiswrapper modprobe -r b43 b44 b43legacy ssb; modprobe --ignore-install ndiswrapper $CMDLINE_OPTS; modprobe ssb; modprobe b44;' | sudo tee -a /etc/modprobe.d/ndiswrapper 
```
It comes from [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-6a90c0182f807f29d1a2f55e8654ac07689542bb](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-6a90c0182f807f29d1a2f55e8654ac07689542bb)

If you lose your connection, you can always do this again to get it back up:
```
sudo modprobe -r b43 b43legacy ssb bcm43xx wl ndiswrapper
sudo depmod -ae
sudo modprobe ndiswrapper
```

---

### Post by Lifeis on 2008-06-21
Just restarted my laptop there, and no wireless.
Ndiswrapper says:
Hardware Present: No

When yesturday it said yes and all was well, has a perfect wireless connection. Also I ran the commands I was suggested and:
[QUOTE=]ubuntu@ubuntu-laptop:~$ sudo modprobe -r b43 b43legacy ssb bcm43xx wl ndiswrapper
FATAL: Module ssb is in use.
ubuntu@ubuntu-laptop:~$ sudo depmod -ae
ubuntu@ubuntu-laptop:~$ sudo modprobe ndiswrappe
[/QUOTE]
So im guessing thats bad. I just dont understand how it can all of a sudden work great, then after a restart, refuse to work again. Wont even detect hardware again.
And I dunno if the quote worked, but in terminal it said, "FATAL Module ssb is in use" and I dunno whats using this module "ssb" what is that?
Thanks so much for all your help guys, the linux community is like no other, Its so much better than talking to someone over the phone on MS who doesnt know ****.
Just gutted im back on ethernet again. And last time this laptop was on, it had perfect wireless. Im really gutted. Its a total nock down for Ubuntu (for me anyway)
Thats why alot of home users and buisnesses wont use it, is because as far as drivers/running those drivers go, Linux is miles behind Microshit Windoze.
Thanks guys. Please post again if you can and try help me sort this out.
Cheers,
-:confused:Craig

---

### Post by Lifeis on 2008-06-21
Oh, and also, runing the first advised command, resulted in this:
> echo -e '#Hardy ssb/ndiswrapper workaround, added' `date` '\ninstall ndiswrapper modprobe -r b43 b44 b43legacy ssb; modprobe --ignore-install ndiswrapper $CMDLINE_OPTS; modprobe ssb; modprobe b44;' | sudo tee -a /etc/modprobe.d/ndiswrapper
#Hardy ssb/ndiswrapper workaround, added Sun Jun 22 00:49:09 BST 2008 
install ndiswrapper modprobe -r b43 b44 b43legacy ssb; modprobe --ignore-install ndiswrapper $CMDLINE_OPTS; modprobe ssb; modprobe b44;
ubuntu@ubuntu-laptop:~$ 

Hope that maybe helps.
To me its all just over my head.
At my office we runaround 100 machines, and 2 servers. Thats just in my office, there are several offices, and im my office admin. I want to go for Linux, but its just not network capable enough yet. Specially wirelessly.
Anyways, thanks guys, help out if you can asap.

---

### Post by Lifeis on 2008-06-21
Sorry to post again, but heres some screenshots to help you understand my situation.
[ATTACH]74897[/ATTACH]

[ATTACH]74898[/ATTACH]

---

### Post by Lifeis on 2008-06-21
Also, if I can get this laptop running on wireless, all the time, as it boots, as though it was windoze, then I **will** run my office network on Linux. I think its the way forwards, and the way to get most from your machines. I don't know how much it costs for an office license for Ubuntu Hardy Heron, but anywhare up to £5000 on a license. Maybe 10 considering its 100 machines.
So thats £5000 for 50 machines, which is *very cheap* compared to our license.
If you could help me out and get my wireless working all the time at boot, just like windows, then that would install some confidence in me. Confidence that my Ubuntu network at my Engineering firm, will be simple for my employee's and reliable for the correctly trained server technical admins.
So  if you could let me know also how much it costs for a license, then that would be awesome. But wireless first if you could help then I can consider formatting my server and machines to linux, but I really am a newby at this. So im sorry if I seem stupid.
Thanks guys.

---

### Post by Lifeis on 2008-06-21
> **Ayuthia said:**
> Well, if you were able to connect once before and you can't right now, it kind of points towards a module conflict.  Can you open up the Terminal and post the results of:
```
lsmod|grep -i -e bcm43xx -e b43 -e ssb -e wl -e ndiswrapper
lshw -C network
cat /etc/modprobe.d/blacklist*|grep -i -e bcm43xx -e b43 -e ssb -e wl -e ndiswrapper
cat /etc/modules|grep -i -e bcm43xx -e b43 -e ssb -e wl -e ndiswrapper
```
The first command will tell us what modules are loaded.  The second command will tell us what driver is being used.  The third will tell us what modules are not supposed to load.  The fourth will tell us what we want to have load.

Here is a command to try to see if you can get connected.  It is a temporary command that will only last for the current session:
```
sudo modprobe -r b43 b43legacy ssb bcm43xx wl ndiswrapper
sudo depmod -ae
sudo modprobe ndiswrapper
```
The first command is the module remover.  We will take out all the possible modules for your card.  The next command will rebuild the module dependencies.  The last command will load the ndiswrapper module.

I ran the first one and got:
> 
ubuntu@ubuntu-laptop:~$ lsmod|grep -i -e bcm43xx -e b43 -e ssb -e wl -e ndiswrapper
ndiswrapper           192920  0 
ssb                    34308  1 b44
usbcore               146028  4 ndiswrapper,ohci_hcd,ehci_hcd
ubuntu@ubuntu-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
ubuntu@ubuntu-laptop:~$ cat /etc/modprobe.d/blacklist*|grep -i -e bcm43xx -e b43 -e ssb -e wl -e ndiswrapper
# replaced by b43 and ssb.
blacklist bcm43xx
ubuntu@ubuntu-laptop:~$ cat /etc/modules|grep -i -e bcm43xx -e b43 -e ssb -e wl -e ndiswrapper
ndiswrapper
ubuntu@ubuntu-laptop:~$ 


Ran The Second And Got:
> 
ubuntu@ubuntu-laptop:~$ sudo modprobe -r b43 b43legacy ssb bcm43xx wl ndiswrapper
[sudo] password for ubuntu: 
FATAL: Module ssb is in use.
ubuntu@ubuntu-laptop:~$ 


---

### Post by Ayuthia on 2008-06-21
Can you post the results of:
```
cat /etc/modprobe.d/ndiswrapper
```
In theory, you should be able to get things back up and running again by doing:
```
sudo modprobe -r b43 b44 b43legacy ssb bcm43xx wl ndiswrapper
sudo depmod -ae
sudo modprobe ndiswrapper
```
What happened is that the command that I gave you included the command to also load b44 that your computer does not need, but it does not hurt anything.  The only thing that it does is provide an extra word to add to our modules to remove.

---

### Post by Lifeis on 2008-06-21
> **Ayuthia said:**
> Can you post the results of:
```
cat /etc/modprobe.d/ndiswrapper
```
In theory, you should be able to get things back up and running again by doing:
```
sudo modprobe -r b43 b44 b43legacy ssb bcm43xx wl ndiswrapper
sudo depmod -ae
sudo modprobe ndiswrapper
```
What happened is that the command that I gave you included the command to also load b44 that your computer does not need, but it does not hurt anything.  The only thing that it does is provide an extra word to add to our modules to remove.

Yeah sure,
First one I got:
```

ubuntu@ubuntu-laptop:~$ cat /etc/modprobe.d/ndiswrapper
alias pci:v000014E4d00004311sv00001363sd0000103Cbc*sc*i* ndiswrapper
alias pci:v000014E4d00004311sv00001364sd0000103Cbc*sc*i* ndiswrapper
alias pci:v000014E4d00004311sv00001365sd0000103Cbc*sc*i* ndiswrapper
alias pci:v000014E4d00004311sv00001374sd0000103Cbc*sc*i* ndiswrapper
alias pci:v000014E4d00004311sv00001375sd0000103Cbc*sc*i* ndiswrapper
alias pci:v000014E4d00004311sv00001376sd0000103Cbc*sc*i* ndiswrapper
alias pci:v000014E4d00004311sv00001377sd0000103Cbc*sc*i* ndiswrapper
alias pci:v000014E4d00004311sv*sd*bc*sc*i* ndiswrapper
alias pci:v000014E4d00004312sv0000135Fsd0000103Cbc*sc*i* ndiswrapper
alias pci:v000014E4d00004312sv00001360sd0000103Cbc*sc*i* ndiswrapper
alias pci:v000014E4d00004312sv00001361sd0000103Cbc*sc*i* ndiswrapper
alias pci:v000014E4d00004312sv00001362sd0000103Cbc*sc*i* ndiswrapper
alias pci:v000014E4d00004312sv00001370sd0000103Cbc*sc*i* ndiswrapper
alias pci:v000014E4d00004312sv00001371sd0000103Cbc*sc*i* ndiswrapper
alias pci:v000014E4d00004312sv00001372sd0000103Cbc*sc*i* ndiswrapper
alias pci:v000014E4d00004312sv00001373sd0000103Cbc*sc*i* ndiswrapper
alias pci:v000014E4d00004312sv*sd*bc*sc*i* ndiswrapper
alias pci:v000014E4d00004318sv00001355sd0000103Cbc*sc*i* ndiswrapper
alias pci:v000014E4d00004318sv00001356sd0000103Cbc*sc*i* ndiswrapper
alias pci:v000014E4d00004318sv00001357sd0000103Cbc*sc*i* ndiswrapper
alias pci:v000014E4d00004318sv*sd*bc*sc*i* ndiswrapper
alias pci:v000014E4d00004319sv00001358sd0000103Cbc*sc*i* ndiswrapper
alias pci:v000014E4d00004319sv00001359sd0000103Cbc*sc*i* ndiswrapper
alias pci:v000014E4d00004319sv0000135Asd0000103Cbc*sc*i* ndiswrapper
alias pci:v000014E4d00004319sv*sd*bc*sc*i* ndiswrapper
alias pci:v000014E4d00004320sv000000E7sd00000E11bc*sc*i* ndiswrapper
alias pci:v000014E4d00004320sv000012F4sd0000103Cbc*sc*i* ndiswrapper
alias pci:v000014E4d00004320sv000012F8sd0000103Cbc*sc*i* ndiswrapper
alias pci:v000014E4d00004320sv000012FAsd0000103Cbc*sc*i* ndiswrapper
alias pci:v000014E4d00004320sv000012FBsd0000103Cbc*sc*i* ndiswrapper
alias pci:v000014E4d00004320sv*sd*bc*sc*i* ndiswrapper
alias pci:v000014E4d00004324sv000012F9sd0000103Cbc*sc*i* ndiswrapper
alias pci:v000014E4d00004324sv000012FCsd0000103Cbc*sc*i* ndiswrapper
alias pci:v000014E4d00004324sv*sd*bc*sc*i* ndiswrapper
alias pci:v000014E4d00004328sv00001366sd0000103Cbc*sc*i* ndiswrapper
alias pci:v000014E4d00004328sv00001367sd0000103Cbc*sc*i* ndiswrapper
alias pci:v000014E4d00004328sv00001368sd0000103Cbc*sc*i* ndiswrapper
alias pci:v000014E4d00004328sv00001369sd0000103Cbc*sc*i* ndiswrapper
alias pci:v000014E4d00004328sv*sd*bc*sc*i* ndiswrapper
ubuntu@ubuntu-laptop:~$ 

```

Second Code I Got:
```

ubuntu@ubuntu-laptop:~$ sudo modprobe -r b43 b44 b43legacy ssb bcm43xx wl ndiswrapper
ubuntu@ubuntu-laptop:~$ sudo depmod -ae
ubuntu@ubuntu-laptop:~$ sudo modprobe ndiswrapper
ubuntu@ubuntu-laptop:~$ 

```

Hope that helps, it hasnt got my wireless up again, Still wont detect hardware. Wierd Man!

---

### Post by Lifeis on 2008-06-21
I have to go for a sleep now unfortunatly. But please post and try and help me, il post back tomorrow. Thank you so much for your support so far.
I just read that ubuntu buisness licenses are free, so if I get this wireless up and running and learn how to do it all, and maybe even get AutoCAD for Ubuntu, that would rock, but I dunno if  windows emulator would handle that, but im sure theres a way.
And if its feasible il run my 2 servers on Linux, and all the machines. And il donate the budget to your excellent cause.
It would be around £10,000 which I think is around $20,000
But im thinking way ahead. First I need to get my home network running first, then learn a bit more. But If this works out wireless on this machine, then that paves the way for the future of my system administration future.
Thanks again.
:)
Talk to you tomorrow.

---

### Post by Ayuthia on 2008-06-21
> ubuntu@ubuntu-laptop:~$ cat /etc/modprobe.d/blacklist*|grep -i -e bcm43xx -e b43 -e ssb -e wl -e ndiswrapper
# replaced by b43 and ssb.
blacklist bcm43xx
This file should have b43 blacklisted also:
```
echo blacklist b43|sudo tee -a /etc/modprobe.d/blacklist
```

It might be best if you reboot from here to see what happens.

Can you post your lshw -C network?  This one will tell us what is being used for your network cards and what drivers it is trying to use.

Also, it does not seem that the following command worked:
```
echo -e '#Hardy ssb/ndiswrapper workaround, added' `date` '\ninstall ndiswrapper modprobe -r b43 b44 b43legacy ssb; modprobe --ignore-install ndiswrapper $CMDLINE_OPTS; modprobe ssb; modprobe b44;' | sudo tee -a /etc/modprobe.d/ndiswrapper
```When you posted your /etc/modprobe.d/ndiswrapper information, there was supposed to be an additional line at the end of the file that contained this information.  Let's hold off on that for now.  We might not need it.

By the way, I might not be able to respond tomorrow until late because I am on the road tomorrow and will not be able to get online until night over here.  I am guessing that I am six hours behind you.

---

### Post by Lifeis on 2008-06-22
Two seconds and il open the Terminal up...

---

### Post by Lifeis on 2008-06-22
Ran the first command and got this:
> 
ubuntu@ubuntu-laptop:~$ echo blacklist b43|sudo tee -a /etc/modprobe.d/blacklist
[sudo] password for ubuntu: 
blacklist b43
ubuntu@ubuntu-laptop:~$ 


Then re-booted and nothing had changed. Went into Ndiswrapper (System-Administration-Windows Wireless Drivers) and it said:
Hardware Present: No

So to run the Lshw -C network I got:
> 
ubuntu@ubuntu-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
ubuntu@ubuntu-laptop:~$   


So I ran 'Sudo lshw -C network'
And I got:
> 
ubuntu@ubuntu-laptop:~$ sudo lshw -C network
[sudo] password for ubuntu: 
ubuntu@ubuntu-laptop:~$    


So basically I got nothing, but it did flash up somethings before it went back to the 'ubuntu@ubuntu-laptop:~$'
It flashed up real quick, the only one I managed to read said: 'PCI (sysfs)'

Sorry that no doubt didnt help you much. Thanks again for your time man, just reply whenever you can. Iv always got my ethernet mean time, untill I get this wireless working. It just confuses me, cause its worked twice now, perfectly, and both times, after I re-boot it just wont detect the hardware again!
Thanks so much for helping me out man.
An yeah I think you are 6 hours behind me, so im usually sitting on this laptop at like 4am in our time lol.
Thanks man, talk to you soon hopefully.

---

### Post by Ayuthia on 2008-06-22
> **Lifeis said:**
> Ran the first command and got this:


Then re-booted and nothing had changed. Went into Ndiswrapper (System-Administration-Windows Wireless Drivers) and it said:
Hardware Present: No

So to run the Lshw -C network I got:


So I ran 'Sudo lshw -C network'
And I got:


So basically I got nothing, but it did flash up somethings before it went back to the 'ubuntu@ubuntu-laptop:~$'
It flashed up real quick, the only one I managed to read said: 'PCI (sysfs)'

Sorry that no doubt didnt help you much. Thanks again for your time man, just reply whenever you can. Iv always got my ethernet mean time, untill I get this wireless working. It just confuses me, cause its worked twice now, perfectly, and both times, after I re-boot it just wont detect the hardware again!
Thanks so much for helping me out man.
An yeah I think you are 6 hours behind me, so im usually sitting on this laptop at like 4am in our time lol.
Thanks man, talk to you soon hopefully.
I should have looked at your screenshots earlier, but I didn't.  I was on dialup at the time so it takes forever to see anything.  Anyway, I looked at the screenshot and realized that the bcmwl5 driver is no longer happy.  When it says hardware present: no, then that means that the driver is not going to work with ndiswrapper.

Can you post the results of:
```
ls -l /etc/ndiswrapper
ls -l /etc/ndiswrapper/bcmwl5
```
The first command is done to see what drivers have been loaded.  The second command is where ndiswrapper keeps some information about the driver.  I just want to see what happened.  We then should use the commands:
```
sudo modprobe -r b43 b44 b43legacy ssb bcm43xx wl ndiswrapper
sudo depmod -ae
sudo modprobe ndiswrapper
dmesg|grep ndiswrapper
```
This will help us see what ndiswrapper does not like about the driver.

One other thing, can you make sure that the card is turned on (if this is a laptop).  Can you also post the results of lspci -nn|grep 14e4?  I just want to make sure that the card is being recognized.  Usually lshw -C network will show your card whether your card is on or not.

Too bad you didn't post this last year when I was living in Peterborough.  There would be no time difference.

---

### Post by durundal on 2008-06-23
I am having the exact same problem except my  BCM94311MCG is rev 01, whatever that means.  None of the fixes have worked for me either, "lshw -C network" can't find the card while it is broken and neither can lspci or any hardware detecting software I have used.

The card is switched to the "on" position on the front of my laptop but when I restart the computer the light will change from blue to red, as if I had switched it off, and it will stay red for days at a time until it randomly starts working again.

After a few days of being undetected as hardware, it is finally working for this session, so I have taken the outputs of the following

```
lsmod|grep -i -e bcm43xx -e b43 -e ssb -e wl -e ndiswrapper
lshw -C network
cat /etc/modprobe.d/blacklist*|grep -i -e bcm43xx -e b43 -e ssb -e wl -e ndiswrapper
cat /etc/modules|grep -i -e bcm43xx -e b43 -e ssb -e wl -e ndiswrapper

cat /etc/modprobe.d/ndiswrapper

ls -l /etc/ndiswrapper
ls -l /etc/ndiswrapper/bcmwl5
```

and saved them for comparing against the outputs after the card breaks again on reboot.  

Is there anything else I should look at now while it is working?

I need my wifi to do work today, so I can't restart it anytime soon, but this is definitely a problem that needs to be looked at further.

---

### Post by Lifeis on 2008-06-23
Aight man, Thanks for looking at the screenshots.
I posted them because im a newb and im not very good at explaining things, or understanding commands etc.
Anyways, I ran the first commands you gave me and got:
> 
ubuntu@ubuntu-laptop:~$ ls -l /etc/ndiswrapper
total 4
drwxr-xr-x 2 root root 4096 2008-06-23 22:15 bcmwl5
ubuntu@ubuntu-laptop:~$ ls -l /etc/ndiswrapper/bcmwl5
total 1524
-rw-r--r-- 1 root root    905 2008-06-23 22:15 14E4:4311:1363:103C.5.conf
-rw-r--r-- 1 root root    905 2008-06-23 22:15 14E4:4311:1364:103C.5.conf
-rw-r--r-- 1 root root    905 2008-06-23 22:15 14E4:4311:1365:103C.5.conf
-rw-r--r-- 1 root root    905 2008-06-23 22:15 14E4:4311:1374:103C.5.conf
-rw-r--r-- 1 root root    905 2008-06-23 22:15 14E4:4311:1375:103C.5.conf
-rw-r--r-- 1 root root    905 2008-06-23 22:15 14E4:4311:1376:103C.5.conf
-rw-r--r-- 1 root root    905 2008-06-23 22:15 14E4:4311:1377:103C.5.conf
lrwxrwxrwx 1 root root     26 2008-06-23 22:15 14E4:4311.5.conf -> 14E4:4311:1363:103C.5.conf
-rw-r--r-- 1 root root    961 2008-06-23 22:15 14E4:4312:135F:103C.5.conf
-rw-r--r-- 1 root root    961 2008-06-23 22:15 14E4:4312:1360:103C.5.conf
-rw-r--r-- 1 root root    961 2008-06-23 22:15 14E4:4312:1361:103C.5.conf
-rw-r--r-- 1 root root    961 2008-06-23 22:15 14E4:4312:1362:103C.5.conf
-rw-r--r-- 1 root root    961 2008-06-23 22:15 14E4:4312:1370:103C.5.conf
-rw-r--r-- 1 root root    961 2008-06-23 22:15 14E4:4312:1371:103C.5.conf
-rw-r--r-- 1 root root    961 2008-06-23 22:15 14E4:4312:1372:103C.5.conf
-rw-r--r-- 1 root root    961 2008-06-23 22:15 14E4:4312:1373:103C.5.conf
lrwxrwxrwx 1 root root     26 2008-06-23 22:15 14E4:4312.5.conf -> 14E4:4312:135F:103C.5.conf
-rw-r--r-- 1 root root    901 2008-06-23 22:15 14E4:4318:1355:103C.5.conf
-rw-r--r-- 1 root root    901 2008-06-23 22:15 14E4:4318:1356:103C.5.conf
-rw-r--r-- 1 root root    901 2008-06-23 22:15 14E4:4318:1357:103C.5.conf
lrwxrwxrwx 1 root root     26 2008-06-23 22:15 14E4:4318.5.conf -> 14E4:4318:1355:103C.5.conf
-rw-r--r-- 1 root root    957 2008-06-23 22:15 14E4:4319:1358:103C.5.conf
-rw-r--r-- 1 root root    957 2008-06-23 22:15 14E4:4319:1359:103C.5.conf
-rw-r--r-- 1 root root    957 2008-06-23 22:15 14E4:4319:135A:103C.5.conf
lrwxrwxrwx 1 root root     26 2008-06-23 22:15 14E4:4319.5.conf -> 14E4:4319:1358:103C.5.conf
-rw-r--r-- 1 root root    901 2008-06-23 22:15 14E4:4320:00E7:0E11.5.conf
-rw-r--r-- 1 root root    924 2008-06-23 22:15 14E4:4320:12F4:103C.5.conf
-rw-r--r-- 1 root root    901 2008-06-23 22:15 14E4:4320:12F8:103C.5.conf
-rw-r--r-- 1 root root    901 2008-06-23 22:15 14E4:4320:12FA:103C.5.conf
-rw-r--r-- 1 root root    901 2008-06-23 22:15 14E4:4320:12FB:103C.5.conf
lrwxrwxrwx 1 root root     26 2008-06-23 22:15 14E4:4320.5.conf -> 14E4:4320:00E7:0E11.5.conf
-rw-r--r-- 1 root root    957 2008-06-23 22:15 14E4:4324:12F9:103C.5.conf
-rw-r--r-- 1 root root    957 2008-06-23 22:15 14E4:4324:12FC:103C.5.conf
lrwxrwxrwx 1 root root     26 2008-06-23 22:15 14E4:4324.5.conf -> 14E4:4324:12F9:103C.5.conf
-rw-r--r-- 1 root root    961 2008-06-23 22:15 14E4:4328:1366:103C.5.conf
-rw-r--r-- 1 root root    961 2008-06-23 22:15 14E4:4328:1367:103C.5.conf
-rw-r--r-- 1 root root    961 2008-06-23 22:15 14E4:4328:1368:103C.5.conf
-rw-r--r-- 1 root root    961 2008-06-23 22:15 14E4:4328:1369:103C.5.conf
lrwxrwxrwx 1 root root     26 2008-06-23 22:15 14E4:4328.5.conf -> 14E4:4328:1366:103C.5.conf
-rw-r--r-- 1 root root 811278 2008-06-23 22:15 bcmwl5.inf
-rw-r--r-- 1 root root 604928 2008-06-23 22:15 bcmwl5.sys
ubuntu@ubuntu-laptop:~$ 

Other commands,
First one did nothing (asked me for password, then went back to the normal command line)
So I dunno whats up with that.
Second one did the same again:
> 
ubuntu@ubuntu-laptop:~$ sudo depmod -ae
[sudo] password for ubuntu: 
ubuntu@ubuntu-laptop:~$ 

The third command (sudo modprobe ndiswrapper) did the same again as the quote above.

But the last command gave me:
> 
ubuntu@ubuntu-laptop:~$ dmesg|grep ndiswrapper
[   36.346668] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[   36.443678] usbcore: registered new interface driver ndiswrapper
[   47.689475] usbcore: deregistering interface driver ndiswrapper
[   47.709941] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[   47.741035] usbcore: registered new interface driver ndiswrapper
[   47.789325] usbcore: deregistering interface driver ndiswrapper
[   47.809743] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[   47.841034] usbcore: registered new interface driver ndiswrapper
[   47.863660] usbcore: deregistering interface driver ndiswrapper
[   47.883816] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[   47.914435] usbcore: registered new interface driver ndiswrapper
[  435.167207] usbcore: deregistering interface driver ndiswrapper
[  457.442521] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[  457.477164] usbcore: registered new interface driver ndiswrapper
ubuntu@ubuntu-laptop:~$ 


Doesnt mean anything to me, but I hope it helps you man. Iv tried removing the driver, then adding it again, and it just doesnt work. Except it has twice, and worked perfectly at that!
Iv read on a forum about something called 'MadWIFI' or something, would that perhaps help?
Thanks alot for your time again man.

---

### Post by Lifeis on 2008-06-23
Durundal,
Nice to hear someone is in the same situation as myself! lol!
Its infuriating, because its worked before, so why cant it work again!!!
You seem to know alot more Linux skills than myself though, but im guessing your still pissed too.
At least we're not alone! :)

---

### Post by Lifeis on 2008-06-23
Oh also, sorry to post again, three times in a row, but heres another screenshot I took from whn I click on 'Edit wireless networks' In the network manager at the top right corner. (Even though Ndiswrapper says: 'Hardware Present: No'

Anyways the screengrabs attached.

---

### Post by Ayuthia on 2008-06-23
> **Lifeis said:**
> Aight man, Thanks for looking at the screenshots.
I posted them because im a newb and im not very good at explaining things, or understanding commands etc.
Anyways, I ran the first commands you gave me and got:

Other commands,
First one did nothing (asked me for password, then went back to the normal command line)
So I dunno whats up with that.
Second one did the same again:

The third command (sudo modprobe ndiswrapper) did the same again as the quote above.

But the last command gave me:


Doesnt mean anything to me, but I hope it helps you man. Iv tried removing the driver, then adding it again, and it just doesnt work. Except it has twice, and worked perfectly at that!
Iv read on a forum about something called 'MadWIFI' or something, would that perhaps help?
Thanks alot for your time again man.
The last part that we need is the lspci -nnm information.  It will give is the subvendor information that will help us match up the information in /etc/ndiswrapper/bcmwl5.  

As for MadWIFI, it is a driver that is for another card type (not Broadcom).

Everything looks right, but the thing that concerns me is that the hardware is not present and nothing is showing up in lshw -C network.  Do you have a HP?  This is the issue that I had with my laptop and I found that there was an issue with the motherboard.

By any chance, are you dual booting with Windows?  If so, does the wireless work there?

---

### Post by Ayuthia on 2008-06-23
> **durundal said:**
> I am having the exact same problem except my  BCM94311MCG is rev 01, whatever that means.  None of the fixes have worked for me either, "lshw -C network" can't find the card while it is broken and neither can lspci or any hardware detecting software I have used.

The card is switched to the "on" position on the front of my laptop but when I restart the computer the light will change from blue to red, as if I had switched it off, and it will stay red for days at a time until it randomly starts working again.

After a few days of being undetected as hardware, it is finally working for this session, so I have taken the outputs of the following

```
lsmod|grep -i -e bcm43xx -e b43 -e ssb -e wl -e ndiswrapper
lshw -C network
cat /etc/modprobe.d/blacklist*|grep -i -e bcm43xx -e b43 -e ssb -e wl -e ndiswrapper
cat /etc/modules|grep -i -e bcm43xx -e b43 -e ssb -e wl -e ndiswrapper

cat /etc/modprobe.d/ndiswrapper

ls -l /etc/ndiswrapper
ls -l /etc/ndiswrapper/bcmwl5
```

and saved them for comparing against the outputs after the card breaks again on reboot.  

Is there anything else I should look at now while it is working?

I need my wifi to do work today, so I can't restart it anytime soon, but this is definitely a problem that needs to be looked at further.

Are you using an HP laptop?  I had the same issue and my laptop is currently with HP to get fixed.  There was some kind of issue with the motherboard that caused my network card to stop working in all the OS partitions that I installed (Vista, Gentoo, Arch, and Kubuntu)

---

### Post by Lifeis on 2008-06-25
Ran the last command there:
> 
ubuntu@ubuntu-laptop:~$ lspci -nnm
00:00.0 "RAM memory [0500]" "nVidia Corporation [10de]" "C51 Host Bridge [02f3]" -ra2 "Hewlett-Packard Company [103c]" "Unknown device [30b7]"
00:00.1 "RAM memory [0500]" "nVidia Corporation [10de]" "C51 Memory Controller 0 [02fa]" -ra2 "Hewlett-Packard Company [103c]" "Presario V6133CL [30b7]"
00:00.2 "RAM memory [0500]" "nVidia Corporation [10de]" "C51 Memory Controller 1 [02fe]" -ra2 "Hewlett-Packard Company [103c]" "Presario V6133CL [30b7]"
00:00.3 "RAM memory [0500]" "nVidia Corporation [10de]" "C51 Memory Controller 5 [02f8]" -ra2 "Hewlett-Packard Company [103c]" "Presario V6133CL [30b7]"
00:00.4 "RAM memory [0500]" "nVidia Corporation [10de]" "C51 Memory Controller 4 [02f9]" -ra2 "Hewlett-Packard Company [103c]" "Presario V6133CL [30b7]"
00:00.5 "RAM memory [0500]" "nVidia Corporation [10de]" "C51 Host Bridge [02ff]" -ra2 "Hewlett-Packard Company [103c]" "Presario V6133CL [30b7]"
00:00.6 "RAM memory [0500]" "nVidia Corporation [10de]" "C51 Memory Controller 3 [027f]" -ra2 "Hewlett-Packard Company [103c]" "Presario V6133CL [30b7]"
00:00.7 "RAM memory [0500]" "nVidia Corporation [10de]" "C51 Memory Controller 2 [027e]" -ra2 "" ""
00:02.0 "PCI bridge [0604]" "nVidia Corporation [10de]" "C51 PCI Express Bridge [02fc]" -ra1 "" ""
00:03.0 "PCI bridge [0604]" "nVidia Corporation [10de]" "C51 PCI Express Bridge [02fd]" -ra1 "" ""
00:05.0 "VGA compatible controller [0300]" "nVidia Corporation [10de]" "MCP51 PCI-X GeForce Go 6100 [0247]" -ra2 "Hewlett-Packard Company [103c]" "Unknown device [30b7]"
00:09.0 "RAM memory [0500]" "nVidia Corporation [10de]" "MCP51 Host Bridge [0270]" -ra2 "Hewlett-Packard Company [103c]" "Presario V6133CL [30b7]"
00:0a.0 "ISA bridge [0601]" "nVidia Corporation [10de]" "MCP51 LPC Bridge [0260]" -ra3 "Hewlett-Packard Company [103c]" "Presario V6133CL [30b7]"
00:0a.1 "SMBus [0c05]" "nVidia Corporation [10de]" "MCP51 SMBus [0264]" -ra3 "Hewlett-Packard Company [103c]" "Presario V6133CL [30b7]"
00:0a.3 "Co-processor [0b40]" "nVidia Corporation [10de]" "MCP51 PMU [0271]" -ra3 "Hewlett-Packard Company [103c]" "Presario V6133CL [30b7]"
00:0b.0 "USB Controller [0c03]" "nVidia Corporation [10de]" "MCP51 USB Controller [026d]" -ra3 -p10 "Hewlett-Packard Company [103c]" "Presario V6133CL [30b7]"
00:0b.1 "USB Controller [0c03]" "nVidia Corporation [10de]" "MCP51 USB Controller [026e]" -ra3 -p20 "Hewlett-Packard Company [103c]" "Presario V6133CL [30b7]"
00:0d.0 "IDE interface [0101]" "nVidia Corporation [10de]" "MCP51 IDE [0265]" -rf1 -p8a "Unknown vendor [f03c]" "Unknown device [30b7]"
00:0e.0 "IDE interface [0101]" "nVidia Corporation [10de]" "MCP51 Serial ATA Controller [0266]" -rf1 -p85 "Hewlett-Packard Company [103c]" "Presario V6133CL [30b7]"
00:10.0 "PCI bridge [0604]" "nVidia Corporation [10de]" "MCP51 PCI Bridge [026f]" -ra2 -p01 "" ""
00:10.1 "Audio device [0403]" "nVidia Corporation [10de]" "MCP51 High Definition Audio [026c]" -ra2 "Hewlett-Packard Company [103c]" "Presario V6133CL [30b7]"
00:14.0 "Bridge [0680]" "nVidia Corporation [10de]" "MCP51 Ethernet Controller [0269]" -ra3 "Hewlett-Packard Company [103c]" "Presario V6133CL [30b7]"
00:18.0 "Host bridge [0600]" "Advanced Micro Devices [AMD] [1022]" "K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1100]" "" ""
00:18.1 "Host bridge [0600]" "Advanced Micro Devices [AMD] [1022]" "K8 [Athlon64/Opteron] Address Map [1101]" "" ""
00:18.2 "Host bridge [0600]" "Advanced Micro Devices [AMD] [1022]" "K8 [Athlon64/Opteron] DRAM Controller [1102]" "" ""
00:18.3 "Host bridge [0600]" "Advanced Micro Devices [AMD] [1022]" "K8 [Athlon64/Opteron] Miscellaneous Control [1103]" "" ""
ubuntu@ubuntu-laptop:~$ 


And yeah, as you can see its a HP laptop. Its the G6000, and its a sole install for Ubuntu. However the wireless card was working perfectly in windows before I formatted the HD and installed Ubuntu.
Then it worked in Ubuntu too, but it just wont work now. Its wierd.
Thanks for your time btw man. And if worst comes to worst, il replace the card with one that will definately work with ubuntu, If we cant fix this up, then it would be great if you could suggest a card that will work for sure.
Thanks again man.

---

### Post by Ayuthia on 2008-06-25
> **Lifeis said:**
> Ran the last command there:


And yeah, as you can see its a HP laptop. Its the G6000, and its a sole install for Ubuntu. However the wireless card was working perfectly in windows before I formatted the HD and installed Ubuntu.
Then it worked in Ubuntu too, but it just wont work now. Its wierd.
Thanks for your time btw man. And if worst comes to worst, il replace the card with one that will definately work with ubuntu, If we cant fix this up, then it would be great if you could suggest a card that will work for sure.
Thanks again man.

You might want to check this link out:
[http://forums11.itrc.hp.com/service/forums/bizsupport/questionanswer.do?admit=109447626+1214432494396+28353475&threadId=1179013](http://forums11.itrc.hp.com/service/forums/bizsupport/questionanswer.do?admit=109447626+1214432494396+28353475&threadId=1179013)

I am not seeing your card.  The link says that it is most likely a board issue and not a card issue.  As for me right now, my laptop is being fixed my HP.  If you do find that your card falls under this category, you might want to get yours looked at by HP.  You probably should install the original OS back on there because they might not fix it if it is running Ubuntu.  Not for sure though.  I was too chicken to try.

---

### Post by Lifeis on 2008-06-29
Ima just buy an adapter that works. Iv got this 'BT Voyager 1010 adapter'
Its an external one, usb.
It wont detect that either, and Ndiswrapper says 'Invalid Driver'
But iv read all over the forums that the adapter 'Just works' and that the driver can be dowbloaded from BT's website, which I did, and installed with wine, which i did, and then use Ndiswrapper, but it wont work.
Im stale mate. Im just going to try and find out what wireless adapter, or PCI card definately works with Ubuntu, and buy it. Any ideas?
Thanks for all your time man.

---

### Post by Ayuthia on 2008-06-30
> **Lifeis said:**
> Ima just buy an adapter that works. Iv got this 'BT Voyager 1010 adapter'
Its an external one, usb.
It wont detect that either, and Ndiswrapper says 'Invalid Driver'
But iv read all over the forums that the adapter 'Just works' and that the driver can be dowbloaded from BT's website, which I did, and installed with wine, which i did, and then use Ndiswrapper, but it wont work.
Im stale mate. Im just going to try and find out what wireless adapter, or PCI card definately works with Ubuntu, and buy it. Any ideas?
Thanks for all your time man.
If the adapter is supposed to just work, there is a chance that ndiswrapper is causing the conflict.  I think that you might be able to get by with just making sure that ndiswrapper doesn't have any drivers to load and that should cause ndiswrapper to be disabled.  To accomplish this you will need to make sure that all the drivers are removed from /etc/ndiswrapper:
```
ls /etc/ndiswrapper
```
This command will list out the folders that are in /etc/ndiswrapper.  You will have to remove the folders by:
```
sudo ndiswrapper -e <folder>
```Just replace <folder> with the name of the folder (without the /etc/ndiswrapper prefix).  Also make sure that b43 is blacklisted in /etc/modprobe.d/blacklist.  You can verify this by:
```
cat /etc/modprobe.d/blacklist|grep b43
```and you should see an entry with 'blacklist b43' that is returned.

If that is all done, restart and hopefully your adapter will just work.  Are you using the 64-bit or 32-bit version of Ubuntu?  If you are using the 64-bit version, that might be the issue with the driver.  There are some drivers that are made for Windows that are 32-bit only.  The Linksys PCI adapter that I purchased only had a 32-bit driver that would work for it.  Fortunately, the card worked out of the box.  I was expecting to get a Broadcom chipset in there, but it ended up being a RaLink(rt61pci).  But just for fun, I was trying to get ndiswrapper to work with it.

---

### Post by Lifeis on 2008-07-08
Im using 32bit Ubuntu. I tried that, and it still didnt work.
So I bought 2 new USB wireless adapters (which said on the box "Linux compatable")
But the install instructions wont work for me at all.
So I used Ndiswrapper (its a Ralink chip by the way) and got the XP driver from the disk provided, and it worked. Then it just stopped working after the third time I booted the machine.
I dunno whats up! Thats been three wireless cards and none of them have worked. Except usually they work for one boot, maybe two.
I dont know where to go from here, iv read all the information I can find, like here [http://ubuntuforums.org/showthread.php?t=400236&highlight=serial+monkey]("http://ubuntuforums.org/showthread.php?t=400236&highlight=serial+monkey")
But its way to advance for me. Plus I cant install the Linux driver on the install disk that came with the adapter, because it's to advance too. I didnt really get anywhere doing that.
Its a pitty there isnt just an install file I could run and that would be it working.
I was in the shop I bought my new adapters from, and they will refund them, and let me swap them for another adapter. This one says on the compatability bit several things about Linux, says it works with Debain, Gnu, Mandrake or Manderva or something, loads of distro's. So I don't know whether I should perhaps do that?
Both the adapters I bought both did the same thing, so It isnt that they are physically brocken. I just dont understand it man!
Thanks for all your time and help.

---

### Post by Lifeis on 2008-07-08
And also, the Card's I bought have the Ralink RT73 chip inside of them.
The CD even comes with a "Linux Driver" folder, with a text file in it full of loads of instructions that dont work. I only did manage to get it working using Ndiswrapper, then after about 2 boots it failed.
When you install a driver in Ndiswrapper, say the .inf file is on your desktop, does it have to be kept there? Cause if you dont then Ndiswrapper cant find it at boot, and therefore wont detect hardware?
Thats the only idea I had.
Thanks again man.

---

### Post by jw5801 on 2008-07-08
> **Lifeis said:**
> And also, the Card's I bought have the Ralink RT73 chip inside of them.
The CD even comes with a "Linux Driver" folder, with a text file in it full of loads of instructions that dont work. I only did manage to get it working using Ndiswrapper, then after about 2 boots it failed.
When you install a driver in Ndiswrapper, say the .inf file is on your desktop, does it have to be kept there? Cause if you dont then Ndiswrapper cant find it at boot, and therefore wont detect hardware?
Thats the only idea I had.
Thanks again man.

No you don't have to keep it where you installed from. NDISwrapper copies it to /etc/ndiswrapper/ when you install it.

I don't know if this has been said yet or not, but if the card is not being detected by lspci or lshw, something is seriously seriously wrong, and it has absolutely nothing to do with ndiswrapper or any module at all, and most likely nothing to do with Linux.

If you're still looking to get the broadcom cards working I wrote a how-to [here](http://ubuntuforums.org/showthread.php?t=760568).

Also, installing a driver with wine isn't going to get you anywhere, a driver in linux is a module, something that can be added to the running kernel to assist with low-level hardware interfaces. Wine can't help at all with any of those things.

Ok, that's my impressions of a brief glance through the last 4 pages :P onto the current issue.

Your new adaptor worked fine, but after a couple of reboots in no longer works? What output do you get from:
```
ndiswrapper -l
lshw -C network
sudo rmmod ndiswrapper
sudo modprobe ndiswrapper
dmesg | tail -n10
```

---

### Post by Bucky Ball on 2008-07-08
Are you using Gutsy or Hardy?

I upgraded to Hardy 8.04 and had my wireless card up in about 5 minutes (exactly the Broadcom one you mention in a HP dv6000) using b43fw-cutter with the new b43 driver. I loaded the Cutter in restricted drivers, Hardy did the rest and works a treat after stuffing about with Gutsy, BCMWL5 driver and ndiswrapper for 6 months. I never got that combination to work. The b43 driver is designed (among other things) to overcome the bcmwl5.inf/linux nightmare anyhow, and Hardy works great with that card in my machine. A definite breakthrough for Ubuntu as that card has been a real bug bear by the looks of the posts concerning it.

Good luck ...

---

### Post by Ayuthia on 2008-07-08
> **Lifeis said:**
> And also, the Card's I bought have the Ralink RT73 chip inside of them.
The CD even comes with a "Linux Driver" folder, with a text file in it full of loads of instructions that dont work. I only did manage to get it working using Ndiswrapper, then after about 2 boots it failed.
When you install a driver in Ndiswrapper, say the .inf file is on your desktop, does it have to be kept there? Cause if you dont then Ndiswrapper cant find it at boot, and therefore wont detect hardware?
Thats the only idea I had.
Thanks again man.

From what I can tell, there is a rt73usb module there for your usb device.  I would think that it would work out of the box, but I have never tried it before.  My rt61pci module works out of the box, but of course, they are both different modules so they will work differently.  

You might check and see if ndiswrapper and rt73usb are both being loaded.  If they are, I would think that they are fighting each other:
```
lsmod|grep ndiswrapper rt71
```
I am not for sure if lshw -C network will work for you with your USB device.  From what I was told, lshw works with pci devices, but does not for USB.

---

### Post by Lifeis on 2008-07-08
Yeah, it would be "lsusb" as apposed to "lspci".
I have both of the cards working now, and iv restarted both machines many times.
I think the problem was that you must keep the driver file saved wherever it was when you browsed to it in Ndiswrapper.
If you browse to it, and install the driver, then delete the folder containing it (which is what I did) as I figured that Ndiswrapper would "Install" IE copy the file and configure it, but apperently it creates like a link. I imagine that it is to save space, by not copying the driver .inf file twice.
Thats what I think anyway, cause I installed the driver from a folder on my desktop called "Wireless Driver" and in there is the .inf file.
It is set up the same on both machines. So I just leave the folders there, and iv restarted the machines around five times, and each time the wireless connects automatically as soon as I log in.
Thanks so much for all your time and help.
I will post again, should I encounter any further problems using wireless, but it looks like iv cracked it.
So thank you very much.
- Craig

---

### Post by Lifeis on 2008-07-08
> **jw5801 said:**
> No you don't have to keep it where you installed from. NDISwrapper copies it to /etc/ndiswrapper/ when you install it.

I don't know if this has been said yet or not, but if the card is not being detected by lspci or lshw, something is seriously seriously wrong, and it has absolutely nothing to do with ndiswrapper or any module at all, and most likely nothing to do with Linux.

If you're still looking to get the broadcom cards working I wrote a how-to [here](http://ubuntuforums.org/showthread.php?t=760568).

Also, installing a driver with wine isn't going to get you anywhere, a driver in linux is a module, something that can be added to the running kernel to assist with low-level hardware interfaces. Wine can't help at all with any of those things.

Ok, that's my impressions of a brief glance through the last 4 pages :P onto the current issue.

Your new adaptor worked fine, but after a couple of reboots in no longer works? What output do you get from:
```
ndiswrapper -l
lshw -C network
sudo rmmod ndiswrapper
sudo modprobe ndiswrapper
dmesg | tail -n10
```

For some reason it just works now, on both machines.
Only different thing I can think of is that I kept the drivers where I installed them from. But as you say, it doesn't matter.
I don't know, but both work a treat now. Another weird thing is that on my desktop I have a hard disk running Windows XP and it wont run the card properly! Its wierd cause it did all the "Found new hardware" ****, and installed from the disk, but then it wont use the card. Its weird. But Im not caring cause Ubuntu's running it just fine. =)
So thanks for your time and help. I will post again if any other problems come up. Im just finding my feet with Ubuntu (Heron) so I might come across as being retarded, but Im still learning.
Thanks alot for your time, and for your help.
Very much appreciated :)

---

### Post by beny-4.56 on 2008-07-26
please use this on your ndiswrapper, coz it looks everyone in this thread use bcmwl5.inf. This is the bcmwl6.inf, hopefully could be used

---

### Post by Ayuthia on 2008-07-26
> **beny-4.56 said:**
> please use this on your ndiswrapper, coz it looks everyone in this thread use bcmwl5.inf. This is the bcmwl6.inf, hopefully could be used
The bcmwl6.inf file is the newer version of the Windows driver.  However, this new version does not work with NDISwrapper yet because of all the changes made to that driver.  Based on their website, they are working on a solution for getting the bcmwl6 driver to work but it is not ready yet.

---

### Post by Bucky Ball on 2008-07-26
> 
I upgraded to Hardy 8.04 and had my wireless card up in about 5 minutes (exactly the Broadcom one you mention in a HP dv6000) using b43fw-cutter with the new b43 driver. I loaded the Cutter in restricted drivers, Hardy did the rest and works a treat after stuffing about with Gutsy, BCMWL5 driver and ndiswrapper for 6 months. I never got that combination to work. The b43 driver is designed (among other things) to overcome the bcmwl5.inf/linux nightmare anyhow, and Hardy works great with that card in my machine. A definite breakthrough for Ubuntu as that card has been a real bug bear by the looks of the posts concerning it.

I posted this an eon ago. Forget bcmwl6.inf. It won't work.

You can try ndiswrapper and bcmwl5.inf if you like (some say to have bcmwl5.sys in the same folder), but if you do some research, you will find this method is now obsolete and covered by the new b43 driver and b43fw-cutter. I can just about guarantee (just about!) that Hardy and b43fw-cutter will get your card up. I have exactly the same one.

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx) 

Good luck ...

---

### Post by jw5801 on 2008-07-26
I wouldn't exactly call ndiswrapper+bcmwl5 obsolete! b43 _still_ doesn't handle 802.11g connections, ndiswrapper, however, does. I can guarantee with about the same level of confidence that ndiswrapper+bcmwl5 will get the card up!

---

### Post by Bucky Ball on 2008-07-27
Good luck. I tried for several months ... :)

---

