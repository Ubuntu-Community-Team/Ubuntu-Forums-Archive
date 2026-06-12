---
title: "Tweaks for Ubuntu"
date: 2014-04-19
forum: Networking &amp; Wireless
---

### Post by vanquishedangel on 2014-04-19
Hello there, I am posting some tweaks that I know about for various parts of ubuntu so that they are in one place. Over the years there have been so many I can not possibly remember them all. Not all of these will have to do with networking however so I suspect this thread may be moved but there is a big part for networking. Keep in mind that many of these settings are for my computer, I have a wireless card (cheap one), 30mb connection, a fairly new wireless router (cheap one), and I am actually on the latest lubuntu (14.04). These settings should be applicable for most people however despite the differences in our computers. Feel free to comment your tweaks!

 **[COLOR="#008000"]*****Legend*****[/COLOR]**
***Bold and italic***= command line, copy and paste
**[COLOR="#FF0000"]Bold and red[/COLOR]**= computer specific information, will need to be replaced with your specific information
**[COLOR="#0000CD"]Bold and blue[/COLOR]**= application the settings will be applied to
_Underlined_= under this category in the window open




***sudo gedit /etc/sysctl.conf***  (add to end of file, makes internet faster for me, copy and paste what is below and save it)

# Tweaks for faster broadband...
net.core.rmem_default = 524288
net.core.rmem_max = 67108864
net.core.wmem_default = 524288
net.core.wmem_max = 67108864
net.ipv4.tcp_wmem = 4096 196608 3145728
net.ipv4.tcp_rmem = 4096 3932160 62914560
net.ipv4.tcp_mem = 524288 524288 524288
net.ipv4.tcp_rfc1337 = 1
net.ipv4.tcp_mtu_probing = 1
net.ipv4.ip_no_pmtu_disc = 0
net.ipv4.tcp_sack = 1
net.ipv4.tcp_fack = 1
net.ipv4.tcp_window_scaling = 1
net.ipv4.tcp_timestamps = 1
net.ipv4.tcp_ecn = 0
net.ipv4.route.flush = 1
# don't cache ssthresh from previous connection
 net.ipv4.tcp_no_metrics_save = 1
 net.ipv4.tcp_moderate_rcvbuf = 1
  # recommended to increase this for 1000 BT or higher
 net.core.netdev_max_backlog = 2500
 # for 10 GigE, use this
 # net.core.netdev_max_backlog = 30000  
[COLOR="#000000"][/COLOR]


***sudo gedit /etc/rc.local***  (you will need to use your connection name and replace mine where it is bold and red, make internet more stable with less fluctuation in speed, some wireless modems and routers may not play nice with this setting, copy and paste what is below and save it)

/sbin/ifconfig [COLOR="#FF0000"]**wlan0**[/COLOR] txqueuelen 10000




***sudo apt-get install hdparm sdparm varnish preload prelink zram-config***  (these help make my computer a little faster)




***sudo aticonfig --initial -f*** (for ati cards only, even if you are using the ones from the repo)





***sudo gedit /etc/default/grub*** (find and replace the lines below with the differences)

GRUB_TIMEOUT=0

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash elevator=deadline"

***sudo update-grub2***




My **[COLOR="#0000CD"]wine registry[/COLOR]** settings (you can copy and paste these to a file and save it as reg.reg, the run **regedit** in terminal, select registry ---> import registry file then pick the file you made) The red bolded parts can be omitted or you will need to place your correct information in place of those lines.

REGEDIT4

[HKEY_CURRENT_USER\Software\Wine\Direct3D]
"DirectDrawRenderer"="opengl"
"Multisampling"="enabled"
"Nonpower2Mode"="repack"
"OffscreenRenderingMode"="fbo"
"RenderTargetModeLock"="readtex"
"StrictDrawOrdering"="enabled"
"UseGLSL"="enabled"[COLOR="#000000"][/COLOR]
"VertexShaderMode"="hardware"
[COLOR="#FF0000"][B]"VideoDescription"="ATI Radeon HD 7750"
"VideoDriver"="ati2dvag.dll"
"VideoMemorySize"="1024"
"VideoPCIDeviceID"="dword:0000683f"
"VideoPCIVendorID"="dword:00001002"[/B][/COLOR]




You can also speed up **[COLOR="#0000CD"]libreoffice[/COLOR]** a ton by opening libreoffice and clicking tools ---> options ---> memory and setting these values under _Graphics cache_ (these valuse can be set to what you desire):

use for libreoffice ---------->200
memory per object --------> 20

Then under _Cache for inserted objects_

number of objects ----------> 100

---

### Post by actionmystique on 2014-07-01
Thanks for sharing your tweaks.

However, I've found some of your settings surprising sometimes; **the max values are not the same**:
- net.core.rmem_max = **67108864**
- net.ipv4.tcp_rmem = 4096 3932160 **62914560**

- net.core.wmem_max = **67108864**
- net.ipv4.tcp_wmem = 4096 196608 **3145728**

- net.ipv4.tcp_mem = 524288 524288 **524288**

Any explanation?

Furthermore, I don't see how **disabling Explicit Congestion Notification** helps to get better performances:losing more segments/packets does not help.
net.ipv4.tcp_ecn = 0

---

