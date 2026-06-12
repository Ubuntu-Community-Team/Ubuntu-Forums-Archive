---
title: "no internet with static IP in intrepid"
date: 2008-10-30
forum: Networking &amp; Wireless
---

### Post by p-stone on 2008-10-30
Hi all

I've installed intrepid and find myself unable to surf the internet with a static IP. When in DHCP mode I pick up an IP and surf just fine, however it's frustrating when my DHCP lease expires and all the other machines on my network lose my nfs share. In hardy and previous releases I simply gave myself a static IP and everything worked fine. Now however I can only access my internal network. I can ping all internal machines, as well as my router, however I cannot reach any external websites. If I try and ping yahoo.com for example I get an unknown host error. If I ping yahoo's IP I get "connect: Network is unreachable" For my static settings I initially left the DNS entry blank, however I've also tried setting the IPs used by opendns, to no effect. Has anyone experienced something similar?

Thanks

---

### Post by p-stone on 2008-10-30
Update, I think it's got to do with how I'm going about configuring the settings, I'm getting some really weird behavior from the network manager. When I created the connection I gave it an IP of 192.168.1.103, subnet 255.255.255.0, GW 192.168.1.1 and opendns 208.67.222.222, 208.67.220.220
however, when I went back to try and edit them again, my IP and DNS were the same but my subnet had changed to 24 and my gateway was 0.0.0.0. I also had an old configuration that I'd deleted come back. I wasn't prompted for my admin password at any point when I was making these changes, which I found odd. Again, with static I can operate on my internal network but no internet, DHCP all is well.

Thanks again

---

### Post by wilberfan on 2008-10-30
I think I'm having a similar problem?   I'm unable to assign a static address.   I enter the via the network manager applet--but it gets reset at the next boot.

---

### Post by emco83 on 2008-10-31
same problem here with the netmask.does anyone found a fix for this?

---

### Post by jokker on 2008-10-31
Similar problem here... Need some kind of patch !

---

### Post by pico on 2008-10-31
I have same problem with 8.10 just after upgrade.
Still have not found solution....
any idea ?

---

### Post by pico on 2008-10-31
I have same problem with 8.10 just after upgrade.
Still have not found solution....
any idea ?

---

### Post by mikesmithv on 2008-10-31
I am having exactly the same problem in Gnome Ubuntu 8.10.  The subnet mask changes to "24" when I entered "255.255.255.0" and then the static address does not save.  After reboot it goes back to dhcp.  So this bug is not just in kubuntu.

---

### Post by vitorgatti on 2008-10-31
Same problem here.
[http://ubuntuforums.org/showthread.php?t=965762](http://ubuntuforums.org/showthread.php?t=965762)

:(

---

### Post by jynyl on 2008-10-31
Looks like this can be done with manual editing
[http://ubuntuforums.org/showthread.php?t=965416]("http://ubuntuforums.org/showthread.php?t=965416")

Edit /etc/network/interfaces like this (adjust to your addresses)
```

auto lo eth0
iface lo inet loopback

iface eth0 inet static
  address 192.168.22.55
  netmask 255.255.255.0
  gateway 192.168.22.1
```
Then restart networking ...

```
/etc/init.d/networking restart
```

Also see man interfaces.

---

### Post by wilberfan on 2008-11-01
[QUOTE=jynyl;6077550]Looks like this can be done with manual editing
[http://ubuntuforums.org/showthread.php?t=965416]("http://ubuntuforums.org/showthread.php?t=965416")

Edit /etc/network/interfaces like this (adjust to your addresses)
```

auto lo eth0
iface lo inet loopback

iface eth0 inet static
  address 192.168.22.55
  netmask 255.255.255.0
  gateway 192.168.22.1
```
Then restart networking ...

```
/etc/init.d/networking restart
```

Anyone get this to work?  I tried it, but my netmask still says "24", and I have no internet connection.

---

### Post by waffen on 2008-11-01
Not for me... I change it and when restart the Ubuntu I have not internet connection](*,) and the network manager applet dont appears...any idea?

---

### Post by mikesmithv on 2008-11-01
According to this post about a similar problem he implies you have to disable the Network Manager first:

[http://ubuntuforums.org/showpost.php?p=6075466&postcount=25]("http://ubuntuforums.org/showpost.php?p=6075466&postcount=25")

```
$ sudo update-rc.d -f NetworkManager remove
```

I'm fighting other battles right now so I have not tried that.

---

### Post by ffchaves on 2008-11-01
Same here.

Manual configuration of the static IP gets me connected to my internal network just fine.

As for the internet, no deal.

Now I checked /etc/resolv.conf for the dns servers, it could be the issue, but they´re fine.

Question: what would happen to the DHCP roaming stuff I have setup if I uninstall NetworkManager?

---

### Post by waffen on 2008-11-01
The workaround is disable the NetworkManager and setup by hand the params in /etc/network/interfaces and the DNS, in my internet search I can see is a possible bad function in the NetworkManager present in the Ubuntu 8.10 Betas and not solved yet...

---

### Post by ffchaves on 2008-11-01
I took another direction...

Not very happy with this workaround but there it goes:

I had both eth0 (wired) and ath0 (wireless) setup as static ip. As I'm only using the wireless for now, I just went to /etc/network/interfaces and set eth0 back to dhcp.

It worked, but the script to start/restart the network took soooo long, made boot last forever, and I simply commented

#auto eth0
#iface eth0 inet dhcp

out of interfaces.

And voila.

Still, waiting for the fix for the bad function...

---

### Post by wilberfan on 2008-11-01
I manually edited the interfaces file, took networkmanager out of the autostart folder (via the sessions config--I'm running gnome), restarted the network....and still had no internet connection.

When I manually opened the Network Configuration gui, it showed "45" as the netmask.

:confused:

---

### Post by sephora on 2008-11-01
I have done everything you proposed in posts! Nothing worked for me!

So I removed network-manager and installed wicd, but it didn't work. So now I don't know what  to do.

Any ideas?

---

### Post by waffen on 2008-11-02
Hello,

I found the solution:

[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

I installed Wicd and all my problems go out! I can connect with my static IP address I see the wifi.

I have a problem with the intrepid repos for Wicd, but I downloaded from sourceforge de deb. packages, uninstall NetworkManage and WifiRadar if you have preintalled both of them.

I can not test with wifi network (actually I can see a pair of new wifi network more.. ) but another user can try it?

---

### Post by Wil Palen on 2008-11-03
Same problem here.

I had disabled NetworkManager already in hardy because it didn't work back then (set everything up in /etc/network/interfaces), but now after the upgrade to Intrepid, of course NetworkManager was installed and running (ruining?) again.

During the upgrade (before rebooting) NetworkManager already managed to mangle my /etc/resolv.conf. No name lookups, so web browsing became somewhat uncomfortable.

reboot.

Got a dynamic IP address. strange. I thought I had fine static IP configured, where you normally configure such things, like /etc/network/interfaces? checking the file.. yep, static IP config still there.

Good I didn't do a remote upgrade, because I would have been unable to connect again, due to portforwarding to the static IP etc.

Ok, I'm still smiling. Lets configure a static (system) IP then! 

No go. whatever I do, it just keeps insisting on a DHCP configured network, or no network at all. And if there IS a network it reinitializes every once in a while so all my open connections disappear.

This happens with both the KDE and GNOME clients.

Maybe it's because the latest and the greatest make nice headlines, but I just can't believe this flawed upgrade process and untested(?) software gets released in a stable Ubuntu release (again! see hardy).

but, to close with something positive:

- for wireless it seems to work ok.
- and for those with a static, wired setup, there's WICD (works great)

---

### Post by dlocutor on 2008-11-04
same here symptoms ..
 
i read this complete thread from top to bottom ..
tried everything in the book no luck
spotty inet connectivity  .. tried both static and dhcp 
some domains connect some don't which is weird ..

interesting it appears this has been going on for awhile:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/272896](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/272896)

this is the worst Ubuntu upgrade scenario I have ever been through ..
goin' back to the Hardy boyz ..

/.d 
 
release 8.10
Kernel 2.6.27-3-rt
Gnome 2.24.1
3.2GB/E8500@3.16GHZ

---

### Post by reader4 on 2008-11-04
I am having a similar problem... netmask turns to 17 after I set it up.  I need to use both wired and wireless on my laptop.  I was forced to edit out the manual configuration lines in /etc/network/interfaces to get the nm-applet to appear on startup.  

[http://ubuntuforums.org/showthread.php?t=956187&page=3](http://ubuntuforums.org/showthread.php?t=956187&page=3)

Mine appears to be a DNS problem, and my settings are never stored after I log out.  I can ping and connect to IPs in Firefox, but not using domain names ([www.google.com](www.google.com)).  This despite using the same DNS settings as I was using before the upgrade, so I know they should work.

---

### Post by Pletch on 2008-11-04
This is only my interpretation but I believe the netmask value in Network Manager is being display in shorthand CIDR notation where the number shown is the number of binary 'one' bits.  

For example, a netmask of 255.255.255.0 is equivalent to /24 or 24.  See here for additional explanation [http://www.unixwiz.net/techtips/netmask-ref.html]("http://www.unixwiz.net/techtips/netmask-ref.html").

---

### Post by Major_Kong on 2008-11-04
No fix for this yet ?

---

### Post by reader4 on 2008-11-05
> **Pletch said:**
> This is only my interpretation but I believe the netmask value in Network Manager is being display in shorthand CIDR notation where the number shown is the number of binary 'one' bits.  [/URL].

Which is fine... the bigger problem (for me at least) is that settings are not saved (I have to re-enter the IP, netmask and gateway every time I login) and DNS isn't working, so I can only see/access local computers.

---

### Post by robertbc on 2008-11-05
From the beginning pardon my english (bless this auto-correct).

The NetworkManager Applet tries to use whatever connection to the internet is available. So it provides a default system-wide setting for your network card (dhcp). It is true that you can change the settings to use a static configuration, but this is in effect only as long as you're logged in (your settings don't stick when you restart). 

So... what you do is: right click on the NetworkManager Applet, left click on "Edit Connections..." (little window pops up), go to the "Wired" tab (if not already there) (here we see the network configurations provided by default "Auto eth0", if you have a second network card "Auto eth1" and so on), in the idea that we want to use the eth0 we select "Auto eth0" and click "Edit", in the new pop-up window go to the "Wired" tab and copy the MAC address (select string and copy), click cancel to close this window, now click "Add" (by default Ubuntu will provide a set of network parameters named "Wired connection 1" or something), we now select "Wired connection 1" and click "Edit", a now familiar window pops-up and we click paste in the field right to the "MAC address" (if your internet provider expects another MAC address - you know it and put that one here; preserve the format XX:XX:XX:XX:XX:XX), now make sure that "System setting" isn't ticked and that "Connect automatically" is, go to the "IPv4 Settings" tab, select "Method" to "Manual", click "Add" and edit the new row by clicking on each column, writing your addresses, and hitting "Enter" ("Return") after each one (I think that your "Netmask" will turn up in its short expression, (but the system knows what you entered)), also write your "DNS Servers" and you're all set. Press "OK". Press "Close".
If your network connection is not functional in in a few moments then left click on the NetworkManager Applet and select "Wired connection 1" (or the name you gave to your set of parameters). If still nothing, then restart your machine. The internet connection should start after NetworkManager probes the "Auto eth0" set of settings and finds that your set of settings is the winner.  

We found out that this applet does not appeal to the common sense without the previous knowledge that a single network card can have more sets of setting.

Go here for more information: [http://live.gnome.org/NetworkManagerConfiguration](http://live.gnome.org/NetworkManagerConfiguration)
 
Hope this helps many of you!

---

### Post by barratt_sab on 2008-11-06
Here’s a quick manual work around, to get internet connectivity:

1. disable the network manager:

```
sudo /etc/init.d/networking stop
```

2. find your wired interface name with

```
ifconfig
```

it will start "eth" – mine was eth0

3. give it a static IP address:

```
sudo ifconfig eth0 192.168.0.90
```

(use your interface name and pick and unused IP address within your local subnet)

4. set up the default gateway:

```
sudo route add default gw 192.168.0.1
```

(use the your own gateway address – most likely your router LAN IP)

5. test ping the IP you set for eth0:

```
ping 192.168.0.90
```

If it doesn’t work, look at the IP address with 

```
ifconfig
```

and make sure it’s right

6. test ping the gateway:

```
ping 192.168.0.1
```

If it doesn’t work, look at the default route using

```
route
```

and check it’s set right
NOTE – some routers won’t return a LAN ping, so if it looks OK, but doesn’t ping, test another node on your network instead:

```
ping 192.168.0.91
```

Until you get something to return

7. test ping a URL:

```
ping www.yahoo.com
```

If that works, then you’re up and running – and can try to download updates etc to fix the original problem

If not:

8. edit your dns file:

```
sudo gedit /etc/resolv.conf
```

And at the end of the file add:

```
nameserver 192.168.0.1
```

(use your gateway address)

Now save the file and exit gedit and (hopefully!) you should have connectivity.

---

### Post by hachel on 2008-11-06
> **barratt_sab said:**
> Here’s a quick manual work around, to get internet connectivity:
...
Now save the file and exit gedit and (hopefully!) you should have connectivity.
just jumped into this thread, is this permanent?

---

### Post by TBHockey on 2008-11-06
I was experiencing the Issue of losing the Static IP settings on reboot, or even after a few days without reboot....actually happened today. Editing the /etc/network/interfaces File as stated on the previous page has worked for me, I am running 8.10 Server.

---

### Post by reader4 on 2008-11-10
> **robertbc said:**
> ... what you do is: right click on the NetworkManager Applet, left click on "Edit Connections..." (little window pops up), go to the "Wired" tab (if not already there) (here we see the network configurations provided by default "Auto eth0", if you have a second network card "Auto eth1" and so on), in the idea that we want to use the eth0 we select "Auto eth0" and click "Edit", in the new pop-up window go to the "Wired" tab and copy the MAC address (select string and copy), click cancel to close this window, now click "Add" (by default Ubuntu will provide a set of network parameters named "Wired connection 1" or something), we now select "Wired connection 1" and click "Edit", a now familiar window pops-up and we click paste in the field right to the "MAC address" (if your internet provider expects another MAC address - you know it and put that one here; preserve the format XX:XX:XX:XX:XX:XX), now make sure that "System setting" isn't ticked and that "Connect automatically" is, go to the "IPv4 Settings" tab, select "Method" to "Manual", click "Add" and edit the new row by clicking on each column, writing your addresses, and hitting "Enter" ("Return") after each one (I think that your "Netmask" will turn up in its short expression, (but the system knows what you entered)), also write your "DNS Servers" and you're all set. Press "OK". Press "Close".

This worked for me, and allowed me to keep my wireless working when I didn't have a wired connection.  I tried this procedure once before; updating the MAC address was the piece I was missing... thanks!

---

### Post by hahahan on 2008-11-10
Can you ping any hard address like $>ping 64.233.161.83?
If so it will help to add a nameserver to your /etc/resolv.conf file like 

$>sudo echo "nameserver xxx.xxx.xxx.xxx" > /etc/resolv.conf .Where xxx.xxx...is the address of a valid nameserver.

---

### Post by jonobr on 2008-11-10
Mikesmithv, 

aren't a netmask of "24"  and "255.255.255.0" the same thing?
Is this only presnetation or something more sinister?

---

### Post by wilberfan on 2008-11-10
Well, I thought [robertbc's post]("http://ubuntuforums.org/showpost.php?p=6114149&postcount=26") was going to do the trick!  It DOES allow me to successfully set up a manual, wired connection, but when I reboot, the "Auto eth0" setting takes over again.   

I've even tried DELETING the lil' *******...unchecking the automatic start box, but it rises from the dead every time, at each reboot.   :confused:

What would be causing *that* behavior?  Do I need to be making those changes as root, or...?  (If so, how would I do that?)

---

### Post by jamb on 2008-11-15
> **waffen said:**
> The workaround is disable the NetworkManager and setup by hand the params in /etc/network/interfaces and the DNS, in my internet search I can see is a possible bad function in the NetworkManager present in the Ubuntu 8.10 Betas and not solved yet...

I had kind of weird experience, with DNS and static IP's but now it fails again with the latest upgraded Intrepid packges. Anyway in my setup I found a workaround by modifying only /etc/resolv.conf.

I have done further investigations, add the 'nameserver' directive to /etc/resolve.conf, which solved the problem in my setup. 
Hardy does not have this problem...  

[http://ubuntuforums.org/showthread.php?p=6186742#post6186742](http://ubuntuforums.org/showthread.php?p=6186742#post6186742)

---

### Post by mccartyj on 2008-11-19
namserver 192.168.1.1 (the IP of my router) worked for me. Thanks for the help!

Now does anyone know how to get CIFS to work again in 8.10? :-P

---

### Post by Roasted on 2008-11-20
Is static IP's officially fixed in Intrepid? Or is this still a problem?

---

### Post by kevinfishburne on 2008-11-23
It's still an issue as far as I can tell. Ubuntu should dump Network Manager completely and use something else. Network Manager has been terrible from the beginning in nearly every aspect. Its main problem, other than failing to provide functionality that its GUI suggests is there, is its unpredictability. Enough ranting, though. :/

I'm running a clean install of Ubuntu 8.10 Desktop AMD64, with no modifications other than installing all updates, uninstalling some unneeded apps, and modifying the exports and fstab files. My LAN has a DHCP server, but this PC is a server and needs a static IP.

While I can create additional network profiles, any modification to the default "auto eth0" profile is undone after a reboot. There appears to be no way to set a profile as default, apply any of the existing profiles, or configure hierarchy/precedence between them. It's also interesting that the Network Manager is now under the Preferences menu and doesn't require root access, which makes me think that Ubuntu uses /etc/network/interfaces pre-login and Network Manger's junk settings post-login.

Is it just me, or is this totally insane? As bad as Network Manager was in previous releases, this one seems to have a serious lack of functionality and is a step backward in many respects (lack of control and intuitiveness being the main ones). I just feel like I'm missing something obvious that will make everything better, but that feeling is slipping away as the process of elimination reveals that new Network Manager truly is worthless. :/ I'm ranting again...

---

### Post by shanix on 2008-11-23
Bug:
[https://bugs.launchpad.net/ubuntu/+source/knetworkmanager/+bug/280762](https://bugs.launchpad.net/ubuntu/+source/knetworkmanager/+bug/280762)

---

### Post by Me2resh on 2008-12-01
you might want to check this way to solve the problem here
[http://www.php-architect.com/blog/2008/11/04/ubuntu-810-interpid-fix-static-ip-network-manager-problem/]("http://www.php-architect.com/blog/2008/11/04/ubuntu-810-interpid-fix-static-ip-network-manager-problem/")

---

### Post by wilberfan on 2008-12-01
> **Me2resh said:**
> you might want to check this way to solve the problem here
[http://www.php-architect.com/blog/2008/11/04/ubuntu-810-interpid-fix-static-ip-network-manager-problem/]("http://www.php-architect.com/blog/2008/11/04/ubuntu-810-interpid-fix-static-ip-network-manager-problem/")

Big thanks to Me2resh for that link!  It's the first solution to this problem that's actually worked for me.  :guitar:

---

