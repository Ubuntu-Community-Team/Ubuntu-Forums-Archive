---
title: "Kismet + 4965"
date: 2007-11-06
forum: Networking &amp; Wireless
---

### Post by Braveheart1980 on 2007-11-06
I just installed gutsy on my laptop (Fujitsu Siemens 2428) which has an Intel 4965 wireless card

Ubuntu sees the card correctly,with no use of ndiswrapper

I also installed kismet and edited kismet.conf like this:

```
source= iwl4965,wlan0,addme
```

BUT when I run kismet I get this error

```
FATAL: Unknown capture source type 'iwl4965' in source 'iwl4965,wlan0,addme'

```

Any ideas??

PS iwl4965 is loaded of course

---

### Post by Siph0n on 2007-11-06
I am not at home to check my kismet out, but did you look at the README for kismet? Did u get the exact name of the source to use? Like for me i had to use madwifiab_g or something.

---

### Post by Braveheart1980 on 2007-11-06
> **Siph0n said:**
> I am not at home to check my kismet out, but did you look at the README for kismet? Did u get the exact name of the source to use? Like for me i had to use madwifiab_g or something.

I've read the README like a billion times and it says iwl4965

iwl4965 DOES exist (here /lib/modules/2.6.22-14-generic/ubuntu/wireless/iwlwifi/iwlwifi/origin/iwl4965.ko )

doing an lsmod | grep iwl I got this

```
george@george-laptop:/etc/kismet$ lsmod | grep iwl
iwl4965               101480  0 
iwlwifi_mac80211      175112  1 iwl4965
cfg80211                7304  1 iwlwifi_mac80211

```

Does the 0 (zero) there mean that it isn't loaded?


Something very weird is happening....

---

### Post by Jimmy_r on 2007-11-07
I am having the same problem on open suse...

---

### Post by Braveheart1980 on 2007-11-09
> **Jimmy_r said:**
> I am having the same problem on open suse...

Glad I am not the only one! lol!
 

All we need now is a brilliant mind with a solution.....

---

### Post by kiloecho7 on 2007-11-14
I've had success with using the ipw3945 drivers in kismet for my 4965AGN card.  All you need to do is add "source=ipw3945,wlan0,ipw3945-source" and it should work.  Please post if it does not.

---

### Post by kasperfish on 2007-11-14
what driver are you using?
what is the output of iwconfig?

cheers

---

### Post by Kubunteando on 2007-11-17
Sorry to ask a not related thing in this thread. But I have been looking around in forums and in the Internet about the AMILO Xi 2428 and I have found absolutely no information about how compatible is with Linux.

I am considering to buy it, but no way without knowing how Linux friendly it is.

I have created a post for this, so I would be happy if you can give me some hints:

[http://ubuntuforums.org/showthread.php?p=3787022#post3787022](http://ubuntuforums.org/showthread.php?p=3787022#post3787022)

Thsnks

---

### Post by NijiHunt on 2007-11-23
Hi,
I have the same problem, are you using the deposit kismet? try compiling the new one and the[ mac80211 and iwlwifi driver]("http://www.intellinuxwireless.org/?p=mac80211&n=Downloads") 
I will give it a try this evening and give you my feedback.

cya, tec

OMG cant register my real nick... TecHunter

---

### Post by Braveheart1980 on 2007-11-24
Any luck anybody?
Any new info?

PS My iwconfig output is this

```
george@george-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

---

### Post by c1rcu17 on 2007-12-10
no ideas?

---

### Post by Sarcaza on 2007-12-24
To get Kismet to work with Intel PRO/Wireless 4965 AG or AGN, using modules iwl4965, I did this:

Download  kismet_2007-10-R1-2_i386.deb from Hardy, it installed fine, despite the fact that I'm running Gutsy.  

I then added:
source=ipw3945,wlan0,ipw3945-source

to the /etc/kismet/kistmet.conf file

After this, kismet started without complaint.

Note that it would NOT work with the version that comes with Gutsy.

Sarcaza

---

### Post by Kevin_Jim on 2008-03-06
I have the exact same laptop and I installed Ubuntu Hardy on it. I have to say that in 7.10 the wi-fi was detected. In Hardy that happened only once... I don't know why.

PS: Just to know, the multimedia keys ( all of them ) work now fine still the web cam don't. If anyone know something about those problems feel free to share :)

---

### Post by farruinn on 2008-04-13
According to [http://www.kismetwireless.net/CHANGELOG](http://www.kismetwireless.net/CHANGELOG) support for the iwl sources was added after version 2007-01 (the one in gutsy):

```
Aug 24 2007  devel  Added iwl4965 source
```

---

### Post by thoughtbox on 2008-05-15
Hello,

With Heron, kismet will trigger a kernel panic when using the iwl4965 drivers (on a t61p, amd64).

I'm unable to provide a good trace as I do not have any serial cables (well, USB to serial in this case, I would think) to hand. In addition, I'm having trouble setting the console resolution so that I may capture more of the trace.

Here's what I've got; this may be too little to be useful.

[FONT="Courier New"][0.000000]   [<ffffffff88b4f64a>] :iwl4965:iwl_rx_queue_restock+0xba/0x140
[0.000000]   [<ffffffff88afb6d2>] iwlwifi_mac80211:ieee80211_tasklet_handler+0xb2/0x110
[0.000000]   [<ffffffff80243329>] tasklet_action+0x49/0xb0
[0.000000]   [<ffffffff80243235>] __do_softirq+0x75/0xe0
[0.000000]   [<ffffffff8020d50c>] call_softirq+0x1c/0x30
[0.000000]   [<ffffffff8020ed25>] do_softirq+0x35/0x90
[0.000000]   [<ffffffff802431b8>] irq_exit+0x88/0x90
[0.000000]   [<ffffffff8020ef70>] do_IRQ+0x80/0x100
[0.000000]   [<ffffffff8020b4e0>] mwait_idle+0x0/0x50
[0.000000]   [<ffffffff8020b390>] default_idle+0x0/0xa
[0.000000]   [<ffffffff8020c891>] ret_from_intr+0x0/0xa
[0.000000]   <EOI> [<ffffffff8020b522>] mwait_idle+0x42/0x50
[0.000000]   [<ffffffff8020b43f>] cpu_idle+0x6f/0xc0
[0.000000]   [<ffffffff805d6bb5>] start_kernel+0x2b5/0x340
[0.000000]   [<ffffffff805d612e>] _sinittext+0x12e/0x140
[0.000000]
[0.000000]
[0.000000]  Code: 0f 0b eb fe 0f 1f 44 00 00 48 83 ec 18 49 89 d2 48 8b 57 20
[0.000000]  RIP 803dd5b7 skb_under_panic+0x57/0x60
[0.000000]   RSP 8062ad10
[0.000000]  ---[ end trace 0c05198b58832548 ]---[/FONT]

Does this help?

/tb

---

### Post by sinling on 2008-05-16
> **thoughtbox said:**
> Hello,

With Heron, kismet will trigger a kernel panic when using the iwl4965 drivers (on a t61p, amd64).

I'm unable to provide a good trace as I do not have any serial cables (well, USB to serial in this case, I would think) to hand. In addition, I'm having trouble setting the console resolution so that I may capture more of the trace.

Here's what I've got; this may be too little to be useful.

[FONT="Courier New"][0.000000]   [<ffffffff88b4f64a>] :iwl4965:iwl_rx_queue_restock+0xba/0x140
[0.000000]   [<ffffffff88afb6d2>] iwlwifi_mac80211:ieee80211_tasklet_handler+0xb2/0x110
[0.000000]   [<ffffffff80243329>] tasklet_action+0x49/0xb0
[0.000000]   [<ffffffff80243235>] __do_softirq+0x75/0xe0
[0.000000]   [<ffffffff8020d50c>] call_softirq+0x1c/0x30
[0.000000]   [<ffffffff8020ed25>] do_softirq+0x35/0x90
[0.000000]   [<ffffffff802431b8>] irq_exit+0x88/0x90
[0.000000]   [<ffffffff8020ef70>] do_IRQ+0x80/0x100
[0.000000]   [<ffffffff8020b4e0>] mwait_idle+0x0/0x50
[0.000000]   [<ffffffff8020b390>] default_idle+0x0/0xa
[0.000000]   [<ffffffff8020c891>] ret_from_intr+0x0/0xa
[0.000000]   <EOI> [<ffffffff8020b522>] mwait_idle+0x42/0x50
[0.000000]   [<ffffffff8020b43f>] cpu_idle+0x6f/0xc0
[0.000000]   [<ffffffff805d6bb5>] start_kernel+0x2b5/0x340
[0.000000]   [<ffffffff805d612e>] _sinittext+0x12e/0x140
[0.000000]
[0.000000]
[0.000000]  Code: 0f 0b eb fe 0f 1f 44 00 00 48 83 ec 18 49 89 d2 48 8b 57 20
[0.000000]  RIP 803dd5b7 skb_under_panic+0x57/0x60
[0.000000]   RSP 8062ad10
[0.000000]  ---[ end trace 0c05198b58832548 ]---[/FONT]

Does this help?

/tb

i have the same problem with my 64bit hardy heron too. once i run kismet for 1 minute, my notebook hang completely. i use iwl4965 as my source. it hapen to airodump and aicrack. my notebook totally locked up and have to do hard reboot.

lsmod | grep iwl4965

:~$ lsmod |grep iwl
iwl4965               118516  0 
iwlwifi_mac80211      251876  1 iwl4965
cfg80211               17680  1 iwlwifi_mac802

any idea what happen?

---

### Post by gimmic on 2008-05-22
Seeing the same problem with my 4965 AGN :(

---

### Post by gimmic on 2008-05-23
Have you guys tried using iwconfig to set the mode to 'monitor' rather than managed? I had to do this to enable sniffing(via tcpdump) with the AGN.

> **Braveheart1980 said:**
> Any luck anybody?
Any new info?

PS My iwconfig output is this

```
george@george-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

---

