---
title: "HP Compaq nx9010 wireless"
date: 2007-11-24
forum: Networking &amp; Wireless
---

### Post by rhydz on 2007-11-24
I have installed gutsy on a HP Compaq nx9010 and i cant get wireless working. Has anyone got it working? If so what steps did u take?

---

### Post by mouseboyx on 2007-11-24
Install ndiswrapper from the synaptic or
```
sudo apt-get install ndiswrapper
```and ndisgtk if you need a GUI
```
sudo apt-get install ndisgtk
```and the driver probably requires wine to extract because it an exe (Windows executable) so install wine
```
sudo apt-get install wine
```Download the driver for the HP Compaq nx9010 Laptop here:

[http://h20000.www2.hp.com/bizsupport/TechSupport/SoftwareDescription.jsp?lang=en&cc=us&prodTypeId=321957&prodSeriesId=321850&prodNameId=321852&swEnvOID=1093&swLang=8&mode=2&taskId=135&swItem=ob-26984-1](http://h20000.www2.hp.com/bizsupport/TechSupport/SoftwareDescription.jsp?lang=en&cc=us&prodTypeId=321957&prodSeriesId=321850&prodNameId=321852&swEnvOID=1093&swLang=8&mode=2&taskId=135&swItem=ob-26984-1)

Extract the driver using 
```
wine [drag n' drop the exe file here]
```If you use default options it should extract to 
~/wine/drive_c/SWSetup/SP29361A

now follow this howto using the drivers and software you got
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

sorry for the painful setup, but your learning!

---

### Post by rhydz on 2007-11-25
i got everything installed package wise.

wine reported errors when extracting the drivers but the files extracted anyways so ignored it. followed how didnt help at all. i get the lost of wireless networks. but i cannot connect to mine,

my network is wpa tk. went through wpa wizard but no luck. any ideas?

---

### Post by rhydz on 2007-11-25
interesting discovery i think my wireless card is prism 2,5 here's the lspci:

00:09.0 Network controller: Intersil Corporation Prism 2.5 Wavelan chipset (rev 01)

if i since done a clean re-install to get rid of all the changes i have made to try get it work. so far here is my clean iwconfig (please note i am on this laptop now using a wired connection):

rhydz@w-usa-kubuntu:/etc$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     IEEE 802.11b  ESSID:"ABK"  Nickname:""
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:90:4C:7E:00:10
          Bit Rate:11 Mb/s   Sensitivity=1/3
          Retry short limit:8   RTS thr:off   Fragment thr:off
          Power Management:off

wlan0     IEEE 802.11b  ESSID:"ABK"  Nickname:""
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:90:4C:7E:00:10
          Bit Rate:11 Mb/s   Sensitivity=1/3
          Retry short limit:8   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=18/70  Signal level=-81 dBm  Noise level=-100 dBm
          Rx invalid nwid:0  Rx invalid crypt:1319  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:4601   Missed beacon:0

any ideas?

---

### Post by idcolvin on 2007-12-14
Hi,
I'm also looking for help with wireless on an nx9010. Have you had any luck yet? If so can you post what is needed?
Many thanks in advance.
Ian

---

### Post by mouseboyx on 2008-01-11
Lol i googled this laptop on looking on buying it to see if the wireless worked well and i found myself!
Sadly still no status.

---

### Post by wsuetholz on 2008-02-12
Try this link..  [http://davidwatson.org/2007/05/broadcom-4306-on-feisty-fawn.html]("http://davidwatson.org/2007/05/broadcom-4306-on-feisty-fawn.html") it worked for me on Gutsy.
I first did an lspci -v to determine what card was installed (BCM4306) and then did a google for "ubuntu bcm4306" to find the above link.

---

### Post by koalix on 2008-04-03
I also have a compaq nx9010 and had the same problem.

I found the solution here:

[URL="http://ubuntuforums.org/showthread.php?t=201902"]http://ubuntuforums.org/showthread.php?t=201902
[/URL]
I followed the steps and then the ones in post #746 and now I'm writing this using my wireless card!

:guitar:

---

