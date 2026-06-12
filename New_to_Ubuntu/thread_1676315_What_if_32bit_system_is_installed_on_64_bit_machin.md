---
title: "What if 32bit system is installed on 64 bit machine?"
date: 2011-01-27
forum: New to Ubuntu
---

### Post by liatodua on 2011-01-27
Hi,

I have Ubuntu 10.10 installed at IBM T30 10-years old laptop. I noticed that the machine hots up more than it used with Windows. I adjusted power management to spin down hard disk when possible. It helped a bit but still temperature seems to me higher than usually. 

Another problem is that the machine gets stuck easily: 6-7 firefox tabs + 1 download +anything else makes computer non-responsive to anything except pushing the power button.

Could that be due to the fact that while selecting the Ubuntu installation package, as I was not sure if my machine is 32bit or 64bit, I selected the  safer - 32bit option? Although I am not sure what this 32bit-64bit thing means. I assume it has to do with the speed, no?

---

### Post by NightwishFan on 2011-01-27
No, for usual tasks there is not much difference between 32-bit and 64-bit (not that you would notice). The main advantage is using more than 3gb of RAM. There are simple workarounds for 32-bit to use more RAM, but it is just much cleaner to support such huge pages natively with 64-bit.

As such I recommend 64-bit but do no recommend a full reinstall unless you have specific needs that are not covered by 32-bit (likely not). Your problem lies elsewhere. Perhaps you can debug it. Using the command "top" from the terminal, you can see what processes are using the most CPU. You might have a runaway process that is slowing the system.

---

### Post by Vaphell on 2011-01-27
standard gnome may be a bit too heavy for 10year old machine. You should consider installing lighter desktop environment.

Flash heavy sites tax cpu hard, ditto tons of javascript. I'd install adblock (with filter list) and noscript addons to reduce the amount of unneeded crap running - ads, datamining scripts, etc.

---

### Post by Ctrl-Alt-F1 on 2011-01-27
32 vs 64bit determines how much data the CPU can handle from RAM.  64bit operating systems can perform some tasks quicker, if the program was compiled in 64bit--which often isn't the case.  The biggest difference most users see is that with 32bit processors your OS will only support 4GB of RAM, while with 64bit you can have many multiples that amount of RAM.

Since 4GB of memory is more than enough for most people. I don't think it's really an issue right now for most people to use a 32bit OS.

If your laptop is 10 years old.  It has a 32bit CPU and a 64bit OS will NOT run on it.  However, 32bit operating systems run perfectly on a machine that is capable of 64bit processing.

---

### Post by cascade9 on 2011-01-27
> **Vaphell said:**
> standard gnome may be a bit too heavy for 10year old machine. You should consider installing lighter desktop environment.

Flash heavy sites tax cpu hard, ditto tons of javascript. I'd install adblock (with filter list) and noscript addons to reduce the amount of unneeded crap running - ads, datamining scripts, etc.

+1

> **Ctrl-Alt-F1 said:**
> 32 vs 64bit determines how much data the CPU can handle from RAM. 64bit operating systems can perform some tasks quicker, if the program was compiled in 64bit--which often isn't the case. The biggest difference most users see is that with 32bit processors your OS will only support 4GB of RAM, while with 64bit you can have many multiples that amount of RAM.

Almost anything with a chipset that supports 4GB+ with work with PAE (which goes much higher than 3.something GB). 

PAE is a bit of hack though, its slower than 'pure' 32bit, let alone 64bit, and cant use more than 3/4GB for a single process. 

> **Ctrl-Alt-F1 said:**
> Since 4GB of memory is more than enough for most people. I don't think it's really an issue right now for most people to use a 32bit OS.

If people have a 64bit capapble CPU, why give away the speed increase of 64bit? If you are one of those unlucky people with something that wont run on 64bit (VERY rare now) I can understand it, but for most people 64bit is a better way to go IMO.

---

### Post by Paqman on 2011-01-27
> **Vaphell said:**
> standard gnome may be a bit too heavy for 10year old machine.

It's not really Gnome that's the problem, but rather the default package ubuntu-desktop. If you install one of the lighter Gnome packages like gnome-core you'll find it'll only consume about 100MB of RAM.

However, it's not your DE that will eat all the RAM (with the possible exception of KDE), but rather the apps. Switching to lighter apps such as Abiword and Gnumeric instead of Open Office will make a huge difference and won't require changing DEs.

How much memory does the machine have liatodua? Those T30s look like they came with 256MB of RAM, which isn't much. Installing moe would make the machine faster, and would also stop it swapping to disk so much, which would help keep the heat down and the battery life up. It can take up to 1GB. 

So you've got the option of either a hardware or a software solution. Hardware is probably quicker and easier, but software is cheaper.

---

### Post by dmizer on 2011-01-27
> **liatodua said:**
> Hi,

I have Ubuntu 10.10 installed at IBM T30 10-years old laptop. I noticed that the machine hots up more than it used with Windows. I adjusted power management to spin down hard disk when possible. It helped a bit but still temperature seems to me higher than usually. 

Another problem is that the machine gets stuck easily: 6-7 firefox tabs + 1 download +anything else makes computer non-responsive to anything except pushing the power button.

Could that be due to the fact that while selecting the Ubuntu installation package, as I was not sure if my machine is 32bit or 64bit, I selected the  safer - 32bit option? Although I am not sure what this 32bit-64bit thing means. I assume it has to do with the speed, no?

The IBM T30 is a 32 bit Pentium 4 laptop. It is most certainly not a 64 bit computer, so you did the correct thing by installing 32 bit.

On a 10 year old computer, the heat could be a result of many things, including dirt/dust.

The "non-responsive" experience you're getting could be a result of your elderly (and only moderately supported) ATI Mobility Radeon 7500 graphics chipset.

edit:
After a bit of research, I found this thread that you might be interested in: [http://ubuntuforums.org/showthread.php?t=1594827](http://ubuntuforums.org/showthread.php?t=1594827)

---

### Post by liatodua on 2011-01-27
> How much memory does the machine have liatodua? 
The ubuntu system monitor says Memory 496.1 MiB
IBM support site says my machine is P4-M 1.8GHz (512KB), 256MB RAM, 40.0GB HDD, 14.1 XGA(1024x768) TFT LCD,  8x-3.3x DVD-ROM, Modem(CDC), Ethernet(LOM), UltraNav, Li-Ion battery

---

### Post by liatodua on 2011-01-27
> The "non-responsive" experience you're getting could be a result of your  elderly (and only moderately supported) ATI Mobility Radeon 7500  graphics chipset

Ubuntu Sysinfo says my graphic card is sth called ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500] (prog-if 00 [VGA controller]). I guess this is the one you mean?

I followed the link you gave and will try to do what is suggested there. If I manage to understand that. Thanks anyway.

---

### Post by cascade9 on 2011-01-27
> **Paqman said:**
> It's not really Gnome that's the problem, but rather the default package ubuntu-desktop. If you install one of the lighter Gnome packages like gnome-core you'll find it'll only consume about 100MB of RAM.

True ;) 

> **liatodua said:**
> The ubuntu system monitor says Memory 496.1 MiB
IBM support site says my machine is P4-M 1.8GHz (512KB), 256MB RAM, 40.0GB HDD, 14.1 XGA(1024x768) TFT LCD,  8x-3.3x DVD-ROM, Modem(CDC), Ethernet(LOM), UltraNav, Li-Ion battery

Ubuntu-desktop wont run very well on that machine, no matter what you do. You could try installing xfce4- 

sudo apt-get install xfce4 

When its finished installing, logout then select 'xfce' at the login screen. 

*edit- yuo might need to reboot instead of just loging out, I'm not sure. 

Or you could try lubuntu.

---

### Post by liatodua on 2011-01-27
Thanks for all your replies. I did not understand all of it but what I understood is that it is not 32-64 bit issue (whatever that issue means) but rather the small RAM and heavy software, or/and the old graphic card which is not properly supported under the Ubuntu. And that I have to either replace Gnome, OpenOffice, or/and flash applications with sth lighter, or do some really tricky thing to make my old graphical card supported properly. OK, I'll try.

---

### Post by liatodua on 2011-01-27
> Or you could try lubuntu.

I like this idea. Thank you.

---

### Post by cascade9 on 2011-01-27
> **liatodua said:**
> I like this idea. Thank you.

Personally, I cant stand the DE (desktop enviroment) lubuntu uses (lxde) and I much prefer xfce4. Which I why I posted the whole 'sudo apt-get install xfce4' option.  

It should be easy enough to do, you just open a terminal, type it in, hit enter and it does the rest. 

But if you like the look of lubuntu, go ahead ;)

---

### Post by liatodua on 2011-01-27
I have no Idea what the Lubuntu looks like. This option just seemed the easiest. Intalling sth called xfce4 sounds really scary. And option with need for rebooting (from where?) - even worse. But  you are right - I might try that and if it will not work will than there is Lubuntu available.

Ok I will now do this xfce4sth. Cross fingers.

---

### Post by cascade9 on 2011-01-27
> **liatodua said:**
> I have no Idea what the Lubuntu looks like. This option just seemed the easiest. Intalling sth called xfce4 sounds really scary. And option with need for rebooting (from where?) - even worse. But  you are right - I might try that and if it will not work will than there is Lubuntu available.

Ok I will now do this xfce4sth. Cross fingers.

You can get an idea of what lubuntu, and xfce4 look like here- 

[http://expressubuntu.blogspot.com/2011/01/6-alternative-ubuntu-desktops.html](http://expressubuntu.blogspot.com/2011/01/6-alternative-ubuntu-desktops.html)

No, they arent great shots, sorry. 

Rebooting, thats not as scary as it sounds. Its pretty much the same as shutdown, but instead of hitting the shutodwn button, you hit reboot. You can even shut downand then start the computer again if you prefer. 

I just wish I could find a screenshot to show you where to change what desktop you are loging into. :(

---

### Post by liatodua on 2011-01-27
Thanks for this link. I understand now what the DE and all this other abbreviations mean.

I installed the xfce4. But I really do not understand how to reboot. I tried to log out, to restart the  computer, to simply shut down and switch on, I even tried to 'boot from temporary device' and selected hard disk as that device - no success. Every time I am getting back to my usual ubuntu desktop and no option for anything else. :(

---

### Post by amra.sonntag on 2011-01-27
The problem is most likely your graphics support. I have to make a point for the older IBM Thinkpads here. From what you posted - you got 500MB ram in that T30 - and it should satisfy the needs of a normal user (web sites, office, music, etc.).

I have been running a T23 with 500 MB ram and an Intel GPU for several years up to Ubuntu 10.04 and never had an Issue with it - using the standard Ubuntu/Gnome environment. (however the cpu fan control is starting to fail by now >.<)

So try to sort that ATI GPU out and you should be fine.

---

### Post by liatodua on 2011-01-27
Oh! So you mean I should rather trust the system monitor saying that the memory is 496MB, not 256MB? Oh, I see. OK than. I'll try to understand this graphic card thing. 

Thanks!

---

### Post by cascade9 on 2011-01-27
@ amra.sonntag- goes to show, what its acceptable to one person isnt for another. Using ubuntu on 512MB machines is slow as hell for me, even with a faster CPU and a newer unsuppoprted ATI card than whats in that T30. 

> **liatodua said:**
> I installed the xfce4. But I really do not understand how to reboot. I tried to log out, to restart the  computer, to simply shut down and switch on, I even tried to 'boot from temporary device' and selected hard disk as that device - no success. Every time I am getting back to my usual ubuntu desktop and no option for anything else. :(

When your computer gets to the screen where you need to enter your username and passowrd, you can change the DE you are loging into there. 

From memory, the selector is at the bottom of the screen, and it should be where it says 'session'. You click that and change to 'xfce4'. 

I cant check because I dont have ubuntu installed now.

---

### Post by liatodua on 2011-01-27
I finally managed it! Wow!

> When your computer gets to the screen where you need to enter your  username and passowrd, you can change the DE you are loging into there. 

The problem was that it only asked password after logging to the DE, not before. Bu I discovered System->Administration->Login Screen and I played with its option and now I have a possibility to select the DE where I log! 

Thank you!

---

### Post by cascade9 on 2011-01-27
No problem. 

Could you please lets us (or at least me! :) ) know if you find it an improvement over standard ubuntu? ;)

---

### Post by liatodua on 2011-01-27
:) OK. I will try it and will write back.

---

### Post by uRock on 2011-01-27
If you can upgrade the RAM, then the system will work much better. 

I have a Dell with a P4  and it runs great with Ubuntu. I have tested Xubuntu on the same machine and it used the same amount of RAM, yet it has much less functionality.

Lubuntu is a great choice. The GUI isn't as pretty, but the performance makes up for the lack of bling.

---

### Post by cascade9 on 2011-01-27
> **uRock said:**
> If you can upgrade the RAM, then the system will work much better. 

I have a Dell with a P4  and it runs great with Ubuntu. I have tested Xubuntu on the same machine and it used the same amount of RAM, yet it has much less functionality.

Xubuntu is fat. Xfce4 is far slimer. 

Yeah, I know, xubuntu isnt as bad as it used to be from all reports, but still is far fatter than it needs to be..thats why I never put xubuntu down, and said get xfce4, not get xubuntu-desktop.

---

### Post by amra.sonntag on 2011-01-27
> **cascade9 said:**
> @ amra.sonntag- goes to show, what its acceptable to one person isnt for another. Using ubuntu on 512MB machines is slow as hell for me, even with a faster CPU and a newer unsuppoprted ATI card than whats in that T30.

Yeah, i realize that and was only pointing it out because he reported an unresponsive system after just a few tabs in firefox. And I never had issues like that. Since I have a new laptop now, i wouldn't want to switch back either. ;)

@liatodua: I hope you get your problem solve one way or the other.

---

### Post by liatodua on 2011-01-28
It worked! I have now open 8 firefox tabs (including facebook, twitter, wikimapia, livejournal - with all their apps) + downloading video file + file manager+ VLC media player = and the machine is just fine.

I still have to find out how to easily switch between the English-Georgian-Russian layouts of keyboard in this new desktop. The rest is fine. Thanks again.

---

### Post by liatodua on 2011-01-28
I still plan to try lubuntu at some point - at least for my 2 years grandchilds education. Thank you!

---

### Post by dudetime on 2011-01-28
> **cascade9 said:**
> True ;) 



Ubuntu-desktop wont run very well on that machine, no matter what you do. You could try installing xfce4- 

sudo apt-get install xfce4 

When its finished installing, logout then select 'xfce' at the login screen. 

*edit- yuo might need to reboot instead of just loging out, I'm not sure. 

Or you could try lubuntu.
  also xubuntu may be able to effectivly run on an IBM

---

### Post by HiImTye on 2011-01-28
ubuntu uses a PAE kernel so the 4GB addressing space limitation is no longer a factor. the only difference now, really, is the ability to do 64bit computing. for most people 32bit is fine but for some they need/want the ability to have 64bit

alot of builds have switched to PAE because of some of the built in security features and they also benefit from the larger addressing space

typically, 32bit is the easiest to use as some programs require more tuning to use 64bit (wine, for example) although not always the case

64bit processors will fall back to 32 bit if they are presented with a 32bit kernel

hope this clears some things up!

---

### Post by cascade9 on 2011-01-30
> **amra.sonntag said:**
> Yeah, i realize that and was only pointing it out because he reported an unresponsive system after just a few tabs in firefox. And I never had issues like that. Since I have a new laptop now, i wouldn't want to switch back either. :wink:

Fair enough. I've found that the content on those tabs can make a big difference, as can addons, etc.. 

> **liatodua said:**
> It worked! I have now open 8 firefox tabs (including facebook, twitter, wikimapia, livejournal - with all their apps) + downloading video file + file manager+ VLC media player = and the machine is just fine.

I still have to find out how to easily switch between the English-Georgian-Russian layouts of keyboard in this new desktop. The rest is fine. Thanks again.

I'm glad it helped. :D 

I dont know anything about keybaord layout switching, but I'd say that whatever program you used in gnome (standard ubuntu) should work well with Xfce4 ;)

---

### Post by Ctrl-Alt-F1 on 2011-01-31
> **cascade9 said:**
> 
If people have a 64bit capapble CPU, why give away the speed increase of 64bit? If you are one of those unlucky people with something that wont run on 64bit (VERY rare now) I can understand it, but for most people 64bit is a better way to go IMO.
Agreed. Which is why I run two 64bit operating system.  Almost all new machines are going to be 64bit, but that doesn't change the fact that there are still more 32bit machines in the wild.

---

### Post by liatodua on 2011-02-05
I did al these (except of installing dkms (not sure how to and if it is necessary):

> First I added the xorg edgers ppa [https://launchpad.net/~xorg-edgers/+archive/ppa]("https://launchpad.net/%7Exorg-edgers/+archive/ppa") and ran a sudo apt-get update && sudo apt-get upgrade

next i install dkms (don't know if this is part of it but it seems to be) 

next I ran sudo echo options radeon modeset=1 | sudo tee /etc/modprobe.d/radeon.conf

next sudo update-initramfs -u and after it was done rebuilding the kernel

sudo nano /etc/default/grub and add radeon.modeset=1 to the  GRUB_CMDLINE_LINUX="" line within the quotes and sudo update-grub and  restart Heat is still there but the movie players work better (used to smash video at some point so I had to restart the player)

And yes - it allowes me to open more applications at the same time now

---

### Post by Paqman on 2011-02-05
> **liatodua said:**
> I did al these (except of installing dkms (not sure how to and if it is necessary):


Go ahead and install it, it's very useful. When you receive a kernel update dkms will make sure that any kernel modules that you've added (eg: graphics and wifi drivers) get automatically added to the new kernel as well. If you don't install dkms then these will break when you get a kernel update (which is fairly often).

To install it, open up Synaptic, search for dkms, tick the box next to it, and hit apply.

---

### Post by liatodua on 2011-02-05
Ok. Done. Thank you!

---

