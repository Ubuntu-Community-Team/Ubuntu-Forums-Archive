---
title: "New to Linux: Networking"
date: 2007-04-06
forum: Networking &amp; Wireless
---

### Post by udstuen on 2007-04-06
I'm new to Linux and am having trouble with networking.

I have a Belking N5D7001 WiFi card already installed in the PC.  The Device Manager in my Ubuntu seems to recognize that the card is in the computer (it shows it's a Belkin and whatnot).  What can I do to get connected to the internet.

I couldn't search for it.  Please don't jump down my throat for this...I know how forums run.

---

### Post by GSF1200S on 2007-04-06
> **udstuen said:**
> I'm new to Linux and am having trouble with networking.

I have a Belking N5D7001 WiFi card already installed in the PC.  The Device Manager in my Ubuntu seems to recognize that the card is in the computer (it shows it's a Belkin and whatnot).  What can I do to get connected to the internet.

I couldn't search for it.  Please don't jump down my throat for this...I know how forums run.

Haha, relax.. noone on this forum will jump down your throat.. its a pretty friendly place. 

You have two options:

madwifi, or ndiswrapper

I would try madwifi first. First, do a google search for madwifi, go to there website and see if your card is supported. Go to the Synaptic Package Manager, and search for 'linux restricted modules' (make sure you enable in the repositories). Once found, download and install. Then search for madwifi tools and install. Upon a reboot, your wireless should work fine. If you intend to get your video drivers working, than eventually you will have to install the madwifi drivers manually via the website. This is fairly easy..

Post back whether or not youve had any luck with the above listed methods. If not Ill do a little research on your card and try to help you. If madwifi will support your card, I should be able to get you going. If you have to use ndiswrapper, I may not be of much help, but Ill try.

Take it easy...

---

### Post by udstuen on 2007-04-06
Thanks for the help,

I have found the "linux restricted modules."  There are several selections that can be made for installation.  Which one should I do?  All?

What are repositories?  How do you "enable" them?

---

### Post by udstuen on 2007-04-06
Also....It won't connect to the internet and cannot download anything.  For each module, it says  it failed to fetch....

---

### Post by udstuen on 2007-04-06
Anyone?

---

### Post by r3m0t on 2007-04-06
A repository is a collection of packages. To enable the repositories, follow  [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu) - you will need to tick "restricted".

Is it possible to connect the computer via an Ethernet wire for a short amount of time, instead of wireless? If it is, connect it up, restart Ubuntu, and do this:

> Tick "restricted" as explained above and then open a terminal (applications -> accessories or applications -> system tools) and type this exactly:
```
sudo apt-get linux-restricted-modules-`uname -r`
```
The ` character is next to 1 on most keyboards.

Otherwise, do this:> 
Instead of downloading the package from Ubuntu, you will need to download it from Windows and transfer it into Ubuntu using a USB memory stick, by burning a CD, or something similar. Do the following:

1) Open a terminal (applications -> accessories or applications -> system tools) and type this exactly:
```
echo `uname -r`
```
Copy the result (it should begin with "2.6.") onto a piece of paper and post it here.

---

### Post by GSF1200S on 2007-04-06
> **r3m0t said:**
> A repository is a collection of packages. To enable the repositories, follow  [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu) - you will need to tick "restricted".

Is it possible to connect the computer via an Ethernet wire for a short amount of time, instead of wireless? If it is, connect it up, restart Ubuntu, and do this:



Otherwise, do this:

He explained the deal with the repositories quite well...

What restricted modules depends on your computer. If you have a computer with a single core processor, install the following restricted modules:

linux-restricted-modules-2.6.20.14-386
linux-restricted-modules-common

If your computer has a dual core, install the following:

linux-restricted-modules-2.6.20.14-generic
linux-restricted-modules-common

Basically, so you know for the future, 386 designates a computer with a single core processor, while generic designates a dual core. If you install a 386 kernel on a computer with a dual core processor, for example, only one core of the processor will be used.

Be sure to search for madwifi in the package manager, and download/install the following:

madwifi-tools

If this doesnt help you, than you may have to try the ndiswrapper route.. let me know...

---

### Post by r3m0t on 2007-04-06
> **GSF1200S said:**
> He explained the deal with the repositories quite well...

What restricted modules depends on your computer. If you have a computer with a single core processor, install the following restricted modules:

linux-restricted-modules-2.6.20.14-386
linux-restricted-modules-common

If your computer has a dual core, install the following:

linux-restricted-modules-2.6.20.14-generic
linux-restricted-modules-common

Basically, so you know for the future, 386 designates a computer with a single core processor, while generic designates a dual core. If you install a 386 kernel on a computer with a dual core processor, for example, only one core of the processor will be used.

Be sure to search for madwifi in the package manager, and download/install the following:

madwifi-tools

If this doesnt help you, than you may have to try the ndiswrapper route.. let me know...

He didn't say whether he was using dapper or edgy... I'm not sure that's the kernel version for both of them. And again, "installing them" is more complicated than just using synaptic because he has no working network connection. He would have to download from here [http://packages.ubuntu.com/](http://packages.ubuntu.com/) and then install them.

---

### Post by udstuen on 2007-04-06
Not possible to just use my Ethernet.  I don't have a cable that long to reach.  It's over 100 feet.

I haven't done any of this editing before.  I've done Windows my whole life...so this is COMPLETELY new to me.

Any way to save madwifi or Ndiswrapper to a CD/Flash and copy to Ubuntu PC?

The computer had XP pro on it before...wouldn't my Ethernet have to be configured for Linux too?

---

### Post by r3m0t on 2007-04-07
Well, maybe you can temporarily move the computer? It's a lot simpler than what I will suggest - downloading madwifi and transferring it and installing it.

Do what I said before (the whole "uname -r" part) and then:

On a computer with a network connection, and:

If you have dapper, go to [http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=linux-restricted-modules-2.6&searchon=names&subword=1&version=dapper&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=linux-restricted-modules-2.6&searchon=names&subword=1&version=dapper&release=all)

If you have edgy, go to [http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=linux-restricted-modules-2.6&searchon=names&subword=1&version=edgy&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=linux-restricted-modules-2.6&searchon=names&subword=1&version=edgy&release=all)

Select the versions which matches the kernel name (2.6.bla) with what you have written on your paper.

Now on the new page, scroll to "Download linux-restric...". There should be a table. Click on "i386". Finally, there will be:
> You can download the requested file from the pool/restricted/l/linux-restricted-modules-2.6.17/ subdirectory at:

    * security.ubuntu.com/ubuntu 

Follow the link and save the file.

Then, _copy_ the file (don't move it!) to a flash disk or burn it to a CD.Bring your CD or flash to the Ubuntu computer.

From being logged in, insert the CD/USB stick and browse it. (It should appear on the desktop.) Double-click the file (which is called linux-restricted-modules-2.6.blabla.deb) and choose to install it.

If you have problems, reply here in as much detail as possible.

---

### Post by GSF1200S on 2007-04-07
> **r3m0t said:**
> He didn't say whether he was using dapper or edgy... I'm not sure that's the kernel version for both of them. And again, "installing them" is more complicated than just using synaptic because he has no working network connection. He would have to download from here [http://packages.ubuntu.com/](http://packages.ubuntu.com/) and then install them.

Good point.. I got to caught up in fixing it to use common sense.. lol.

Yeah, so as r3m0t said, what version of Ubuntu do you have? 

r3m0t, if hes dual booting, he might be able to d/l these packages on windows and read them with Ubuntu. He would have to mount his partition, but once accomplished, it might make it easier... Then simply downloading all the packages he might need to his desktop would allow him to hopefully fix his problem. This is, of course, of no worth if hes not dual booting...

---

### Post by udstuen on 2007-04-07
I just found a long enough rj45 to reach downstairs.  That has to only be temorary though...I can't leave a blue cord running through the house every day...haha.

So now what?  Do I have to do anything to make Ubuntu recognize my normal modem (10/100)?

If you can give that to me in plain English I'd appreciate it.  You can PM me as well if that saves time.

---

### Post by r3m0t on 2007-04-07
So you have it connected to a router?


Step one: get an internet connection through your wired connection.

First try rebooting the Ubuntu computer. If Internet works now (open firefox and visit google and one other website), move to step two.

Otherwise, go to System -> Administration -> Network. Tick the first network labelled "wired" or "eth#" (e.g. eth0, eth1). After you tick each one, check again whether you can load Google or one other website. If you can't load it, untick that wired connection and tick the next one. If you can load a website, go to step two.

You will need your router settings (e.g. static IP? DHCP? address of DNS server?) - you are probably using DHCP so for each wired connection, go to properties and make sure anything labelled "DHCP" is ticked or selected. This is probably done by default. (I'm sorry I'm not sure.)

Step two: install madwifi.

Open a terminal (Applications -> Accessories -> Terminal or Applications -> System Tools -> Terminal depending on your version of Ubuntu) and copy and paste this command:

```
sudo apt-get install linux-restricted-modules-`uname -r`
```

If you receive a prompt for your password, enter your normal Ubuntu password.

If it asks for a confirmation, say yes (please! ;-)).

If you get the error "E: Couldn't find package linux-restricted-modules-2.6.bla" then follow the instructions earlier in this thread about "enabling restricted repositories" and start step two again.

If it appears to be successful (just looked at the last few lines of text when it's done) then move on to step three. Otherwise, post the full text from the terminal (don't worry, it won't include your password) into this forum. (This shouldn't be difficult because your internet connection will be working.)

Step three: test madwifi.

Reboot Ubuntu (System -> Quit of course) and go to System -> Administration -> Network. If it has worked, a new entry will have appeared (regarding your wireless card). If you have problems setting it up from there, please ask here.


If you need to post again here and you have passed step two, please go to the terminal and put these commands one-by-one:
```
dmesg > ~/w0dmesg.txt
ifconfig > ~/w1if.txt
iwconfig > ~/w2iw.txt
tar -zc w*.txt > ~/w.tar.gz

```

You will not see (many) messages from these commands. When you post again, attach the file "w.tar.gz" which you should be able to find in your "Home Folder".

---

### Post by udstuen on 2007-04-08
Excellent.

I will do this in the AM...well I guess it is AM now...but you know what I mean.

I'll report back.

---

### Post by bluedalmatian on 2007-04-09
Doesnt that card use a Ralink RT2500 chipset.. I think it might... in which case it will work natively in Ubuntu 6 without having to install anything.

---

### Post by udstuen on 2007-04-13
Here's what I have done so far:

Enabled the repositories as indicated.

Connected with Ethernet

Downloaded all of the Linux restriced modules and restarted the computer

After enabling the ETH1 Wireless...nothing happened.

It does work correctly on Ethernet.

What should I do?

---

### Post by GSF1200S on 2007-04-13
> **udstuen said:**
> Here's what I have done so far:

Enabled the repositories as indicated.

Connected with Ethernet

Downloaded all of the Linux restriced modules and restarted the computer

After enabling the ETH1 Wireless...nothing happened.

It does work correctly on Ethernet.

What should I do?

Eth1 never worked for me. Try enabling Ath1

---

### Post by udstuen on 2007-04-13
ATH isn't even listed.

Whats up?

---

### Post by GSF1200S on 2007-04-13
> **udstuen said:**
> ATH isn't even listed.

Whats up?

Did you reboot after installing that stuff? I know I had to...

Thats weird. I have 3 different "connections." Eth0, Ath0 and WLAN0. I dont know why, but Ath0 is the only way I can get my wireless working..

---

### Post by udstuen on 2007-04-13
I did reboot.

It asked me what I should boot...a long list with numbers and such.

Which should I pick?

---

### Post by GSF1200S on 2007-04-13
[http://madwifi.org/wiki/Compatibility/Belkin]("http://madwifi.org/wiki/Compatibility/Belkin")

This link under madwifi doesnt show the 7001 you listed... Assuming the 7000 they list encompasses the 7000 series, then you have a chance. Notice some versions say they work fine, and others litterally say it would be "futile" to even try... As I said in the beginning, we may need to go the ndiswrapper path. That sucks, because I could never get ndiswrapper to work under my Gigabyte W101GT...

---

### Post by udstuen on 2007-04-15
I now have Fiesty and have installed madwifi-tools.

What do I do from there?

Computer working fine on wired connection...but I need WiFi soon.

---

