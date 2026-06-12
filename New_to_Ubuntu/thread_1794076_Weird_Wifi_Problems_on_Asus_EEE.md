---
title: "Weird Wifi Problems on Asus EEE"
date: 2011-06-30
forum: New to Ubuntu
---

### Post by nosehat on 2011-06-30
I've got an **Asus EEE PC 1000HE netbook** which had Eeebuntu installed on it for quite a while, and which used to work fine.  Unfortunately, Eeebuntu stopped being maintained about a year ago, so I finally decided to replace the OS with **Ubunutu 10.4**.  Big mistake!

I've set up the connection information in a way that should work.  The wifi tries to connect for a while, then pops up the "Wireless Network Authentication Required" window.  If I hit "connect" it will try again for a while, then pop up the window.  Etc.
[B]
Here's where it gets weird[/B]:  I plugged a network cable into the netbook this morning, then turned it on.  As soon as Ubuntu booted, it connected to my wifi network instantly.  I unplugged the cable, and it remained connected via wifi (for about 5 minutes before disconnecting and going back to the behavior described above).  This is 100% replicable--the wifi works every time (for about 5 minutes), as long as Ubuntu boots with a wired network cable already plugged in.

Aargh!

Any suggestions??

---

### Post by Rex Bouwense on 2011-06-30
I have Lucid installed on my Eee PC and have not had any problems with the WiFi.  From reading your post I understand that you connect with the wireless when you plug in an Ethernet cable to the router.  That is weird.  OK.  
Can you connect to the Internet via wired network?  
Are both wired and wireless enabled?

---

### Post by nosehat on 2011-06-30
Thanks for your reply.  Yes, both wired and wireless are enabled, and it never has trouble finding the ethernet wire when I plug it in.

In the situation where I boot it with a cable attached, it will connect via both the cable (Auto eth0) and via Wifi to my router.  When I unplug the cable, eth0 goes away, but I stay connected via Wifi for about 5 minutes.

This tells me:

[LIST]
[*]There's nothing wrong with my wifi hardware (I knew that already, because it worked fine with eeebuntu).
[*]There's nothing wrong with the wifi driver, once a successful connection is established.
[*]Something is preventing my wifi from connecting properly.
[/LIST]
Did you install any extra packages/drivers to manage the hardware on your eee?

---

### Post by Rex Bouwense on 2011-06-30
I didn't install any additional packages to manage the hardware and before I installed 10.04, I had 9.04 installed.  It worked flawlessly also.
I don't understand how the netbook can connect via wired and wireless simultaneously.
OK, right click on the Internet icon on the top panel and go to edit connections and then wireless.  Delete your connection and then back out.  Now your computer will search for networks and then find yours.  Connect and then enter your password or authentication code.  Hopefully, that will fix the problem.

---

### Post by nosehat on 2011-06-30
Well, I tried deleting the connection information as you suggested, and reentering it, but that did not work.

I should add another item to the list of things I know about this situation:


[LIST]
[*]There's nothing wrong with my connection settings (because it will connect to the wifi without a problem when I boot the netbook in the way I described).
[/LIST]

---

### Post by Rex Bouwense on 2011-06-30
After re-reading the posts, I'm not sure that you are really connecting to the Internet with WiFi because it keeps asking you for your password.  Just as a check, change the security on your network temporarily to none and try to connect.  I used to have a similar problem with an old Dell laptop but I don't remember what I did to fix it.

---

### Post by nosehat on 2011-06-30
I thought about that, but in fact it is connecting via wifi with my normal security (WPA2).

Perhaps I wasn't clear.  Here are the steps that will get me a wifi connection every time:

1) Plug in ethernet cable with netbook off.
2) Boot netbook.  When it boots *both* eth0 *and* the wifi become connected.
3) Unplug the ethernet cable.  This disconnects eth0, *leaving the wifi connection as the only possible connection to the internet.*
4) Open Firefox.  Browse the web, do a new google search, etc.  It works fine for about 5 minutes before disconnecting.

Note that at this point the only possible way it could connect at all is via wifi, and this works fine.

Frankly, I'm bewildered.

---

### Post by TerribleLIar on 2011-06-30
I have the exact same model EEEPC. This thread fixed my problems. See if you have the same wireless drivers showing. [http://ubuntuforums.org/showthread.php?t=1727945&highlight=1000he](http://ubuntuforums.org/showthread.php?t=1727945&highlight=1000he)

That topic has a lot of big messages in it. Basically, run lsmod in the terminal and see if you have the same drivers listed as in the second post.

---

### Post by Rex Bouwense on 2011-06-30
I have another couple of words but they probably mean bewildered as well.  Perhaps someone with more knowledge that I have will jump in and solve the mystery.  Sorry.  Have some :popcorn: while you wait.

That didn't take so long.

---

### Post by nosehat on 2011-06-30
Thanks TerribleLIar, I blacklisted the 4 items listed in the other thread.  However, I'm not sure they are included in 10.04.

Running lsmod I now get:

```
lsmod
Module                  Size  Used by
aes_i586                7268  133 
aes_generic            26863  1 aes_i586
binfmt_misc             6587  1 
dm_crypt               11331  0 
ppdev                   5259  0 
joydev                  8740  0 
snd_hda_codec_realtek   203376  1 
snd_hda_intel          22069  2 
snd_hda_codec          74201  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70694  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
uvcvideo               57374  0 
snd                    54244  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
videodev               34361  1 uvcvideo
v4l1_compat            13251  2 uvcvideo,videodev
rt2860sta             481561  1 
psmouse                63245  0 
serio_raw               3978  0 
soundcore               6620  1 snd
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
lp                      7028  0 
eeepc_laptop           14331  0 
parport                32635  2 ppdev,lp
fbcon                  35102  71 
tileblit                1999  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
i915                  287810  3 
drm_kms_helper         29329  1 i915
drm                   162377  4 i915,drm_kms_helper
i2c_algo_bit            5028  1 i915
intel_agp              24375  2 i915
video                  17375  1 i915
ahci                   32360  2 
output                  1871  1 video
atl1e                  28018  0 
agpgart                31724  2 drm,intel_agp

```To me, it looks like the only wireless driver there is rt2860sta.  Should I blacklist that one too?  Is there any command to just list wireless drivers/conflicts?

By the way, I now am getting 5 minutes of Wifi connectivity every time I turn the netbook on, whether it's connected with a wire or not.  I'm not sure if that's a result of blacklisting those items, or if it's something else.

EDIT:  I should clarify, I'm still having the same problem--5 minutes of wifi connectivity and then it disconnects and won't reconnect.

Also, blacklisting rt2860sta just removed all ability to connect to wifi at all (not surprising, but I had the hope that without that ubuntu would revert to a more generic wireless driver that might work better).

Also, I take back what I said about getting 5 min of wifi every time I turn the netbook on.  SOmetimes I do, and sometimes I don't.  :(

---

### Post by TerribleLIar on 2011-06-30
Sorry. Sounds like your problem is different than mine then. You  probably should have run lsmod before blacklisting the drivers to make  sure you had the same problem. It could just make things more  complicated if you're not having the exact same issue. Sorry, I should  have specified that. I dug around in the networking subforum trying to  find a similar problem. None of them really had a solution that I could  see though. It may be worthwhile to ask for a mod to move this topic to that  subforum as well. At the least, it might be good to read the  sticky there and include the information they ask to include in your  first post. The topic I'm talking about is  [http://ubuntuforums.org/showthread.php?p=6183681](http://ubuntuforums.org/showthread.php?p=6183681) Someone that knows what they're doing could probably make sense of all of it.

---

### Post by nosehat on 2011-06-30
That's ok, I can comment out the lines for the blacklisted items, reboot, and put it back to normal.

A driver conflict is what I was starting to suspect, like driver A and driver B both competing for the wifi card.  When I boot the netbook with the cable connected, maybe driver A takes on eth0, allowing driver B to talk to the wifi card without interference?  

Thanks for the suggestion to move to the other forum.  I'll make a fresh post there, since this thread has gotten pretty confusing.

---

### Post by nosehat on 2011-07-04
Note:  I've cleaned this up and reposted it on the Networking and Wireless forum, [here]("http://ubuntuforums.org/showthread.php?t=1797053").

---

### Post by nosehat on 2011-07-07
Finally solved.

The Ubuntu kernel does not include the latest driver for the wifi card in this netbook.  Newer, working versions of the driver have been available since 2009.

The solution is to download the source for the updated driver and build it yourself, then replace the driver included with the Ubuntu kernel.

Somewhat complicated, but now it works like a charm.

Details in this thread:  [http://ubuntuforums.org/showthread.php?t=1797053](http://ubuntuforums.org/showthread.php?t=1797053)

---

