---
title: "cannot connect to wireless network in Ubuntu 12.04 LTS"
date: 2014-12-01
forum: Networking &amp; Wireless
---

### Post by RICuser on 2014-12-01
Hi,

I am not very confident with computers. I used to depend on Windows, and recently thought of trying out Ubuntu for shifting to this operating system in future.

I recently installed Ubuntu 12.04 LTS with dual-boot on my computer and trying to connect to an existing home wireless connection. That is, there is a wired internet line provided by a university campus which comes to an wireless router and the home computer/s connect to that router via wireless connection. When the computer is started with Windows, the wireless connection works fine. In Ubuntu what happens is: it keeps asking for the password, and the same password that is used in Windows does not work (it tries for a while, and asks for the password again, and it keeps happening). Even if I cancel that (to not connect), it still keeps coming back on my screen. I tried editing the connection from the network applet at the top right portion of the Ubuntu screen (and selected wireless, chose the connection that is used in Windows), and found the password field is empty. There is no way to write the password and save it, because the 'save' button is diabled.

I found from this forum people using a command "nm-tool" in the terminal. I am pasting the output here.

 




NetworkManager Tool

State: connected (global)

- Device: ttyUSB0  [Vodafone Vodafone Connect] ---------------------------------
  Type:              Mobile Broadband (GSM)
  Driver:            option1
  State:             connected
  Default:           yes

  Capabilities:

  IPv4 Settings:
    Address:         10.130.48.97
    Prefix:          32 (255.255.255.255)
    Gateway:         10.64.64.64

    DNS:             10.174.30.245
    DNS:             10.172.30.244


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        6C:62:6D:7C:CE:F2

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8192cu
  State:             disconnected
  Default:           no
  HW Address:        84:1B:5E:9C:8C:14

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    ***** (the name masked)*:           Infra, BC:F6:85:C2:97:92, Freq 2427 MHz, Rate 54 Mb/s, Strength 100 WPA WPA2
    *****(the name masked)*:            Infra, AC:F1:DF:CC:D7:86, Freq 2462 MHz, Rate 54 Mb/s, Strength 100 WPA WPA2








Interestingly, the Mobile Broadband connection works in Ubuntu, but I need the wireless connection as well, to access the university subscribed journals and other resources.

Would appreciate if someone can give any idea how to solve that. Sorry if this is a re-post. I have tried looking for the answer in this forum, but could not find out a solution that is working for this system. 

Thanks in advance.

---

### Post by chili555 on 2014-12-01
Please see my answer here: [http://askubuntu.com/questions/551522/netis-wf2120-wifi-adapter-drops-signal-within-seconds/551648#551648](http://askubuntu.com/questions/551522/netis-wf2120-wifi-adapter-drops-signal-within-seconds/551648#551648)

---

### Post by RICuser on 2014-12-03
Thanks chili555, let me try that out.

---

### Post by RICuser on 2014-12-04
I tried to use the fix suggested by chili555, but for some reason it got stuck while running "git", because it was not installed it said. I tried installing it from suggestions given at other forums, but it just would not work. A part  of it I thought was a connection issue, like multiple times of:  

"*407  Proxy Authentication Required [IP: 10.93.0.32 3128*]" ,   [I]
"[/I]Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/g/git/git-man_1.7.9.5-1_all.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/g/git/git-man_1.7.9.5-1_all.deb)  407  Proxy Authentication Required [IP: 10.93.0.32 3128]*", *
and finally ended with[I] [I]
"[/I][/I]*E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?**[I]"*[/I]
 
Are there any alternatives? May be use some driver that is Ubuntu /Linux compatible? The present USB adaptor is a thumbnail sized Netgear adaptor (can not make out the model number), and it has decided to use the Driver made by Raltek Semiconductors. The website of Netgear products says that they would work with Windows 7, but does not quite promise about Ubuntu or Linux. Thanks.

---

### Post by chili555 on 2014-12-04
Please show me:```
sudo apt-get update
sudo apt-get install git
lsb_release -d
```Thanks.

---

### Post by RICuser on 2014-12-04
Hi chili555,

It is now working.
I have in fact re-installed Ubuntu with the same DVD. This installation was easy, it just asked whether I wanted to replace the old Ubuntu. I think this time it got installed properly (took longer time without error message), and I am also able to use the Update Manager to keep the OS fresh (this was not possible earlier). The wireless got connected easily, and as you said, it took a reboot to function properly. Hope that it continues to run like this. I will have to install Skype again, and hope it does not change any of the settings of the wireless adaptor.

I have run those lines you suggested in your reply, and I saw a big output page. It might not be relevant to paste the whole of it (quite big in size), and I am therefore pasting the first and the last few lines of the output of each input line here:

**RICuser@RICuser:~$ sudo apt-get update **
[sudo] password for RICuser:
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release.gpg
...........[ many lines ]..............
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports/universe Translation-en     
Fetched 4,456 kB in 11s (396 kB/s)                                             
Reading package lists... Done

**RICuser@RICuser:~$ sudo apt-get install git**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  git-man liberror-perl
Suggested packages:
  git-daemon-run git-daemon-sysvinit git-doc git-el git-arch git-cvs git-svn
  git-email git-gui gitk gitweb
The following NEW packages will be installed:
  git git-man liberror-perl
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 6,741 kB of archives.
After this operation, 15.2 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) precise/main liberror-perl all 0.17-1 [23.8 kB]

.......[ and so on ].........

Unpacking git (from .../git_1%3a1.7.9.5-1_amd64.deb) ...
Processing triggers for man-db ...
Setting up liberror-perl (0.17-1) ...
Setting up git-man (1:1.7.9.5-1) ...
Setting up git (1:1.7.9.5-1) ...

**RICuser@RICuser:~$ lsb_release -d**
Description:    Ubuntu 12.04.5 LTS

Finally it is working. Thank you very much, chili555, and Thanks Ubuntu for hosting the forum. Moderators may please consider this thread as solved. Thanks again, and see you when something new crops up.

---

### Post by chili555 on 2014-12-04
Awesome! Glad it's working.> Moderators may please consider this thread as solved. Only the original poster is allowed to use thread tools at the top to mark solved.

---

