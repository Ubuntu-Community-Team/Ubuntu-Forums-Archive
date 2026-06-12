---
title: "Need Auto - etho"
date: 2010-01-17
forum: New to Ubuntu
---

### Post by eopi on 2010-01-17
Karmic Kola

I installed Wicd but now it can't find my IP Address for a basic **_Wired_** internet connection..  

Is there a quick fix; like to uninstall Wicd and get back my _**Auto Etho**_?

Wicd
Wired Network Connection
Then says, obtaining IP Address

Then 

Error: "Connection failed, unable to get IP address"

---

### Post by knxville on 2010-01-18
Well, I had almost the same problem, I also installed WICD, because I had trouble connection to a non broadcasting wep encrypted AP, but I couldn't get it to work, and after that, it wouldnt get a ip address at all, on eth, or wlan, none worked, so I uninstalled, and then I tried:

```
ifconfig eth0 down
```

Which closed my eth0 connection

```
ifconfig eth0 up
```Then it fetched an ip address..


Good Luck!

---

### Post by ja660k on 2010-01-18
if that doesnt work you can force ubuntu to connect
```
sudo dhclient eth0
```

until you fix the problem

---

### Post by warfacegod on 2010-01-18
Removing Network Manager *can* cause odd behaviors in your system.

---

### Post by eopi on 2010-01-24
> **knxville said:**
> Well, I had almost the same problem, I also installed WICD, because I had trouble connection to a non broadcasting wep encrypted AP, but I couldn't get it to work, and after that, it wouldnt get a ip address at all, on eth, or wlan, none worked, so I uninstalled, and then I tried:

```
ifconfig eth0 down
```

Which closed my eth0 connection

```
ifconfig eth0 up
```Then it fetched an ip address..


Good Luck!
Thanks for all the suggestions, everyone. 

I was able to go into Synaptic Package Manager and uninstall Wicd.

I then attempt the ifconfig down; ifconfig up suggestion and it reads **permission denied**.

But I'm in synaptic Package Manager to I've entered in my **Password**. Also, I've rebooted - on the off chance that it needed a reboot

Any other suggestions?

(other than reinstalling Ubuntu OS)

---

### Post by knxville on 2010-01-24
> **eopi said:**
> Thanks for all the suggestions, everyone. 

I was able to go into Synaptic Package Manager and uninstall Wicd.

I then attempt the ifconfig down; ifconfig up suggestion and it reads **permission denied**.

But I'm in synaptic Package Manager to I've entered in my **Password**. Also, I've rebooted - on the off chance that it needed a reboot

Any other suggestions?

(other than reinstalling Ubuntu OS)

If it says permission denied it's because you need to be root..

you just have to write:

```
sudo ifconfig down
```

and then

```
sudo ifconfig up
```

Many commands requires you to be logged in as root!

---

### Post by eopi on 2010-01-24
> **knxville said:**
> If it says permission denied it's because you need to be root..

you just have to write:

```
sudo ifconfig down
```

and then

```
sudo ifconfig up
```

Many commands requires you to be logged in as root!

Ok, I now remember about the Sudo thing.  Also, I think there's a typo "Eth0" needed; but I included that in my command ...

I did it and it entered well meaning it didn't give me an error.  

I entered both commands back to back.  It still doesn't give me internet access as with Auto Eth0.

---

### Post by warfacegod on 2010-01-24
Does Network Manger see the connection? If so, then highlight the connection and click Edit and then check connect automatically.

---

### Post by eopi on 2010-01-24
> **warfacegod said:**
> Does Network Manger see the connection? If so, then highlight the connection and click Edit and then check connect automatically.

I've uninstalled Wicd.

I just now need Auto Etho to magically appear as it did when I first installed Karmic Koala.

---

### Post by warfacegod on 2010-01-24
Right click your N.M. applet and make sure Networking is enabled. Then use:

```
sudo ifconfig
```

and use the eth0 data to manually create a new connection in Network Manager.

---

### Post by eopi on 2010-01-24
> **warfacegod said:**
> Right click your N.M. applet and make sure Networking is enabled. Then use:

```
sudo ifconfig
```

and use the eth0 data to manually create a new connection in Network Manager.
**Is it possible that I no longer have a Network Manager? **

I've uninstalled Wicd.  Also when I go to Applications -> Internet and System -> Administration; I don't see anything called Network Manager. 

I see Network Tools.  

On the top Right hand corner of my desktop I don't see a Network Manager.

---

### Post by gnometorule on 2010-01-24
Go to

Applications->Ubuntu Software Center,

then click 'Installed Software.' Browse for Network Manager, or type into the search field 'net'. Network Manager will show up as installed if you still got it. If not, go to 'Get Free Software' (other tab) next, and download it. I haven't manually downloaded it, but I assume it will re-insert itself as an icon on the top of your screen, probably after you reboot your system.

---

### Post by warfacegod on 2010-01-24
> **eopi said:**
> **Is it possible that I no longer have a Network Manager? **

I've uninstalled Wicd.  Also when I go to Applications -> Internet and System -> Administration; I don't see anything called Network Manager. 

I see Network Tools.  

On the top Right hand corner of my desktop I don't see a Network Manager.

Network Manager is called Network Settings in the Preferences menu. If it's not there then open a Terminal:

```
sudo apt-get install network-manager
```

---

### Post by eopi on 2010-01-24
> **gnometorule said:**
> Go to

Applications->Ubuntu Software Center,

then click 'Installed Software.' Browse for Network Manager, or type into the search field 'net'. Network Manager will show up as installed if you still got it. If not, go to 'Get Free Software' (other tab) next, and download it. I haven't manually downloaded it, but I assume it will re-insert itself as an icon on the top of your screen, probably after you reboot your system.


> **warfacegod said:**
> Network Manager is called Network Settings in the Preferences menu. If it's not there then open a Terminal:

```
sudo apt-get install network-manager
```

I attempted to do all the above.

Don't forget I don't have a wired internet connection (muchless a wireless connection).  It think both of the above option require internet connection.  The attempts failed.  :(

---

### Post by warfacegod on 2010-01-24
Install it from your install disc.

---

### Post by gnometorule on 2010-01-25
No, you don't need to be connected to the internet to check, via the software manager, if you got a package installed. Just to be safe, I confirmed right now: disabled wireless and checked if 'Network Manager' is installed. Works fine.

So i'd check if you still have it; and if not, do as warfacegod suggest: install from CD, if you still got your cd. Shouldn't be too bad to get it back into your system like this.

---

### Post by eopi on 2010-02-04
Ok, from where we last left off. 

I'm trying to install Network Manager back onto Karmic K. 

I have a **thumb drive** and I have the **ISO file** for Karmic K on the thumb drive.  I can explore the file but I can't find Network Manager.  

How would I install Network Manager from a thumb drive from the ISO file?

---

### Post by warfacegod on 2010-02-04
[http://ubuntuforums.org/showthread.php?t=1395641]("http://ubuntuforums.org/showthread.php?t=1395641")

---

### Post by eopi on 2010-02-04
> **warfacegod said:**
> [http://ubuntuforums.org/showthread.php?t=1395641]("http://ubuntuforums.org/showthread.php?t=1395641")
Ok.

I see that in ISO data / Thumb drive / Burned CD that there is a folder Pool/main/d/dpkg and in there you find Dpkg-dev 1.15 4ubuntu2_all.deb

I tried to copy and paste that .deb into /var/cache/apt/archives/

Just as the post said.  That's the only thing I understood in that Thread. 

It doesn't copy and paste, any ideas?

PS, I dont want to have to re-install just to get Auto Etho again.  I have Windows partition that is Blue Screened but I have access to folders and if I re-install I might lose everything.

---

### Post by cenzorrll on 2010-02-05
can you post:
the contents of your /etc/network/interfaces

and the output of:
```
ifconfig
```

---

### Post by eopi on 2010-02-05
> **cenzorrll said:**
> can you post:
the contents of your /etc/network/interfaces

and the output of:
```
ifconfig
```I can't really paste it. 

See I don't have Wired connection on **laptop**, the problem computer, much less Wireless. 

On the laptop, I get the "lo" but not the "Etho" after typing in Ifconfig.  My desktop is how I'm replying to this thread.  

I will be golden if I can just get Network Manager off of the BURNED CD; from the .DEB File. 

How do I do this?

After I get this done, I'm wiring my house with 150 feet of Ethernet Cable and Duck Tape, a Jerry-rigged wire job.  

Remember my simple goal is to get the Karmic K Network Manager back onto my Laptop (I need Auto Etho).  Wicd didnt work for me.

---

### Post by warfacegod on 2010-02-05
Did you read the link I posted? There is an explanation in post #09 on how to use the disc to update.

---

### Post by eopi on 2010-02-10
> **warfacegod said:**
> Did you read the link I posted? There is an explanation in post #09 on how to use the disc to update.

Thanks for the posts and the link, I really do appreciate it. 

You guys make things happen; unfortunately it didn't work for me. 

I sought out response #09 but couldn't make sense of it. 

So I re-install Karmic and I now have AutoEtho.

Time to wire my house for my laptop.  Again Thx.

---

### Post by warfacegod on 2010-02-10
Then mark this as Solved under thread tools I guess.

---

