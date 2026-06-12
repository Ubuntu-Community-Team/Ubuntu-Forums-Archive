---
title: "NYU Wireless (updated)"
date: 2008-07-28
forum: Networking &amp; Wireless
---

### Post by juliansuddaby on 2008-07-28
** updated Sep 4 2009 **

Things keep changing! On my new laptop with a fresh install of Jaunty, I can connect to the "nyu" WPA2 network with the standard Network Manager (hidden network, wpa2 enterprise with username & password). This, however, occasionally drops connection for no reason, so I installed wicd and that works fine with encryption settings on "PEAP with GTC". No need for certificates! Stable.

Check the rest of the posts in this thread if you're having problems. #14 is particularly helpful:
[http://ubuntuforums.org/showpost.php?p=7510578&postcount=14](http://ubuntuforums.org/showpost.php?p=7510578&postcount=14)

** Older versions: This works with Gutsy, but not with Intrepid **

To connect you need to go to the network manager (usually on the top bar) where you select wireless networks, click the left mouse button and select 'connect to other wireless network'.

Select 'WPA2 Enterprise' for a 'Wireless Security', and a whole bunch of new options will appear.

Network Name is 'nyu'
EAP Method is PEAP
Key Type: Automatic (or, I believe, AES)
Phase2 Type is MSCHAPv2
Identity is your NYU NetID (eg. js123 -- don't include the @nyu.edu )
Password is your NetID password.

Anonymous Identity, Client Certificate File, CA Certificate file, Private Key File, and Private Key Password should be left blank.

It then should work fine. If it does, do let NYU IT services know about it...

---

### Post by mediamind on 2008-09-10
juliansuddaby,

These instructions worked perfectly for me - thanks very much!

---

### Post by bongtothesoo on 2008-09-15
wow and i thought i was probably the only one using ubuntu at nyu. thanks a bunch this is really awesome

---

### Post by soro2005 on 2008-09-20
Does this work for anyone at Bobst. I've been trying for months now, from all sorts of different locations, and the only thing I ever get is a very short and spurious connection that breaks up almost as soon as it is established. And that's usually after like 20 attempts at least.

NYU-ROAM3 with vpnc is still by far the most stable way for me to connect to the network. Thank god they haven't switched it off.

---

### Post by mbs348 on 2008-09-29
Hi, I can't seem to get this to work... I can log into NYU-ROAM2 via leap, but it is really annoying...

I too have tried in a variety of places, but I can't seem to ever get on to nyu


Also, for the previous poster who got the vpn to work, care to share your config file for how to set up vpn access....the difference in verbiage is really throwing me off.

Thanks,

Max

---

### Post by soro2005 on 2008-09-30
I'm using the network-manager-vpnc 0.6.4. So from the network manager --> vpn connections, it's

Gateway: vpn.nyu.edu
Group Name: nyu-vpn

On the Optional tab, select Override user name and enter your NetID. On connect, you will be asked two passwords (one group, one your own). The Group password is: nyu-net

I think that's all. Has been working great and stable lately around Bobst. You have to be connected to NYU-ROAM3, of course.

There is one hitch: If my Network-Manager tries to autoconnect to NYU-ROAM3, it always identifies some encryption method and asks me for a secret. I can connect reliably by being quick, before the autoconnect kicks in, or if it is too late, by restarting the network manager:
```
sudo /etc/init.d/network-manager force-reload
```
and then quickly connecting manually (Connect to Other Wireless Network). I don't know why that is, there may be some residual configuration which I haven't yet spotted.

---

### Post by mediamind on 2008-11-26
I'm running Intrepid on an MSI Wind and have recently replaced Network Manager with Wicd (1.5.3) using these instructions: [http://wicd.sourceforge.net/download.php](http://wicd.sourceforge.net/download.php) 

I've only tested it in a couple of buidings on campus (e.g. Starbucks on the square) but so far Wicd seems to work well with the "nyu" hidden network and even reconnects consistently after reboot or suspend. It also works well with my WPA2 network at home. 

A couple of things Fyi:

1. This version of Wicd (1.5.3) adds an entry in Startup programs (System => Preferences => Sessions) to automatically launch the wicd tray icon. After installing Wicd, you'll need to reboot or log out (Ctrl + Alt + Backspace) in order to launch the wicd tray icon for the first time.

2. When I click on the wicd tray icon to open the Wicd Manager, the Wicd Manager window often goes gray while scanning for networks  (sometimes a message window even pops up indicating that the program is not responding). This whole process takes 10-12 seconds - just wait it out and everything will be good.  

3. To connect to the nyu network using Wicd, click on the wicd wireless icon at the top of your screen to open the Wicd Manager. Click on the arrow beside "Network" and select "Hidden Network." Enter "nyu" (without the quotes) in the "Hidden Network ESSID" box. Click "Add" and wait while the Wicd Manager rescans the available networks. 

Next, click on the triangle beside the nyu network with the best signal (Wicd Manager may pick up more than one "nyu" network) and then click on the "Advanced Settings" button. Click the "Use Encryption" box and select "PEAP with GTC" from the dropdown menu. Enter your NYU ID and password. Click OK and then press the "Connect" button.

Assuming everything works and you successfully connect, go back to the nyu network entry in the Wicd Manager and click on the triangle to display more options. Check the "Automatically connect to this network" box. You should now automatically connect to the nyu network each time you're within range. 

Note: I've noticed that reconnecting to the nyu wireless network can take anywhere from 10-45 seconds.

---

### Post by Gaccm on 2008-12-05
Just to add my 2 cents. I had tried for months to get a solid connection with the default network manager and always i either 1) couldn't connect, or 2) I would get kicked off after 5-15min. 
I recently tried Wicd and with that I have gotten a solid connection every time.

Getting it to work was a little tricky. First, do step 3 as Mediamind says, but that wont necessarily only show you the nyu wireless signals for some reason. 
Then find any that are secured "WPA2" Choose settings and select encryption: PEAP + GTC. Type in your username and password and give it a while (a full minute) and it should connect. 

After the first time, I've never had problems. Now, I'm not using a CA certificate, so I can't vouch for how secure this method is, but it's a reliable connection which makes me happy.

---

### Post by juliansuddaby on 2009-01-03
I upgraded to Intrepid and my previously fine WPA2 connection to 'nyu' no longer worked.

One option that seems to be working for me right now is to connect to NYU-ROAM2 using LEAP wireless security (standard username and password). Seems fairly reliable right now. Clearly the problem here is with GNOME Network-Manager -- there's a whole bunch of bug reports listed on Intrepid and WPA2/PEAP etc.

I couldn't get the NYU-ROAM3 & VPN working, for whatever reason.

---

### Post by zulnov on 2009-02-15
I've been having to install linux back and forth and I always tend to forget the different steps needed to install the wireless network at NYU so I wrote a little script that gets the certificate, puts it in the right place and tells you what to do in the Network Manager or Wicd (that I highly recommend by the way).

Hope this helps someone eventually,

---

### Post by soro2005 on 2009-02-15
> **juliansuddaby said:**
> I upgraded to Intrepid and my previously fine WPA2 connection to 'nyu' no longer worked.

One option that seems to be working for me right now is to connect to NYU-ROAM2 using LEAP wireless security (standard username and password). Seems fairly reliable right now. Clearly the problem here is with GNOME Network-Manager -- there's a whole bunch of bug reports listed on Intrepid and WPA2/PEAP etc.

I couldn't get the NYU-ROAM3 & VPN working, for whatever reason.

At Bobst, I can connect to NYU_ROAM3 if I restart the network manager (sudo /etc/init.d/network-manager force-reload) and then immediately do a manual connect before the network manager recognizes the network. For some reason, the network manager always identifies the network as encrypted and asks for a secret. Once I am connected to NYU_ROAM3, I can log into the VPN without any problem. I've never been able to connect to the new nyu at Bobst, although at some other places around the campus it works. I think that the problem is that those access points just offer too many different connection methods at the same time, which seems to be seriously confusing for poor network manager. It's a shame.

I've found out, however, that it's now very very very easy to register your computer for use of the wired network that's still around at Bobst on some floors. You just plug in the cable, try to go somewhere with your browser, and are prompted to register the computer. You fill in your netid and password, and in no time you're set up. Not like in the past when you had to file a written petition for each network card you wanted to use.

---

### Post by irtx92 on 2009-04-13
> **zulnov said:**
> I've been having to install linux back and forth and I always tend to forget the different steps needed to install the wireless network at NYU so I wrote a little script that gets the certificate, puts it in the right place and tells you what to do in the Network Manager or Wicd (that I highly recommend by the way).

Hope this helps someone eventually,

zulnov,

Does your script configure for the NYU-ROAM(X) networks or the nyu network? I have NYU-ROAM working at the moment using vpnc. Should I bother fiddling around?

Thanks,
irtx92

---

### Post by zulnov on 2009-04-13
This is for direct connection to the NYU Wifi Network. No VPN needed here.

---

### Post by jawahar on 2009-06-24
I can connect to the "nyu" network using WPA2 enterprise every time and get a stable connection. The connections is authenticated using the Verisign Class 3 Public certificate as well.

**_Networking setup:_**
1. Follow the instructions in [post #1]("http://ubuntuforums.org/showpost.php?p=5474220&postcount=1") of this thread
2. For the CA certificate, select the "Verisign_Class_3_Primary_Public_Certification_Authority.pem" file from the /usr/ssl/certs directory

**_How to Connect_**
1. You will initially not see an "nyu" network. If there is one and you try to select it, you might be asked for a WEP key. Ignore this connection.
2. Select "Connect to Hidden Wireless Network" from the network manager icon and select the nyu profile you created. Click Connect.
3. **_After 10-20 seconds, the connection attempt will fail and bring up the connection settings window. This is normal. Do not try to connect again, click cancel_**
4. Go back to the Network Manager icon and you will notice a new "nyu" entry. Select this entry and enjoy your connection.


**_My computer setup:_**
Del M1330
Broadcom wireless chip (requires proprietary wl drivers)
kernel 2.6.28-13 (previous versions probably work)
Gnome using network manager


**_Note:_** If the above instructions do not work for some reason, try the other class 3 certificates, or download the certificate as given in this previous post:
[http://ubuntuforums.org/showthread.php?t=636986](http://ubuntuforums.org/showthread.php?t=636986)

---

### Post by ShadowWraith on 2010-09-08
Thank you all, this worked for me, just one note:

In ubuntu 10.04, ssl certificates are located in
```
/etc/ssl/certs
```
The
```
Verisign_Class_3_Public_Primary_Certification_Authority.pem
```
certificate works fine

---

### Post by mediamind on 2010-09-24
Thanks everyone for the great tips. I'm running 10.10 Beta and have successfully connected to the nyu network numerous times over the last couple of weeks. Here's what has worked for me...

**1.** Click on your Network Manager icon at the top right of the screen and select: Connect to Hidden Wireless Network...

**2.** Under "Wireless security" select: WPA & WPA2 Enterprise

**3.** A new window will pop up - complete the fields using the following parameters:

Connection: New...
Network Name: nyu
Wireless security: WPA & WPA2 Enterprise
Authentication: PEAP
Anonymous Identity: n/a
CA certificate: Verisign_Class_3_Public_Primary_Certification_Authority.pem
*Note: In Ubuntu 10.10, ssl Certificates are found in: /etc/ssl/certs
PEAP version: Automatic
Inner authentication: MSCHAPv2
Username: your NYU NetID (eg. dd123 - don't include the @nyu.edu) 
Password: your NYU NetID password.

**4.** Once the fields are completed, click the "Connect" button and wait 20 or so seconds. You should now be connected to the "nyu" network. Begin surfing...and if all goes well, the next time you open your computer on campus, your system should automatically join the "nyu" network.

---

