---
title: "Network Manager not playing nice? Get Wicd!"
date: 2007-04-19
forum: Networking &amp; Wireless
---

### Post by RavanH on 2007-04-19
Hey everybody!

Just have to share this little success story (sounds like a bad infomercial doesn't it, Mike? ;) ) after my huge fight with Network Manager in Feisty. But it should apply to Dapper and Edgy too...

I have a laptop with a Ralink RT2500 based pcie card and it just didn't work right with Network Manager that came with Feisty preinstalled. I could see WLAN's (but without signal strenght) but could not make it connect with my wifi, whatever I tried. Not even without any encryption, it just couldn't get an IP assigned.

I found out that if I uninstalled Network Manager completely, I could connect to my wifi but not with WPA encryption (WPA_supplicant not working with driver or something)... And when I wanted to use other hotspots, I had to configure the network each time manually. Not my ideal situation...

After reading lots of threads about wifi networking on these forums and testing a few other alternatives to Network Manager until the small hours grew bigger again - with similar results :( - I came across Wicd Manager. After downloading the .deb installation package and installing it, my sleepy eyes cracked wide open again! Straight away: it worked! Even with WPA!! 

Had to manually ad the tray icon to my session (see [http://adam.blackhole.cx/wicd/wb/pages/f.a.q..php#question_2](http://adam.blackhole.cx/wicd/wb/pages/f.a.q..php#question_2)) and from that moment on, I've had no issues with my wireless networking anymore :)

So............

Anyone with similar head-aches feel the need to get wicked with it? 
Go to [http://adam.blackhole.cx/wicd/wb/](http://adam.blackhole.cx/wicd/wb/) and get Wicd!

It just might :guitar: for you too ;)

EDIT:
The Wicd website and forums have had some problemsof late. The main developer of Wicd, Adam, informed me that due to DNS issues the site has moved. Below is the new location:
> [http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

---

### Post by neilq101 on 2007-04-19
Hey, I just installed Feisty in the hope that it would allow me to finally  get my wireless working; it seemed to have been successful, as after I installed ndiswrapper (for the dreaded Broadcom Air Force One chip), it recognised all the networks in the area; however, it would not connect to my WPA home network, as it simply sat there trying to connect until it gave up.  I installed wicd, and it also recognised the networks, but again, it fails to connect to WPA.  I tried using the Advanced settings and putting in the key, but it simply says 'obtaining ip address' and then gives up.  Any ideas?:confused:

---

### Post by jhpope on 2007-04-19
i have the same problem only i have the edimax ew-7128 card. wicd told me to delete network-manager and now i had to reinstall ubuntu cause i couldn't get it back

---

### Post by RavanH on 2007-04-20
> **neilq101 said:**
> Hey, I just installed Feisty in the hope that it would allow me to finally  get my wireless working; it seemed to have been successful, as after I installed ndiswrapper (for the dreaded Broadcom Air Force One chip), it recognised all the networks in the area; however, it would not connect to my WPA home network, as it simply sat there trying to connect until it gave up.  I installed wicd, and it also recognised the networks, but again, it fails to connect to WPA.  I tried using the Advanced settings and putting in the key, but it simply says 'obtaining ip address' and then gives up.  Any ideas?:confused:

Have you tried their forum: [http://adam.blackhole.cx/wicd/phpbb/index.php](http://adam.blackhole.cx/wicd/phpbb/index.php)

---

### Post by Pomo on 2007-04-20
> **RavanH said:**
> Have you tried their forum: [http://adam.blackhole.cx/wicd/phpbb/index.php](http://adam.blackhole.cx/wicd/phpbb/index.php)

And that's gonna help, yea right. Network manger and wicd both for me are useless. Neither give me connection to my wpa protected wifi network. It is a great issue for ubuntu and I think it should be resolved asap. Wirelless security is being taken too lightly by ubuntu developers.
Network manager does not even give me an option for wpa key (noit working with hidden ssid, I presume), and wicd just goes "generating psk" forever...
BTW it is THE only thing keeping me from crossing to ubuntu from win xp since dapper.
Wonder what scandal would such a security issue cause in M$ world.

---

### Post by RavanH on 2007-04-21
> **Pomo said:**
>  It is a great issue for ubuntu and I think it should be resolved asap. Wirelless security is being taken too lightly by ubuntu developers.
I agree that WPA should be given proirity by developers. Although WPA is not that secure at all, at least it is way better than worthless WEP.

This is indeed one of the big dealbreakers for many (including small businesses and semi-/governmental orgs) to cross to Linux.

I really hope this will get resolved soon, so Network Manager works straight out of the box for much more people than that happy few that got the right network card...

---

### Post by sionghua on 2007-04-21
I think the wicd site is down...

---

### Post by davegod75 on 2007-04-21
> **sionghua said:**
> I think the wicd site is down...


I cannot get to the site either  :(

---

### Post by Skidpad on 2007-04-21
> **davegod75 said:**
> I cannot get to the site either  :(

Try: [http://218.46.125.189/wicd/wb/](http://218.46.125.189/wicd/wb/)

---

### Post by RavanH on 2007-04-22
The Wicd website has moved.

* the forums are at [http://compwiz18.ig3.net/wicd/phpbb](http://compwiz18.ig3.net/wicd/phpbb)
* the website is at [http://compwiz18.ig3.net/wicd/wb](http://compwiz18.ig3.net/wicd/wb)
* the wiki is at [http://compwiz18.ig3.net/wicd/wiki](http://compwiz18.ig3.net/wicd/wiki)

---

### Post by ziadoz on 2007-04-22
This isn't a solution for everyone. I can't access my wireless network through Network Manager, Wifi-Radar or Wicd, despite the fact I can see it in all of them. There is a clearly an issue here, and its not related to wireless management applications. 

I hope the Ubuntu developers resolve this soon!

---

### Post by neilq101 on 2007-04-22
Yeah, this is a very annoying problem, but one that has also taken on a rather strange dimension; on Friday night, my laptop finally decided to connect to the WPA secured home network I had previously not been able to access (using Network Manager, which I had re-installed in place of Wicd).  It kept a fast, stable connection all night, but since then I have not been able to connect, however, I now know that a connection can be made.  I have no idea what is going on here, but I hope the devs figure it out soon and update it, assuming nobody else has any idea why it randomly decided to connect?

---

### Post by mabelrxu on 2007-04-22
my wireless is kinda odd ... after adding some lines to my /etc/network/interfaces so that it now looks like this:
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp
pre-up wpa_supplicant -Bw -Dwext -ieth1 -c/etc/wpa_supplicant.conf
post-down killall -q wpa_supplicant

```
my network only works if i do a manual ```
sudo /etc/init.d/networking restart
``` after I login ... it's kinda annoying, but at least it works ... oh yeah, and my /etc/wpa_supplicant.conf goes something like this:
```

ctrl_interface=/var/run/wpa_supplicant
ap_scan=1

network={
        ssid="mGenius"
        scan_ssid=1
        proto=RSN
        key_mgmt=WPA-PSK
        pairwise=CCMP
        group=CCMP
        psk=<generated psk here>
}

```
i generated my psk by saying:
```

wpa_passphrase mGenius <your network password ... the human readable one>

```
and then copying and pasting the generated code (it's really long and alpha-numeric) into my /etc/wpa_supplicant.conf

i got this solution through a combination of [http://ubuntuforums.org/showthread.php?t=263136]("http://ubuntuforums.org/showthread.php?t=263136") and [http://ubuntuforums.org/showthread.php?t=202834]("http://ubuntuforums.org/showthread.php?=202834")

---

### Post by AleXit on 2007-04-22
Hello,

Ralink drivers (legacy ones) does not work with wpasupplicant (and networkmanager) because they don't support Linux Wireless Extensions.
Encyption (wep and wpa) is set by private commands (through iwpriv).

However, exist a nice tool to configure Ralink drivers, it's RutilT.

Homepage: [http://cbbk.free.fr/bonrom](http://cbbk.free.fr/bonrom)

I also made an Ubuntu .deb package which should work great:
[rutilt_0.14-0~3v1ubuntu1_i386.deb](http://3v1n0.tuxfamily.org/pool/edgy/3v1n0/rutilt_0.14-0~3v1ubuntu1_i386.deb)

here a screenshot: [http://img133.imageshack.us/img133/3259/rutiltfirstxg8.png](http://img133.imageshack.us/img133/3259/rutiltfirstxg8.png)

---

### Post by dcapurro on 2007-04-22
> **AleXit said:**
> Hello,

Ralink drivers (legacy ones) does not work with wpasupplicant (and networkmanager) because they don't support Linux Wireless Extensions.
Encyption (wep and wpa) is set by private commands (through iwpriv).

However, exist a nice tool to configure Ralink drivers, it's RutilT.

Homepage: [http://cbbk.free.fr/bonrom](http://cbbk.free.fr/bonrom)

I also made an Ubuntu .deb package which should work great:
[rutilt_0.14-0~3v1ubuntu1_i386.deb](http://3v1n0.tuxfamily.org/pool/edgy/3v1n0/rutilt_0.14-0~3v1ubuntu1_i386.deb)

here a screenshot: [http://img133.imageshack.us/img133/3259/rutiltfirstxg8.png](http://img133.imageshack.us/img133/3259/rutiltfirstxg8.png)

Excuse the ignorance... I downloaded the Ubuntu .deb package. As I cannot connecto to the internet I transferred the file to the desktop through a pendrive. After that how can I install the package? I followed the instrucions at [https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/apt.html](https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/apt.html) but it keeps saying that it doesn't find the package.

---

### Post by RavanH on 2007-04-22
> **AleXit said:**
> 
I also made an Ubuntu .deb package which should work great:
[rutilt_0.14-0~3v1ubuntu1_i386.deb](http://3v1n0.tuxfamily.org/pool/edgy/3v1n0/rutilt_0.14-0~3v1ubuntu1_i386.deb)

Will this work on 64bit architecture?

EDIT:
found [http://rutilt-debian.googlecode.com/svn/packages/debian/](http://rutilt-debian.googlecode.com/svn/packages/debian/) but that gives me an error:
```
An error occured :
Can't get injection mode through private ioctl.
Code : 1
```

---

### Post by mabelrxu on 2007-04-22
do install any package from a local source (like your home folder, or a usb pen drive, or whatever), just do
```

sudo dpkg -i package_version0.0-ubuntu.deb

```
or whatever your .deb file is named ... you can use tab completion, just type the first couple of letters and hit tab, and it'll give auto-complete it for you ... if it doesn't, hit tab again (so it's like double-tab), and it'll give you a list of possible auto-completions

hope this helps!

---

### Post by dcapurro on 2007-04-22
> **dcapurro said:**
> Excuse the ignorance... I downloaded the Ubuntu .deb package. As I cannot connecto to the internet I transferred the file to the desktop through a pendrive. After that how can I install the package? I followed the instrucions at [https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/apt.html](https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/apt.html) but it keeps saying that it doesn't find the package.

Thanks, I got the package installed and now the application is running, I can detect the available wireless networks. The problem arises when I try to connect to the selected one, type the WEP key but I still cannot get connected. Do you know what else can I do?

---

### Post by mabelrxu on 2007-04-22
hmmm ... well, the screenshot ([http://img133.imageshack.us/img133/3259/rutiltfirstxg8.png](http://img133.imageshack.us/img133/3259/rutiltfirstxg8.png)) doesn't provide much detail, and I don't have a card, so I can't really help you ... actually, I don't use Wicd at all, i just saw your question and could help ... srry :-k

---

### Post by timmahhny on 2007-04-22
I just installed Feisty / dual boot with XP Pro.. Feisty installed fine, no problems, but can't connect with my internal WiFi connection. I can't even start the wireless using ifup /down. The button when pushed doesn't light up.
 I have a Linksys Wireless G card, but I don't think that will work in Linux. 
 I just downloaded the mentioned program and will see if that helps. I do like the dapper network manager better than Feisty. 
T

---

### Post by keith11 on 2007-04-23
> **RavanH said:**
> 
EDIT:
The Wicd website and forums have had some problems of late. The main developer of Wicd, Adam, informed me that due to DNS issues the site has moved. Below are the new locations - don't know if this is temporary or permanent...

I don't know what's wrong again but even the new addresses are not working. I read somewhere on Adam's forums that he is using a DSL connection and he was wanting someone to host the website. I think he should arrange for that as soon as possible and also resolve the DNS issues he has been having. Have you heard anything from him about the recent shutdown of the websites?

---

### Post by ernstblaauw on 2007-05-06
[http://wicd.sf.net](http://wicd.sf.net)

---

### Post by bodhi.zazen on 2008-08-03
I know this is an old thread, but I just wanted to say wicd worked very nice (solved my problem with network manager) for me and I like the interface. It has a number of superior features to network manager, wonder why it is not installed by default ?

---

### Post by jpeddicord on 2008-08-03
> **bodhi.zazen said:**
> I know this is an old thread, but I just wanted to say wicd worked very nice (solved my problem with network manager) for me and I like the interface. It has a number of superior features to network manager, wonder why it is not installed by default ?

Good luck getting responses on that.

*cough*

---

### Post by bodhi.zazen on 2008-08-04
Hmm ... well wicd is not the panacea I imagined.

I tried with another machine and had difficulty with network manager (never connected with network manager). 

Installed wicd ... connected right away (sweet).

But when I rebooted wicd will not connect, it throws an error about no networks detected (although the wireless card is working at boot ... ).

Odd.

Not much luck with google on this either ...

---

### Post by p_quarles on 2008-08-04
> **jacobmp92 said:**
> Good luck getting responses on that.

*cough*
> **bodhi.zazen said:**
> Hmm ... well wicd is not the panacea I imagined.

I tried with another machine and had difficulty with network manager (never connected with network manager). 

Installed wicd ... connected right away (sweet).

But when I rebooted wicd will not connect, it throws an error about no networks detected (although the wireless card is working at boot ... ).

Odd.

Not much luck with google on this either ...
I think what jacob is saying, bodhi, is that you are posting in a read-only forum, which means no one (other than staff) can actually reply. :)

---

### Post by bodhi.zazen on 2008-08-04
Yes, I know, I understand that. I am posting here because this thread is top of the list on google (at least on the google search I use).

So, I am not necessarily looking for support *yet* , just updating for anyone who stumbles across this thread.

Along those lines :

I added irqpoll to the boot options (add it in at the end of the kernel line in /boot/grub/menu.lst and in kopts earlier in the file)

Like this :

> kernel /boot/vmlinux.xyz ... root=/abc ... ro quite splash **irqpoll**With that option all is working just fine, so I change my vote back to 

+1 wicd :)

LOL

---

