---
title: "Problem configuring Wireless , intel 3945ABG"
date: 2008-05-28
forum: Networking &amp; Wireless
---

### Post by Kinnza on 2008-05-28
hi guys
im pretty new in linux so bare with me if im a little bit clueless

i installed ubuntu about a week ago and i still cannot manage to get my wireless up
i've tried almost anything i could find in the forums, but still didnt manage to solve it.

im using lenovo 3000 v100 , which has intel 3945abg as said in the title

as far as i could find this card is supposed to be supported, but for some reason i cannot get it to work

first it didnt recognize it, then i did some stuff that were mentioned here mostly and then it recognized it, but didnt find networks.
during everything i tried, i also tried to use the windows driver. that made me able to see the wireless networks but not to connect to any

i prefair to make the linux driver work instead of using the windows one, especially when its supposed to be supported...

output of lshw:
kinnza@kinnza-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network UNCLAIMED     
       description: Network controller
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 7
       bus info: pci@0000:0a:07.0
       logical name: eth0
       version: 10
       serial: 00:16:d3:37:f2:35
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.1.103 latency=32 maxlatency=64 mingnt=32 module=8139too multicast=yes

i already managed to get it to be without the claimed, and then i tried to install the restricted module and it totaly screwed my system
later i saw in synaptic that there are several versions of it, and i played with that and now .... it doesnt recognize the driver again, and the sound is gone :S

can anyone help?

thanks,
Kinnza

---

### Post by Kinnza on 2008-05-28
to add something:
i used those commands to list the driver details 
$ modinfo ipw3945
$ modinfo iwl3945

and before it returned 
FATAL: Module ipw3945 not found.
and some data for the second one
and now.... im getting module not found on both :S

---

### Post by Kinnza on 2008-05-30
ok i basicly reinstalled ubuntu (for this and for some more reasons)

now the driver stuff looks ok, its not unclaimed anymore, everything seems cool
but... it wont scan networks and ofcourse cannot connect to anything

after some research i found this in the syslog (messages i saw on boot)

May 30 02:05:20 kinnza-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
May 30 02:05:20 kinnza-laptop NetworkManager: <info>  Will activate connection 'eth0'. 
May 30 02:05:20 kinnza-laptop NetworkManager: <info>  Device eth0 activation scheduled... 
May 30 02:05:20 kinnza-laptop NetworkManager: <info>  Wireless now enabled by radio killswitch 
May 30 02:05:20 kinnza-laptop NetworkManager: <info>  Activation (eth0) started... 
May 30 02:05:20 kinnza-laptop NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled... 
May 30 02:05:20 kinnza-laptop NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started... 
May 30 02:05:20 kinnza-laptop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled... 
May 30 02:05:20 kinnza-laptop NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete. 
May 30 02:05:20 kinnza-laptop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting... 
May 30 02:05:20 kinnza-laptop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful. 
May 30 02:05:20 kinnza-laptop NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled. 
May 30 02:05:20 kinnza-laptop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete. 
May 30 02:05:20 kinnza-laptop NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started... 
May 30 02:05:21 kinnza-laptop kernel: [   52.341144] iwl3945: Microcode SW error detected.  Restarting 0x82000008.
May 30 02:05:21 kinnza-laptop kernel: [   52.341215] iwl3945: Error Reply type 0x00000005 cmd REPLY_SCAN_CMD (0x80) seq 0x4418 ser 0x0000004B
May 30 02:05:21 kinnza-laptop NetworkManager: <info>  Activation (eth0) Beginning DHCP transaction. 
May 30 02:05:21 kinnza-laptop NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete. 
May 30 02:05:21 kinnza-laptop NetworkManager: <info>  DHCP daemon state is now 12 (successfully started) for interface eth0 
May 30 02:05:21 kinnza-laptop kernel: [   53.343442] iwl3945: Can't stop Rx DMA.
May 30 02:05:22 kinnza-laptop dhclient: wmaster0: unknown hardware address type 801
May 30 02:05:23 kinnza-laptop anacron[5482]: Anacron 2.3 started on 2008-05-30
May 30 02:05:23 kinnza-laptop anacron[5482]: Will run job `cron.weekly' in 10 min.
May 30 02:05:23 kinnza-laptop anacron[5482]: Will run job `cron.monthly' in 15 min.
May 30 02:05:23 kinnza-laptop anacron[5482]: Jobs will be executed sequentially
May 30 02:05:23 kinnza-laptop NetworkManager: <info>  DHCP daemon state is now 1 (starting) for interface eth0 
May 30 02:05:23 kinnza-laptop dhclient: wmaster0: unknown hardware address type 801

later on i find this in the log:

May 30 02:11:24 kinnza-laptop NetworkManager: <info>  Updating allowed wireless network lists. 
May 30 02:11:24 kinnza-laptop NetworkManager: <WARN>  nm_dbus_get_networks_cb(): error received: org.freedesktop.NetworkManagerInfo.NoNetworks - There are no wireless networks stored.. 
May 30 02:12:19 kinnza-laptop NetworkManager: <WARN>  request_and_convert_scan_results(): card took too much time scanning.  Get a better one. 
May 30 02:14:33 kinnza-laptop NetworkManager: <WARN>  request_and_convert_scan_results(): card took too much time scanning.  Get a better one. 
May 30 02:15:23 kinnza-laptop anacron[5482]: Job `cron.weekly' started
May 30 02:15:24 kinnza-laptop anacron[6555]: Updated timestamp for job `cron.weekly' to 2008-05-30
May 30 02:15:27 kinnza-laptop syslogd 1.5.0#1ubuntu1: restart.
May 30 02:15:27 kinnza-laptop anacron[5482]: Job `cron.weekly' terminated
May 30 02:16:47 kinnza-laptop NetworkManager: <WARN>  request_and_convert_scan_results(): card took too much time scanning.  Get a better one. 
May 30 02:17:01 kinnza-laptop /USR/SBIN/CRON[7842]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
May 30 02:19:01 kinnza-laptop NetworkManager: <WARN>  request_and_convert_scan_results(): card took too much time scanning.  Get a better one. 
May 30 02:20:23 kinnza-laptop anacron[5482]: Job `cron.monthly' started
May 30 02:20:24 kinnza-laptop anacron[8080]: Updated timestamp for job `cron.monthly' to 2008-05-30
May 30 02:21:15 kinnza-laptop NetworkManager: <WARN>  request_and_convert_scan_results(): card took too much time scanning.  Get a better one. 
May 30 02:23:29 kinnza-laptop NetworkManager: <WARN>  request_and_convert_scan_results(): card took too much time scanning.  Get a better one. 
May 30 02:25:16 kinnza-laptop anacron[5482]: Job `cron.monthly' terminated (mailing output)
May 30 02:25:16 kinnza-laptop anacron[5482]: Can't find sendmail at /usr/sbin/sendmail, not mailing output
May 30 02:25:16 kinnza-laptop anacron[5482]: Normal exit (2 jobs run)
May 30 02:25:43 kinnza-laptop NetworkManager: <WARN>  request_and_convert_scan_results(): card took too much time scanning.  Get a better one. 
May 30 02:27:58 kinnza-laptop NetworkManager: <WARN>  request_and_convert_scan_results(): card took too much time scanning.  Get a better one. 
May 30 02:30:12 kinnza-laptop NetworkManager: <WARN>  request_and_convert_scan_results(): card took too much time scanning.  Get a better one. 
May 30 02:32:26 kinnza-laptop NetworkManager: <WARN>  request_and_convert_scan_results(): card took too much time scanning.  Get a better one. 

and another section:
May 30 16:29:13 kinnza-laptop NetworkManager: <info>  Found radio killswitch /org/freedesktop/Hal/devices/ipw_wlan_switch 
May 30 16:29:13 kinnza-laptop kernel: [   44.013767] ADDRCONF(NETDEV_UP): wlan0: link is not ready
May 30 16:29:13 kinnza-laptop hcid[5423]: Bluetooth HCI daemon
May 30 16:29:13 kinnza-laptop NetworkManager: <info>  wlan0: Device is fully-supported using driver 'iwl3945'. 
May 30 16:29:13 kinnza-laptop NetworkManager: <info>  wlan0: driver does not support SSID scans (scan_capa 0x00). 
May 30 16:29:13 kinnza-laptop NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start 
May 30 16:29:13 kinnza-laptop NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing. 
May 30 16:29:13 kinnza-laptop NetworkManager: <info>  Now managing wireless (802.11) device 'wlan0'. 
May 30 16:29:13 kinnza-laptop NetworkManager: <info>  Deactivating device wlan0. 
May 30 16:29:13 kinnza-laptop hcid[5423]: HCI dev 0 registered
May 30 16:29:13 kinnza-laptop hcid[5423]: Starting SDP server
May 30 16:29:13 kinnza-laptop NetworkManager: <debug> [1212154153.781101] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_model_DVDRAM_GMA_4082N'). 


i think that those are the messages i saw on boot

May 30 16:29:14 kinnza-laptop NetworkManager: <info>  Wireless now enabled by radio killswitch 
May 30 16:29:14 kinnza-laptop kernel: [   44.542728] iwl3945: Microcode SW error detected.  Restarting 0x82000008.
May 30 16:29:14 kinnza-laptop kernel: [   44.542797] iwl3945: Error Reply type 0x00000005 cmd REPLY_SCAN_CMD (0x80) seq 0x4418 ser 0x0000004B
May 30 16:29:16 kinnza-laptop kernel: [   45.536167] iwl3945: Can't stop Rx DMA.

im sorry for the long post, but i've been trying to get this to work for a while now, and its pretty annoying

---

### Post by chili555 on 2008-05-30
Please do two things:```
sudo apt-get install linux-backports-modules-hardy-generic
```After you have done that, please try to connect again. If no connection is made, try:```
sudo rmmod -f iwl3945
sudo modprobe iwl3945 disable_hw_scan=1
```Can you now connect? If not, please let us see:```
sudo cat /var/log/messages | grep iwl
```

---

### Post by timcredible on 2008-05-30
i installed ubuntu 7.10 on a dell with the intel 3945abg card and it worked perfect out of the box.  i don't have that laptop anymore so i can't try 8.04 on it.

---

### Post by Kinnza on 2008-05-30
OMG!!!
chili555 i LOVE you!

it did the trick....

after the install of backports it didnt work

(
iwlist wlan0 scan
wlan0     Failed to read scan data : Resource temporarily unavailable
)

but the other one did it

thanks sooooo much!

i've been trying to solve it for so long

can you explain to me what does that do?
i understand that i removed the module and reinstalled it (the driver module), right?
and then defined it to be able to scan? 
if so, why was it disabled? was that the default or something? :S

---

### Post by Kinnza on 2008-05-30
ok one last question i hope

this has all worked but when i reboot i have to do it all over again
is there a way i can configure it to run at boot or save this settings or something like that?

---

### Post by dpsf on 2008-05-30
Hi Kinnza,

I just solved this very problem by using all the steps outlined here:

[http://www.ubuntugeek.com/using-ipw3945-instead-iwl3945-in-hardy.html](http://www.ubuntugeek.com/using-ipw3945-instead-iwl3945-in-hardy.html)
[http://james.colannino.org/downloads.html](http://james.colannino.org/downloads.html)
(Simply awesome! Many thanks Thomer & James Colannino for the posts!)

Basically the problem stems from Ubuntu devs discontinuing the ipw3945
binary blob module for Hardy Heron, and moving to iwl3945. As you'll
notice if you read the various links there, ipw3945 is 'obsolete' &
development has moved to the iwl3945. But... iwl3945 is *not ready
for prime time yet* (!!!) as numerous posts in various Linux forums
suggest.  My own issue was that I was still able to connect to
an unsecured wireless network, but could not use WPA, as I could
with Feisty Fawn.

When following the procedure outlined in the site above, pay attention
to reply #16 to avoid an error. If you'd like, I will send you my newly
compiled module together with its support scripts. It's working like a
charm so far, though I haven't set things up so that it's all taken
care of at boot time yet-- a few manual steps at the command prompt
for now.

Ciao,

dpsf.

For the Ubuntu devs:

Why couldn't we have a choice between modules in Hardy Heron? I know
iwl3945 is now the 'default', but the simple fact is that it's clearly
not ready yet. So why remove the working module & watch your users
flounder about if they use this popular chipset? :/

---

### Post by Kinnza on 2008-05-30
thanks i will look into that

like i said chili555's post did the trick, i just want not to run those commands everytime i'll login.

---

### Post by chili555 on 2008-05-30
> this has all worked but when i reboot i have to do it all over again
is there a way i can configure it to run at boot or save this settings or something like that? Yes, you can do:```
sudo su
echo -e 'alias wlan0 iwl3945 \noptions iwl3945 disable_hw_scan=1' > /etc/modprobe.d/iwl3945
reboot
```> can you explain to me what does that do?
i understand that i removed the module and reinstalled it (the driver module), right?
and then defined it to be able to scan? You applied a parameter that the iwl3945 allows to scan in software, rather than hardware, I believe. See *modinfo iwl3945* and read the params. I actually don't know why it works for some people and is not needed for others, including me.

I was helping a pal in the UK figure out his 3945ABG by IM and after about five hours of trying, I stumbled on this in Google/linux. He tried it and screamed so loud I could hear him in South Carolina.> OMG!!!
chili555 i LOVE you!
Thank you for your kind comments.

---

### Post by Kinnza on 2008-05-30
ok thanks soooo much i'll try that too :D

---

### Post by Kinnza on 2008-05-30
ok it totaly worked
you are best!!!

---

### Post by Kinnza on 2008-05-30
ok last question i hope

i see that in that lib, there is a file called aliases and a file called options and im guessing it has something to do with what we did here

but that was a specific file named according to the driver, or does that not matter? (maybe it loads all the files there or something)

am i right?

---

### Post by Gwaihirjp on 2008-05-31
I had the exact same problem after my Hardy update and thanks to this thread, my wireless is now up and running again. Thank you!!! :D

---

### Post by chili555 on 2008-05-31
> there is a file called aliases and a file called options and im guessing it has something to do with what we did hereIt has *nothing* to do with what we did here. The purpose of /etc/modprobe.d, roughly, is to specify any options that are needed at the time the module is loaded. So we have created a file, *iwl3945* that says, 'please disable hardware scan, because it isn't working for me and I can't connect using it.' 

Scan results are required for Network Manager or Wicd in order to connect. If you are going to see an access point and click 'Connect,' the wireless card must be able to see it in scan.

---

### Post by Kinnza on 2008-05-31
ok cool
thanks :D

---

### Post by Maputo on 2008-07-09
I have a similar problem.  My wireless too works perfectly, but only after I do this:

```

sudo modprobe -r b44 ndiswrapper
sudo modprobe ndiswrapper
sudo ifconfig eth1 up

```

Is there way to automate this process, so I don't have to do it every time I boot up my computer?

Thanks!

---

### Post by chili555 on 2008-07-09
Your question has nothing to do with Intel 3945ABG. Please start a new thread perhaps referring to Broadcom and ndiswrapper right in the title.

---

### Post by Maputo on 2008-07-09
Oh, ok.  Sorry about that.

---

### Post by TadeoDiaz on 2008-12-07
I am having a similar but less severe issue with my Lenovo 3000 v100 running Intrepid. I upgraded about a week ago and had no problems connecting to my home wireless network (WEP encrypted) but when I get to school and try to connect to their hidden networks (WEP encrypted and open) it fails. Both networks are added to automatically connect to them upon finding them but I have to choose them and try to force the connection every time. I have to try it several times and it seems to come down to luck when it connects.

I didn't have a problem in Hardy and was wondering if I am having this problem because of iwl3945 and if the above described method would work for Intrepid

---

### Post by TadeoDiaz on 2009-01-05
Update: I reinstalled Intrepid on the laptop and had no issue connecting to networks at home and at friends home. However, I run into the same problem (outlined above) at school. Can anyone help?

This is the output of  sudo lshw -C network

```
  *-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wmaster0
       version: 02
       serial: 00:18:de:1a:44:4a
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 ip=192.168.0.105 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11abg
  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 7
       bus info: pci@0000:0a:07.0
       logical name: eth0
       version: 10
       serial: 00:16:d3:2a:7c:05
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=32 link=no maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=10MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 52:24:50:7e:95:01
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
```


It seems that I am running the iwl3945 module but don't know if the solution posted by chili555 would work for intrepid.

Thanks in advanced for the help

---

