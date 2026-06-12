---
title: "Problem with WPA keys, Works with none"
date: 2008-06-07
forum: Networking &amp; Wireless
---

### Post by juiceman on 2008-06-07
Hey guys,
I just installed Ubuntu 8.04 on my wife's laptop.

Hers is a IBM Thinkpad T30, as specified here:
[http://www.thinkwiki.org/wiki/Category:T30](http://www.thinkwiki.org/wiki/Category:T30)

I'm pretty sure she has the IBM internal wifi and not the cisco/aironet.  If you know how I can find out in the OS, please tell me.

Back to the point:
I am able to connect wirelessly to our neighbors network and our network if there is no security.  But when WPA 128 bit Open encryption is on, I cannot get it to connect.  I can click on the wireless network connector, enter the correct passkey, and it will doodle around a bit before coming back and asking me for the key again.

Please help!?
Juice

---

### Post by juiceman on 2008-06-08
bumpin to the front of the line.

---

### Post by GuruCesc on 2008-06-09
Hello All,
  I have the VERY same problem... I have a Thinkpad T20 with an external Netgear WG511v2 card.

  Everything seems to work properly. The network manager displays all the available wireless networks on my area, I select my own network and starts connecting. After a moment, it pops up a dialog for me to enter the WPA (or WPA2) password. I do so and it continues the process just to show me the dialog requesting my password again (and again and again) no matter if I select WPA Personal, WPA2 Personal or anything else).

  The wired network works properly and the wireless works properly on a different (XP) laptop. It used to work properly on Ubuntu 6.10 as well.

  I'm using the Windows XP drivers through ndiswrapper (just as I used to).

  Any Ideas??

Thanks in advance,
Cesar

---

### Post by rlzyoner on 2008-06-09
Maybe try

sudo apt-get update
sudo apt-get install wpasupplicant

Now reboot and try again

Also, you may find the following link helpful

[http://ubuntuforums.org/showthread.php?t=684495](http://ubuntuforums.org/showthread.php?t=684495)

---

### Post by juiceman on 2008-06-11
> **rlzyoner said:**
> Maybe try

sudo apt-get update
sudo apt-get install wpasupplicant

Now reboot and try again

Also, you may find the following link helpful

[http://ubuntuforums.org/showthread.php?t=684495](http://ubuntuforums.org/showthread.php?t=684495)

It said that the newest wpasupplicant is already installed.

As for that link, I am looking for a permanent fix for this issue instead of a way to connect to one-specific SSID/Network.  This is my wife's laptop and she doesn't have any of the necessary knowledge for doing command line modifications for each network she runs into.

It seems there is a more serious flaw in the software and these terminal commands are a forceful workaround for specific situations.  

Help?

---

### Post by kevdog on 2008-06-12
Have you tried a manual connection?

You can post back with questions, however here are two useful links:

[http://ubuntuforums.org/showthread.php?t=684495](http://ubuntuforums.org/showthread.php?t=684495)
[http://linux.die.net/man/8/iwconfig](http://linux.die.net/man/8/iwconfig)

---

### Post by juiceman on 2008-06-12
> **kevdog said:**
> Have you tried a manual connection?

You can post back with questions, however here are two useful links:

[http://ubuntuforums.org/showthread.php?t=684495](http://ubuntuforums.org/showthread.php?t=684495)
[http://linux.die.net/man/8/iwconfig](http://linux.die.net/man/8/iwconfig)

I did try the manual connection in the GUI.  Didn't work out.  I'll check those links for something.

The thing that gets me is that all the 'help' I've found so far is   not a fix for the overall WPA/Security element not working, but rather a workaround that allows you to connect to a specific network.  A viable fix that allows you to utilize the WPA element of wireless in the GUI for networks you roam-into would be the best answer.

---

### Post by kevdog on 2008-06-12
Do not try the GUI -- that is Network Manager -- troubleshoot directly from the command line -- just an FYI.

---

### Post by chili555 on 2008-06-14
> I'm pretty sure she has the IBM internal wifi and not the cisco/aironet. If you know how I can find out in the OS, please tell me.
```
sudo lshw -C network
```I have a T40 with the Aironet card and WPA is not supported until a later firmware. I believe the same is true for the other card available on the T30, which is a Prism 2.5.

Flashing firmware on either wireless card is not for the faint of heart.

---

### Post by juiceman on 2008-06-16
> **chili555 said:**
> ```
sudo lshw -C network
```I have a T40 with the Aironet card and WPA is not supported until a later firmware. I believe the same is true for the other card available on the T30, which is a Prism 2.5.

Flashing firmware on either wireless card is not for the faint of heart.

I have flashed firmware on many systems in many cases, but my main concern will be if I will be able to do it in Ubuntu.

So you're telling me that WPA didn't initially work with these?  So these wireless chips worked on open/unsecured networks only?  Wow.

Thanks for the heads up.  Now I just gotta figure out why my linksys WPC54G v1 PCMCIA card (on my T23) won't use WPA.

---

### Post by chili555 on 2008-06-16
> So you're telling me that WPA didn't initially work with these?Yes, however, they work quite well with WEP. Did you run:```
sudo lshw -C network
```Then we can tell what we are working with. On my T40, the command```
dmesg | grep -i airo
```Tells me that the firmware in my Aironet card does *not* support WPA. I guess I am going to have to drag myself upstairs and boot it up.

> chili@LAPTOP40:~$ dmesg | grep -i airo
[  108.050195] airo(): Probing for PCI adapters
[  108.050716] airo(): Found an MPI350 card
[  108.606466] airo(): WPA unsupported (only firmware versions 5.30.17 and greater support WPA.  Detected 5.20.17)
[  108.613061] airo(eth1): MAC enabled 00:02:8a:c8:3e:b2
[  108.613604] airo(): Finished probing for PCI adapters

---

### Post by dmedell on 2008-06-18
I too have just upgraded my wife's T30 to hardy and was encountering WPA problems. I had to change from WPA on my linksys router wireless security setting, to WEP 128bit HEX and use a key. 

The pass code that is asked for when you log on to the wireless network via the network manager applett will not work even though you may have put one on the router passcode section. 

You should try using the WEP 64/128 HEX from the drop down menu not the WEP 128 bit. As soon as you clik on the WEP 64/128 HEX, the passcode section changes to ask for the key. Put in the key that your router is set to. You can click on the "show key" to make sure it matches.

It may not be WPA but it is still hard to hack.:)

---

### Post by juiceman on 2008-06-18
Yeh... i actually realized what wasn't working was WEP open.  Right now i've got the wireless without security but is using mac address allow/disallow.  This should probably be sufficient...

Bummer is my only choices are these:  Both the WEP ones don't seem to work out.  They have worked in XP in the past.. 

WEP-Open
WEP-Shared
WPA-PSK
WPA2-PSK

I have a 2wire 2701 (i think thats the model).

---

### Post by dmedell on 2008-06-19
I too had to use WEP open. 

I made up my own 128 bit hex key. A hex key uses numbers 0 thru 9and letters A thru F and is not case sensitive.... anyway with the key you should not need to use the mac address allow disallow feature unless your ISP requires your mac address. 

As far as your AP goes the key is your pass. The key makes your packets secure and appear scrambled to any packet sniffers.

I looked at a screen shot of your routers' set up for wireless... WEP open probably isn't working because the key from you computer and the key the router is looking for don't match. You can choose the custom encryption key and enter one and make sure that it is the same one you are putting into the network manager GUI. If you want to use the default key then find out what it is and put that one in the NM GUI.  And it appears you would have the option to make up your own key if you choose.
[http://www.fone.net/~techs/dsl/qwest/2wireadvanced.html#wireless]("http://www.fone.net/~techs/dsl/qwest/2wireadvanced.html#wireless").

You just need to make sure that the key you choose matches the one you put in the network manager. Wether it is the default key or a custom one.

---

### Post by Peter K Nicol on 2008-06-20
Have you tried this?  [http://ubuntuforums.org/showthread.php?t=830762](http://ubuntuforums.org/showthread.php?t=830762)
I know it is not that secure but if you change the password on your router to something more secure than password it may not be too bad.

Peter

---

### Post by juiceman on 2008-06-20
I used the WEP 64/128 HEX and it worked without doing anything strange! 

I'm guessing the majority of my flaws in this case were either hardware limitations or the strange case where WEP Open (not specifically hex) didn't allow the simple passkeys i made, but now specifically using HEX it works fine.

interesting.  Thanks for the help guys

---

### Post by chili555 on 2008-06-20
From *man iwconfig:*>  To set the current encryption key, just enter the key in hex digits as XXXX-XXXX-XXXX-XXXX or XXXXXXXX.  To set  a key other than the current key, prepend or append [index] to the key itself (this won&#8217;t change which is the active key). You can also enter the key as an ASCII string by using the  s:  prefix.  Passphrase  is    currently not supported.

---

