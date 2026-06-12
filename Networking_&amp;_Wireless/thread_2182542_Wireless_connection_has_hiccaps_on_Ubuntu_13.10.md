---
title: "Wireless connection has hiccaps on Ubuntu 13.10"
date: 2013-10-21
forum: Networking &amp; Wireless
---

### Post by wC3F7mB on 2013-10-21
I remember having the same issue some time ago, one or two Ubuntu releases before.
I just installed the 13.10 and now the Wifi connection "hangs". It connects without any problem, it never disconnects but when I browse the internet it looks like the wireless accepts the requests only occasionally. Happens that I click a link and the page loads, loads and loads continuosly without ending. I stop the loading, reclick the link and the page comes instantly. This happens on every website, alternating: first the site A hangs, while site B loads normally. Then site B hangs and A works. It seems all the connection has big difficulties. It's really really frustrating!
Now, it's a fresh Ubuntu install, I didn't change anything, router, browser setting (this is fresh install too), already changed DNS, etc... the only thing I can think it's the wireless drivers

This is my wireless adapter:
```
~$ lspci | grep -i wireless
02:00.0 Network controller: Qualcomm Atheros AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
```

```
~$ iwconfig
eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"HOME"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:22:3F:6C:88:6C
          Bit Rate=48 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=46/70  Signal level=-64 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:11  Invalid misc:3   Missed beacon:0

```

and I'm using the default ath9k drivers included. On Ubuntu 13.04 they worked normally.
Already applied these changes: [http://www.unixmen.com/resolve-slow-connexion-when-using-wifi-in-ubuntu-1104-natty-narwhal/](http://www.unixmen.com/resolve-slow-connexion-when-using-wifi-in-ubuntu-1104-natty-narwhal/) 
but doesn't solve.
Has somebody idea about what this strange behaviour could be? Do I need to wait a kernel update, hoping it fixes the problem?

---

### Post by wildmanne39 on 2013-10-21
Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
 wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a file named (wireless-info.txt, or wireless-info.txt.tar.gz) in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back, click on the paper clip and attach the wireless-info.tar.gz file as a zip file. 

If you do not have ethernet either then follow the directions at this link for running the script without internet.
[http://ubuntuforums.org/showpost.php?p=12350385](http://ubuntuforums.org/showpost.php?p=12350385)
Thanks

---

### Post by wC3F7mB on 2013-10-22
Oh yes, I forgot to say my connection has no protections. Anyway, here is my results.

---

### Post by wildmanne39 on 2013-10-22
How many of the things did you try in the link you posted? and please open the files you created and post the contents here so we will know if the changes were saved.

Please turn UFW off tempararly and see if you can connect.
Thanks

---

### Post by wC3F7mB on 2013-10-23
I applied all the changes and now these are my files:
```
~$ cat /etc/modprobe.d/ath9k.conf
options ath9k nohwcrypt=1

~$ cat /etc/modprobe.d/iwlagn-disable11n.conf
options iwlagn 11n_disable=1

~$ cat /etc/sysctl.conf
#
# /etc/sysctl.conf - Configuration file for setting system variables
# See /etc/sysctl.d/ for additional system variables
# See sysctl.conf (5) for information.
#

#kernel.domainname = example.com

# Uncomment the following to stop low-level messages on console
#kernel.printk = 3 4 1 3

##############################################################3
# Functions previously found in netbase
#

# Uncomment the next two lines to enable Spoof protection (reverse-path filter)
# Turn on Source Address Verification in all interfaces to
# prevent some spoofing attacks
#net.ipv4.conf.default.rp_filter=1
#net.ipv4.conf.all.rp_filter=1

# Uncomment the next line to enable TCP/IP SYN cookies
# See http://lwn.net/Articles/277146/
# Note: This may impact IPv6 TCP sessions too
#net.ipv4.tcp_syncookies=1

# Uncomment the next line to enable packet forwarding for IPv4
#net.ipv4.ip_forward=1

# Uncomment the next line to enable packet forwarding for IPv6
#  Enabling this option disables Stateless Address Autoconfiguration
#  based on Router Advertisements for this host
#net.ipv6.conf.all.forwarding=1


###################################################################
# Additional settings - these settings can improve the network
# security of the host and prevent against some network attacks
# including spoofing attacks and man in the middle attacks through
# redirection. Some network environments, however, require that these
# settings are disabled so review and enable them as needed.
#
# Do not accept ICMP redirects (prevent MITM attacks)
#net.ipv4.conf.all.accept_redirects = 0
#net.ipv6.conf.all.accept_redirects = 0
# _or_
# Accept ICMP redirects only for gateways listed in our default
# gateway list (enabled by default)
# net.ipv4.conf.all.secure_redirects = 1
#
# Do not send ICMP redirects (we are not a router)
#net.ipv4.conf.all.send_redirects = 0
#
# Do not accept IP source route packets (we are not a router)
#net.ipv4.conf.all.accept_source_route = 0
#net.ipv6.conf.all.accept_source_route = 0
#
# Log Martian Packets
#net.ipv4.conf.all.log_martians = 1
#
#disable ipv6
net.ipv6.conf.all.disable_ipv6 = 1
net.ipv6.conf.default.disable_ipv6 = 1
net.ipv6.conf.lo.disable_ipv6 = 1

```

UFW is not the problem, the connection was warking bad also when I didn't configure it.

---

### Post by wC3F7mB on 2013-10-23
Looks like I got it! The issue was simply the powersaving function for wlan0 given by the tool "powertop". I didn't even think about it because in previous versions I always activated it and got no problems...
I'm not sure if powertop v 2.4 is the faulty one or just this version of Ubuntu can't handle it. I'll try to contact powertop devs.
Thanks for your help!

---

### Post by wildmanne39 on 2013-10-23
Glad it is working! this > ~$ cat /etc/modprobe.d/iwlagn-disable11n.conf
options iwlagn 11n_disable=1
can be removed it is for the iwlagn driver which you are not using.
Thanks

---

### Post by metoikos on 2014-02-16
I have very same problem too. I just changed my computer, and this problem keeps annoying me. I did a lot of thing my still having issue.
Here is my wifi output. [https://www.dropbox.com/s/94yo5hmla6e0rl1/wireless-info.tar.gz](https://www.dropbox.com/s/94yo5hmla6e0rl1/wireless-info.tar.gz)

---

### Post by wildmanne39 on 2014-02-16
I am having trouble opening that file please attach it here.
Thanks

---

### Post by metoikos on 2014-02-16
Sorry for that, here is the file.

---

### Post by wildmanne39 on 2014-02-16
There are only a few things we can try, as you know this is a staging driver which means all the issues may not be worked out with it yet.

Please do:
```
sudo modprobe -rv rtl8821ae

sudo modprobe -v rtl8821ae swenc=1
```
this is only temporary the change will be lost at reboot so if it helps we will need to make it permanent.
Thanks

---

### Post by metoikos on 2014-02-16
Hello again,
nothing seems changed. So i will wait till it release to figure out the problem. 
Thank you for your time.

---

### Post by wildmanne39 on 2014-02-16
Their are still a few things we can try if you want too?

---

### Post by metoikos on 2014-02-17
Of course i want to, you said few things then i thought we're done :) my bad.

---

### Post by wildmanne39 on 2014-02-17
First I noticed you have your wired connection connected you need to disconnect it then test your wifi connection because while the wired is connected it overrides the wifi.

If you still have issues try the first set of commands I gave you while wired is disconnected if it does not help then reboot and run these commands please:
```
sudo modprobe -rv rtl8821ae
sudo modprobe -v rtl8821ae ips=0 fwlps=0
```
remember this command only works until you reboot so if it help we will need to make it permanent.
Thanks

---

### Post by metoikos on 2014-02-17
Hello again,
i tried but same issue continues to bug me.
By the way i am not connected with wire i have only wifi connection just let you know.

---

### Post by chili555 on 2014-02-17
We see many dozens of these:> [ 3322.415030] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 3322.521590] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 3322.783480] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 3322.889965] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4GThe wireless device is hopping back and forth from the 2.4 GHz band to the 5 GHz band and never seems to settle down and stick. I suggest you disable the 5 GHz band in the router and also:> [  151.913822] rtl8821ae-0:rtl_op_set_key():<0-0> alg:TKIPTKIP is tricky and getting a bit old. I suggest you set the encryption method to WPA2-AES. The troublesome WPA and WPA2 mixed mode is to be avoided.

After these changes, try to connect again and if not successful, let us see another script as above.

---

### Post by metoikos on 2014-02-17
Nope issue continues.
I am loosing packages at network connection. I have mac and tried with it, never lost any package.
Basicly I am using ping to test my connection, and process always hangs between responses and loose packages, but other box in my network does not do the same.

So, I set my router to 802.11b which is 2.4 Ghz and set WPA2/PSK AES
and attached new output to post

thank you.

---

### Post by chili555 on 2014-02-18
We are rapidly running low on ideas. As I said to a friend, new devices and new drivers bring new challenges and new headaches. Is the behavior better or worse with:```
sudo modprobe -r rtl8821ae
sudo modprobe rtl8821ae swenc=1
```Thanks.

---

### Post by metoikos on 2014-02-18
Nope made no difference.
New devices new problems I should buy NUC instead of this ViVo PC I guess.

Thanks again.

---

### Post by chili555 on 2014-02-18
Or at least a different wireless card for your ViVo. My NUC connects with ethernet, so wireless is thankfully not an issue.

---

### Post by metoikos on 2014-02-18
I am waiting latest 3.14 RC3 kernel. As i read they added 8821 driver to config so it will be install and no need to custom build. Also checked driver source and saw some fixes. I will update here if achieve any progress.

Thanks.

---

### Post by metoikos on 2014-02-23
Nope, I installed latest rc3. it ships with 8821 driver but still very slow or laggy internet connection and all problems still there.

---

### Post by simons2 on 2014-03-25
I'm also experiencing the same problem with my wifi connection on my HP probook 6570b. Wifi on 13.10 used to work fine, however with one of ubuntu updates, the hiccup problem appeared. The zip file with info about my connection is attached. Any help appreciated.

---

### Post by chili555 on 2014-03-25
> **simons2 said:**
> I'm also experiencing the same problem with my wifi connection on my HP probook 6570b. Wifi on 13.10 used to work fine, however with one of ubuntu updates, the hiccup problem appeared. The zip file with info about my connection is attached. Any help appreciated.Your device 14e4:4329 is very tricky to get going properly. Let's try a few things. First, check the settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, I have better luck with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz. I also have better luck with a fixed channel, either 1 or 11, rather than automatic channel selection. After making these changes, reboot the router.

Second, in your message log, I see a little stumble with IPv6. Please right-click the Network Manager icon, select Edit Connections > Wireless > IPv6 and set it to ignore. [http://digitizor.com/wp-content/uploads/2009/11/disable-ipv6-network.png](http://digitizor.com/wp-content/uploads/2009/11/disable-ipv6-network.png) This example is ethernet, but you should select wireless. 

Any improvement?

---

### Post by simons2 on 2014-03-25
Security mode is set to WPA2PSK. I chose channel 1 instead of AUTO. I can't find any option to select the channel width. I also set IPv6 to ignore. During 5 min of browsing, no hiccups yet, seems to be working better. In case the problem reoccurs, I'll get in touch again. Thanks!

---

### Post by chili555 on 2014-03-25
> **simons2 said:**
> Security mode is set to WPA2PSK. I chose channel 1 instead of AUTO. I can't find any option to select the channel width. I also set IPv6 to ignore. During 5 min of browsing, no hiccups yet, seems to be working better. In case the problem reoccurs, I'll get in touch again. Thanks!Please do; your device is interesting.

---

