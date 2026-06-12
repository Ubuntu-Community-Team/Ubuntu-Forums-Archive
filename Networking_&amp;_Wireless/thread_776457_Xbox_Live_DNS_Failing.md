---
title: "Xbox Live DNS Failing"
date: 2008-04-30
forum: Networking &amp; Wireless
---

### Post by condawg on 2008-04-30
Hey =]
I've used some tutorials around here (bits and pieces from a few, as none of them seemed to work fully), and my Xbox can find the IP address in a jiff, but when it gets to DNS, it fails.
I've fiddled with it for a while to no avail.

Firestarter doesn't work for me, so that's out of the question.

Anybody able to help?
Thanks =]

---

### Post by coheed on 2008-04-30
condawg, same problem here. I've searched EVERYWHERE and spent hours trying to get a wireless->wired network bridge to work with Ubuntu 8.04 and nothing has worked. Keep me posted on what you find out, and I'll do the same for you!

---

### Post by superprash2003 on 2008-04-30
i believe you can set the DNS manually in the dashboard.. have you tried that?

---

### Post by condawg on 2008-04-30
> **superprash2003 said:**
> i believe you can set the DNS manually in the dashboard.. have you tried that?

Yessir... I have it set to 192.168.1.1 and 192.168.1.2 as the secondary.
Am I doing something wrong there?
Thanks =]

---

### Post by superprash2003 on 2008-05-01
set it as 208.67.222.222 and 208.67.220.220 instead .. these are opendns servers..

---

### Post by condawg on 2008-05-01
Damn. Still doesn't work.
Thanks, anyway.

I'll try some messing around with that later (gotta go to school now).

---

### Post by condawg on 2008-05-01
Nope.
Can't get it.

I even added those DNS' to the list under "System > Admin > Network" and it doesn't work.

---

### Post by condawg on 2008-05-02
Anyone else?
I'd really like to get this working. =]

---

### Post by robotcontrolledbiodomes on 2008-05-02
Just want to clear this up before I help out more: Is your computer connected wirelessly to your router, and your xbox is connected via crossover cable to your computer's ethernet card?

---

### Post by condawg on 2008-05-02
Yessir, that's the situation.

---

### Post by robotcontrolledbiodomes on 2008-05-02
Ok I was in the same situation so I'll post the steps I took to get xbox live working. I don't know what tutorials you looked at so i'll start from the top

**1)** Assign an ip address to your ethernet card that isn't being used by your router, and isnt on the same network. For instance, if your router's IP is 192.168.1.1, assign the interface an IP of 192.168.2.1

In console: 
> 
sudo ifconfig eth0 up
sudo ifconfig eth0 192.168.2.1

**2)** Check for and enable IP forwarding

> cat /proc/sys/net/ipv4/ip_forward

If the ouput is 0, you will need to enable it by doing (in a root terminal)

> echo "1" > /proc/sys/net/ipv4/ip_forward

**3)** Set up iptables

> sudo iptables -t nat -A POSTROUTING -o wlan0 -s 192.168.2.0/24 -j MASQUERADE

You may have to change 'wlan0' to whatever your wireless device is called (check with the command 'iwconfig'). The 192.168.2.0 is the network you chose for step 1. If you used 192.168.3.1 instead, then change the ip in this command to 192.168.3.0

**4)** Set up the xbox:
Go into dashboard. If you set the eth0 IP from step 1 to 192.168.2.1, set the xbox's IP to 192.168.2.2.
The Gateway will be the IP address of your ethernet card (in this example, 192.168.2.1). The subnet mask will be 255.255.255.0. The primary DNS server will be your router's IP address.

I took these exact steps with my machine and it connected just fine. I think there may be a few more commands you can enter to forward all ports used by xbox live, but I know that this method connects without them. I'll look into it. It looks like a lot but it's only a few commands. Hope this helps

---

### Post by condawg on 2008-05-02
That looks awesome, but in step 2 when making it output 1, it says

"bash: /proc/sys/net/ipv4/ip_forward: Permission denied"

---

### Post by robotcontrolledbiodomes on 2008-05-02
Ah yes indeed it does. Sorry about that. You will need to open a root terminal to do that command, I guess it doesn't work with sudo.

In hardy heron, you can right click on the top bar on the desktop-> edit menus-> then under system tools enable the Root Terminal button, open root terminal, and try the command again, without sudo in front of it

Edit: by right click on the top bar I meant the Applications button

---

### Post by condawg on 2008-05-02
Okay.. I followed all the steps as layed out, and the IP address on the XBL test now fails.

I have it set to 192.168.1.11, since my router is .1.1

---

### Post by robotcontrolledbiodomes on 2008-05-02
Darn it I really messed up on the directions. The IP network on the xbox and the ethernet card have to be different than your router's (like 2.1 instead of 1.1)

Ok lets try this once again (check back on the original instructions in a few mins -- i'll update it)

Restart your comp to clear all the stuff you changed while following the directions

---

### Post by condawg on 2008-05-02
Damn...
I don't see *why*, but the IP is still failing... =S

Thanks for all your help so far, though. I understand this stuff better now.

---

### Post by robotcontrolledbiodomes on 2008-05-02
What is the exact error message? You are configuring IP settings on the xbox manually right? and not with DHCP. The Xbox IP should be on the same network as your ethernet card

---

### Post by condawg on 2008-05-02
Yes, I'm doing it manually, and it's plugged into the ethernet card, so I can only imagine it's on the same network :P

There's no error message, just when I test my XBL connection, it says

"Network Adapter - Wired
 IP Address - Failed"

---

### Post by robotcontrolledbiodomes on 2008-05-02
Ok by same network I meant if the ethernet card's IP is 192.168.2.1, the xbox has to be 192.168.2.something

I guess that would be a subnet and not a network

---

### Post by condawg on 2008-05-02
Yessir
I have my ethernet card's IP as what you have up there ^^
and my xbox's is 192.168.2.2

---

### Post by robotcontrolledbiodomes on 2008-05-02
Sorry it worked for me just fine. Not sure what is causing that error message

---

### Post by condawg on 2008-05-02
Damn.
I'll go through the process again tomorrow.
Thanks, man =]

---

### Post by robotcontrolledbiodomes on 2008-05-04
Hey what a surprise I found another mistake in the procedure. In dashboard, the setting for gateway needs to be the IP address of your ethernet card --not the router.

If you still check this thread and wonder why there are so many mistakes, it's because I had a tutorial for this written for slackware, and I changed some things for ubuntu, but rewrote the tutorial from memory instead of referring back to the old one.

Good luck

---

### Post by condawg on 2008-05-04
Ohhh.
Damn. That's a big one.
Hahaha
I'll try that in a few minute. Thanks =]

Edit: Alriiight! Now the IP is working again!
But we're still failing at DNS... I'll screw with that a bit...
That's the IP of the router, right?

---

### Post by robotcontrolledbiodomes on 2008-05-04
Yea that's definitely the router IP address. Maybe go into your router, and write down the primary and secondary DNS servers it is using and use those in the dashboard.

What's the output of **lsmod** after you've gone through the steps?

---

### Post by condawg on 2008-05-04
Alright, I'll try that. Thanks =]

The output of lsmod is

```
Module                  Size  Used by
af_packet              23812  4 
isofs                  36388  0 
udf                    88612  0 
ipv6                  267780  8 
binfmt_misc            12808  1 
rfcomm                 41744  2 
l2cap                  25728  13 rfcomm
bluetooth              61156  4 rfcomm,l2cap
ppdev                  10372  0 
speedstep_lib           6532  0 
cpufreq_conservative     8712  0 
cpufreq_stats           7104  0 
cpufreq_userspace       5284  0 
cpufreq_powersave       2688  0 
cpufreq_ondemand        9740  0 
freq_table              5536  2 cpufreq_stats,cpufreq_ondemand
sbs                    15112  0 
container               5632  0 
dock                   11280  0 
video                  19856  0 
output                  4736  1 video
sbshc                   7680  1 sbs
battery                14212  0 
ac                      6916  0 
sbp2                   24072  0 
lp                     12324  0 
wlan_scan_sta          14720  1 
ath_rate_sample        14336  1 
snd_intel8x0           35356  4 
snd_ac97_codec        101028  1 snd_intel8x0
ac97_bus                3072  1 snd_ac97_codec
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  1 snd_pcm_oss
snd_pcm                78596  4 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
parport_pc             36260  1 
parport                37832  3 ppdev,lp,parport_pc
snd_seq_dummy           4868  0 
gspca                 643920  0 
evdev                  13056  3 
videodev               29440  1 gspca
v4l2_common            18304  1 videodev
v4l1_compat            15492  1 videodev
snd_seq_oss            35584  0 
snd_seq_midi            9376  0 
snd_rawmidi            25760  1 snd_seq_midi
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24836  3 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    56996  17 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
pcspkr                  4224  0 
soundcore               8800  1 snd
snd_page_alloc         11400  2 snd_intel8x0,snd_pcm
usbhid                 31872  0 
hid                    38784  1 usbhid
ath_pci               101024  0 
wlan                  207728  4 wlan_scan_sta,ath_rate_sample,ath_pci
ath_hal               192592  3 ath_rate_sample,ath_pci
nvidia               7825536  34 
i2c_core               24832  1 nvidia
button                  9232  0 
iTCO_wdt               13092  0 
iTCO_vendor_support     4868  1 iTCO_wdt
shpchp                 34452  0 
pci_hotplug            30880  1 shpchp
intel_agp              25492  1 
agpgart                34760  2 nvidia,intel_agp
iptable_nat             8324  0 
nf_nat                 20396  1 iptable_nat
nf_conntrack_ipv4      19080  2 iptable_nat
nf_conntrack           66752  3 iptable_nat,nf_nat,nf_conntrack_ipv4
iptable_mangle          3712  0 
iptable_filter          3840  0 
ip_tables              14820  3 iptable_nat,iptable_mangle,iptable_filter
x_tables               16132  2 iptable_nat,ip_tables
ext3                  136712  1 
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
sg                     36880  0 
sr_mod                 17956  0 
sd_mod                 30720  3 
cdrom                  37408  1 sr_mod
ata_generic             8324  0 
pata_acpi               8320  0 
8139cp                 24704  0 
floppy                 59588  0 
ata_piix               19588  2 
ohci1394               33584  0 
8139too                27520  0 
mii                     6400  2 8139cp,8139too
ieee1394               93752  2 sbp2,ohci1394
libata                159344  3 ata_generic,pata_acpi,ata_piix
scsi_mod              151436  5 sbp2,sg,sr_mod,sd_mod,libata
ehci_hcd               37900  0 
uhci_hcd               27024  0 
usbcore               146028  5 gspca,usbhid,ehci_hcd,uhci_hcd
thermal                16796  0 
processor              36872  1 thermal
fan                     5636  0 
fbcon                  42912  0 
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50580  3 

```

Where do I find the DNS my router uses?
I'm in the router control panel (192.168.1.1), but I don't see it in there.

EDIT: Nevermind -- found my router's DNS that it uses, tried it, and it *still* doesn't work.

---

### Post by condawg on 2008-05-09
Bump.
I felt like we were onto something there.

---

### Post by slick_8199 on 2008-07-12
Alrighty then. I have been working on this for a week with only dissapointment.

Here is my situation. I am currently trying to completly do away with winblows but I have to prerecs to get out of the way first.

1) ICS xbox live. I have been using winblows with ICS  for my xbox live with a 360. I use a strait cat5 cable connected from the xbox 360 to the laptop and evdo for internet. It works pretty good. I can't however, for the life of me figure out how to get the computer and the xbox to talk to each other in linux. I know you are saposed to use a crossover cable or router but I don't have either. I drive truck so getting to the store is next to impossible.

I'm wondering how windows can use a strait cat5 cable and linux can't (or can it?)

2) still working on getting the delorme earthmate to work with gpsdrive. One thing at a time. I have to prioritize :)

---

### Post by slick_8199 on 2008-07-14
Success!!!!

I have finely got it. The trick is to set the ip address on both the laptop and the xbox and find the ppp0 dns address and then set that on the xbox!
And don't forget to mascorade. NAT
I now have lag free xbox live with evdo

---

