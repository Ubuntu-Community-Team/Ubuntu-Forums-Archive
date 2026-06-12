---
title: "wifi problem"
date: 2010-08-01
forum: New to Ubuntu
---

### Post by abibcn on 2010-08-01
hello

sorry, i'm new to ubuntu and i'm trying to help my dad solve a long running problem with his eee pc 1000.  The wifi just doesn't seem to work. when i open the network connections there is a list of old wifi networks but none that are currently available.  is this normal for ubuntu 10.4 or should there be a list of available networks?  any ideas or help would be greatly appreciated!  I should also mention that the wifi worked before the upgrade to 10.4.

thanks

abi

---

### Post by jtarin on 2010-08-01
> **abibcn said:**
> hello

sorry, i'm new to ubuntu and i'm trying to help my dad solve a long running problem with his eee pc 1000.  The wifi just doesn't seem to work. when i open the network connections there is a list of old wifi networks but none that are currently available.  is this normal for ubuntu 10.4 or should there be a list of available networks?  any ideas or help would be greatly appreciated!  I should also mention that the wifi worked before the upgrade to 10.4.

thanks

abi

First check your version of Network Manager. It should be at least 0.7. If not upgrade then follow [these instructions]("https://help.ubuntu.com/community/NetworkManager0.7"). Please read carefully.

---

### Post by Samana on 2010-08-01
Let me know if the last suggestion worked. I am assuming it will not. I haev an EEEPC 1001p and have a fix I used for mine which is rather simple.

---

### Post by jtarin on 2010-08-01
> **Samana said:**
> Let me know if the last suggestion worked. I am assuming it will not. I haev an EEEPC 1001p and have a fix I used for mine which is rather simple.
You should post the fix if you have one that works.

---

### Post by Samana on 2010-08-02
> **jtarin said:**
> You should post the fix if you have one that works.

Well, I tend not to bring out the big guns if a minor fix works. But here you are:

[http://www.ramoonus.nl/2010/02/linux-kernel-2-6-33-installation-guide-for-ubuntu-linux/](http://www.ramoonus.nl/2010/02/linux-kernel-2-6-33-installation-guide-for-ubuntu-linux/)

but instead of the kernel they suggest, I use:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-lucid/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-lucid/)

or you can try

[http://linuxon1001p.blogspot.com/2010/06/fixing-wireless-updated.html](http://linuxon1001p.blogspot.com/2010/06/fixing-wireless-updated.html)

I use the first method on my 1001p running Ubuntu 64 Bit and I have no problems.

---

### Post by abibcn on 2010-08-02
thanks for all your replies, i'll try them today and get back to you!

---

### Post by abibcn on 2010-08-02
> **jtarin said:**
> First check your version of Network Manager. It should be at least 0.7. If not upgrade then follow [these instructions]("https://help.ubuntu.com/community/NetworkManager0.7"). Please read carefully.



I tried jtarin's suggestion of checking the network manager and it appears that for some reason there isn't one.  Perhaps I am asking the wrong question about the wifi.....?  

There is no nm-aplet in the top bar that has the wifi symbol. I have read about similar problems in other forums but with these the nm-aplet appears and reappears.  Do I need to reinstall the network manager and if so which packages do I need.  I have tried reinstalling the obvious ones but nothing obvious has happened.  I'm sorry to be so thick but I'm a mac user!  

I'm working on trying the other suggestion about the kernle, but to be honest, as a mac user, it's probably a bit over my head!  

Any other ideas greatly appreciated

Thanks

---

### Post by evstevemd on 2010-08-02
> **abibcn said:**
> I tried jtarin's suggestion of checking the network manager and it appears that for some reason there isn't one.  Perhaps I am asking the wrong question about the wifi.....?  

There is no nm-aplet in the top bar that has the wifi symbol. I have read about similar problems in other forums but with these the nm-aplet appears and reappears.  Do I need to reinstall the network manager and if so which packages do I need.  I have tried reinstalling the obvious ones but nothing obvious has happened.  I'm sorry to be so thick but I'm a mac user!  

I'm working on trying the other suggestion about the kernle, but to be honest, as a mac user, it's probably a bit over my head!  

Any other ideas greatly appreciated

Thanks
System>Preference>**Network Connections**

---

### Post by abibcn on 2010-08-02
> **evstevemd said:**
> System>Preference>**Network Connections**


and then what?  as I mentioned earlier there are no available networks for me to connect to,  only some old ones. Also, the problem is with the ubuntu system not a mac.

The problems are that:
1.  There is no nm-aplet in the top bar
2.  I can't find a list of available wifi networks to connect to 
3.  I'm not very experienced with ubuntu 
4.  This has been going on for some time and I've tried all the basic things that I know of
5.  There is a strong possibility that something has been deleted by accident but I don't know what or how to find out what.

The wired network works fine by the way.  The only information I have found on the ubuntu documents all states that the network manager is installed by default, but I have a feeling it has not been in this case.  

Does anyone know how I can check using the terminal?

Thanks

---

### Post by skyjacker on 2010-08-02
Try this..... connect to an ethernet cable and run the following command```
hardwire drivers
```. This should locate one or two wireless drivers for your system, ie. "broadcom STA". Pick one and choose install. Restart and you should see a wireless icon on the top bar.

---

### Post by evstevemd on 2010-08-02
> **skyjacker said:**
> Try this..... connect to an ethernet cable and run the following command```
hardwire drivers
```. This should locate one or two wireless drivers for your system, ie. "broadcom STA". Pick one and choose install. Restart and you should see a wireless icon on the top bar.
And In some computers you have to switch on the physical switch. It is small switch with antenna signals

try these links

[http://www.linux.com/news/enterprise/networking/8259-making-wireless-work-in-ubuntu](http://www.linux.com/news/enterprise/networking/8259-making-wireless-work-in-ubuntu)
[https://help.ubuntu.com/community/WifiDocs/WiFiHowTo](https://help.ubuntu.com/community/WifiDocs/WiFiHowTo)
[http://beginlinux.com/twitter/1096-ubuntu-wireless-setup](http://beginlinux.com/twitter/1096-ubuntu-wireless-setup)
[https://help.ubuntu.com/10.04/internet/C/connecting-wireless.html](https://help.ubuntu.com/10.04/internet/C/connecting-wireless.html)

---

### Post by Samana on 2010-08-02
**abibcn**, forgive these people. They tend to throw out ideas without trying to understand the problem first. They suckered me into it as well and that led me to give you information overload. jtarin remarked "if I know a fix", well, I did not know a fix because I did not know the problem. I should have stayed silent. Apologies.

I used to be all Mac as well so I know where you are coming from. Ubuntu as an operating system makes much less human sense.

So, back to the issue. When your father "upgraded", what did he do? Did he upgrade from ubuntu 9.04 to ubuntu 10.04, and if he did, did he (1) do a clean install (back up his data, reformat the drive, etc) or did he (2) upgrade the old system already on his computer? I ask this because if he did (2) the easiest option out of your mess is to do a clean install of 10.04. The in-use system upgrades are usually a clusterfrak on the eeepc's.

But, also, I would like to see the output of two terminal commands. Open Applications>Accesories>Terminal and type in

ifconfig

and then

iwconfig

and paste them in your reply.

---

### Post by abibcn on 2010-08-03
Hello everyone

Thank you all for your replies

I have solved the problem! I will explain what I did in case it helps anyone else.

There appeared to be no network manager on the computer so I tried to install it using the synaptic package manager but that didn't work.  I then tried to install WICD using the synaptic package manager and just searching.  I selected all 6 options that came up (a total of 8 packages) just to be on the safe side!  Installed this and restarted. At first nothing, but then I typed wlan0 into Network Interfaces, Wireless Interfaces and that seemed to solve the problem.  WICD found all the wifi networks available so I selected mine.  However, when I tried to connect it didn't have tthe option for a  wpa personal password.  At that point I noticed that the old network manager applet had started working again and gave me the option to connect to the network I wanted using the wpa personal password.  So here we are!

I have no idea exactly what happened originally but I imagine that something was deleted by accident and the new WICD somehow bridged a gap....... 

If someone could develop a child (or parent) safety lock for ubuntu to stop these  sorts of things happening, I (and my boyfriend) would be very very happy.

The link to  WICD is here, [http://ubuntuforums.org/showthread.php?t=527488](http://ubuntuforums.org/showthread.php?t=527488)  but you don't need to use the terminal window, all can be done through the synaptic package manager (which is very nice if you are new to ubuntu)!

Thanks for all the suggestions.

---

### Post by Samana on 2010-08-03
Well good. But WICD did not really fix your problem. (And I hope all the junk you added did not create some more.)

You wireless interface was down (not powered off).

It could have been fixed with **ifconfig** **wlan0** [B]up.

[/B][COLOR=#2D4038]That is why network manager came back. WICD set your interfaces to "up".[/COLOR][COLOR=#2D4038][/COLOR]

---

