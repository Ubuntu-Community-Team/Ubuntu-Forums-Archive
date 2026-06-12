---
title: "RDP assistance"
date: 2015-06-15
forum: Networking &amp; Wireless
---

### Post by phillip16 on 2015-06-15
Hello everyone,

I have been having another problem with RDP. Concering the VPN, I am installing teamviewer and using this until I can figure out a method for VPN between my two computers.

Now, I have multiple ubuntu machines in my work. All of which are connected to each other via network switch (they all have multiple nics. One is for the switch, the other is for the internet).

I successfully setup the ip addresses for the switch because I am able to ping all of them from each computer. For this issue, I am only going to be focusing on two.

I have two ubuntu computers computer A is attempting to rdp to computer B. Using vino-preferences, I have setup computer B to allow remote desktop with a password. I have installed xrdp and vnc4server (trying different methods). On computer A, I am running remmina. WIth remmina, I am able to connect to computer B via rdp protocol. I know that this is a sercuity concern and that I should do SSH tunneling; however, they are all on the same switch and thus, I figured it was unneccessary. 

I come to the login screen and I see the different options such as sesman-any, rdp-any, and sesman-VNC, and etc. However, I am unable to control the desktop with any of them. The application will "connect" and hang at a black screen, display a successful connection and crash, or will hang at TCP connected. 

I have been  editting the xrdp.ini on computer B for hours and I am unable to determine come up with a solution. Any help will be much appreciated!

Please find below my current configuration for the xrdp.ini:

```
[globals]
bitmap_cache=yes
bitmap_compression=yes
port=3389
crypt_level=low
channel_code=1
max_bpp=24
#black=000000
#grey=d6d3ce
#dark_grey=808080
#blue=08246b
#dark_blue=08246b
#white=ffffff
#red=ff0000
#green=00ff00
#background=626c72

[xrdp1]
name=sesman-Xvnc
lib=libvnc.so
username=
password=
ip=127.0.0.1
port=3350

[xrdp2]
name=console
lib=libvnc.so
ip=127.0.0.1
port=5900
username=
password=

[xrdp3]
name=vnc-any
lib=libvnc.so
ip=ask
port=ask5900
username=
password=

[xrdp4]
name=sesman-any
lib=libvnc.so
ip=192.168.0.2
port=3350
username=
password=

[xrdp5]
name=rdp-any
lib=librdp.so
ip=192.168.0.2
port=ask3389

[xrdp6]
name=freerdp-any
lib=libxrdpfreerdp1.so
ip=ask
port=ask3389
username=
password=

[xrdp7]
name=sesman-X11rdp
lib=libxup.so
username=
password=
ip=127.0.0.1
port=3350
xserverbpp=24
```

---

