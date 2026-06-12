---
title: "vodafone k3565 dongle problems"
date: 2011-08-11
forum: New to Ubuntu
---

### Post by Dermot Doyle on 2011-08-11
Hi All,
I've spent days trying to get this dongle to work on 10.04. I have read countless forums, followed often completely contradictory advice, downloaded things and have just about given up. My Dell Inspiron 1525 usually recognises it (I once had to restart with the dongle already plugged in) and it has a green light which flashes twice every 3 seconds or so. I think this means it has found a network, but isn't connected. Is that true? The dongle was given to me so I don't know if there is any sort of setting already in there that I can't over ride that is causing a problem. Can any one help someone not very computerate to get it going? Feel free to post links to other threads, but I can almost guarantee I've already seen it to no avail. Also feel free to suggest that I am being mean trying to get a used dongle to work on Ubuntu and it would be quicker and easier to give up.
Cheers

---

### Post by Daveth on 2011-08-11
side-stepping the issue, anything useful on here?
[HTML]http://www.betavine.net/bvportal/resources/datacards[/HTML]

---

### Post by Dermot Doyle on 2011-08-11
Hi,
Any idea why this site comes up as untrustworthy and Firefox tries to get me to abandon an attempt to enter it?

---

### Post by Dermot Doyle on 2011-08-12
Right, I went to that site and installed the packages. Now when I try to run from the terminal I get:

get_plugin_by_vendor_product_id called with 0x12D1 and 0x1003
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/twisted/application/app.py", line 693, in run
    runApp(config)
  File "/usr/lib/python2.6/dist-packages/twisted/scripts/twistd.py", line 23, in runApp
    _SomeApplicationRunner(config).run()
  File "/usr/lib/python2.6/dist-packages/twisted/application/app.py", line 411, in run
    self.application = self.createOrGetApplication()
  File "/usr/lib/python2.6/dist-packages/twisted/application/app.py", line 494, in createOrGetApplication
    application = getApplication(self.config, passphrase)
--- <exception caught here> ---
  File "/usr/lib/python2.6/dist-packages/twisted/application/app.py", line 505, in getApplication
    application = service.loadApplication(filename, style, passphrase)
  File "/usr/lib/python2.6/dist-packages/twisted/application/service.py", line 390, in loadApplication
    application = sob.loadValueFromFile(filename, 'application', passphrase)
  File "/usr/lib/python2.6/dist-packages/twisted/persisted/sob.py", line 210, in loadValueFromFile
    exec fileObj in d, d
  File "/usr/share/vodafone-mobile-connect/gtk-tap.py", line 44, in <module>
    ensure_have_config()
  File "/usr/share/vodafone-mobile-connect/vmc/common/startup.py", line 70, in ensure_have_config
    from vmc.common.oal import osobj
  File "/usr/share/vodafone-mobile-connect/vmc/common/oal.py", line 44, in <module>
    osobj = get_os_object()
  File "/usr/share/vodafone-mobile-connect/vmc/common/oal.py", line 38, in get_os_object
    if osplugin.is_valid():
  File "/usr/share/vodafone-mobile-connect/vmc/common/oses/linux.py", line 120, in is_valid
    from vmc.common.hardware.hardwarereg import hw_reg
  File "/usr/share/vodafone-mobile-connect/vmc/common/hardware/hardwarereg.py", line 27, in <module>
    from vmc.common.hardware._unixhardwarereg import hw_reg
  File "/usr/share/vodafone-mobile-connect/vmc/common/hardware/_unixhardwarereg.py", line 474, in <module>
    hw_reg = HardwareRegistry()
  File "/usr/share/vodafone-mobile-connect/vmc/common/hardware/_unixhardwarereg.py", line 122, in __init__
    d = self.get_devices()
  File "/usr/share/vodafone-mobile-connect/vmc/common/hardware/_unixhardwarereg.py", line 151, in get_devices
    d = self._get_devices_from_udis(parent_udis)
  File "/usr/share/vodafone-mobile-connect/vmc/common/hardware/_unixhardwarereg.py", line 184, in _get_devices_from_udis
    unknown_devs = map(self._get_device_from_udi, udis)
  File "/usr/share/vodafone-mobile-connect/vmc/common/hardware/_unixhardwarereg.py", line 177, in _get_device_from_udi
    device = self._get_device_from_info_and_ports(info, udi, ports)
  File "/usr/share/vodafone-mobile-connect/vmc/common/hardware/_unixhardwarereg.py", line 392, in _get_device_from_info_and_ports
    dport, cport = probe_ports(ports)
  File "/usr/share/vodafone-mobile-connect/vmc/common/hardware/_unixhardwarereg.py", line 70, in probe_ports
    if probe_port(port):
  File "/usr/share/vodafone-mobile-connect/vmc/common/hardware/_unixhardwarereg.py", line 56, in probe_port
    raise RuntimeError('Port %s not available: check permissions' % port)
exceptions.RuntimeError: Port /dev/ttyUSB0 not available: check permissions

Failed to load application: Port /dev/ttyUSB0 not available: check permissions

Does anyone know what this means? If I try to connect from Applications-internet-Vodaphone Internet Connect it says it is starting, but nothing happens.

---

### Post by Dermot Doyle on 2011-08-14
I'll give up, shall I?

---

### Post by alexfish on 2011-08-14
Hi

the k3565 has proved to be a problematic device , (multiple ports registering during switching) may be more than one device registering on the system . but should work with ubuntu versions 10.10 onwards ,

ADDED: can have a look at this site with reference to VMC ,, "Look at the permisions"
[Vodafone Mobile Connect Software]("http://www.pcurtis.com/ubuntu-mobile.htm#vmc")

can also try sakis3g

have a look through 

[How To : Mobile Broadband Connections [ Ubuntu 10.10 : 10.04 : 9.10 ]]("http://ubuntuforums.org/showthread.php?t=1466490") 

regards
alexfish

---

### Post by snip3r8 on 2011-08-14
Have you tried using wvdial to connect?

---

### Post by Dermot Doyle on 2011-08-14
Hi Alexfish, thanks for the link to the thread, I think it has answered my question if not in the way meant. I understand little of most of the questions asked and less of the answers. I can cut and paste things and have used the terminal with some success, but reading the thread (yes, all 6 pages of it) I could see that I was in way over my head. My understanding of computers is not much past the works-out-of-the-box, plug-and-play level and I know when I am beaten. Please don't think I don't appreciate the help on offer on this forum. I have usually had success with solving my problems, but I have to accept it is the nature of open source software that it has its problems as does micrsoft and apple. We simply choose what we are willing to compromise on and Ubuntu is still the best system for me.
Thanks again to everyone who offered advice.
Cheers

---

### Post by BongMasteR on 2011-08-14
Dermot, I can tell that you've given up, but I also had endless problems with my k505 unit on 11.04 Natty. Then a friend installed [sakis3G]("http://www.sakis3g.org/") for me. Problem solved. 

use it, don't use it

---

### Post by Dermot Doyle on 2011-08-14
Damn, BongMasterR you've sucked me back in. I tried to download Sakis3G before without success, but this time I have done it properly. Now when I try to get it to connect with 3G I get:
Port /dev/ttyUSB0 is currently occupied by 821 modem-manager. and then failed to connect.
I have no idea what this means, but I think I may be close. Any ideas?
Cheers

---

### Post by gandaran on 2011-08-14
> **Dermot Doyle said:**
> Damn, BongMasterR you've sucked me back in. I tried to download Sakis3G before without success, but this time I have done it properly. Now when I try to get it to connect with 3G I get:
Port /dev/ttyUSB0 is currently occupied by 821 modem-manager. and then failed to connect.
I have no idea what this means, but I think I may be close. Any ideas?
Cheers
maybe you have 3G setup connections using other methods so ensure you have removed them before trying sakis3G
for network manager remove every setup in the mobile broadband tab and try remember what else you tried.

and just a note, I think your modem should work with network manager on ubuntu 10.04 if you have usb-modeswitch installed and ubuntu fully updated.

---

### Post by Dermot Doyle on 2011-08-14
Hi gandaran, thanks for the reply.
I have usb-modeswitch installed and the computer is fully updated. I took a chance and went to synaptic package manager and removed modem manager and now I get sakis3G to get as far as trying to register the network and failing. Then it offers a manual choice and I choose vodaphone uk (available) and the percentage climbs a bit and stops. I manually select vodaphone uk again and after repeating this a few times I get up to 97%. The next time I go back to 0% and nothing further happens. The dongle has a flashing green light which I thought meant that it had found a network and I assumed it was the network it was designed for.
Any ideas anyone?

---

### Post by Dermot Doyle on 2011-08-14
I think I just spotted my mistake for what it's worth. I found an instruction book on the internet for the vodafone k3565 and the green flashing light says that the dongle has found a GPRS signal, not a 3G one. Well I did say I wasn't very good at this.
Thanks for all the advice anyway.

---

### Post by gandaran on 2011-08-14
> **Dermot Doyle said:**
> I think I just spotted my mistake for what it's worth. I found an instruction book on the internet for the vodafone k3565 and the green flashing light says that the dongle has found a GPRS signal, not a 3G one. Well I did say I wasn't very good at this.
Thanks for all the advice anyway.
yes, the flashing light is just an indication it found the mobile signal (not sure if it's just GPRS) but even if you just have GPRS in your area it should still connect only you would have a slow working internet so that is not the problem, I think you still have a vodafone login authentication issue, I haven't tried sakis3G so I don't know how it works but I would have a look at the login details like APN and authentication handshake if they are the correct ones your ISP uses.

---

### Post by alexfish on 2011-08-15
> **Dermot Doyle said:**
> Damn, BongMasterR you've sucked me back in. I tried to download Sakis3G before without success, but this time I have done it properly. Now when I try to get it to connect with 3G I get:
Port /dev/ttyUSB0 is currently occupied by 821 modem-manager. and then failed to connect.
I have no idea what this means, but I think I may be close. Any ideas?
Cheers

the modem-manager may be holding onto the port , start sakis3g , do not connect, open up a terminal and enter this command
```
sudo killall modem-manager
```then start the connection with sakis3g

Added:
Note if the device is Huawie(k3565) then it should be recognized by the kernel , IE does not require usb_modeswitch, but has a inherent fault
that been if the device shows on the desktop and the user ejects the device then the ports will register in reverse order, (modem-manager will try to connect to the wrong port) do not eject the device, can safely remove the device sometimes works depending on the kernel version , yet can sometimes remount, as mentioned more than one device can register on the system.

you will have to be patient with this device , as said it is a problematic device.

alexfish

---

### Post by Dermot Doyle on 2011-08-15
Hi,
Since my last post I have got as far as sakis3G trying to connect twice,failing, then giving up. I suspect that it is now down to the settings in the dongle. As I said in the begining it was given to me and we are unsure of the user name and password. I have tried allthe possible variations we could think of plus the ones suggested on the internet ie. web and web. Is it possible to reset the dongle to factory settings and start again?

---

### Post by gandaran on 2011-08-16
> **Dermot Doyle said:**
> Hi,
Since my last post I have got as far as sakis3G trying to connect twice,failing, then giving up. I suspect that it is now down to the settings in the dongle. As I said in the begining it was given to me and we are unsure of the user name and password. I have tried allthe possible variations we could think of plus the ones suggested on the internet ie. web and web. Is it possible to reset the dongle to factory settings and start again?
hi
I still think the problem is the authentication details, I'm using ubuntu 11.04 so I don't know if ubuntu 10.04 has the same updated packages, I tried the network manager mobile broadband wizard here, choose UK and vodafone and it surprised me as I thought vodafone settings where standard worldwide, well vodafone in UK it seams is in fact "airtel vodafone" and APN is "airtel-ci-gprs.com" so check sakis3g if the same applies and try the network manager too, I'm sure if you have the right login details in network manager it will work, mobile internet doesn't use usernames or passwords, you just have to have the right APN to connect.

edit
if the dongle was given to you do you know if the account is still active?

---

### Post by Dermot Doyle on 2011-08-16
Thanks for the continuing help. I used the set up wizard and chose airtel vodafone and let it set the APN you mentioned as default. In fact the plan on the dongle is 'Top up and Go' which isn't listed under airtel vodafone. Whatever, I got the same result. Then I got rid of the username and password, the IPv4 settings I found on the internet, reset the username and password as 'web' and 'web' respectively, one at a time. Still no joy. Now I don't know whether to set it to vodafone and top up and go or airtel vodafone for the best chance of getting it to work.
Finally, you're right, I don't know if the account is active. Will they cancell a top up and go dongle account even though with vodafone there is no time limit on using your credit (why my friend bought it in the first place)?

---

### Post by gandaran on 2011-08-16
hi again
I have been googling your modem K3565 and it seams it really works fine on ubuntu 10.04 according to this 
[http://www.kickenhardware.net/showthread.php?19274-K3565-Mobile-Broadband-dongle-on-Ubuntu-Netbook-Remix](http://www.kickenhardware.net/showthread.php?19274-K3565-Mobile-Broadband-dongle-on-Ubuntu-Netbook-Remix)

> Then I got rid of the username and password, the IPv4 settings I found on the internet, reset the username and password as 'web' and 'web' respectively, one at a time. Still no joy. Now I don't know whether to set it to vodafone and top up and go or airtel vodafone for the best chance of getting it to work.
you are trying to many things, everything should be kept blank as in default setup, only the dial out number and APN is needed and must be right APN, some mobile operators require different APN for different internet plans, maybe your prepaid (top up) internt plan uses a custom APN.
you can also try with blank APN, this also works but for some mobile operators.

---

### Post by Dermot Doyle on 2011-08-16
Hi gandaran,
Yes, I tried the betavine software before without success. I gave it one last shot and uninstalled it all and started again following the advice there. No joy I'm afraid. I think that's it for me. Thanks to you and everyone who tried to help, but it's all become too frustrating and I worry my life is ebbing away as I go goggle eyed.
Thanks again.

---

### Post by HarriU11-04 on 2011-09-01
> **Dermot Doyle said:**
> Hi gandaran,
Yes, I tried the betavine software before without success. I gave it one last shot and uninstalled it all and started again following the advice there. No joy I'm afraid. I think that's it for me. Thanks to you and everyone who tried to help, but it's all become too frustrating and I worry my life is ebbing away as I go goggle eyed.
Thanks again.
Hello Dermot

Just found your thread. I too have a Vodafone K3565, but I use it on Ubuntu 11.04. I too went trough a frustrating time of getting the blasted thing to work in linux. If your game, you can try what I tried (bearing in mind I'm using Natty). Also, I'm on PAYG 3G broadband:-

1. Boot into linux with the modem already attached. 
2. Create NetworkManager MobileBroadband connection

NetworkManager settings:
Country: United Kigdom
Provider: Vodafone (*NOT* "Airtel vodafone", which appears at the top since providers are listed alphabetically)
The APN you will have to enter this manually, as Pre-paid and PAYG settings were wrong for me
APN: pp.internet
IPv4 tab. Automatic (PPP) addresses only. Set DNS servers here, separated by a comma: 208.67.222.222,208.67.220.220 (OpenDNS)
Mobile Broadband tab
Basic section. Number: *99***3#
Username: web Password: web
Advanced section. APN: pp.internet

"Connect automatically" and "Available to all users" were selected2.

3. Check that Network Manager has updated /etc/resolv.conf to contain DNS nameservers.

Open up firefox and try to browse

Good luck!

---

