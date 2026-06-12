---
title: "Ubuntu won't apply wireless settings"
date: 2007-11-03
forum: Networking &amp; Wireless
---

### Post by alexjohnc3 on 2007-11-03
When I choose the ESSID from the dropdown menu, enter the key for the wireless router, and  set it to DHCP, Ubuntu never connects except for when it arbitrarily gives me a message saying "Changing interface configuration." When that happens, it connects every time, but otherwise it just doesn't do anything and the connection doesn't work. That is, when Ubuntu doesn't freeze my computer and force me to turn it off and on again. (I'd also like to know how to stop this, though that may be out of the scope of this thread.) Thanks for any help that you guys can offer!

---

### Post by kevdog on 2007-11-03
Not sure where to start here.  Need some more specifics.  Here is a thread that explains basics:

[http://ubuntuforums.org/showthread.php?t=596797](http://ubuntuforums.org/showthread.php?t=596797)

---

### Post by alexjohnc3 on 2007-11-03
The problem is that it doesn't "change the interface connection" when I put all the correct settings in under System -> Administration -> Network. It's worked once and the two or three other times it was about to work (out of maybe 20 to 25 tries), but the computer froze before it could finish "changing the interface connection." I've had this same problem with other computers that I've tried Ubuntu on before, so this isn't something new. The only difference is that my computer freezes (even when booting up sometimes), which prevents me from connection to the network and then I have to reload the entire Live CD.

---

### Post by kevdog on 2007-11-03
Try booting from the command line (Yikes)  - the instructions are on in my signature.  This isnt a permanent solution -- only to check and see if everything works.

---

### Post by maestrobwh1 on 2007-11-03
Odd... are you using network manager?  It might be above my head, but I had a "similar" issue and just installed WICD instead.  Goolge WICD and follow the directions there for installing.  It works like a charm for me.  My issue wasn't "exactly" the same though.  I do know that WICD seems to solve some people's connection issues.

---

### Post by alexjohnc3 on 2007-11-03
> **maestrobwh1 said:**
> Odd... are you using network manager?  It might be above my head, but I had a "similar" issue and just installed WICD instead.  Goolge WICD and follow the directions there for installing.  It works like a charm for me.  My issue wasn't "exactly" the same though.  I do know that WICD seems to solve some people's connection issues.
Okay, thanks, I'll try that. I had some issues with the terminal-based solution from kevdog, so this is greatly appreciated. I'll post if it works later.

---

### Post by alexjohnc3 on 2007-11-04
Is it possible to download WICD, put it on a flash drive, and then install it on Ubuntu? Remember, I don't have the ability to connect to the Internet via the computer I have with Ubuntu on it.

---

### Post by alexjohnc3 on 2007-11-04
> **alexjohnc3 said:**
> Is it possible to download WICD, put it on a flash drive, and then install it on Ubuntu? Remember, I don't have the ability to connect to the Internet via the computer I have with Ubuntu on it.
Bump...

---

### Post by alexjohnc3 on 2007-11-05
> **alexjohnc3 said:**
> Bump...
I hate bumping threads, but I *really* need some help here.

---

### Post by a__l__a__n on 2007-11-05
You will need to find a computer with network connectivity, and download the correct WICD debian package.  There are debian packages here:

[https://sourceforge.net/project/showfiles.php?group_id=194573](https://sourceforge.net/project/showfiles.php?group_id=194573)

although I don't know whether these are appropriate for your version of ubuntu.

You might also find these instructions useful:

[http://www.ossgeeks.co.uk/?p=166](http://www.ossgeeks.co.uk/?p=166)  

I hope that helps.

---

### Post by alexjohnc3 on 2007-11-05
> **a__l__a__n said:**
> You will need to find a computer with network connectivity, and download the correct WICD debian package.  There are debian packages here:

[https://sourceforge.net/project/showfiles.php?group_id=194573](https://sourceforge.net/project/showfiles.php?group_id=194573)

although I don't know whether these are appropriate for your version of ubuntu.

You might also find these instructions useful:

[http://www.ossgeeks.co.uk/?p=166](http://www.ossgeeks.co.uk/?p=166)  

I hope that helps.
I'm using Ubuntu 7.10 and when I tried to install that wicd_1.3.1-all.deb (after I removed Network Manager, like the OSSGeeks page said to), I got a pop-up saying, "The NetworkManager applet could not find some required resources. It cannot continue."

---

### Post by alexjohnc3 on 2007-11-06
Bump. :(

---

### Post by alexjohnc3 on 2007-11-06
Yet another bump...

---

### Post by MaximusTG on 2007-11-06
Are you sure you removed all networkmanager packages? Seems like you still have the applet installed. try a

sudo apt-get remove network-manager-gnome

Does WICD work for you?

---

### Post by peebly on 2007-11-06
If you get wicd working tell me how, I have never got it to work with 7.10

---

### Post by alexjohnc3 on 2007-11-06
> **MaximusTG said:**
> Are you sure you removed all networkmanager packages? Seems like you still have the applet installed. try a

sudo apt-get remove network-manager-gnome

Does WICD work for you?
When I do cd Desktop and sudo dpkg -i wicd_1.3.1-all.deb, it installs, but it can't find any networks. For the network manager I tried sudo apt-get remove network-manager before and this time I did that for both network-manager and network-manager-gnome.

---

### Post by MaximusTG on 2007-11-06
okay, so what is you situation like? What wireless card do you have? What kind if wireless network are you connecting to(wpa, wpa2, wep)? Is it a desktop or a laptop, and do you have to have it able to roam, or is it just at home, and will it be connecting to the same network every time?

---

### Post by alexjohnc3 on 2007-11-06
> **MaximusTG said:**
> okay, so what is you situation like? What wireless card do you have? What kind if wireless network are you connecting to(wpa, wpa2, wep)? Is it a desktop or a laptop, and do you have to have it able to roam, or is it just at home, and will it be connecting to the same network every time?
Wireless card: I'm not sure.
Connection to a router with WEP security.
It's a desktop computer; a Dell Inspiron 531.
It will be connecting to the same network every time.

---

### Post by MaximusTG on 2007-11-07
Okay, now we are getting somewhere.

Could you type the following in a terminal and post the results?

lspci


and


sudo iwlist scan


Then, in the meanwhile you could try this:

Edit your /etc/network/interfaces file (as root)

and put in (or edit the section for your wireless card if it is already there)
Assuming the name of your wireless card is 'eth2'

iface eth2 inet dhcp
wireless-key your-wep-key
wireless-ssid your-wlan-ssid

If your wep-key is 64-bit ascii, enter it like this:

wireless-key s:abcde

where abcde would be the key, the s: means string value.
After editing /etc/network/interfaces you could restart networking like this:

sudo /etc/init.d/networking restart

or just reboot

---

### Post by alexjohnc3 on 2007-11-09
\

---

### Post by alexjohnc3 on 2007-11-10
Bump...

---

### Post by alexjohnc3 on 2007-11-10
Bump. Again.

---

### Post by alexjohnc3 on 2007-11-14
...and again.

---

### Post by MaximusTG on 2007-11-19
Here are the windows drivers for your wireless card, a realtek 8185 a/b/g wireless card.
Use them with ndiswrapper, since the linux native driver supplied with Ubuntu is known to freeze systems. You could also try compiling the linux driver that's available on the realtek website, but that's a bit more complicated than using ndiswrapper.

---

