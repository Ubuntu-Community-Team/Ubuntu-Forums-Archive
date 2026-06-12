---
title: "hp pavillion laptop wireless disabled"
date: 2007-04-09
forum: Networking &amp; Wireless
---

### Post by whitea on 2007-04-09
I am new to Ubuntu and so far I love it.  I am having difficulty using my wireless card.  It is detected but as I read in the troubleshooting guide some laptops(like mine) have an enable/disable button and I am unable to enable it.  Any help would be greatly appreciated!!

Andrew

---

### Post by rolando on 2007-04-09
what model is the laptop, is it here  [http://tuxmobil.org/hp.html](http://tuxmobil.org/hp.html)

how about using ifup, iwconfig, ifconfig to see if your adapter is up

Alternatively insall nm-applet from the DVD.

:)

---

### Post by whitea on 2007-04-09
Thanks for the help.  I am very, very new, so please bare with me!  My laptop is listed on the page you linked.  I am slightly (when I say slightly, I mean very!) unfamiliar with the terminal commands.

Andrew

---

### Post by whitea on 2007-04-09
Rolando,

it is an hp pavillion zv5000.

---

### Post by whitea on 2007-04-09
> **rolando said:**
> what model is the laptop, is it here  [http://tuxmobil.org/hp.html](http://tuxmobil.org/hp.html)

how about using ifup, iwconfig, ifconfig to see if your adapter is up

Alternatively insall nm-applet from the DVD.

:)
Rolando,

Also, although it is listed on the page you linked, the ubuntu distro is not listed?

Thanks,
Andrew

---

### Post by whitea on 2007-04-09
More info.  This is what I get when I use the terminal.  Where can I go from here?

whitea@whitea-laptop:~$ sudo ifdown eth1
Password:
ifdown: interface eth1 not configured
whitea@whitea-laptop:~$ sudo iwconfig eth1
eth1      IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4306"
          Mode:Managed  Access Point: Invalid   
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

Any help would be greatly appreciated!

---

### Post by sabi on 2007-04-09
We can get your wireless card working in just a few minutes.

From a terminal type the following:

```
sudo iwconfig
```

Post the results.

Sabi

---

### Post by whitea on 2007-04-09
This is what shows up:

whitea@whitea-laptop:~$ sudo iwconfig
Password:
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4306"
          Mode:Managed  Access Point: Invalid   
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

---

### Post by rolando on 2007-04-09
I would always use network-admin before I start mucking around with the command line.

We want Ubuntu to be as easily configurable as Windows, so no command line unless absolutely necessary.

at a terminal type

```
sudo network-admin
```

have go in there, see if you card is listed and if it is enable it.  Dont forget to put your routers IP address in the DNS tab.

If not you will have to roll up your sleeves and get your hands dirty.

Here is a good site: [http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_activate.2Fdeactivate_network_connections](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_activate.2Fdeactivate_network_connections)

:)

---

### Post by sabi on 2007-04-09
> **whitea said:**
> This is what shows up:

whitea@whitea-laptop:~$ sudo iwconfig
Password:
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4306"
          Mode:Managed  Access Point: Invalid   
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

Well, your card is recognized and driver loaded. 
What release are you using, Ubuntu, Kubuntu, Xbuntu?
What release version, Dapper, Edgy, Feisty?

Subi

---

### Post by whitea on 2007-04-09
Subi,

I am using Ubuntu Edgy 6.10

---

### Post by whitea on 2007-04-09
> **rolando said:**
> I would always use network-admin before I start mucking around with the command line.

We want Ubuntu to be as easily configurable as Windows, so no command line unless absolutely necessary.

at a terminal type

```
sudo network-admin
```

have go in there, see if you card is listed and if it is enable it.  Dont forget to put your routers IP address in the DNS tab.

If not you will have to roll up your sleeves and get your hands dirty.

Here is a good site: [http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_activate.2Fdeactivate_network_connections](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_activate.2Fdeactivate_network_connections)

:)
I just tried.  Sure enough the device was not enable so i clicked the checkbox.  However it still does not work.  When I return it is again disabled.

---

### Post by sabi on 2007-04-09
> **whitea said:**
> Subi,

I am using Ubuntu Edgy 6.10

In the upper left corner, in the system tray click-on:

System>Administration>Network

Do you see 3 entries? Does the wireless entry indicate it has roaming enabled?

Sabi

---

### Post by whitea on 2007-04-09
> **sabi said:**
> In the upper left corner, in the system tray click-on:

System>Administration>Network

Do you see 3 entries? Does the wireless entry indicate it has roaming enabled?

Sabi
I do see three entries but I am not sure how to tell whether roaming is enabled.

---

### Post by sabi on 2007-04-09
> **whitea said:**
> I do see three entries but I am not sure how to tell whether roaming is enabled.

Look under the line labeled "Wireless connection", what do you see ?

Sabi

---

### Post by whitea on 2007-04-09
> **sabi said:**
> Look under the line labeled "Wireless connection", what do you see ?

Sabi
The connection is checked off and it says Essid: Whitehouse Address: DHCP

---

### Post by whitea on 2007-04-09
> **whitea said:**
> The connection is checked off and it says Essid: Whitehouse Address: DHCP
[IMG]desktop\screenshot.png[/IMG]

---

### Post by whitea on 2007-04-09
> **whitea said:**
> [IMG]desktop\screenshot.png[/IMG]
I'm not really sure how to post the screenshot.  Sorry.

---

### Post by whitea on 2007-04-09
Sabi and Rolando,

Thank you so much for your help so far!!  As a newbie I have much much to learn and I really appreciate your patience with me.

I am still unable to get my wireless working but I am optistic that it can be done.  I have read that sometimes it is necessary to load the windows driver (there is a section in the installation notes on this).  Is this a good idea?  

I only hope I can get this working soon.  I have to connect to my internet directly from the router and it is cold in the basement!!!:)  I am trying to get away from windows but it is much nicer to work on the couch under a warm blanket.:lolflag:

---

### Post by whitea on 2007-04-14
Well, I finally did it!!  I am posting this using Ubuntu and accessing the Internet wirelessly!!  It is thanks to many very smart members of this community who helped me through it.  I am a newbie through and through but I am learning and that is the important thing.  I learned that there are two basic ways to enable a Broadcom wireless card that is common in HP and Dell laptops.  The first is with the bcm43xx driver which did not work for me.  The second way is by using ndiswrapper and importing the driver over from windows (which I did) or downloading it from the various threads in this forum.  I am linking to both methods as one way may work better for some and not for others.

These are the very helpful postings that got me through:

[http://ubuntuforums.org/showthread.php?t=201902]("http://ubuntuforums.org/showthread.php?t=201902") (this is the one that worked for me!!)
[http://ubuntuforums.org/showthread.php?t=25683]("http://ubuntuforums.org/showthread.php?t=25683")
[http://ubuntuforums.org/showthread.php?t=185174]("http://ubuntuforums.org/showthread.php?t=185174")


One other tip if you have the same model laptop as I do (HP Pavillion zv5000).  The wireless indicator button above the function keys does not always remain lit (as it does in Windows).  I had it working earlier in the process but didn't think it worked because I expected it to remain lit.  I wasted a lot of time trying to figure that out!


Thanks again to everyone who contributes to this forum.  I look forward to using Ubuntu and learning more and more about how to extend it's functionality to meet my needs.  So far I cannot say enough good things about this OS! 

:guitar:

---

