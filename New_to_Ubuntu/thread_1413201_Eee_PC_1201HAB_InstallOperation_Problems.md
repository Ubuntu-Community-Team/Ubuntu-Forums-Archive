---
title: "Eee PC 1201HAB Install/Operation Problems"
date: 2010-02-22
forum: New to Ubuntu
---

### Post by Bearhardt on 2010-02-22
Hey everyone! My name is Mark and I am a brand new adventurer in the world of Linux. I recently decided to start fiddling with Linux distros and have honestly been having quite a bit of difficulty.

I've succeeded in installing Ubuntu 9.10 on my desktop and that's been working fine. What I really want to do, however, is get a distro running on my netbook.

My machine is an Asus Eee PC 1201HAB with an Intel GMA 500 Media Accelerator. I have attempted to install several Linux distros, each time with a full format so I knew I was starting from a clean slate. Linux Mint 8 would install fine, but during operation it would intermittently stop responding, with my display becoming a garbled mess of flickering junk not unlike when a GPU explodes (something I, sadly, experienced with my iMac). I then tried Ubuntu Netbook Remix and the same thing happened, but during installation this time. Then I tried regular Ubuntu 9.10 and it crashed out with the same graphical garble.

Thus far the only distro that I've successfully installed and run is Jolicloud and I'm not a big fan. I know UNR is similar but I really would rather just have that instead of Joli.

So after failing several times I just went back to Windows 7 which, interestingly enough, works just fine all by itself.

I would really love to get Ubuntu running on my netbook but I'm starting to think it just won't happen. 

Any thoughts?

---

### Post by NCLI on 2010-02-22
> **Bearhardt said:**
> Hey everyone! My name is Mark and I am a brand new adventurer in the world of Linux. I recently decided to start fiddling with Linux distros and have honestly been having quite a bit of difficulty.

I've succeeded in installing Ubuntu 9.10 on my desktop and that's been working fine. What I really want to do, however, is get a distro running on my netbook.

My machine is an Asus Eee PC 1201HAB with an Intel GMA 500 Media Accelerator. I have attempted to install several Linux distros, each time with a full format so I knew I was starting from a clean slate. Linux Mint 8 would install fine, but during operation it would intermittently stop responding, with my display becoming a garbled mess of flickering junk not unlike when a GPU explodes (something I, sadly, experienced with my iMac). I then tried Ubuntu Netbook Remix and the same thing happened, but during installation this time. Then I tried regular Ubuntu 9.10 and it crashed out with the same graphical garble.

Thus far the only distro that I've successfully installed and run is Jolicloud and I'm not a big fan. I know UNR is similar but I really would rather just have that instead of Joli.

So after failing several times I just went back to Windows 7 which, interestingly enough, works just fine all by itself.

I would really love to get Ubuntu running on my netbook but I'm starting to think it just won't happen. 

Any thoughts?

The GMA 500 Poulsbo... Ouch. [This link]("http://en.wikipedia.org/wiki/Intel_GMA#GMA_500_on_Linux") should tell you everything you need to know. Good luck though, it's not easy. I've heard that a better driver will be ready in time for Lucid.

---

### Post by walt.smith1960 on 2010-02-22
I'm a newbie myself but here is that I would try. Search in synaptic for "backports" and check the box then install. You can also enable backports via the command line. Here is something I saved:
From an account with administrative priviledges:

sudo apt-get update

sudo apt-get upgrade

sudo apt-get install linux-backports-modules-karmic

restart the machine

I'm not sure how important the update and upgrade entries are but presumably that get you to the latest version.  As I understand it backports are unofficial patches that may support new hardware.  I had good luck using backports on an Eee1005HAB when the wireless chip was not supported under 9.04. Enabling backports made the wireless work.  The other thing I might try would be to download the latest developmental release of Lucid. Expect developmental releases to have some bugs but it sounds like Lucid should support that graphics chip natively.  I used 9.10 alpha 2 or 3 on the Netbook and it worked quite reliably. I kept running update frequently while using the alpha version as updates were quite frequent. This may or may not help but if it were me I'd give it a try.  One of the beauties of Ubuntu is you don't have to go on bended knee to some dictatorial company and beseech them for permission to reinstall an operating system or other software.

---

