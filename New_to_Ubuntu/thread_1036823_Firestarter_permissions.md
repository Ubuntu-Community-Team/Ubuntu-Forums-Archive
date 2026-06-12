---
title: "Firestarter permissions"
date: 2009-01-11
forum: New to Ubuntu
---

### Post by SillySod on 2009-01-11
Is there a way of starting Firestarter without being asked for my root password?  It starts automatically after I log in, but I don't really want to have to put my password in for a second time after logging in each time.

---

### Post by mcduck on 2009-01-11
Is there a specific reason why you want the Firestarter GUI to run always?

The Firestarter's graphical interface is just a tool for configuring the firewall, the actual firewall will start on boot and run whether you have the graphical interface open or not..

As the GUI runs with root privileges having it open all the time is not recommended.

Actually, unless you are running some server software on the machine you shouldn't need a firewall at all. Since the default install has no running services that would respond to incoming network connections it makes no difference if you have a firewall or not.

---

### Post by bryncoles on 2009-01-11
it is possible, and i used to have a link explaining how!

... found it! i think this will explain it..

[http://ubuntuforums.org/showthread.php?t=542756](http://ubuntuforums.org/showthread.php?t=542756)

but be advised that you dont actually need to do this, as firestarter is more a way to configure the IP tables, ([https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)) which dictate how your computer interacts with the internet. so, you need to boot firestarter once, use it to set your internet connection rules, and then these rules are in effect regardless of whether you boot firestarter or not. you'll only need firestarter running if you want to change these rules at a later date.

*** edit ***

so +1 to mcduck above - dont run firestarter as root all the time, its not recommended or needed. just use it to set your firewall (or use the built in UFW - [http://ubuntuforums.org/showthread.php?t=823741](http://ubuntuforums.org/showthread.php?t=823741)) and then relax, safe in the knowledge that you're firewalled regradless of whether you boot firestarter or not.

---

### Post by SillySod on 2009-01-14
Thanks for this, I understand it now.  I didn't actually set anything when I first ran Firestarter as I was thinking that this was the firewall itself and was protecting me by running.  The Events and Policy tabs do not have any entries, should I be putting something in there or do I leave this as it is?

---

### Post by alienexplorers on 2009-01-14
Instead of firestarter try running ufw.  to enable it and have it start with each boot type in terminal:
> sudo ufw -enable

---

### Post by cariboo on 2009-01-14
Just to add to your confusion if you are running behind a router, you shouldn't need to set up iptables at all, as you already have a firewall running.

I've had high speed cable for about 6 years, and have felt the need for any other firewall but the routers. Even when I was on dialup I never used a firewall on my linux installation.

Jim

---

### Post by kansasnoob on 2009-01-14
> **alienexplorers said:**
> Instead of firestarter try running ufw.  to enable it and have it start with each boot type in terminal:

+1!

Firestarter has been out of development since 2005!

To run ufw from terminal:

[https://help.ubuntu.com/community/Uncomplicated_Firewall_ufw](https://help.ubuntu.com/community/Uncomplicated_Firewall_ufw)

If you want a gui on 8.10 just install gufw from synaptic or:

```
sudo apt-get install gufw
```

On earlier versions download the .deb:

[http://gufw.tuxfamily.org/index.html](http://gufw.tuxfamily.org/index.html)

Typical Gufw gui:

[ATTACH]99838[/ATTACH]

For a typical installation just "tick" Firewall Enabled!

---

### Post by handydan918 on 2009-01-14
> **kansasnoob said:**
> +1!

Firestarter has been out of development since 2005!



I still don't understand why anyone thinks this matters. Are there unsupported features in iptables now?

---

### Post by bryncoles on 2009-01-16
> **SillySod said:**
> Thanks for this, I understand it now.  I didn't actually set anything when I first ran Firestarter as I was thinking that this was the firewall itself and was protecting me by running.  The Events and Policy tabs do not have any entries, should I be putting something in there or do I leave this as it is?

to answer your question, i would do 

```
sudo ufw default deny
sudo ufw enable
```and leave it at that. this sets your default behaviour to 'deny' incoming connections (as i understand it) and thus, you're protected. read through the link i posted before ([http://ubuntuforums.org/showthread.php?t=823741](http://ubuntuforums.org/showthread.php?t=823741)) for information on how to tweak the rules further. 

and a word of warning on gufw: the gui tool is ace, but i manage to be over zealous using that and cripple my internet completely! if you do that to yourself, try turning gufw off completely and rebooting...

---

