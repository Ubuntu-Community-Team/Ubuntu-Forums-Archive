---
title: "Dell inspiron 1501 network problems"
date: 2014-01-05
forum: Networking &amp; Wireless
---

### Post by mike24216 on 2014-01-05
Hey I am newbie to ubuntu 12.04 Lts and I installed it on my dell inspiron 1501 laptop.  I installed it with dual boot with windows vista.  I am having problems with the network.  The wired and the wireless does not work.  Can anyone help me out.  I have tried some of the post but most threads i found want you to hook up the wired connection but like I said it does not work. Thanks.

---

### Post by chili555 on 2014-01-05
Please give us more information about your ethernet and wireless devices. Please open a terminal and run and post:```
lspci -nn | grep -e 0200 -e 0280
```

---

### Post by mike24216 on 2014-01-05
mike@mike-Inspiron-1501:~$ lspci -nn | grep -e 0200 -e 0280
  05:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
  08:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
  mike@mike-Inspiron-1501:~$

---

### Post by chili555 on 2014-01-05
Please get a temporary wired ethernet connection. We are going to get it going easily in one step:```
sudo modprobe b44
sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get install linux-firmware-nonfree
```Detach the ethernet, reboot and everything should now be working.

---

### Post by mike24216 on 2014-01-05
mike@mike-Inspiron-1501:~$ sudo modprobe b44
  [sudo] password for mike:
  mike@mike-Inspiron-1501:~$ sudo apt-get remove --purge bcmwl-kernel-source
  Reading package lists... Done
  Building dependency tree       
  Reading state information... Done
  The following packages were automatically installed and are no longer required:
    fakeroot dkms
  Use 'apt-get autoremove' to remove them.
  The following packages will be REMOVED:
    bcmwl-kernel-source*
  0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
  After this operation, 4,274 kB disk space will be freed.
  Do you want to continue [Y/n]? y
  (Reading database ... 142635 files and directories currently installed.)
  Removing bcmwl-kernel-source ...
  Removing all DKMS Modules
  Done.
  update-initramfs: deferring update (trigger activated)
  Purging configuration files for bcmwl-kernel-source ...
  update-initramfs: deferring update (trigger activated)
  Processing triggers for initramfs-tools ...
  update-initramfs: Generating /boot/initrd.img-3.8.0-29-generic
  mike@mike-Inspiron-1501:~$ sudo apt-get install linux-firmware-nonfree
  Reading package lists... Done
  Building dependency tree       
  Reading state information... Done
  E: Unable to locate package linux-firmware-nonfree
  mike@mike-Inspiron-1501:~$


When I entered the first line of the code the wired connection established but toward the end it says E:unable to locate package.  Did something go wrong.

---

### Post by chili555 on 2014-01-05
> sudo apt-get install linux-firmware-nonfree
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Unable to locate package linux-firmware-nonfreePlease try this instead:```
sudo apt-get install firmware-b43-installer
```

---

### Post by mike24216 on 2014-01-05
ok tried that and still says unable to locate it.  I did the additional driver update and it found the sta driver and it said it needed to reboot and now it is stuck on a bunch of writting and it will not boot into ubuntu.  Well have to go to bed work comes early I will get back tomorrow.

---

### Post by chili555 on 2014-01-05
You do not want the STA driver! That's what is causing all these problems in the first place!! Now you've reinstalled it!

See you tomorrow...

Sigh...

---

### Post by mike24216 on 2014-01-05
ohh well that is why I am a newbie.  Sorry about that.  I will holler at you tomorrow if you are around.  I dont know what kind of mess I am in now.  I will worry about it tomorrow after work.  Thanks.

---

### Post by chili555 on 2014-01-06
> **mike24216 said:**
> ohh well that is why I am a newbie.  Sorry about that.  I will holler at you tomorrow if you are around.  I dont know what kind of mess I am in now.  I will worry about it tomorrow after work.  Thanks.I am posting this so that, perhaps, other newbies and searchers will see and heed it.

The 'Additional Drivers' tool cheerfully offers the *wrong* driver for a few Broadcom wireless cards, including your 4311. Then you get in more difficulty than just, 'my wireless won't work.' You get:> it said it needed to reboot and now it is stuck on a bunch of writting and it will not boot into ubuntu. So, newbies, search this forum for SOLVED and your pci.id, something like 14e4:4311. Follow the process in the solved thread and don't take Additional Drivers' suggestion to wreck your system.

End rant.

So, Mike, start by telling me what Ubuntu version you have:```
lsb_release -a
uname -r
```Next, hook up the ethernet and do:```
sudo modprobe b44
sudo apt-get remove -purge bcmwl-kernel-source
```You need firmware for your 4311 wireless and the best method to install it depends on your version.

---

### Post by mike24216 on 2014-01-06
Yes it is a good ideal to post for newbies so that don't make the same mistake I am in.  Ok chili555 get me back on track.  Still it will not boot into ubuntu.  What do I do now.  Do I run the live cd again and install all over.  Please let me know.  This time I will follow step by step without clicking on stuff.  Thanks.  


My dell wireless card is a 1390.

---

### Post by chili555 on 2014-01-06
To what does it boot? A command prompt? Straight to Windows, or ... what?

---

### Post by mike24216 on 2014-01-06
I have dual boot with vista and ubuntu and when I choose ubuntu it gets stuck on a bunch of writing.  I am using easybcd for the boot option.  It says something like fixing recursive fault. It has numbers out side of it 9.808731. It keeps jumping around on different numbers. Vista works fine and Ubuntu will not boot up.

---

### Post by chili555 on 2014-01-06
If you wait long enough, does it eventually boot to a command prompt?

---

### Post by mike24216 on 2014-01-06
Well I have not left it for a long time but I will If you want me too.  It just gets stuck at one point with the blinking curser.

---

### Post by chili555 on 2014-01-06
I'd give it three minutes. Is there a message showing just before it sticks? Can you jot it down and post it?

---

### Post by mike24216 on 2014-01-06
Ok it has been like 15 minutes so far. Here is the last line above the blinking curser.  


[    9.808731] ---[ end trace c187eec093527941 ]---

---

### Post by chili555 on 2014-01-06
I'd recommend a reinstall.

---

### Post by mike24216 on 2014-01-06
ok can i just stick the live cd and just hit install or is it best to format first.

---

### Post by chili555 on 2014-01-06
> ok can i just stick the live cd and just hit installYes, just be sure to watch carefully and select 'along side Windows.' If in doubt, stop and ask. We don't want to wipe out Windows by mistake.

[http://www.techotopia.com/images/7/7a/Ubuntu_11_dual_boot_resize_windows.jpg](http://www.techotopia.com/images/7/7a/Ubuntu_11_dual_boot_resize_windows.jpg)

---

### Post by mike24216 on 2014-01-06
ok thanks.  Yes i have read all of that.  Everything was going good and I was very happy with the easybcd dual boot option.  I even went into terminal and set the timeout from 10sec to 0.  The network connection was the only issue and I was going to be set.  Lesson learn now back to square one.  One more question before proceding do I need to remove the easybcd before I start the install all over or well it be fine.

---

### Post by chili555 on 2014-01-06
I think it will prompt you that the install is finished and to remove the CD so you boot from the harddrive and not the CD.

---

### Post by mörgæs on 2014-01-06
If you are going to reinstall on a 1501 I would suggest Lubuntu 13.10. Will give you a faster system than Ubuntu.

---

### Post by mike24216 on 2014-01-06
ok thanks. My inspiron 1501 does have a dual core processor.  My goal was to load ubuntu on this older laptop before I put it on my desktop.  Just to play around with it.  I have never heard of Lubuntu.  Something new to me.  I will look into it and I will decide.  I installed the ubuntu 12.04 LTS for long term support.  This is the first time for the dual boot and ubuntu.  It is all new to me.

---

### Post by chili555 on 2014-01-06
Once you get reinstalled, please shun the Additional Drivers tool. You only need firmware in addition to the built-in b43/ssb drivers.

---

### Post by mike24216 on 2014-01-06
Ok I reinstalled ubuntu 12.04 LTS.  I am now ready to get my wireless driver working.  Guide me threw this.  My wireless card is a 1390.

---

### Post by chili555 on 2014-01-06
Please get a temporary wired ethernet connection, open a terminal and do:```
sudo apt-get update
sudo apt-get install firmware-b43-installer
```Detach the ethernet, reboot and report your success.

---

### Post by mike24216 on 2014-01-06
My wired connection is not working at all.  Just tried the command and it failed.  Yesterday when I ran this command it connected do you want me to run this first.
sudo modprobe b44

---

### Post by chili555 on 2014-01-06
Yes, please.

---

### Post by mike24216 on 2014-01-06
Still no wireless.  After running this command sudo modprobe b44 wired connection established.  Then I  ran your command and everything went good.  I unplugged ethernet and reboot and still no wireless.  I do have a security enable.  Wpa security.

---

### Post by chili555 on 2014-01-06
When you click on the Network Manager icon, do you see your network? Any clues here?```
dmesg | grep b43
```

---

### Post by mike24216 on 2014-01-06
It says no network devices available.  When I run the command it does nothing.

---

### Post by mike24216 on 2014-01-06
Well it is time for bed again.  I will check tomorrow and see if you have anything for me to try.  Thanks.

---

### Post by chili555 on 2014-01-06
How about now?```
sudo modprobe b43
dmesg | grep b43
```

---

### Post by mike24216 on 2014-01-06
I ran that command and boom wireless connection established.  Now when I restart will the wireless connect or will I have to go threw this everytime.

---

### Post by mike24216 on 2014-01-06
Ok I rebooted and it would not connect on its on and it says no devices available. It wont work unless I run that command.

---

### Post by mike24216 on 2014-01-06
Here is the command results

  mike@mike-Inspiron-1501:~$ sudo modpobe b43
  [sudo] password for mike:
  sudo: modpobe: command not found
  mike@mike-Inspiron-1501:~$ sudo modprobe b43
  mike@mike-Inspiron-1501:~$ dmesg | grep b43
  [  310.782573] b43-phy0: Broadcom 4311 WLAN found (core revision 10)
  [  310.824105] b43-phy0: Found PHY: Analog 4, Type 2 (G), Revision 8
  [  311.196084] b43-phy0: Loading firmware version 508.1084 (2009-01-14 01:32:01)
  mike@mike-Inspiron-1501:~$

---

### Post by chili555 on 2014-01-07
Let's try the easy things first:```
sudo -i
echo b43  >>  /etc/modules
echo b44  >>  /etc/modules
exit
```Reboot and let us hear the result.

---

### Post by mike24216 on 2014-01-07
I did the commands you posted and it works when I reboot.  It seems like it takes it about 3 to 4 minutes to connect after ubuntu has loaded but it does connect without having to give commands.  Im I good to go start playing.

---

### Post by herman2 on 2014-04-26
I'm experiencing the same issues described in this thread.  I don't have the Inspiron with me but plan to try again on Monday to get it working.  My plan is to install the AMD 64-bit version of Lubuntu 14.04.  If I've followed this thread correctly these are the steps I need to take ...

To get a temporary wired ethernet connection, open a terminal and do:

```
sudo modprobe b44 
sudo apt-get update
sudo apt-get install firmware-b43-installer

```
Detach the ethernet cable, reboot, open a terminal and do:

```
sudo modprobe b43
dmesg | grep b43
sudo -i
echo b43  >>  /etc/modules
echo b44  >>  /etc/modules
exit

```

Does this look right?

---

### Post by chili555 on 2014-04-27
> **herman2 said:**
> I'm experiencing the same issues described in this thread.  I don't have the Inspiron with me but plan to try again on Monday to get it working.  My plan is to install the AMD 64-bit version of Lubuntu 14.04.  If I've followed this thread correctly these are the steps I need to take ...

To get a temporary wired ethernet connection, open a terminal and do:

```
sudo modprobe b44 
sudo apt-get update
sudo apt-get install firmware-b43-installer

```
Detach the ethernet cable, reboot, open a terminal and do:

```
sudo modprobe b43
dmesg | grep b43
sudo -i
echo b43  >>  /etc/modules
echo b44  >>  /etc/modules
exit

```

Does this look right?Assuming yours is the same device, 14e4:4311, that's pretty close.

If you accept the offer to install Additional Drivers during the install, which you may need for your video card, it will likely install the *wrong *driver for your wireless. That driver will blacklist (!!!) the ethernet driver. 

I suggest you confirm your wireless device. Is it 14e4:4311? If so, I'd accept the Additional Drivers process so that your video driver, if needed, gets installed. Then I would boot into the fresh install and hook up the ethernet and do:```
sudo apt-get purge bcmwl-kernel-source  [COLOR="#FF0000"]<--the wrong driver for your 4311[/COLOR]
sudo modprobe b44
sudo apt-get install linux-firmware-nonfree
```Reboot and enjoy.

If yours is not a 4311, my recommendations change.

---

### Post by herman2 on 2014-05-03
Thanks for the help, Chili. The wired connection worked fine from the get go.  I issued the commands you recommended, 

```
sudo apt-get purge bcmwl-kernel-source
sudo modprobe b44
sudo apt-get install linux-firmware-nonfree
```

but still can't get the wireless connection to work.  Here's what I have:

```
herman@Inspiron:~$ lspci -nn | grep -e 0200 -e 0280
05:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
08:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
```

The wifi light is on.  I'm using Wicd Network Manager.  It sees my wireless network.  When I click on "Connect" it always gets hung up at "Validating authentication ...".

We had the same problem trying to connect to a different wireless network in a different location.

The working settings on my Windows 7 laptop have the security type as WPA-Personal and the encryption type as AES.
 
Trying to match these the best I can on this laptop I've got WPA2-LEAP.  I don't know what to put in as the username.  I tried the username for the computer account which is "herman" and I tried the wireless network name which is "Sherwood".  The password matches the network security key on the Windows 7 machine. 

I'm so close ... :(

---

### Post by chili555 on 2014-05-03
What does a scan say about your encryption?```
sudo iwlist wlan0 scan
```> I've got WPA2-LEAP.The encryption is set in the router. It will be the same for all the computers connected to it.

---

### Post by herman2 on 2014-05-03
What I meant is that I know the router is set to WPA2.  I was trying to ask if WPA2-LEAP is the correct setting in Wicd.

```
herman@Inspiron:~$ sudo iwlist wlan0 scan
[sudo] password for herman: 
wlan0     No scan results
```

---

### Post by chili555 on 2014-05-03
Why are there no scan results? Let's see:```
iwconfig
rfkill list all
```> I was trying to ask if WPA2-LEAP is the correct setting in Wicd.I doubt it. You really shouldn't have to set *anything* in Wicd. It should see your network. You should then select it. Wicd will ask for the password and you connect.

If you can't scan and see your network, then Wicd can't see it either. That suggests that something else is wrong.

[http://n1tr0g3n.com/wp-content/uploads/2011/12/wicd_applet_thumb1.png](http://n1tr0g3n.com/wp-content/uploads/2011/12/wicd_applet_thumb1.png)

---

### Post by herman2 on 2014-05-03
```
herman@Inspiron:~$ iwconfig
eth0      no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11bg  ESSID:"Sherwood"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
herman@Inspiron:~$ rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

```

> **chili555 said:**
> 
If you can't scan and see your network, then Wicd can't see it either. That suggests that something else is wrong.

[http://n1tr0g3n.com/wp-content/uploads/2011/12/wicd_applet_thumb1.png](http://n1tr0g3n.com/wp-content/uploads/2011/12/wicd_applet_thumb1.png)

I see something very similar to that, but when I click on "Connect" in the entry for my wireless network it always hangs up during the [COLOR=#000000]"Validating authentication ...".[/COLOR]

---

### Post by chili555 on 2014-05-04
> wlan0     IEEE 802.11bg  ESSID:"[COLOR="#FF0000"]Sherwood[/COLOR]"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: [COLOR="#FF0000"]Not-Associated [/COLOR]  
          Tx-Power=20 dBm   Where does it get 'Sherwood?' Is that a detail you've filled in? I think all that needs to be removed so that Wicd can see the network for itself.>  it always hangs up during the "Validating authentication ...".Do you mean that it thinks for a while and just comes back to that same window or do you mean that Wicd freezes up?

Are there any clues here?```
cat /var/log/syslog | grep -e etwork -e wicd -e wlan | tail -n20
```Why did you install Wicd? Did you completely remove Network Manager?

---

### Post by herman2 on 2014-05-04
> **chili555 said:**
> Where does it get 'Sherwood?' Is that a detail you've filled in? I think all that needs to be removed so that Wicd can see the network for itself.Do you mean that it thinks for a while and just comes back to that same window or do you mean that Wicd freezes up?

It sees Sherwood (my wireless network) as well as my neighbors' networks.  It doesn't freeze.  It hangs up, meaning that for about 2 or 3 minutes the slider moves back and forth until it times out.  Wicd does not freeze.

```
herman@Inspiron:~$ cat /var/log/syslog | grep -e etwork -e wicd -e wlan | tail -n20
May  4 08:27:16 Inspiron NetworkManager[747]: <info> (eth0): device state change: secondaries -> activated (reason 'none') [90 100 0]
May  4 08:27:16 Inspiron NetworkManager[747]: <info> NetworkManager state is now CONNECTED_GLOBAL
May  4 08:27:16 Inspiron NetworkManager[747]: <info> Policy set 'Wired connection 1' (eth0) as default for IPv4 routing and DNS.
May  4 08:27:16 Inspiron NetworkManager[747]: <info> DNS: starting dnsmasq...
May  4 08:27:16 Inspiron NetworkManager[747]: <warn> dnsmasq not available on the bus, can't update servers.
May  4 08:27:16 Inspiron NetworkManager[747]: <error> [1399210036.449130] [nm-dns-dnsmasq.c:396] update(): dnsmasq owner not found on bus: Could not get owner of name 'org.freedesktop.NetworkManager.dnsmasq': no such name
May  4 08:27:16 Inspiron NetworkManager[747]: <warn> DNS: plugin dnsmasq update failed
May  4 08:27:16 Inspiron NetworkManager[747]: <info> Writing DNS information to /sbin/resolvconf
May  4 08:27:16 Inspiron NetworkManager[747]: <info> Activation (eth0) successful, device activated.
May  4 08:27:16 Inspiron NetworkManager[747]: <warn> dnsmasq appeared on DBus: :1.21
May  4 08:27:16 Inspiron NetworkManager[747]: <info> Writing DNS information to /sbin/resolvconf
May  4 08:27:18 Inspiron NetworkManager[747]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) starting DHCPv6 as requested by IPv6 router...
May  4 08:27:18 Inspiron NetworkManager[747]: <info> Activation (eth0) Beginning DHCPv6 transaction (timeout in 45 seconds)
May  4 08:27:18 Inspiron NetworkManager[747]: <info> dhclient started with pid 1372
May  4 08:27:21 Inspiron NetworkManager[747]: <info> WiFi hardware radio set enabled
May  4 08:28:03 Inspiron NetworkManager[747]: <warn> (eth0): DHCPv6 request timed out.
May  4 08:28:03 Inspiron NetworkManager[747]: <info> (eth0): canceled DHCP transaction, DHCP client pid 1372
May  4 08:28:03 Inspiron NetworkManager[747]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
May  4 08:28:03 Inspiron NetworkManager[747]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) started...
May  4 08:28:03 Inspiron NetworkManager[747]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) complete.



```


> Why did you install Wicd? Did you completely remove Network Manager?

My friend installed that to try and troubleshoot this problem.  I doubt that he would have removed anything.  I also have WiFi Radar.

---

### Post by chili555 on 2014-05-04
> <info> NetworkManager state is now CONNECTED_GLOBALIn fact, Network Manager is still installed and probably conflicting. I suggest you remove Wicd and let NM handle networking as it usually does quite reliably. Often, when Wicd is installed, the suspicion is that there is a flaw in NM that Wicd will overcome. Actually, the fault almost always lies elsewhere.```
sudo apt-get purge wicd*
```Reboot.

Now does NM see your network and try to connect? If it doesn't connect, what are its symptoms?```
cat /var/log/syslog | grep -e etwork -e wlan | tail -n20
```Just in the interest of troubleshooting, I suggest you, at least temporarily, set IPv6 to 'Ignore' in NM: [http://digitizor.com/wp-content/uploads/2009/11/disable-ipv6-network.png](http://digitizor.com/wp-content/uploads/2009/11/disable-ipv6-network.png)  This example is for wired ethernet, but we'd like to see it set for wireless.

---

### Post by herman2 on 2014-05-04
> **chili555 said:**
> In fact, Network Manager is still installed and probably conflicting. I suggest you remove Wicd and let NM handle networking as it usually does quite reliably. Often, when Wicd is installed, the suspicion is that there is a flaw in NM that Wicd will overcome. Actually, the fault almost always lies elsewhere.```
sudo apt-get purge wicd*
```Reboot.

Ok, I did that.

> Now does NM see your network and try to connect? 

I don't know how to launch NM (Network Manager).  I don't see it in my Internet menu.  I do see WiFi Radar but I think that was also installed by my friend when he installed Wicd.


> If it doesn't connect, what are its symptoms?```
cat /var/log/syslog | grep -e etwork -e wlan | tail -n20
```

```
herman@Inspiron:~$ cat /var/log/syslog | grep -e etwork -e wlan | tail -n20May  4 16:13:03 Inspiron NetworkManager[747]: <info> (eth0): device state change: secondaries -> activated (reason 'none') [90 100 0]
May  4 16:13:03 Inspiron NetworkManager[747]: <info> NetworkManager state is now CONNECTED_GLOBAL
May  4 16:13:03 Inspiron NetworkManager[747]: <info> Policy set 'Wired connection 1' (eth0) as default for IPv4 routing and DNS.
May  4 16:13:03 Inspiron NetworkManager[747]: <info> DNS: starting dnsmasq...
May  4 16:13:03 Inspiron NetworkManager[747]: <warn> dnsmasq not available on the bus, can't update servers.
May  4 16:13:03 Inspiron NetworkManager[747]: <error> [1399237983.568476] [nm-dns-dnsmasq.c:396] update(): dnsmasq owner not found on bus: Could not get owner of name 'org.freedesktop.NetworkManager.dnsmasq': no such name
May  4 16:13:03 Inspiron NetworkManager[747]: <warn> DNS: plugin dnsmasq update failed
May  4 16:13:03 Inspiron NetworkManager[747]: <info> Writing DNS information to /sbin/resolvconf
May  4 16:13:03 Inspiron NetworkManager[747]: <info> Activation (eth0) successful, device activated.
May  4 16:13:03 Inspiron NetworkManager[747]: <warn> dnsmasq appeared on DBus: :1.15
May  4 16:13:03 Inspiron NetworkManager[747]: <info> Writing DNS information to /sbin/resolvconf
May  4 16:13:04 Inspiron NetworkManager[747]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) starting DHCPv6 as requested by IPv6 router...
May  4 16:13:04 Inspiron NetworkManager[747]: <info> Activation (eth0) Beginning DHCPv6 transaction (timeout in 45 seconds)
May  4 16:13:04 Inspiron NetworkManager[747]: <info> dhclient started with pid 1184
May  4 16:13:08 Inspiron NetworkManager[747]: <info> WiFi hardware radio set enabled
May  4 16:13:48 Inspiron NetworkManager[747]: <warn> (eth0): DHCPv6 request timed out.
May  4 16:13:48 Inspiron NetworkManager[747]: <info> (eth0): canceled DHCP transaction, DHCP client pid 1184
May  4 16:13:48 Inspiron NetworkManager[747]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
May  4 16:13:48 Inspiron NetworkManager[747]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) started...
May  4 16:13:48 Inspiron NetworkManager[747]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) complete.



```

> Just in the interest of troubleshooting, I suggest you, at least temporarily, set IPv6 to 'Ignore' in NM: [http://digitizor.com/wp-content/uploads/2009/11/disable-ipv6-network.png](http://digitizor.com/wp-content/uploads/2009/11/disable-ipv6-network.png)  This example is for wired ethernet, but we'd like to see it set for wireless.

How do I get to that screen?

---

### Post by chili555 on 2014-05-04
> I don't know how to launch NM (Network Manager). I don't see it in my Internet menu. Is this by chance lubuntu? There is a known issue. Let's try to solve it temporarily:```
nm-applet &
```Does the icon appear?> How do I get to that screen?Right-click the applet we just brought up and select 'Edit Connections.'

---

### Post by herman2 on 2014-05-04
> **chili555 said:**
> Is this by chance lubuntu? 

Yes.  And I noticed just now that the WiFi light on the keyboard is no longer lit.

> CODE]nm-applet &[/CODE]Does the icon appear?Right-click the applet we just brought up and select 'Edit Connections.'

Ok.  I now see a pair of arrows (up and down) just to the left of the clock.  I right click on it and select "Edit Connections".

And then ... ?

---

### Post by chili555 on 2014-05-04
> And then ... ?Select Wifi > Edit > IPv6 Settings > Ignore.

The arrows indicate you have a wired ethernet connection. Please detach the ethernet and see if the wireless access points appear.

So is it lubuntu?```
env | grep DESKTOP_SESSION=
```

---

### Post by herman2 on 2014-05-04
> **chili555 said:**
> Select Wifi > Edit > IPv6 Settings > Ignore.

Ok, but when I do that the Save ... button is grayed out, so the only options are to Cancel or close the dialog box.  If I type in Sherwood for the SSID on the Wi-Fi tab then I can at least save the connection.

> The arrows indicate you have a wired ethernet connection. Please detach the ethernet and see if the wireless access points appear.

No wireless connection.  No access points appear.  Also, the WiFi light is still off because of what I did a couple of posts back.

> So is it lubuntu?

Yes.

> ```
env | grep DESKTOP_SESSION=
```

Yes, it's Lubuntu.

---

### Post by herman2 on 2014-05-05
If this is a known issue with Lubuntu that can't be resolved then perhaps I should instead install Xubuntu?

---

### Post by chili555 on 2014-05-06
> **herman2 said:**
> If this is a known issue with Lubuntu that can't be resolved then perhaps I should instead install Xubuntu?The only known issue is that the Network Manager icon doesn't show up automatically. It is easily fixable. You have a problem that is completely unrelated to the windowing manager LXDE (lubuntu) or XFCE (xubuntu). Your problem is that you have a driver and firmware, however, the wireless radio refuses to start.

Let's see:```
dmesg | grep -e b43 -e wl
cat /etc/network/interfaces
cat /etc/NetworkManager/NetworkManager.conf
```Something simple is wrong here.

---

### Post by herman2 on 2014-05-06
> **chili555 said:**
> The only known issue is that the Network Manager icon doesn't show up automatically. It is easily fixable. You have a problem that is completely unrelated to the windowing manager LXDE (lubuntu) or XFCE (xubuntu). Your problem is that you have a driver and firmware, however, the wireless radio refuses to start.

When the WiFi light on the keyboard is lit, doesn't that mean that the wireless radio is running?  I'm confused here, please help me.  We've gone through a number of steps.  That light was on, now it's off.  I had the Network Manager icon showing up, now I don't.

> Let's see:```
dmesg | grep -e b43 -e wl
cat /etc/network/interfaces
cat /etc/NetworkManager/NetworkManager.conf
```

```
herman@Inspiron:~$ dmesg | grep -e b43 -e wl
[   15.362930] b43-phy0: Broadcom 4311 WLAN found (core revision 10)
[   15.404074] b43-phy0: Found PHY: Analog 4, Type 2 (G), Revision 8
[   20.328051] b43-phy0: Loading firmware version 666.2 (2011-02-23 01:15:07)
[   20.405051] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   20.405446] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   20.412398] b43-phy0: Radio hardware status changed to DISABLED
herman@Inspiron:~$ cat /etc/network/interfaces
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback
herman@Inspiron:~$ cat /etc/NetworkManager/NetworkManager.conf
[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq


[ifupdown]
managed=false


```

---

### Post by chili555 on 2014-05-07
> b43-phy0: Radio hardware status changed to DISABLEDGenerally, that appears because the wireless switch or key combination is set to turn the wireless radio off. Is that the case?```
rfkill list all
```Let's try to fix the Network Manager icon issue now. To fix the Network Manager not showing up on the panel issue, from the Lubuntu menu select Preferences > Default applications for LXSession, then click on the Autostart tab and under "Manual autostarted applications" type "nm-applet", then click the "+ Add" button on the left.

Now log out, log back in and you should see the Network Manager icon on the panel.

---

### Post by herman2 on 2014-05-07
> **chili555 said:**
> Generally, that appears because the wireless switch or key combination is set to turn the wireless radio off. Is that the case?```
rfkill list all
```

There is no wireless switch.  The key combination does nothing, and before when the WiFi light was on, it also did nothing.

```
herman@Inspiron:~$ rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

```

> Let's try to fix the Network Manager icon issue now. To fix the Network Manager not showing up on the panel issue, from the Lubuntu menu select Preferences > Default applications for LXSession, then click on the Autostart tab and under "Manual autostarted applications" type "nm-applet", then click the "+ Add" button on the left.

Now log out, log back in and you should see the Network Manager icon on the panel.

Alright ... logging off now to see if that worked.

Be right back ...

Ok, success. Yeah, it finally worked!  Thank you.


Anyone else who's trying to get this to work and has gotten this far, you'll notice that if you left-click on the icon there are two grayed out menu choices in the second grouping.  The first is "Wi-Fi Networks" and the second alternates between "disconnected" and "Wi-Fi is disabled by hardware switch" when you operate the key combination Fn-F2 (this is the key combination that is supposed to turn the WiFi light on and off).  Operate the key combination so that you see "disconnected".  

Right-click on the Network Manager icon and choose "Enable Wi-Fi".  Then when you left-click you'll see your wireless network on the menu.  Select it, enter the password, and off you go.

Thanks again, Chili.  You rock!

---

### Post by chili555 on 2014-05-08
Woo hoo! Awesome. Glad it's working finally.

---

### Post by vk_Ubie on 2014-07-13
Hi, 
I'm a newbie with Linux, I've been reading this thread all along, because I have the same computer Dell 1501, but not same Ubuntu (mine is 14.04).

I installed Ubuntu 14.04 LTS as a main OS in my spare laptop; however, there is NO way it recognizes Ethernet or  wireless connection at all.
I tried all commands as this thread suggested, and it still not working.

When I had Win 7 before, it recognizes both Ethernet and wireless connection. This made me thinking that after erased Win 7, and installed 14.04. Linux does not recognize the Ethernet & wireless card at all.

Can anyone recommend where should I start again (step-by-step if possible please)?

Thank you


> **mike24216 said:**
> Hey I am newbie to ubuntu 12.04 Lts and I installed it on my dell inspiron 1501 laptop.  I installed it with dual boot with windows vista.  I am having problems with the network.  The wired and the wireless does not work.  Can anyone help me out.  I have tried some of the post but most threads i found want you to hook up the wired connection but like I said it does not work. Thanks.

---

### Post by chili555 on 2014-07-13
> **vk_Ubie said:**
> Hi, 
I'm a newbie with Linux, I've been reading this thread all along, because I have the same computer Dell 1501, but not same Ubuntu (mine is 14.04).

....

Can anyone recommend where should I start again (step-by-step if possible please)?

Thank youLet's start by identifying your network devices. Please open a terminal Ctrl+Alt+t and run and post:```
lspci -nn | grep -e 0200 -e 0280
```The pipe symbol | is on the right side of my keyboard on the same key with \.

---

