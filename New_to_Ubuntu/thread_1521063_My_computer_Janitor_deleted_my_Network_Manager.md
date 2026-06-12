---
title: "My computer Janitor deleted my Network Manager"
date: 2010-06-30
forum: New to Ubuntu
---

### Post by John Phang on 2010-06-30
what should i do now to install back my computer network manager?

---

### Post by Rubi1200 on 2010-06-30
From the terminal:

```
sudo apt-get install network-manager-gnome
```

And please read this:

[http://sites.google.com/site/easylinuxtipsproject/fatalmistakes](http://sites.google.com/site/easylinuxtipsproject/fatalmistakes)

---

### Post by John Phang on 2010-06-30
I've just tried what you said but when i click on my network manager it says 'network manager is not running'. what should i do now to make it run?

---

### Post by QIII on 2010-06-30
There is an adage in the Military that deals with how to go about making "command decisions" in the absence of guidance from superiors.

"It’s easier to ask forgiveness than it is to get permission."  Strangely, the quote is attributed to Rear Admiral Grace Murray Hopper, who also is the one attributed with coining the term "bug" as it relates to computers.  (The moth in the circuitry of an ancient computer.)

Anyway.

That's not a good way to approach Linux as a relative newcomer.  Before you do anything -- and I mean anything -- it is best to ask a question in an open venue, such as this forum, what people think.  There is great wisdom in the collective experience of the many users, young and old, who fritter away their youth (or collect more gray hairs) here.

In short:  Ask before you do things you are unfamiliar with.

---

### Post by John Phang on 2010-06-30
ok, maybe i know what you want to tell me. anyways i will try, but is there anyway to fix my problem?

---

### Post by Rubi1200 on 2010-06-30
Have you tried logging out and then back in again?

---

### Post by QIII on 2010-06-30
The short answer is "I'm pretty sure there is."

I thought the previous suggestion would work immediately.  I'm surprised it didn't.

Did you try shutting down and restarting?

Give that a try.  If that doesn't work, we'll try to find something else.

If I have some time today (I got to work early and was goofing off a bit), I'll do a little research.

---

### Post by John Phang on 2010-06-30
only i tried log in and log out,i tried too restart too. but the network manager says the same 'network manager is not running' what should i do now?

---

### Post by Rubi1200 on 2010-06-30
You could try this:

```
sudo /etc/init.d/network-manager-gnome start
```

If that doesn't work try taking the gnome part off the command and just use network-manager

---

### Post by John Phang on 2010-06-30
when i type in the code it says:
sudo: /etc/init.d/network-manager-gnome: command not found
 what should i do next?

---

### Post by Rubi1200 on 2010-06-30
> **John Phang said:**
> when i type in the code it says:
sudo: /etc/init.d/network-manager-gnome: command not found
 what should i do next?

Did you copy and paste from my post?

What you have:

```
sudo: /etc/init.d/network-manager-gnome
```

is different from this:

```
sudo /etc/init.d/network-manager-gnome start
```

As I said you can also try:

```
sudo /etc/init.d/network-manager start
```

---

### Post by vegetarianshrimp on 2010-06-30
If the actual package was deleted, and you can't install it because you can't connect to the internet (because you don't have network manager), you can [download the deb]("http://packages.ubuntu.com/lucid/i386/network-manager-gnome/download") from a different computer, put it on a USB drive, and install on the computer with the problem. Sorry if this is completely off :D.

---

### Post by John Phang on 2010-07-01
Rubi1200: when i try the 2 codes you gave me it appear something like this: Attachment (image screenshots 2)

vegetarianshrimp: i also tried the way you thought me but when i install it appear something like this: attachment (screenshot)
 
PS: after a few restart my network manager icon on my notification are gone and completely removed from my computer. 
what should i do to connect to the internet to fix this problem using fixed line?

---

### Post by Rubi1200 on 2010-07-01
If network manager was installed correctly the first time, the way I suggested, then there is no need to use a .deb package.

Try what the terminal suggested:

```
service network-manager start
```

---

### Post by John Phang on 2010-07-01
i've just tried 'service network-manager' start and it comes out like this:

---

### Post by Rubi1200 on 2010-07-01
> **John Phang said:**
> i've just tried 'service network-manager' start and it comes out like this:

Sorry to say this, but I am running out of ideas :-(

Are you prepared to do a re-install? I don't know that I can think of anything else right now.

Alternatively, remove network manager from Synaptic and start the process again, but this time no .deb packages please. Use what is there in the repositories.

---

### Post by John Phang on 2010-07-01
but, do you know how to use terminal to connect to the internet using wired line?

---

### Post by Rubi1200 on 2010-07-01
> **John Phang said:**
> but, do you know how to use terminal to connect to the internet using wired line?

I am sorry I don't know. But if you plug the cable in and start the web browser are you not automatically connected?

Also look here; it may help

[https://help.ubuntu.com/7.04/internet/C/connect-to-internet.html](https://help.ubuntu.com/7.04/internet/C/connect-to-internet.html)

---

### Post by John Phang on 2010-07-01
I'm so sorry for wasting your time, anyway i know it is no use to  try anything now. I only want to tell you is THANK YOU so much for helping me out.. 
cheers,
John :)

---

### Post by Rubi1200 on 2010-07-01
> **John Phang said:**
> I'm so sorry for wasting your time, anyway i know it is no use to  try anything now. I only want to tell you is THANK YOU so much for helping me out.. 
cheers,
John :)

First of all, you did not waste my time. It is my heartfelt desire to try and help. I am sorry that I was not able to help you resolve these issues.

As I said before, you could still try a fresh install unless that would be too complicated or mean losing valuable data (though you should always be backing things up anyway).

Don't give up hope! Someone may come along and offer a solution.

Good luck!

---

### Post by k3lt01 on 2010-07-01
> **Rubi1200 said:**
> Don't give up hope! Someone may come along and offer a solution.My only suggestion is do a re-install of / leaving /home untouched. I have never seen anyone successfully recover a working Network Manager after deleting it.

It is always advisable to know what is what before you allow applications like Computer Janitor delete anything.

---

### Post by John Phang on 2010-07-01
Thanks for your support :)

---

### Post by Rubi1200 on 2010-07-01
Just out of curiosity what does 

```
/etc/networks/interfaces
```

show?

---

### Post by dineshs on 2010-07-01
can you post the output of
```
cat /etc/network/interfaces
```and
```
cat /etc/NetworkManager/nm-system-settings.conf
```

---

### Post by John Phang on 2010-07-02
this is the screen shots after i type the codes you guys gave me:

---

### Post by k3lt01 on 2010-07-02
put sudo in front of the code

---

### Post by John Phang on 2010-07-02
Here is it:

---

### Post by kimikrishna on 2010-07-02
Friend, 
My little tip : Do Not use Janitor for cleaning.
Use "Ubuntu tweak" for the same purpose (But it is not limited to it alone)

---

### Post by John Phang on 2010-07-02
ok i'll try to use the ubuntu tweak next time. and i'm so sorry i'm new on ubuntu and i dont know which program are stable and which aren't.

---

### Post by k3lt01 on 2010-07-02
> **John Phang said:**
> Here is it:Sorry my mistake

Try this:
```
gksudo gedit /etc/networks/interfaces
```

If you are opening a file that is text based you should always use gksudo gedit. This is because you are trying to open it in a graphic interface.

---

### Post by k3lt01 on 2010-07-02
> **kimikrishna said:**
> Friend, 
My little tip : Do Not use Janitor for cleaning.
Use "Ubuntu tweak" for the same purpose (But it is not limited to it alone)I disagree, you should always try to learn and use the native tools before you move onto "add-ons". Computer Janitor is installed as standard so it has the support of Canonical, Ubuntu's parent company. Ubuntu Tweak, while it is a great tool, does not and simply duplicates many things already available.

---

### Post by Rubi1200 on 2010-07-02
> **k3lt01 said:**
> I disagree, you should always try to learn and use the native tools before you move onto "add-ons". Computer Janitor is installed as standard so it has the support of Canonical, Ubuntu's parent company. Ubuntu Tweak, while it is a great tool, does not and simply duplicates many things already available.

+1 to this advice.

I would only add the following as a gentle reminder:

[http://sites.google.com/site/easylinuxtipsproject/fatalmistakes](http://sites.google.com/site/easylinuxtipsproject/fatalmistakes)

Read especially what it says about using tools like Ubuntu Tweak and Computer Janitor; these tools can potentially destroy your setup and for what? The few MB of extra disk space you *might* gain! Is it really worth it?

---

### Post by swagerr on 2010-07-02
When we right click a window on the task manager we get a context panel on it have the options. I find the bit odd to have an option to the minimize there we can just left click it to do it.

---

### Post by corncob on 2010-07-02
I used Computer Janitor once and it deleted a program (Caffeine) while I was using it.  I saw it in the list but thought it was only referring to the deb file which had already been installed.  I downloaded  ( [http://www.omgubuntu.co.uk/2009/08/caffeine-delay-screensaversuspend.html](http://www.omgubuntu.co.uk/2009/08/caffeine-delay-screensaversuspend.html) ) it again and reinstalled it without problems but I'm reluctant to use Computer Janitor again -- maybe I will if my hard drive gets full.

---

### Post by freelancer1995 on 2010-07-02
i have suggestion for restoring the network interface, not as pretty as the gnome-network-manager, but it may bring the interface up to allow internet access.

source: [http://www.cyberciti.biz/faq/setting-up-an-network-interfaces-file/]("http://www.cyberciti.biz/faq/setting-up-an-network-interfaces-file/")

the section, i refer to is the "setup a dhcp interface" by adding the lines after the lo in your interfaces file, then doing an;

```
sudo ifconfig eth0 down
```

and then a

```
sudo ifconfig eth0 up
```

the commands, turn the interface(network) off and on again and hopefully restores your access to your network :-)

---

### Post by dineshs on 2010-07-02
please try this 
```
gksudo gedit /etc/NetworkManager/nm-system-settings.conf 
``` 
and change```
managed=true
``` 
Restart
If this is not working try post #2 suggested by chili555 in
[http://ubuntuforums.org/showthread.php?p=8975701#post8975701](http://ubuntuforums.org/showthread.php?p=8975701#post8975701)
(I am not an expert so wait for other suggestions and if nothing works you can try this)

---

### Post by John Phang on 2010-07-02
when i type the code (k3it01) you gave me it comes out something like this (screenshot).

freelancer1995, when i type in the code you gave me it comes out like this (screenshot-1)

dinesh, when i type in the code you gave me it comes out like this (screenshot-2) i've save and restart my computer, it also cant connect to the internet or recover the Network Manager.

what should i do now?

---

### Post by k3lt01 on 2010-07-02
John I just tried it and it did the same thing. I then went into Nautilus and opened the file and it is like this screenshot. I can't explain why it wouldn't open with gksudo gedit.

You could try this code.
```
gksudo nautilus
```

It will open Nautilus with admin rights but be careful what you then do as you can cause damage to your system if your not careful. Once Nautilus is open you can go to /etc/network/interfaces and open the file to see what it looks like.

---

### Post by John Phang on 2010-07-02
i've done what you said, it just appear something like this (screenshot), then what should i do next?

---

### Post by k3lt01 on 2010-07-02
Post the contents of the file for people like Rubi1200 and dineshs so they can respond because they asked to see what it contained.

---

### Post by John Phang on 2010-07-02
can you tell me more detail? i can't get what you said. and i'm so sorry because i'm not very good in English...

---

### Post by k3lt01 on 2010-07-02
Post the information in the /etc/network/interfaces file so other people who know more than I do can help you.

---

### Post by John Phang on 2010-07-03
ok. here is it the file you told me to post.

---

### Post by dineshs on 2010-07-03
/etc/network/interfaces look OK.
By the way after making *managed=true*,did you save the file before restarting (you should)

---

### Post by kimikrishna on 2010-07-04
> **k3lt01 said:**
> I disagree, you should always try to learn and use the native tools before you move onto "add-ons". Computer Janitor is installed as standard so it has the support of Canonical, Ubuntu's parent company. Ubuntu Tweak, while it is a great tool, does not and simply duplicates many things already available.


But ubuntu Tweak Does not K-I-L-L My ubuntu like Janitor did .

You can also google around for many damages caused by this computer janitor.

---

### Post by k3lt01 on 2010-07-04
@John Phang. 3 days ago I suggested you just do a reinstall. I sincerely hope your still not battling trying to get Network Manager up and running again.

@kimikrishna
> **kimikrishna said:**
> But ubuntu Tweak Does not K-I-L-L My ubuntu like Janitor did .With all due respect, Computer Janitor has never killed my Ubuntu and that is because I know how to deal with it. Likewise I know how to deal with UbuntuTweak. I would never advise someone who is obviously having difficulty with basic Ubuntu tools that are supported by the parent company to go and use something that is more complex and not supported by the parent company. Have you heard the phrase "horses for courses"?

> **kimikrishna said:**
> You can also google around for many damages caused by this computer janitor.Again with all due respect. You can for UbuntuTweak as well. Note our friend Rubi1200 has linked to a very wise page no less than twice in this thread. I would advise the OP and yourself to read it.

This is not a competition on what tool can bork your system the quickest, nor is it a competition on who is able to use what tool. Instead of arguing with me using C-A-P-I-T-A-L letters explain to the OP how UbuntuTweak is better than Computer Janitor. While you are at it you should probably also write a thread on how to use each and every aspect of UbuntuTweak so he doesn't break alot more. Being helpful is very admirable, telling him a multifaceted and complex tool is better without showing him how to use it is a recipe for disaster.

---

### Post by kimikrishna on 2010-07-04
k3lt01, Ok. I have understood Your post. Thanks for spending so much of your time typing me a post. 


Network Manager should be added to the whitelist of janitor :( and other important ....

---

### Post by John Phang on 2010-07-05
Dinesh: i've save and restart my computer and it doesn't has any effect.
I don't know what to do now.Should i just format my computer?

---

### Post by k3lt01 on 2010-07-05
> **John Phang said:**
> I don't know what to do now.Should i just format my computer?Yes, just save your important files and do a clean re-install of Ubuntu.

---

### Post by John Phang on 2010-07-05
actually how to re-install? do you mean format it?

---

### Post by k3lt01 on 2010-07-05
You will have to format / at least, if you have your personal files safely backed up you can also format /home as well.

There are some other tricks you can do if you don't want to format /home but you will need to be very confident in your ability. Being respectfully blunt, I can help you do it other ways BUT if you choose to go any way apart from what I wrote in the above paragraph you will need to ask all your questions before you start because there is NO turning back once you start deleting files.

---

### Post by dineshs on 2010-07-05
> **John Phang said:**
> Dinesh: i've save and restart my computer and it doesn't has any effect.
I don't know what to do now.Should i just format my computer?

If you have no other alternative try this as I suggested earlier
[http://ubuntuforums.org/showthread.php?p=8975701#post8975701](http://ubuntuforums.org/showthread.php?p=8975701#post8975701)
(you should substitute your IP values and nameserver you can try 4.2.2.1)

---

### Post by John Phang on 2010-07-08
I've try the link you gave me and here is the screenshot, what should i do next?
if i didn't success can you (k3lt01) please tell me how can i reinstall ubuntu 9.10 with 10.04?

---

### Post by k3lt01 on 2010-07-08
John before we try re-installing Ubuntu could you go into Synaptic and Mark for Reinstallation network-manager, network-manager-gnome, network-manager-pptp, network-manager-pptp-gnome. Click apply up the top of Synaptic and let it reinstall those 4 packages and any others it says it must install with them.

After this has been done reboot and let us know what is happening.

If that doesn't fix your problem get your CD and put it in your drive. Open Synaptic again and go to Edit > Add CD-ROM. Now go down to the Origin button in Synaptic and click on it, up the top will show various places and the CD will be one of them. Select the four packages I mentioned in the first paragraph and click apply. After they install reboot, see what happens and let us know if it works.

If that doesn't work you will have to reinstall Ubuntu. Do you have 10.04 on a disk?

---

### Post by tarps87 on 2010-07-08
Assuming you have the wire connected and you do not need to use a fixed ip and you haven't already reinstalled, copy the three attached files to your desktop.  Now open a terminal and type the following
```
sudo sh ~/Desktop/clean.sh
```
It will reboot, log back on an run the following commands
```
sudo sh ~/Desktop/setup.sh
```

I have tested this by removing the network manager myself.
The first file will remove the network manager and set the networking, the second will reinstall and configure the network manager

---

### Post by k3lt01 on 2010-07-08
tarps, I hope that works because if it does I'll bookmark that post and put it in other threads that I come across with such problems.

---

### Post by dineshs on 2010-07-08
> **John Phang said:**
> I've try the link you gave me and here is the screenshot, what should i do next?

You have to edit /etc/network/interfaces as follows
```
gksudo gedit /etc/network/interfaces
```
copy and paste the following (the file should contain only this)
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

``` save the file and close
Now edit /etc/resolv.conf as follows
```
gksudo gedit /etc/resolv.conf
```
copy and paste the following (the file should contain only this)
```
nameserver 4.2.2.1
``` save the file and close
now run
```
sudo /etc/init.d/networking restart
```and see what happens
If you still have problems please run
```
sudo dhclient eth0
```and post the output of```
ifconfig -a
```
[COLOR="Blue"]Anyway try what is suggested by tarps87 first[/COLOR]

---

### Post by John Phang on 2010-07-09
traps87:-
I've tried what you said and it doesn't has the effect on my laptop. It only restart my computer. PS: i forgotten to tell you that my ubuntu can't restart properly.

Dinesh:-
I've tried what you told me. and it also doesn't had any effects. and here are the screen shot.

Do you guys think that it has no solution for this type of situation?

---

### Post by dineshs on 2010-07-09
pl try these commands
```
ifconfig eth0 up
```
```
ifconfig eth1 up
```
```
sudo dhclient
```
and try ```
ifconfig -a
```

---

### Post by tarps87 on 2010-07-09
I have a feeling there is a deeper issue then, before it reset did you set it downloading packages?
How many network ports do you actually have?
Can you connect to the internet (despite not having the network manager)?

---

### Post by Rubi1200 on 2010-07-09
John,
some of us have been following this thread now for some time. We all hoped that you would be able to resolve these issues.

But honestly, I think it is time to backup your data and go for a fresh install.

New start = no problems (hopefully, at least not what you have been experiencing)

We would be happy to help walk you through the process of re-installing your system.

---

### Post by k3lt01 on 2010-07-09
I agree with Rubi1200, it is time to stop trying to fix it. You have now had this issue for at least 7 days.

Use the latest version of LiveCD that you have and lets do a clean re-installation AFTER you have backed up the things you need to back up.

---

### Post by John Phang on 2010-07-09
Yes, you guys are right. i should do a new installation of ubuntu.
But i've still have question to ask, why when i install the latest version of ubuntu, the screen size doesn't fit the screen?

And if you guy can, can you guys add me on Y messenger? so that i can ask you guys question easily. 

Anyway, I so appreciate that you guys help me out, thanks you guys very very much.:KS
And i'm so sorry for wasting the time you have.

And PS: should i use kubuntu instead of ubuntu?

---

### Post by mhgsys on 2010-07-10
Wait WHAT!, Reinstalling because of this>>? The way I see it; 
(I'll must be missing a part but hey , ,It's six in the morning here and I did not sleep)

All that should be necessary is downloading gnome-network-manager again.

We need some internet for that.;
So.. put it on a networkcable; open up a terminal and type;

```
sudo dhclient
```
(This will allow you to obtain a ip adres automatically)

 after the sudo dhclient (eth0) got the offered ip adres.
do a

```
sudo apt-get install network-manager-gnome
```

reboot.

And all should be working back to normal.

---

### Post by John Phang on 2010-07-10
I've tried what you said. and the screen shot is here. I think it really doesn't had any solution for it.

---

### Post by mhgsys on 2010-07-10
Problem seems to be deeper then just the gnome-network-manager.

Reinstalling probably would be the most easy way I guess,

It was really worth a try though,,

---

### Post by John Phang on 2010-07-10
Yeah, anyway thank you so much for helping me out. :) 
And do you know why when i install ubuntu 10.04 the screen size doesn't fit my screen?
is there anyway to make the screen size compatible with my laptop screen?

---

### Post by k3lt01 on 2010-07-10
> **John Phang said:**
> Yes, you guys are right. i should do a new installation of ubuntu.
But i've still have question to ask, why when i install the latest version of ubuntu, the screen size doesn't fit the screen?

And if you guy can, can you guys add me on Y messenger? so that i can ask you guys question easily. 

Anyway, I so appreciate that you guys help me out, thanks you guys very very much.:KS
And i'm so sorry for wasting the time you have.

And PS: should i use kubuntu instead of ubuntu?John, you didn't waste anyones time. We are here to help as volunteers so it's all ok.

Instead of adding us to messenger you are better off asking the questions on the forum. Start a new thread and ask your questions about installation in that. That way many people can help and many can also learn from your experiences.

My personal preference is Ubuntu, I'm not a fan of KDE but many people are.

---

### Post by John Phang on 2010-07-10
Oh i see. thanks you guys very much.:)
And i'm backing up my computer now, after this i'm going to reinstall ubuntu but do you think should i install ubuntu 9.10 rather than 10.04?

---

### Post by k3lt01 on 2010-07-10
If you have a 10.04 LiveCD try it without installing it so you can see if things work as thy should. If it is fine then install 10.04 as it is an LTS (Long Term Support=3 years) while 9.10 is just an ordinary support version (18 months).

---

### Post by John Phang on 2010-07-10
oh ok, thanks. :)

---

### Post by Rubi1200 on 2010-07-10
Hi John,

I just want to give you the following links which will hopefully help you with a successful fresh install:

[http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html) (if you are dual-booting)

[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall) (shows you the various installation options)

Good luck and let us know what happens.

:)

---

### Post by John Phang on 2010-07-10
Rubi1200 now i've downloaded ubuntu 10.04 (again) and when i started the live cd the screen size does not fit the screen i have. what should i do to make it to become full size/fit the screen i have?

---

### Post by Rubi1200 on 2010-07-10
What is your screen size?

Do you have a desktop PC, a laptop, or a netbook?

What graphics card do you have?

Thanks.

---

### Post by kiang on 2010-10-19
I met the same issue. I guess that's because 'My computer Janitor' deleted some packages that needed by NetworkManager. But I couldn't remember what packages were deleted by it...

I currently could only use manual settings with static IP to have internet access. I would try to upgrade from 10.04 to 10.10 to see if it help. God bless me...

---

### Post by kiang on 2010-10-19
Great news. Upgrading from 10.04 to 10.10 fixed the problem. ;)

---

