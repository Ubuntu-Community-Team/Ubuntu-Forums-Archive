---
title: "Hi all! I'm in need of some help with wireless!"
date: 2009-02-21
forum: New to Ubuntu
---

### Post by Lorjan on 2009-02-21
[FONT="Palatino Linotype"][COLOR="Black"][SIZE="3"]
Hi Everyone,

I'm quite new to Linux, I started using Gutsy almost a year ago and I was doing OK, until I fiddled around with my wireless in the summer. Since then I haven't been able to get it working, no matter what I do, and I decided it was high time I asked for help. I've given it a good go on my own, but with my extremely limited knowledge I'm really struggling! I wish I hadn't left it so long to ask, because various things I have done have made changes - none that have got me online, but things have happened! - and I'm not too sure that I can remember clearly what's what.
I've copied all the suggestions that I've found in forums and I have a page full of notes that make not one bit of sense to me! I'm really hoping some kind person will have a go at figuring out what's wrong. I'll do what I can to help, I'm more than willing to learn!
I am running Gutsy 7.10 on a Siemens AMILO Pi 2515 Notebook, and my wireless router is a BTHomeHub-F418. I'm not sure what else you need to know but I'll do my best give you all the information!
My wireless always worked without a single hitch. As soon as I got the laptop I installed Ubuntu and it all worked perfectly from the start. Then I went on a trip and had to switch between ethernet and wireless a few times. Somewhere around this time the wireless option on network manager disappeared altogether, and was gone for a few days. I did a lot of fiddling over that time but nothing seemed to do any good, then suddenly it was back. It didn't seem like it came back because of anything I had done, but I really don't know. Unfortunately, I couldn't connect to the internet, and haven't since. I have recieved various error messages, the nature of which have changed over time, presumably due to other settings I may have changed. Sorry, I know that's unhelpful!
Now, when I go to connection properties there are two options in the drop down list: eth1:avahi and lo. The status for eth1:avahi is 'disconnected' and when I try to configure it it says "the interface does not exist". The status for lo is 'idle' and it will not let me press the configure button.
When I do lshw -C network the information I get is exactly same as it was when I last tried a month or two ago. I don't know what bits are relevant. It says wireless=unassociated. I'm not sure what else I should be looking for. Any advice would be so much appreciated - I have let this go on for too long!
Apologies for the length of this post, and thanks in advance!

Lorjan
[/SIZE][/COLOR][/FONT]

---

### Post by jerrynewt on 2009-02-21
What is the output of  "ifconfig" and  "iwconfig" in terminal?

---

### Post by Lorjan on 2009-02-21
Hi! Thanks for helping me. Here it is:

ifconfig

eth1      Link encap:Ethernet  HWaddr 00:1C:BF:54:73:97  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:106 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:18 Base address:0x2000 Memory:f8000000-f8000fff 

eth1:avah Link encap:Ethernet  HWaddr 00:1C:BF:54:73:97  
          inet addr:169.254.7.86  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:18 Base address:0x2000 Memory:f8000000-f8000fff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:334 errors:0 dropped:0 overruns:0 frame:0
          TX packets:334 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:30590 (29.8 KB)  TX bytes:30590 (29.8 KB)


iwconfig

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:off/any  
          Mode:Managed  Frequency=nan kHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:16 dBm   
          Retry limit:15   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:107   Missed beacon:0

---

### Post by Lorjan on 2009-02-21
Oh and one thing, maybe irrelevant. I made a couple of rough notes of what it said last time I did ifconfig and it looks similar, but I noticed that last time for eth1 it said RX bytes: 9kb, TX bytes: 7.5kb - I don't know what that means or if it's relevant. I haven't changed any settings since then so I don't know why it would be different.
Thanks again :)

Lorjan

---

### Post by _noob_ on 2009-02-22
is there a switch to turn the internet on or off? If there is try rebooting after turning it on.

---

### Post by bgates on 2009-02-22
The avahi thing is troubling me.  It may be that you do need to use avahi, but it may be helpful to disable it temporarily to do some troubleshooting first and get basic internet working.  Once you can like, ping google and browse to it then avahi could be the second priority if you need it.

Disabling avahi:  [http://ubuntuforums.org/showthread.php?t=499929](http://ubuntuforums.org/showthread.php?t=499929)

---

### Post by Lorjan on 2009-03-01
Hi everyone,

Sorry, I know it's been a few days, I've been away. _noob_ thank you for your suggestion, but unfortunately I have tried all that! It's definitely some sort of configuration problem.
bgates, thanks a lot, I will follow that link and hopefully that will help, my memory is terrible but I don't think I've attempted to turn avahi off before, I wasn't sure why it was on! I'm useless, I know!

Thanks so much, everyone - I'll post after I've tried the avahi thing and let you know how it goes :)

Lorjan

---

### Post by Lorjan on 2009-03-01
Hi,

I just did that avahi thing, now the only option when I click network monitor is 'lo'. I don't know what to do now!! I'm feeling really stuck because it feels as though the tiny amount of knowledge I had is gone and this OS is as foreign to me as ever! I know there has to be a solution though, I'm sure I've just done something stupid. And if someone here can help me I hope will never do something stupid again!!

Thanks again for all your help,

Lorjan

---

### Post by ncoop23 on 2009-03-01
> **Lorjan said:**
> Hi,

I just did that avahi thing, now the only option when I click network monitor is 'lo'. I don't know what to do now!! I'm feeling really stuck because it feels as though the tiny amount of knowledge I had is gone and this OS is as foreign to me as ever! I know there has to be a solution though, I'm sure I've just done something stupid. And if someone here can help me I hope will never do something stupid again!!

Thanks again for all your help,

Lorjan

does ifconfig eth1 up work for you?

---

### Post by Lorjan on 2009-03-09
Hi! Thanks for the reply! No, it doesn't work! 
It says SIOCSIFFLAGS: Permission denied
Someone once told me that that meant the card doesn't understand the command it's being given or something? Is that right?
What can I do?
Thank you all so much
Lorjan

---

### Post by Lorjan on 2009-04-20
Hi Everyone!

Unfortunately I have still had no luck. I have been away, I had to take this computer with me as I didn't have room for both. My problems with the other one are still no closer to a solution! I'm back with it now, and I'm hoping that in bringing this back up someone will be able to tell me something! I am at a total loss!!

Please help!!
Thank you!!

Lorjan

---

### Post by john stiles on 2009-04-20
I know this is not conventional wisdom, but at this stage rather than continue twiddling, I'd backup up your data and simply reinstall. You said in the original post that it worked straight out of the box, so provided you still have the CD you can restart. Then keep a log of your changes and additions. If the problem reoccurs we will have more information to identify what's happened.

---

### Post by Lorjan on 2009-04-20
Hi

Thanks for your reply! That is certainly an idea, and one I have toyed with, I'm just wary about doing in case next time it didn't work. Or perhaps I've installed some things which took a lot of time, which I wouldn't remember how to do again. To be honest I'm not quite sure how it works when you reinstall, I'm not sure what can be backed up, and how much I might lose, etc. But I have a terrible memory and I don't like the idea of starting again and having to do all the little tweaks and things, in case I do something wrong this time. Although I suppose it would be a good learning experience, wouldn't it?

Maybe I'll just do it. I'm not 100% sure if I should! But you've encouraged me! If no one can suggest a way of fixing this, then I'm definitely leaning towards your idea. Thanks!

Lorjan

---

### Post by ninjapirate89 on 2009-04-20
Are you still using Gutsy? Have you considered trying out Hardy or you could wait three more days and give Jaunty a go. Wireless support has only gotten better with each new release.

---

### Post by Lorjan on 2009-04-20
Hi

I am still using Gutsy, I downloaded a Hardy CD a few months ago, but I wasn't too sure about it, and I think as I started to install it I became worried about what I might lose, as I said above, and I decided not to go through with it. I think I might well just back everything up and go for it when the new release comes out. Am I brave enough? I think maybe I am!!

Lorjan

---

### Post by ninjapirate89 on 2009-04-20
Personally I would go ahead and make a backup of any important files and do a fresh install when Jaunty is officially released 3 days from now.

---

### Post by john stiles on 2009-04-20
You have 2 days until the new Jaunty release CD is available to make a list of your favourite programs and back up data.

Personally I clean install each year. I'm always terrified of losing all my tweaks, but strangely never miss them as there are invariable plenty of new toys. 

The caveat to this is that I make a complete back up of my home directory and have my essential internet bookmarks, usernames and passwords on Xmarks (was foxmarks). So just remember your Xmark account and password.

---

### Post by halitech on 2009-04-20
I'm not sure why your wireless is showing as eth1 but it seems to me from this that the card is recognized

```
eth1 unassociated ESSID:off/any
Mode:Managed Frequency=nan kHz Access Point: Not-Associated
Bit Rate:0 kb/s Tx-Power:16 dBm
Retry limit:15 RTS thr:off Fragment thr:off
Power Management:off
Link Quality:0 Signal level:0 Noise level:0
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:107 Missed beacon:0
```

do you have a wired connection to the router? Reason I'm wondering is if you do, you can check and make sure that MAC filtering is not enabled and blocking you from getting an IP address.

whats the output of```
lshw -C network
```

---

### Post by tentaro on 2009-04-28
Well I haven't been able to get my wireless to work at all. Here is what me my lshw showed:
 tentaro@tentaro-desktop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network UNCLAIMED
       description: Ethernet controller
       product: 88W8361 [TopDog] 802.11n Wireless
       vendor: Marvell Technology Group Ltd.
       physical id: a
       bus info: pci@0000:03:0a.0
       version: 03
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list
       configuration: latency=0
  *-network DISABLED
       description: Ethernet interface
       physical id: 3
       logical name: pan0
       serial: 2a:02:20:53:83:69
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

Kinda fuzzy as to why it says network Disabled when that is what I am using lol. Well anyway, I have looked and I can not find a driver for this and since it is Wireless N. problem really is I am on the second floor and my wired connection is going from the router to a Netgear Home Wiring Network box through the home wiring upstairs in to the output box, from there into a pure 10/100Mbps router then to my computer. the home wiring kit is old version and only runs at 54Mbps so is a bit slower than my liking. Would really like to get this wireless up and running if possible that is.

---

### Post by lkraemer on 2009-04-29
Open a Terminal window and Do:
```

lshw -C network
lsmod
ndiswrapper -l
cat /etc/modprobe.d/blacklist
iwconfig

```
and post the output of each.

lkraemer

---

### Post by tentaro on 2009-04-29
```
]tentaro@tentaro-desktop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network UNCLAIMED
       description: Ethernet controller
       product: 88W8361 [TopDog] 802.11n Wireless
       vendor: Marvell Technology Group Ltd.
       physical id: a
       bus info: pci@0000:03:0a.0
       version: 03
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list
       configuration: latency=0
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 8e:37:f9:c8:9b:59
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
```

```
tentaro@tentaro-desktop:~$ lsmod                                                              
Module                  Size  Used by                                                         
nls_iso8859_1          13440  0                                                               
nls_cp437              15104  0                                                               
vfat                   21120  0                                                               
fat                    65592  1 vfat                                                          
binfmt_misc            18572  1                                                               
ppdev                  16904  0                                                               
bridge                 63904  0                                                               
stp                    11140  1 bridge                                                        
bnep                   22912  2                                                               
input_polldev          12688  0                                                               
video                  29204  0                                                               
output                 11648  1 video                                                         
lp                     19588  0                                                               
parport                49584  2 ppdev,lp
joydev                 20864  0
hid_sony               11520  0
snd_hda_intel         557364  5
snd_pcm_oss            52352  0
snd_mixer_oss          24960  1 snd_pcm_oss
snd_pcm                99336  3 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          11524  0
snd_seq_oss            41984  0
snd_seq_midi           15744  0
snd_rawmidi            33920  1 snd_seq_midi
snd_seq_midi_event     16512  2 snd_seq_oss,snd_seq_midi
snd_seq                66272  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              34064  3 snd_pcm,snd_seq
snd_seq_device         16276  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    78792  17 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              16800  1 snd
snd_page_alloc         18704  2 snd_hda_intel,snd_pcm
psmouse                64028  0
serio_raw              14468  0
pcspkr                 11136  0
i2c_nforce2            16136  0
usbhid                 47040  0
nvidia               8123768  48
usb_storage            94912  0
forcedeth              68368  0
fbcon                  49792  0
tileblit               11264  1 fbcon
font                   17024  1 fbcon
bitblit                14464  1 fbcon
softcursor             10368  1 bitblit
tentaro@tentaro-desktop:~$
```

```
tentaro@tentaro-desktop:~$ ndiswrapper -l
The program 'ndiswrapper' is currently not installed.  You can install it by typing:
sudo apt-get install ndiswrapper-common
bash: ndiswrapper: command not found
tentaro@tentaro-desktop:~$
```

```
tentaro@tentaro-desktop:~$ cat /etc/modprobe.d/blacklist
cat: /etc/modprobe.d/blacklist: No such file or directory
tentaro@tentaro-desktop:~$
```

```
tentaro@tentaro-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

tentaro@tentaro-desktop:~$

```

should I install ndiswrapper? I know sometimes they work if there is no normal driver. Thanks for the response.

---

### Post by lkraemer on 2009-04-29
I am afraid at this point I'm not going to be much help.
Maybe some kind soul will jump in that knows more and
solve your problem.

What about doing a fresh install?  I just don't know what else
to suggest.

lkraemer

---

### Post by tentaro on 2009-04-30
Thanks for trying anyway. This is a new install anyway :)  I fear the card may be too new for Linux and as far as I have seen there is not alot of support for 11N yet. Oh well, if anyone else can help I would appreicate it. Thanks again.

---

