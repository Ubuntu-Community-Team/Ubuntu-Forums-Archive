---
title: "slow download rate"
date: 2009-02-10
forum: New to Ubuntu
---

### Post by anico on 2009-02-10
I'm very new to Ubuntu 8.04 so i appreciate step by step guides :)
I have been getting trouble with download speeds as they are ridiculously slow compared to my vista. I looked at many forums and it looks like i'm not the only one...however i don't always understand the steps they carry out. Any sort of download goes an average of 25kb/sec which is horrible! I already followed the procedure to disable Ipv6 but still nothing..i appreciate any sort of help.
Thank you!

---

### Post by jbrown96 on 2009-02-10
What type of connection are you using? Is it DSL, cable, etc.? How is your computer connected to the modem? Directly, through a router (wired/wireless)? If wireless, is it encrypted (WEP/WPA) and what is the strength (how many bars)? Could you give some more information about your hardware? Open a terminal (Apps--->Accessories--->terminal) and copy/paste the output of ```
lspci
```

---

### Post by anico on 2009-02-10
thank you for replying so soon,
i am currently connected to cable via wireless which i don't believe is encrypted WPA/WEP . The strength is very good 98% and full bars.
Here is the info when i typed lspci:

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8055 PCI-E Gigabit Ethernet Controller (rev 13)
03:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN Network Connection (rev 61)
09:04.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ba)
09:04.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 04)
09:04.3 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 11)
09:04.4 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 11)

I hope this helps!

---

### Post by mkvnmtr on 2009-02-10
You are talking about download speed. Is it torrents or something else. You might try to download just a little of the Ubuntu distro to see how your speeds are there. Or mention the program youo are using to get slow speeds.

---

### Post by avtolle on 2009-02-10
One other thing to keep in mind; downloading is a two-way street, and if the source from which you are downloading is busy, the speed you see will, in many instances, be reduced over what it might otherwise be. I notice great variances depending on the time of day, etc. 

That said, what is being downloaded and from where? And, as posted earlier, what program are you using for your downloads?

---

### Post by jbrown96 on 2009-02-10
As others have said, it could be slow servers, but I seriously doubt it.

Sometimes Ubuntu decides to drop into lower transmission rates if the signal is noisy. This can happen with a weak signal, but also with too strong of one as well. My dad had a problem with this; his laptop was about 2 feet from the wireless router. If you're this close try moving farther away. We can also check the transmission speed with ```
iwconfig
```

If it is unencrypted, there may also be other people using your wireless, which could cause the slowdown. I know how to help if the router is Linksys brand (blue and black), but not sure about other companies.

---

### Post by anico on 2009-02-10
I am not downloading torrents. Whenever i download a file from anywhere.. say i want to open a file that was sent to me as an attachment.. it will literally take more than half an hour to open 24MB worth of a .pdf file. I know that downloading is a two way process but i suspect it's something to do with Ubuntu. I mean.. it's so slow that it took me 5 minutes to load a wallpaper right now. (I am sorry i am not very technical.. )
This is something that shouldn't take that long...
I moved far and near the Linksys wireless but it doesn't seem to improve this...Surfing itself the internet is fine with firefox but anything that seems to require some sort of downloading takes all of it's time. Youtube videos are also very slow. I reinstalled flash but i don't think that's the problem.
I typed in iwconfig:

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"datavalet-902"  Nickname:""
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:1D:7E:96:9D:D8   
          Bit Rate=54 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Power Management:off
          Link Quality=80/100  Signal level=-49 dBm  Noise level=-83 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

I am in a student residence and the internet is provided by the place.. it is secured though via password so only my two other roommates can connect to this linksys.

---

### Post by anico on 2009-02-10
there's no smileys on my code though (they kinda take away the seriousness haha)

---

### Post by unutbu on 2009-02-10
I don't know how to solve your problem, but perhaps try pinging the router and then some external site like google.com. Try it from Linux, and also from Windows. Please post the result.

I'm just curious if the problem can be exhibited in a low-level way (through pings -- in which case it might be a driver problem) or only in a high-level way (via downloading -- in which case it might be an application software issue).

---

### Post by jbrown96 on 2009-02-10
I want to try transferring something over the local network and see what type of transfer speed you get. Perhaps someone else knows a better way to do this, but I can't think of one. ```
sudo apt-get install openssh-server
``` That 24MB pdf will work, but the large the file is the better. the following command is going to create a secure link from your computer to your router and then back to your computer. This will your local connection. 

1) find you ip address ```
ifconfig
``` It will be in the wlan0 section and will probably be start with 192 or 10. Remember this. I'm going to call it $IP, so just replace it with what you've found.

2) Find your file that you want to transfer. videos would be good. 

3) transfer the file using the following command. ```
scp $file $USER@$IP:./Desktop/test
``` This needs little explanation. After you type scp and the space, you can either type in your file for $file or you can drag and drop it. You can leave $USER. 

4) agree to add the host and then enter your password
What kind of transfer speed do you see?

After this test, you should remove the server since it opens a hole in your firewall and adds another service that starts at boot up.
```
sudo apt-get remove openssh-server
```

---

### Post by anico on 2009-02-10
jbrown96: I've been trying to do that for some time now. After the first command something installed and it downloaded at 34kb/s. i get everything ok until typing the name of the file or dragging it. When i dragged it and typed the rest of the command it asked me for permission.. and then it replies:
"no such file in directory"

I tried many combinations but i cannot understand what is going on! Sorry for my complete lack of knowledge but this is all so new to me.

Unutbu: I am sorry i couldn't follow your advice :( i didn't really understand what you meant! thank you for trying to help me though

---

### Post by unutbu on 2009-02-10
Hi anico, sorry about being cryptic in my last post. 
Perhaps try this: While in Ubuntu, open a terminal (Applications>Accessories>Terminal) and type

```
route -n
```
You should see a line that looks something like this:

```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         **UG **   100    0        0 wlan0
```
You might see many lines. Look for the one with UG flag.
Look for the gateway address. In the above example, the gateway address is 192.168.1.1. That is the IP address of your router.

Now try pinging your router and google.com:

```

ping -c 5 192.168.1.1
ping -c 5 google.com

```

The output will show us how long it takes for your machine to send/receive a packet to/from the router.

Save the output in a file, so you can post it later. 

Next, boot up Windows. Click the start button, and select the menu item to run a command. Then type
```

ping -n 5 192.168.1.1
ping -n 5 google.com
```
Please post that output too.

---

### Post by vernonrj on 2009-02-11
I have the same wireless card, and the default driver is at fault. Luckily, that means that there's a very easy fix for this: download a better driver.
I've had a lot of luck with Compat-Wireless' driver, which you can get from here:
[http://www.orbit-lab.org/kernel/compat-wireless-2.6/2009/02/](http://www.orbit-lab.org/kernel/compat-wireless-2.6/2009/02/)
Just download the latest driver. In advance, I'm not the best with code, so bear with me.
1) extract the driver. Personally, I have a 'wireless drivers' folder in my home folder, but I'm pretty sure there's a better place for it.
2) navigate to the folder in terminal. If you put it straight into your home folder, just type (in terminal)

```
cd ~/folder-name
make
sudo make install
sudo make unload
sudo make load
```

Hopefully, you'll have a new driver running. Keep in mind this does not set the driver to automatically load at startup. (if you have problems, you can just restart and the default driver will load). Then I think you can type in terminal:

```
gksudo gedit /etc/modules
```

Now I think you just add 

```
iwlagn 
```

to the list and it should load at startup.

---

### Post by anico on 2009-02-11
Uh-oh.. guys i appreciate the help! i tried to follow the post above telling me to change driver but what happened now is that i lost complete access to the internet! My gedit did not show anything and i couldn't type the code necessary. I restarted many times but i can't connect to the internet again! what do i do?? Please help!! I would really appreciate this!!:confused:

---

### Post by jbrown96 on 2009-02-11
Try ```
sudo modrpobe iwlagn
``` to load the module. You might have to ```
sudo ifconfig wlan0 up
``` afterwards.

If that still doesn't work, post back with the following outputs, but reboot if you did the two steps previous. ```
cat /etc/modules
``` ```
lsmod
``` ```
ifconfig
```

---

### Post by vernonrj on 2009-02-11
your gedit didn't show anything? Could you be more specific? Did a file come up? The title should be "modules." if it didn't come up, try navigating to /etc and see if there is a "modules" file. 

Have you tried manually loading the driver from its folder? Just navigate to the folder in terminal and type:
```
sudo make load
```
and that should load the driver. 

did you edit the modules file? If so, to revert to the original driver you can just type
```
gksudo gedit /etc/modules
```
into terminal and remove iwlagn from the list. You can then reboot, and that should get you back up.

---

### Post by hyperyoda on 2009-02-11
First make sure you do not have some process that is eating up your bandwidth. Download a program like ethstats which will show you the traffic passing through your network interface card. Also look at the output of "ps auxw" and see if there are any strange processes in there. You may want to use one of the programs that checks for rootkits present to see if you were hacked. If you were hacked your system could be used as a torrent node or an FTP server etc. I suggest you get an Ubuntu Live CD and boot off of it (if you don't have it or can't burn one ask a friend) and then test your network connecting by pinging a site like google.com. Let us know what you find out.

Zach

---

### Post by anico on 2009-02-11
I tried all the following commands:
alexander@alexander-laptop:~$ sudo modrpobe iwlagn 
sudo: modrpobe: command not found 
alexander@alexander-laptop:~$ iwlagn 
bash: iwlagn: command not found 
alexander@alexander-laptop:~$ sudo modrpobe iwlagn 
sudo: modrpobe: command not found 
alexander@alexander-laptop:~$ sudo ifconfig wlan0 up 
SIOCSIFFLAGS: No such file or directory 
alexander@alexander-laptop:~$ cat /ect/modules 
cat: /ect/modules: No such file or directory 
alexander@alexander-laptop:~$ lsmod 
Module                  Size  Used by 
ipv6                  311848  10  
i915                   38144  2  
drm                   105896  3 i915 
rfcomm                 47392  2  
l2cap                  28800  13 rfcomm 
ppdev                  11400  0  
acpi_cpufreq           10832  2  
cpufreq_ondemand       11152  1  
cpufreq_conservative    10632  0  
cpufreq_stats           8416  0  
cpufreq_powersave       3200  0  
freq_table              6464  3 acpi_cpufreq,cpufreq_ondemand,cpufreq_stats 
cpufreq_userspace       6180  0  
sbs                    17808  0  
dock                   12960  0  
container               6656  0  
sr_mod                 20132  0  
cdrom                  41512  1 sr_mod 
sbshc                   8960  1 sbs 
iptable_filter          4608  0  
ip_tables              24104  1 iptable_filter 
x_tables               23560  1 ip_tables 
sbp2                   27272  0  
parport_pc             41128  0  
lp                     14916  0  
parport                44300  3 ppdev,parport_pc,lp 
joydev                 15488  0  
arc4                    3456  2  
snd_hda_intel         442200  3  
ecb                     5248  2  
blkcipher               9476  1 ecb 
snd_pcm_oss            47648  0  
snd_mixer_oss          20224  1 snd_pcm_oss 
snd_pcm                92168  2 snd_hda_intel,snd_pcm_oss 
snd_page_alloc         13200  2 snd_hda_intel,snd_pcm 
snd_hwdep              12552  1 snd_hda_intel 
pcmcia                 45976  0  
snd_seq_dummy           5764  0  
iwlagn                116228  0  
iwlcore                97792  1 iwlagn 
snd_seq_oss            38912  0  
led_class               7176  1 iwlcore 
uvcvideo               62212  0  
hci_usb                19228  2  
snd_seq_midi           10688  0  
mac80211              267392  2 iwlagn,iwlcore 
compat_ioctl32         11136  1 uvcvideo 
snd_rawmidi            29856  1 snd_seq_midi 
videodev               30720  1 uvcvideo 
bluetooth              67620  7 rfcomm,l2cap,hci_usb 
snd_seq_midi_event     10112  2 snd_seq_oss,snd_seq_midi 
v4l1_compat            15492  2 uvcvideo,videodev 
usb_storage            82624  1  
sky2                   53892  0  
psmouse                46236  0  
ac                      8328  0  
v4l2_common            21888  3 uvcvideo,compat_ioctl32,videodev 
libusual               23648  1 usb_storage 
snd_seq                63232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event 
evdev                  14976  7  
cfg80211               41752  3 iwlagn,iwlcore,mac80211 
tpm_infineon           11836  0  
tpm                    19488  1 tpm_infineon 
tpm_bios                9728  1 tpm 
battery                16776  0  
serio_raw               9092  0  
snd_timer              27912  2 snd_pcm,snd_seq 
sony_laptop            40624  0  
snd_seq_device         10644  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq 
video                  23444  0  
yenta_socket           30092  1  
rsrc_nonstatic         14080  1 yenta_socket 
pcmcia_core            46116  3 pcmcia,yenta_socket,rsrc_nonstatic 
pcspkr                  4992  0  
iTCO_wdt               15312  0  
snd                    70856  17 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device 
output                  5632  1 video 
ricoh_mmc               5120  0  
iTCO_vendor_support     5764  1 iTCO_wdt 
button                 10912  0  
shpchp                 38172  0  
pci_hotplug            34608  1 shpchp 
intel_agp              30624  1  
soundcore              10400  1 snd 
ext3                  149264  1  
jbd                    57000  1 ext3 
mbcache                11392  1 ext3 
sg                     41880  0  
sd_mod                 33280  5  
ata_piix               24196  2  
pata_acpi               9856  0  
ata_generic             9988  0  
libata                176560  3 ata_piix,pata_acpi,ata_generic 
scsi_mod              178488  6 sr_mod,sbp2,usb_storage,sg,sd_mod,libata 
ehci_hcd               41996  0  
ohci1394               36532  0  
ieee1394              106968  2 sbp2,ohci1394 
uhci_hcd               29856  0  
usbcore               170288  7 uvcvideo,hci_usb,usb_storage,libusual,ehci_hcd,uhci_hcd 
thermal                19744  0  
processor              40424  4 acpi_cpufreq,thermal 
fan                     6792  0  
fbcon                  46336  0  
tileblit                4096  1 fbcon 
font                   10112  1 fbcon 
bitblit                 7424  1 fbcon 
softcursor              3712  1 bitblit 
fuse                   56112  5  
alexander@alexander-laptop:~$ ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:1a:80:58:0a:5e   
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000  
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
          Interrupt:16  
 
lo        Link encap:Local Loopback   
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0  
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 

Whenever i type gedit /ect/modules it opens gedit and it is a file named modules but it is completely blank! in fact that happened to me every single time i typed something with gedit in it! 

umm.. the fact that you think i'm hacked scares the crap out of me.. i'm really beginning to think ubuntu is much more complicated and vulnerable than i originally thought! I will download the programs you indicated promptly!!

Thanks a lot!

---

### Post by vernonrj on 2009-02-11
1) Copy and paste this code into your terminal:
```
gksudo gedit /etc/modules
```
you should get the correct file if you just copy/pasted this in. Now add ```
iwlagn
``` to the bottom of the list to load it at startup.

2) to load it type
```
sudo modprobe iwlagn
```

I think that should do it.

---

### Post by anico on 2009-02-11
Ok i was able to get gedit to actually show something! so that's progress i guess.. i typed in iwlagn and saved the file.. loaded it with the modprobe command.. but still nothing.. 
i tried connecting it LAN and it works fine! i guess it's the wireless that somehow is screwed up. Another thing.. when i clicked on [http://www.orbit-lab.org/kernel/comp...s-2.6/2009/02/](http://www.orbit-lab.org/kernel/comp...s-2.6/2009/02/) i downloaded the file that contained 'old' in it: "compat-wireless-old 2009 02-11.tar.bz"... should have i downloaded the one without it??

---

### Post by anico on 2009-02-11
nevermind i downloaded that one and it prompted an error message in terminal telling me to use the 'old' file... is there a way to uninstall this driver and install the old one??

---

### Post by trikster_x on 2009-02-11
When you used vernonrj's instructions, did you get any errors other the the gedit ordeal?  Specifically errors involving the make commands.

---

### Post by anico on 2009-02-11
while i was installing the driver i did get some errors which ran along the lines of "FATAL: ....." I cannot remember the exact line these errors occured in the sudo make install command.. when i reinstalled the driver it gave me "FATAL: driver already in use. ERROR=1"
...maybe it's the driver itself?

The gedit problem is fixed though i am able to see the codes and modify them by typing iwlagn...

---

### Post by trikster_x on 2009-02-11
The first thing you need to do is remove everything that has failed.  Basically undo everything that has been done since you started this thread.  I think you have too much extra stuff floating around right now.  Do you know the locations of everything you have installed to try and fix the problem?

Even better yet, do you have access to a liveCD right now?

---

### Post by anico on 2009-02-11
To be honest i don't think i even know how to begin to uninstall all i've installed these 2 days. 
I do have the installation cd for ubuntu.. is that the same as the liveCD?

---

### Post by vernonrj on 2009-02-11
Did modprobe give any errors? If it didn't, the module should be loaded. If it didn't give any errors, make sure wireless networking is enabled (the network icon in your notification area).

edit: some of those fatal errors are not so fatal... They show up for some reason even if the driver is working. Don't ask me why. Anyway, to uninstall, navigate to the driver's folder in terminal and simply type

```
sudo make unload
sudo make uninstall
```

Also, I know for a fact that the 2009-01-19 driver works really well, if you want to try another one.
And one last thing I forgot... I think it's best to only keep one compat-wireless driver installed at a time, since they conflict and give that error. I think that's it this time.

---

### Post by anico on 2009-02-11
Thanks vernonrj for all of your input! I hope i can get this to work! 
so what i've done now is that i uninstalled the driver with those commands...i will download the driver that you just mentioned i'll let you know if something goes buggy!

---

### Post by vernonrj on 2009-02-11
okay... last thing. You don't have to use a livecd as long as you were just sticking to what I saw in this guide. You just have to uninstall one of the drivers.

edit: sorry, didn't see you replied while I was typing. Good luck with the driver.

---

### Post by anico on 2009-02-11
I tried to install the driver but it gave me this error:
alexander@alexander-laptop:~/compat-wireless-2.6-old$ make unload
Unloading mac80211...
FATAL: Module mac80211 is in use.
Unloading cfg80211...
FATAL: Module cfg80211 is in use.
make: *** [unload] Error 1

this i guess shows that the previous driver was not uninstalled...how can i make sure that the driver is uninstalled completely? 
Also.. i don't get any errors at all with the sudo modprobe iwlagn..

---

### Post by vernonrj on 2009-02-11
try
```
sudo make unload
```

edit: also, type
```
sudo make uninstall
```
in any driver folder you think is still installed.

---

### Post by anico on 2009-02-11
ugh.. no change what-so-ever
alexander@alexander-laptop:~/compat-wireless-2.6-old$ sudo make unload
Unloading mac80211...
FATAL: Module mac80211 is in use.
Unloading cfg80211...
FATAL: Module cfg80211 is in use.
make: *** [unload] Error 1

---

### Post by vernonrj on 2009-02-11
Okay, so I think I know what your problem is. Don't worry about the 'old' driver. Go to the folder of the driver you intend to use, in terminal. If you haven't 'made' it already, type

```
make
```

Then type

```
sudo make install
```

Finally, type

```
sudo make load
```

I just figured out that ubuntu automatically uninstalls the other compat-wireless drivers when you type sudo make install, so you don't need to worry about old drivers. That should be it.

---

### Post by anico on 2009-02-12
ok i've tried with various drivers... still nothing.. the wireless doesn't work at all. Do you know if i can make my old one work again??

---

### Post by vernonrj on 2009-02-12
One final thing... 
```
sudo ifconfig wlan0 up
```
and make sure the 'enable wireless' is checked in the network icon in your notification area.

If that doesn't work, to get the default driver again, go to where the driver is installed, and
```
sudo make uninstall
```

remove the driver from startup by typing
```
gksudo gedit /etc/modules
```
and removing iwlagn. Sorry I couldn't get it to work for you... I don't know what the problem is; it should be working.

---

### Post by anico on 2009-02-12
I can't seem to understand why when i copy/paste "sudo ifconfig wlan0 up"
i get the following result:

SIOCSIFFLAGS: No such file or directory

Also.. one last thing.. (i'm so sorry to bother you this way) the driver is installed in home right? so in order to uninstall it i have to do the following? 
~cd /compat-wireless-2.6-old 
and then type the command to uninstall??

Again thank you so much

---

### Post by vernonrj on 2009-02-12
yeah, the driver is installed in home, so yeah, you would navigate to it with 
```
cd ~/compat-wireless-x-x-x
```
and then uninstall it with
```
sudo make uninstall
```
... what is your kernel version? You can use
```
uname -r
``` to find out.
Did you get an error when you tried to install or make the compat-wireless-old driver?

---

### Post by anico on 2009-02-12
first of all thank you so much for all of your help!!
somehow.. my wireless came back!! although the downloading speed isn't that fantastic.. it's still amazing to get my wireless working again!
I think i'm going to relax a little bit when it comes to dealing with my driver for the moment but i will address the issue some time later! 
Again thank you!

---

### Post by vernonrj on 2009-02-12
No problem. Sorry I couldn't help you.

---

