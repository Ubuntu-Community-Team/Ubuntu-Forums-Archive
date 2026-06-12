---
title: "Network Manager problems after upgrade to 14.04"
date: 2014-09-20
forum: Networking &amp; Wireless
---

### Post by rachel-g41 on 2014-09-20
Very sorry for yet another thread on this - there seem to be many on related issues; however I've trawled through lots of them without finding a solution.

I lost my network manager /nm-applet icon after upgrading to 14-04. I found advice on another thread here about adding nm-applet to the autostart options and on another laptop, it worked perfectly.

However on this little ASUS netbook it's not working. I tried adding it but no icon appears and when I tried running nm-applet from terminal I get this error

> ** (nm-applet:4309): WARNING **: Couldn't connect to accessibility bus: Failed to connect to socket /tmp/dbus-yxBzxzLQMs: Connection refused
nm-applet-Message: using fallback from indicator to GtkStatusIcon



I found a workaround by using Preferences-Network Connections to manually add a new connection, but still can't find a way to search for available networks. I have a network icon which I managed to add to the status bar but it doesn't help, with LeftCLick it tells me which network I'm connected to and with RightClick it gives me the options Repair and Disable  - I've tried repair but with no luck.

I've also read that nm-applet is no longer included in the repository(?) and to try wicd, but I tried installing wicd and still with no luck. 

Any advice would be greatly appreciated.

---

### Post by varunendra on 2014-09-21
> **rachel-g41 said:**
> I've also read that nm-applet is no longer included in the repository(?)

I don't think nm-applet has ever been an independent package in repository. I may be wrong, but at least currently it seems to be a part of 'network-manager-gnome' package.

So what happens if you try to purge and reinstall network-manager-gnome? If you can somehow get an internet connection on the system -
```
sudo apt-get install --reinstall -d network-manager network-manager-gnome
sudo apt-get purge network-manager-gnome network-manager
```
Then, after a reboot, reinstall it from the packages that were downloaded from the first command (of course run the 2nd one above ONLY if the first one completes successfully) -
```
sudo apt-get install network-manager network-manager-gnome
```


However, if you can't connect this machine to internet, does the following command give us any download URIs so we can manually download the required packages to try a reinstall ? -
```
apt-get install --reinstall --print-uris network-manager network-manager-gnome
```
On my machine here, it does, but the package versions would be different for yours.

---

### Post by rachel-g41 on 2014-09-21
Thank you I have just tried this.

the first bit worked ok because I did have an internet connection (I just couldn't search for networks), so I did the 2nd bit but the 3rd line fails because it's looking for additional files and can't connect to the internet presumably because of the purge.

So now I don't have a connection at all and even the workaround doesn't work.

HELP!

---

### Post by rachel-g41 on 2014-09-21
OK, stuck a cable in so managed to get network manager back and am back to square one. I still can't search for available networks, I still get the same error message when I try to run/install nm-applet

---

### Post by varunendra on 2014-09-23
Could you test the network on a Live DVD/USB of 14.04.1? Is a clean install an option? If yes, that would be quickest and most promising solution. If not, what are your permissions? That is, the output of -
```
id
```

---

### Post by tgalati4 on 2014-09-23
Post the output of:

```
cat /etc/network/interfaces
```

It should look like:

> tgalati4@Mint14-Extensa ~ $ cat /etc/network/interfaces
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

---

### Post by rachel-g41 on 2014-10-12
Many thanks again for the suggestions and sorry for not replying sooner. Being away from home I decided to leave it until I was back and with a spare PC just in case. 

Before I go ahead with these suggestions, some developments. While I did nothing more to solve the problem, I did allow the system to do some recommended software updates. Network manager now works some of the time - and always at first boot-up. After suspension/hibernation it often fails or tells me there are no networks in range. Occasionally, sudo restart network-manager works but sometimes a reboot is needed. Possibly unrelated, I also get multiple 'system error detected' messages at boot-up. 

OK, I'm now going to look at the suggestions above.

---

### Post by rachel-g41 on 2014-10-12
> **varunendra said:**
> Could you test the network on a Live DVD/USB of 14.04.1? Is a clean install an option? If yes, that would be quickest and most promising solution. If not, what are your permissions? That is, the output of -
```
id
```

Than you for this. The first part was impractial while I was travelling; however I'm going to try it from the live USB today. What most puzzles me is that I used the same installation disk for a laptop and a netbook, and while the same problem arose with both, the solution that worked for the laptop didn't work for the netbook. I accept that a new install is probably the best way -or is it worth waiting for 14.10?

anyway, ```
id
``` gives me this:

```
uid=1000(rachel) gid=1000(rachel) groups=1000(rachel),4(adm),24(cdrom),27(sudo),30(dip),46(plugdev),112(lpadmin),118(sambashare)
``` but I have no idea what any of this means.

Thanks again.

---

### Post by rachel-g41 on 2014-10-12
> **tgalati4 said:**
> Post the output of:

```
cat /etc/network/interfaces
```


The output is:

```
rachel@rachel-1025CE:~$ cat /etc/network/interfaces
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

```

which looks just like yours, but then networkmanager is working at the moment. Next time it stops working I'll try it again and see if it has changed.

---

### Post by rachel-g41 on 2014-10-16
Ok,today on boot up, although the netbook connected automatically to the house wifi, network manager isn't working, ie I can't view available networks. 

This time the result is different:

```
rachel@rachel-1025CE:~$ cat /etc/network/interface
cat: /etc/network/interface: No such file or directory


```

Does this help to work out what's wrong?

Thanks again for any advice


Edited to add:

```
sudo restart network-manager
``` has got the networks viewable again BUT it's not giving me the option to connect via VPN, which it used to do.

---

### Post by rachel-g41 on 2014-10-19
I have just realised that when I log in as guest, network manager displays as it always did and as it should. 

So, why not in my own profile?

---

### Post by varunendra on 2014-10-22
If you need to restart network-manager service to make it work after suspend/resume, you can try what is suggested here : [http://ubuntuforums.org/showpost.php?p=13085936](http://ubuntuforums.org/showpost.php?p=13085936)

Regarding why the problem is specific to your main user account, no idea. Permissions and group-memberships look okay as per the output in post #8.

---

### Post by Martinjo84 on 2014-10-22
I have the same problem on my Thinkpad T440, i have try alot of things, but nothings work. 
Now i uninstalled network-manager and install WICD

hope for a fix soon, there is allready a Bugreport on this

---

### Post by rachel-g41 on 2014-10-22
Thank you  varunendra for the new suggestions.  meanwhile, in the absence of a solution I did a new install (of 13.10) 

I will try to find time at the weekend to have another go with 14.04 and your suggestions - or might leave it now and see what 14.10 brings. 

Thanks again to all who replied.

---

