---
title: "Unable to install Netgear wg311v3"
date: 2008-09-20
forum: Networking &amp; Wireless
---

### Post by kamlesh30rao on 2008-09-20
Hi Guys,

I am facing unknown problem to setup Netgear USB WG311v3 adapter.  It was working fine with UBUNTU.

Now, I have installed Kubuntu and its not able to work.  

I referred the below link to setup:
[https://help.ubuntu.com/community/WifiDocs/Device/Netgear_WG311_v3](https://help.ubuntu.com/community/WifiDocs/Device/Netgear_WG311_v3)

The GUID based Wireless tool is installed.

I install the Additional Info for you:

1) The "lsusb"command returns:
Bus 002 Device 002: ID 0846:4260 NetGear, Inc.
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000

2) The "ndiswrapper -l" command showed only the driver, but no device.  So, I added the same using "ndiswrapper -a devid wg311v3" command.  After doing this change, the output of "ndiswrapper -l" command  is shown below:

wg311v3 : driver installed
        device (0846:4260) present


Now, what when I use the "iwconfig" command, its not listing the "wlan0".  The output of this command shows:

lo        no wireless extensions.
eth0      no wireless extensions.


I am currently using the Wired connection to get help from internet and troubleshoot my NetGear USB adapter.  

The wireless broadband router is Cisco Linksys and it does not have any security enabled.  Can someone please help me.  

Let me know if you need output of any specific commands from my installation.

Thanks in advance
Kamlesh

---

### Post by kamlesh30rao on 2008-09-20
Got this resolved self.  The problem was I was using the wrong driver.  The driver given at [[https://help.ubuntu.com/community/WifiDocs/Device/Netgear_WG311_v3]](https://help.ubuntu.com/community/WifiDocs/Device/Netgear_WG311_v3]) was the culprit in my case.

I used the help from [[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper]](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper]) and learnt that its better to get the driver from your Windows Installation location (i.e c:\windows\inf\WG111v3).  The .inf and .sys file is enough, but I copied entire directory.

Then all the regular steps works fine and I am up with the Driver.

Thanks,
Kamlesh

---

