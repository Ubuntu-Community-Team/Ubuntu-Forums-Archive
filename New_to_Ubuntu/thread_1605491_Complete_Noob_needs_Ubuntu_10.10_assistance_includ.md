---
title: "Complete Noob needs Ubuntu 10.10 assistance including the great Nvidia driver debacle"
date: 2010-10-25
forum: New to Ubuntu
---

### Post by I Am Noob on 2010-10-25
Hey Guys,

Firstly I have tried to be a good Noob and  googled/searched these forums and the official Ubuntu wiki for all the  answers to my questions/issues, but i'm now into double figures in  regards to Maverick Meerkat clean installs on my system after attempting  all the solutions I have found... and its driving me round the bend!  ](*,)

I would like to point out that i'm not a cheapskate, as  i've noticed through my searches the bashing of some Ubuntu 10.10 users  wishing to use low-spec systems on the forums (not necessarily all on  here)... I do have a very high custom Windows 7 64bit box, which is  Intel Quad Core, 8gig Ram, Nvidia Quadro FX blah blah blah... but  because i'm a complete noob to Ubuntu I dare not even attempt to load in  onto that system via dual boot, and so far with all my troubles I think  that's been a very wise decision :D

So, I've ended up using the following old system for my Ubuntu endeavours:

**Operating System:** Ubuntu 10.10 (Maverick Meerkat)
**Processor:** AMD Athlon XP processor 2400+
**Hard Disk Drive:** 60GB Samsung
**Standard Ram:** 512 MB (2x 256 MB DDR SDRAM PC2100) (Ubuntu has created an extra 1500ish MB)
**L2 Cache Memory:** 256 KB (on die)
**Graphics:** Nvidia GeForce4 MX460 graphics chip with 64 MB DDR RAM
**Disk Drive Bay 1:** DVD-RW
**Disk Drive Bay 2:** CD-ROM
**Modem:** Belkin Wireless G Desktop Network Card F5D7000uk (actually works fine in Ubuntu 10.10)
**Connection Capabilities:** i.LINK (4-pin) **/** i.LINK (6-pin) **/** 4 USB ports **/** Memory Stick slot **/** VGA connector **/** DVI connector **/** TV Out **/** and more...

and here are my questions/issues:

**1) The great Nvidia Legacy driver debacle**

I  have tried many of the fixes on this forum and elsewhere as mentioned  above but cannot for the life of me get any kind of support for my  GeForce4 MX460 card! I've been through tones of walk-throughs but they  always result in the buggering up of my system or the reducing of its quality! I  am using the default Ubuntu 10.10 drivers (Nouveau I believe) and at  the moment (from clean install) i'm not particularly fussed with the  loss of 3D (though I would love it) but what is incredibly frustrating  is that I cannot even change my resolution beyond 1024x768 and neither  can I add Visual Effects! Both of which this Nvidia card is perfectly  capable of...

Can anyone point me to a genuine  (completely-noob-friendly) step-by-step guide to how to get my Nvidia  card recognised? Or are there other graphic drivers out there by other  providers that would at least give me more choices on screen resolution  and visual effects!??

**2) The strange Ubuntu/Linux security escapade (Anti-Virus/Firewall)**

Ok,  so I do read a lot across all the forums that Ubuntu and Linux are  perfectly secure... Though this was once mentioned about my beloved  Apple OS X and now we realise that this isn't necessarily true! I get  the picture that i'm very secure from Viruses and the complete trashing  of my system, though after a rather strange occurrence earlier today i'm  more bothered that any remarkably talented Ubuntu/Linux user could  probably be browsing my system just for the kicks!?

[The strange  occurrence that happened a couple of times earlier today has been when I  have needed to use my password, while typing it in, the password box  disappears and then my password re-appears in a box (not blocked  out/obscured) in the bottom right of my screen... which suggests i'm the  victim of key-logging]

Please can someone give me some genuine advice on this issue, as I feel it gets poo-pooed quite a lot..
If  I would like to have Anti-Virus and Firewall on Ubuntu 10.10 for my own  piece of mind what are my options/your recommendations? 

I am  currently running Avast for Linux as my Anti-Virus  ([http://www.avast.com/linux-home-edition#tab1](http://www.avast.com/linux-home-edition#tab1)) and have read some good  reviews on ClearOS Firewall  ([http://www.clearfoundation.com/Software/overview.html](http://www.clearfoundation.com/Software/overview.html)) which I was  contemplating installing on my system.

(Also I did install the  official AVG AV software originally but that never appeared in my  Applications... does it need removing? And what commands can I safely  use to remove it? Assuming the install file is in my Downloads folder)

**3) Hardware Drivers application within System or System/Preferences**

On a couple of posts I have seen people mention a Hardware Drivers application, for detecting your current hardware and finding its most appropriate drivers online... Can anyone tell me if this feature has been removed or re-named in Ubuntu 10.10? I do have the obvious features such as Update Manager but as of now I currently don't not appear to have a Hardware Drivers application anywhere in my system or applications :(

**THE END**

Sorry for rolling on, and **THANK YOU** if you've read this far... **PLEASE**  respond if you feel your knowledge can assist me in anyway, whether it  be direct step-by-step advice or pointing me to another site that has  some completely-noob-friendly answers... All advice will be extremely  appreciated, Ubuntu 10.10 looks awesome so far, I just want to be able to use it properly! :D


[I also would have asked about the wireless (WiFi)  hardware issues i've been having but during this last clean install my  system was hooked-up to the internet directly via Ethernet and all the  online updates downloaded during install seemed to do the trick just  fine - thought i'd mention this in case anyone else has had a similar  problem in 10.10, as I originally had to use a very informative post  that involved me using ralink.com to build my own drivers.. but turned  out there was a much simpler way :)]

---

### Post by cariboo on 2010-10-25
> 1) The great Nvidia Legacy driver debacle

I have tried many of the fixes on this forum and elsewhere as mentioned above but cannot for the life of me get any kind of support for my GeForce4 MX460 card! I've been through tones of walk-throughs but they always result in the buggering up of my system or the reducing of its quality! I am using the default Ubuntu 10.10 drivers (Nouveau I believe) and at the moment (from clean install) i'm not particularly fussed with the loss of 3D (though I would love it) but what is incredibly frustrating is that I cannot even change my resolution beyond 1024x768 and neither can I add Visual Effects! Both of which this Nvidia card is perfectly capable of...

Can anyone point me to a genuine (completely-noob-friendly) step-by-step guide to how to get my Nvidia card recognised? Or are there other graphic drivers out there by other providers that would at least give me more choices on screen resolution and visual effects!??

Nvidia hasn't created a driver for your graphics card that is compatible with the latest version of Xorg used in Maverick. The nouveau drivers work quite well on even newer graphics cards. To get 3D you need to install libgl1-mesa-dri-experimental, it is in the repositories.

> 2) The strange Ubuntu/Linux security escapade (Anti-Virus/Firewall)

Ok, so I do read a lot across all the forums that Ubuntu and Linux are perfectly secure... Though this was once mentioned about my beloved Apple OS X and now we realise that this isn't necessarily true! I get the picture that i'm very secure from Viruses and the complete trashing of my system, though after a rather strange occurrence earlier today i'm more bothered that any remarkably talented Ubuntu/Linux user could probably be browsing my system just for the kicks!?

[The strange occurrence that happened a couple of times earlier today has been when I have needed to use my password, while typing it in, the password box disappears and then my password re-appears in a box (not blocked out/obscured) in the bottom right of my screen... which suggests i'm the victim of key-logging]

Please can someone give me some genuine advice on this issue, as I feel it gets poo-pooed quite a lot..
If I would like to have Anti-Virus and Firewall on Ubuntu 10.10 for my own piece of mind what are my options/your recommendations?

I am currently running Avast for Linux as my Anti-Virus ([http://www.avast.com/linux-home-edition#tab1](http://www.avast.com/linux-home-edition#tab1)) and have read some good reviews on ClearOS Firewall ([http://www.clearfoundation.com/Software/overview.html](http://www.clearfoundation.com/Software/overview.html)) which I was contemplating installing on my system.

(Also I did install the official AVG AV software originally but that never appeared in my Applications... does it need removing? And what commands can I safely use to remove it? Assuming the install file is in my Downloads folder)

The problem you suffered from is probably a bug, I haven't heard of it before, but most new users attribute any strange behaviour to viruses. The likelihood of a key logger being installed on your system is slim to none, without user intervention, in other words the key logger would have to be installed by someone who has administration rights on your system. If you are running a default install, you are the only user with administration rights,

There is a firewall, iptables installed by default, so all you need is a frontend to set firewall rules. Ufw is installed by default, it stands for uncomplicated firewall, it is a command line tool for setting firewall rules. There is also a graphical tool that has the same function called Gufw, it is in the repositories. To enable the default rules with ufw, just open a Applications->Accessories->Terminal and type:

```
sudo ufw enable
```

If you are running a default installation without any extra services like, ssh, remote desktop or a web server the default firewall rules are more than enough. If you have an other computer on your local network, you can do a port scan against the system to check it for yourself.

AVG is a command line application, that's why it isn't in your menu system, I've never installed it on a Linux system, but if it has a .deb extension, you can use System->Administration->Synaptic Package Manager to remove it. If you really feel the need for an av scanner, be aware that most of them only scan for Windows viruses, as ther aren't any Linux viruses in the wild at the moment. I've been using a Linux variant since 1998, and I have yet to see a real Linux virus.

> 3) Hardware Drivers application within System or System/Preferences

On a couple of posts I have seen people mention a Hardware Drivers application, for detecting your current hardware and finding its most appropriate drivers online... Can anyone tell me if this feature has been removed or re-named in Ubuntu 10.10? I do have the obvious features such as Update Manager but as of now I currently don't not appear to have a Hardware Dryivers application anywhere in my system or applications


The Additional Driver menu item is only for hardware that needs proprietary drivers, like graphics or wireless cards. All the open source drivers are included as part of the kernel, and your hardware should be auto-detected, and the proper drivers loaded.

Hardware detection has become quite a bit better in Maverick, and will continue to get better in following versions.

---

### Post by I Am Noob on 2010-10-26
Ok.. firstly I would like so send out a **HUGE** thank you to [[COLOR=#d40000]**cariboo907**[/COLOR]]("http://ubuntuforums.org/member.php?u=77104"):KS [John Harrington]("http://ubuntuforums.org/member.php?u=370025"):KS and [christian.remboldt]("http://ubuntuforums.org/member.php?u=1162302"):KS for their replies and feedback into resolving the issues I have mention on this thread and two others... nobody forces you to help out of these forums and your help with me has been **GREATLY** appreciated... Than you :mrgreen:


**My Original Thread:** [http://ubuntuforums.org/showthread.php?t=1605491](http://ubuntuforums.org/showthread.php?t=1605491) 
**[John Harrington]("http://ubuntuforums.org/member.php?u=370025")'s post is in this thread:** [http://ubuntuforums.org/showthread.php?t=1592628](http://ubuntuforums.org/showthread.php?t=1592628)
**[christian.remboldt]("http://ubuntuforums.org/member.php?u=1162302")'s post/thread can be found here:** [http://ubuntuforums.org/showthread.php?t=1590367](http://ubuntuforums.org/showthread.php?t=1590367)


I have not managed to resolve ALL my issues (will ask you another Question at the end of this reply), but here's what I did:

> **cariboo907 said:**
> Nvidia hasn't created a driver for your graphics card that is compatible with the latest version of Xorg used in Maverick. The nouveau drivers work quite well on even newer graphics cards. To get 3D you need to install libgl1-mesa-dri-experimental, it is in the repositories.

I took this advice and did install libgl1-mesa-dri-experimental from my repositories within System>Administration>Synaptic Package Manager but unfortunately this did not solve my issue, I was still unable to activate Visual Effects within System>Preferences>Appearance after double checking with a new reboot of course :(

Then I re-read this thread: [http://ubuntuforums.org/showthread.php?t=1590367](http://ubuntuforums.org/showthread.php?t=1590367) from [christian.remboldt]("http://ubuntuforums.org/member.php?u=1162302") and decided that because I had a FRESH install I would not need to make changes to /etc/X11/xorg.conf.
as the Nouveau drivers were already installed by default. However I did take the following advice...

> **christian.remboldt said:**
> you need the 3d driver this file is not included in any package. /usr/lib/dri/nouveau_vieux_dri.so

...but instead building the file myself (because im SUCH a noob) I took a big leap of faith...

> **christian.remboldt said:**
> If you don't want to build it yourself, here is a link to the one I built yesterday. [http://www.mediafire.com/?bzszrsej376y8q7](http://www.mediafire.com/?bzszrsej376y8q7)

and did the unthincable, as a noob, to download and used someone else' self built file!

I then moved my file  to /usr/lib/dri 

> **christian.remboldt said:**
> "Ctrl+Alt+t" this will open a terminal window. In the terminal type "cd  /home/<user name>/Desktop" then hit enter. In place of <user  name> make sure to put your user name. This will change you current  working directory to the desktop. Then type "sudo cp  nouveau_vieux_dri.so /usr/lib/dri" and hit enter. You will be prompted  for your administrator password. On successfully entering the password  and pressing enter the file will be copied.

and restarted... Sh'bang, Sh'bong Thongsong! I suddenly had my Ubuntu 10.10 singing and dancing, running all the extra Visual Effects quite nicely :D

[B]NOW... the only problem is that Ubuntu still does not recognise my LG M228WA - BZ monitor!
Its a 22" screen and has always run at much higher resolutions than 1024x768, I do realise that my Nvidia graphics card(s) may have had some role to play in that but im sure this monitor once told me itself (when I configured Windows resolution wrong) that its best resolution was something like 1680 x 1050... so my question is HOW do I get Ubuntu to recognise the true potential of my monitor?[/B] :confused:

[B]PLEASE HELP ME ONCE MORE...

[/B]:mrgreen:I Am Noob

P.S.

> **cariboo907 said:**
> There is a firewall, iptables installed by default, so all you need is a  frontend to set firewall rules. Ufw is installed by default, it stands  for uncomplicated firewall, it is a command line tool for setting  firewall rules. There is also a graphical tool that has the same  function called Gufw, it is in the repositories. To enable the default  rules with ufw, just open a Applications->Accessories->Terminal  and type:

```
sudo ufw enable
```If you are running a default installation  without any extra services like, ssh, remote desktop or a web server the  default firewall rules are more than enough. If you have an other  computer on your local network, you can do a port scan against the  system to check it for yourself.

I also took this advice and my firewall is now enabled GUI style, thanks again!

---

### Post by Thorondir on 2010-10-29
> **I Am Noob said:**
> 

[The strange  occurrence that happened a couple of times earlier today has been when I  have needed to use my password, while typing it in, the password box  disappears and then my password re-appears in a box (not blocked  out/obscured) in the bottom right of my screen... which suggests i'm the  victim of key-logging]



just to set straight what is happening there:
the field where you should be typing your password in is not active, and the system goes on to search for whatever you are typing in the window that is active.
[you can try this in nautilus. just open a folder and start typing. you get the same box, and if it does find something beginning with your keywords, it will select it.]

cheers,
Thorondir

---

### Post by beew on 2010-10-29
Regarding the Nvidia card. I found a way to install the nvidia-96 driver (also used by your card) in 10.10. I have been testing it for a while,  I am having full 3D effect and compiz etc (resolution 1680X1050) with no issue.

Basically I downgraded xorg to the 10.04 version. 

[http://ubuntuforums.org/showthread.php?t=1598591](http://ubuntuforums.org/showthread.php?t=1598591)

---

### Post by vanislej on 2010-10-30
Thankyou for this posting.  I am basically a complete newbie too, I played with linux many times and different distributions many years ago, but never quite got anything installed right, now I have ubuntu 10 working on two computer, and the desktop visuals thing was driving me nuts.  

Its all working now, thanks so much!!

~Justin

---

