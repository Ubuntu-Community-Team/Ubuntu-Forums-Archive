---
title: "Live CD U Mate 16.04 doesn't show me WiFi"
date: 2016-11-01
forum: Networking &amp; Wireless
---

### Post by Odyssey1942 on 2016-11-01
I have a Dell Latitude E5510 which I upgraded to a SSD with 8GB RAM (before 4GB) and to W10 from W7Pro. It works fine for an hour or so then gives me a unknown error message on blue background and I have to reboot. Spent way too much time trying to determine what was wrong, so decided to install a Live CD version on it to see if the error message re-appears. If so, must be hardware, and if not, probably something in W10 (never had the problem in W7).

I managed to break one of the leads to the built in WiFi so am trying to use an AirLink 101 Wireless N USB adapter. UM 16.04 doesn't seem to see it. Is that likely because it is N, and this older computer may not have N drivers?

Or what? 

I am not very experienced in network issues so plain talk at ABC level will be appreciated. Thanks

---

### Post by chili555 on 2016-11-01
First, let's identify your device. Please open a terminal Ctrl+Alt+t and run:```
lsusb
```Post the result.

I promise to be gentle.

---

### Post by Odyssey1942 on 2016-11-01
> **chili555 said:**
> First, let's identify your device. Please open a terminal Ctrl+Alt+t and run:```
lsusb
```Post the result.

I promise to be gentle.

Thank you in advance for your kindness.

for Bus 2: 
--Dev. 3 is Realtek Semi RTL8192SU 802.11n adapter
--Dev 2 is Intel Integrated Rate Matching Hub
--Linux Fndn 2.0 root hub

for Bus 1:
--Dev 2 is Intel Integrated Rate Matching Hub
--Linux Fndn 2.0 root hub

---

### Post by chili555 on 2016-11-01
> --Dev. 3 is Realtek Semi RTL8192SU 802.11n adapterOne of the reasons we want to see lsusb is so we can see the usb.id; something like 1234:7890 or some such. May I gently suggest that you not redact the data we've requested. To paraphrase Miranda, any data you provide can and will be used to help you!

---

### Post by Odyssey1942 on 2016-11-01
OK, kinda expected that but I am a painfully slow typist. Will type the whole thing. May take a few mins, but please hang with me cause I am holed up in a rainstorm, can't do all the other many things that need to be done, and am delighted to be able to progress this in the vacuum.
Back soon.

---

### Post by Odyssey1942 on 2016-11-01
> **Odyssey1942 said:**
> OK, kinda expected that but I am a painfully slow typist. Will type the whole thing. May take a few mins, but please hang with me cause I am holed up in a rainstorm, can't do all the other many things that need to be done, and am delighted to be able to progress this in the vacuum.
Back soon.

figured out I could copy from the above and fill in the missing bits:

Bus 2 Dev. 3: ID 0bda:8174 Realtek Semiconductor Corp. RTL8192SU 802.11n WLAN adapter
Bus 2 Dev 2: ID 8087:0020 Intel Integrated Rate Matching Hub
Bus 2 Dev 1: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 1 Dev 2: ID 8087:0020 Intel Integrated Rate Matching Hub
Bus 1 Dev 1: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by chili555 on 2016-11-01
Your 0bda:8174 device works with the driver r8712u that is built in to 16.04 by default. Verify:```
modinfo r8712u | grep 8174
```If the driver is present and covers your device, you should see:> alias:          usb:v0BDAp[COLOR="#FF0000"]8174[/COLOR]d*dc*dsc*dp*ic*isc*ip*in*Try loading it and see if the wireless starts or, in the alternative, any informative errors, warnings, etc. appear:```
sudo modprobe r8712u
```Also, check to see if the wireless switch or key combination is set to enable or disable wireless:```
rfkill list all
```

---

### Post by Odyssey1942 on 2016-11-01
The line is there, but I don't know how to "Try loading it.." Thanks for your patience.

---

### Post by chili555 on 2016-11-01
>  "Try loading it.."That means that, since the driver apparently didn't load automagically when you ran the live DVD, let's load it, that is, modprobe it now:```
sudo modprobe r8712u
```Then tell us what happens; errors, warnings, or does Network Manager notify you that wireless networks are available to connect to. 

Depending on the response, we'll figure out what to do next.

---

### Post by Odyssey1942 on 2016-11-01
thanks, now see that you were telling me how to do. However no response whatsoever. Maybe because I am running from Live CD?

If necessary, can just go ahead and install it as I can't live with those periodic blue screens/seizeup. I think I can go back to W10, should I ever want to, as the W10 install puts some code somewhere that allows it. Don't understand that either.

---

### Post by chili555 on 2016-11-01
> thanks, now see that you were telling me how to do. However no response whatsoever. Excellent. No errors, warnings, etc. 

I wonder if you are not seeing the wifi because the Network Manager icon is missing. Do you see it there in the upper right? [http://i.stack.imgur.com/UBOU7.jpg](http://i.stack.imgur.com/UBOU7.jpg) Does it appear if you do, in the terminal:```
nm-applet &
```When you finally see it, can you click on it and see your network listed to connect to?

[http://www.omgubuntu.co.uk/wp-content/uploads/2016/04/ubuntu-mate-1604-desktop-screenshot.jpeg](http://www.omgubuntu.co.uk/wp-content/uploads/2016/04/ubuntu-mate-1604-desktop-screenshot.jpeg) In this image, the Network Manager icon is the two up and down arrows indicating an ethernet connection.

---

### Post by Odyssey1942 on 2016-11-01
There is a little V with a rounded top (like the pattern a windshield wiper makes) which says:

Wifi Network (Broadcom BCM4313 802.11bgn Wireless Network Adapter (Inspiron M5010 / XPS 8300)) [this may be the one I broke?]
Wifi is disabled

Wifi Network (Mfgr Realtek RT:8192S WLAN Adapter)
Wifi is disabled

(ALL ABOVE GREYED OUT)

VPN Connections

(checkmark) Enable Networking
(checkmark) Enable Wi-Fi

Connection Information (greyed out)

Edit Connections

---

### Post by chili555 on 2016-11-01
Now we're cookin' with gas!!!

First, let's find out the loaded driver for the possibly broken Broadcom. We'll blacklist it so it doesn't load and conflict. Please run and post:```
lsmod | grep -e brcm -e bcma
```Next, when we see that both are disabled, we remember this:> Also, check to see if the wireless switch or key combination is set to enable or disable wireless:
Code:
rfkill list allNow we know that the switch is set to disable the wireless. Find it and switch it. This, maybe?? [https://www.helpowl.com/images/answer_images/image/56444bcf26ce194b9309dc255d31b8cc.jpg](https://www.helpowl.com/images/answer_images/image/56444bcf26ce194b9309dc255d31b8cc.jpg)

Yes, the switch generally disables *BOTH* the internal and any USB.

---

### Post by Odyssey1942 on 2016-11-01
I really appreciate your help more than I can convey, but I need to run my daughter to the doctor and will be away for an hour maybe a little longer. Will you be around later, and if not tomorrow?

Will be back online immediately upon my return.

---

### Post by chili555 on 2016-11-01
I'll be around for about two more hours. Good luck at the doc and I'll see you later.

---

### Post by Odyssey1942 on 2016-11-01
She insisted on her mother taking her, so I'm back. Thanks

---

### Post by chili555 on 2016-11-01
> **Odyssey1942 said:**
> She insisted on her mother taking her, so I'm back. ThanksPlease go back to post #13 and let's continue.

---

### Post by Odyssey1942 on 2016-11-01
brcmsmac    573440 0
cordic            16384 1 brcmsmac
brcmutil         16384 1 brcmsmac
mac80211     737280 2 b43, brcmsmac
cfg80211       565248 3 b43, brcmsmac, mac80211
bcma              53248 3 b43, brcmsmac

Not sure how to proceed from here. Do I run "rkill list all" in terminal, then turn the computer off using the switch, then back on? 

Booting up with the Live CD takes several minutes, but I can continue to discuss with
 this computer while all that is going on

---

### Post by chili555 on 2016-11-01
Let's unload the Broadcom drivers:```
sudo modprobe -r brcmsmac
sudo modprobe -r bcma
```Now, just turn the wireless switch from off to on. Your USB should spring to life!

It doesn't turn the computer off, it turns the wireless on and off.

---

### Post by Odyssey1942 on 2016-11-01
It accepted those commands without protest

I misunderstood the bit about the switches. The only hardware switch I see is the switch on the front of the computer (ref: your photo). I never actually knew what that was for. I just switched it to the left and it rebooted the computer so it may not be the Wifi switch. Will take awhile to come back up but maybe the terminal history will be intact

---

### Post by chili555 on 2016-11-01
> The only hardware switch I see is the switch on the front of the computer (ref: your photo). I never actually knew what that was for. Does it have a picture of an antenna right next to it? I'd surmise it's the wireless switch, then and I'd be shocked if it rebooted the computer.

---

### Post by Odyssey1942 on 2016-11-01
Wow, Not sure I understood very much of what we just did, but I had Wifi for a very brief period! For awhile, when it booted into Live CD, it froze up shortly after bringing up the desktop (with the blue WiFi light at the top of the keyboard lit up.

I have rebooted several times and it now stays up, but no WiFi. I have clicked on enable Wifi in the icon at the top right and the click stays in place but the Wifi light does not come on and it does not show any of the networks available (in fact it has the same wording as I posted above)

---

### Post by chili555 on 2016-11-02
If the wireless is shown as disabled, then the switch is set to turn _off_ the wireless radio. Do you or do you not have the switch with the antenna next to it? 

Remove the USB. Shut down the machine. Set the wireless switch to enable wireless. Start the machine. Before you do anything, check the Network Manager icon. Is the Broadcom shown as enabled or disabled?

Once we know what the switch is or isn't doing, we'll proceed to the next steps.

---

### Post by Odyssey1942 on 2016-11-02
Apologies. I am being a bit thick here. I unplugged the laptop and got it into a decent light and do see that there is a Wifi symbol next to that switch. It was in the leftmost position with a red band visible to the right of the slider. I shut it down, pushed the slider to the right and turned it back on. (FWIIW, if it is pushed hard to the left it does NOT reboot the computer.)

As it booted into the Live CD, the blue Wifi indicator at top left of keyboard came on and the wifi symbol in the panel shows networking to be enabled, but no mention of wireless.

Then I plugged the adapter back in and voila! It is there.

Unfortunately, shortly thereafter the computer freezes and requires a hard reset to turn it back on. Since it is a Live CD session, I assume that nothing was changed within hardware or code in the machine other than changing the position of the front Wifi switch. Can you think of any reason why I shouldn't go ahead and install 16.04, given that the W10 install is not working acceptably?

Either the freeze problem will go away, or if not will allow a code change or other that may resolve that issue and this would remain in place for future bootups.

Or should we try to get to the bottom of the freeze issue first? Thanks.

Edit: The freeze up seems not to happen until I actually log onto to an available AP

---

### Post by chili555 on 2016-11-03
I suspect that part of the freeze is the conflict between the drivers for the internal device and the USB. If you do the permanent install, we'll blacklist the drivers for the internal and reboot. Then insert the USB and I'm fairly confident you will be all good.

By the way, you said you broke one of the wires in the internal. Did you have the laptop apart? Perhaps you can simply remove the internal wireless card. Please tell me more so I can advise you. Please do not attack the poor laptop with a screwdriver until we know more.

---

### Post by Odyssey1942 on 2016-11-03
One of the little wires to the wireless board was in the way of the HDD/SDD change so I tried to ever so gently move it to remove the HDD and unfortunately was not gentle enough and I broke the wire off. Way too tiny for me to solder it back into place. I am in the Yucatan at the moment without a screwdriver so that would need to wait in any case.

During the lull, and since I didn't know what to do next but wanted to try something, I attempted to go ahead and install Ubuntu Mate 16.04 onto the Dell. Chose install alongside W10.

However, it cannot even do that. It freezes as soon as it gets into the formatting to create a partition for UM. Did that twice and now I have a sdd with about 6 or 7 small partitions on it. Pretty sure that the E5510 has EUFI (maybe one of the earlier to so have) which I don't understand much about and that may be an issue

So in summary what I can see with the E5510 is that:

When it was running under W10, I got random freezes

When running Live CD Ubuntu Mate 16.04, the computer freezes as soon as I try to connect to a wifi AP

When I try to install UM 16.04 alongside W10, it freezes immediately upon starting to create a new partition.

Now will not boot under w10 but I can run the Mate Live CD

So I think that the next step is to remove the SDD and replace it with another to see if that can install. If so, it may pinpoint the issue as the existing SSD. While I am doing that exchange, do you suggest that I try to remove the wireless board, tape off the broken lead, or ?

Or is there something that I can try before I return to the US tomorrow? Thanks.

---

### Post by chili555 on 2016-11-03
> 
Pretty sure that the E5510 has EUFI (maybe one of the earlier to so have) which I don't understand much about and that may be an issue
Is the behavior improved if you go into the BIOS and disable secure boot? There may be a Legacy mode which I'd try.> 
One of the little wires to the wireless board was in the way of the HDD/SDD change so I tried to ever so gently move it to remove the HDD and unfortunately was not gentle enough and I broke the wire off. 
On the wireless card I just replaced on this laptop and, for that matter, many others, the little antenna wires are snap on-snap off connectors. Is that, perhaps, the case here?

[https://qph.ec.quoracdn.net/main-qimg-2b4bb1b47c585d9a423ceb5453ccdade-c?convert_to_webp=true](https://qph.ec.quoracdn.net/main-qimg-2b4bb1b47c585d9a423ceb5453ccdade-c?convert_to_webp=true)

---

### Post by Odyssey1942 on 2016-11-03
Took every pointed thing in the place but I finally got the back off and see that it is indeed a snap off connector that came loose. However I am not having much luck snapping it back in. Any technique that I should try?

Will reboot into BIOS as soon as I can get the card reconnected.

BTW, since you have one of these, what is that bus looking thing on the back just above the cover that I just removed?

---

### Post by chili555 on 2016-11-03
> **Odyssey1942 said:**
> Took every pointed thing in the place but I finally got the back off and see that it is indeed a snap off connector that came loose. However I am not having much luck snapping it back in. Any technique that I should try?

Will reboot into BIOS as soon as I can get the card reconnected.

BTW, since you have one of these, what is that bus looking thing on the back just above the cover that I just removed?I don't have the subject Dell, I have a Lenovo. My insatiable urge to tweak required that I add RAM, swap to an SSD and upgrade the wireless card. Then, the best upgrade of all; I installed Ubuntu!

All I can suggest is to get the post and the wire connector lined up well and press firmly but not hard. If it is properly lined up, it will snap in fairly easily. There is no need to press hard enough to risk breaking it. If you have trouble getting fat fingers in a tight spot, you might try a pencil eraser to press with.

---

### Post by Odyssey1942 on 2016-11-03
OK, got the post reconnected. Thank you for your insight on this. Very grateful.

However, so far no indication that the WiFi is working.

Just got into boot Sequence and see that it is set to boot Legacy. Should I try a UEFI boot?

Also booting from DVD each time takes lots of time. I am using a W10 computer to post here. Is there a simple way, on a W10 puter, to create a boot USB with UM 16.04 to reduce the several minutes required to boot with the DVD?

Now running live CD and Bluetooth turned on when I slid the switch to on, but not the wifi. lsusb returns the same lines as I provided earlier except nothing about Realtek, i.e., no dev 3.

Edit: some changes with the internal wifi reconnected. Using the same sequence as was successful last night, the wifi is enabled and actually lets me bring up firefox for a couple of minutes, but then freezes again. Trying again but the reboot takes about 15 mins each time.

---

### Post by chili555 on 2016-11-03
> the reboot takes about 15 mins each time.Then something is very wrong. I think I'd let it boot and check for errors:```
dmesg | grep -i error
```Have you made any progress on a full installation, secure boot and so on?

---

### Post by Odyssey1942 on 2016-11-05
Back in the USA and no internet! Go figure!

Chilli, here is the report:

> 
[     0.272350] acpi PNP0A08:00 _OSC failed (AE_ERROR); disabling ASPM
[  136.693723] b43: probe of bcma0:1 failed with error -524
[  980.049532] [drm:intel_cpu_fifo_underrun_irq_handler [i915]] *ERROR* CPU pipe 
A FIFO underrun 

Have been putting out fires since our return so have not tried to replace the SSD yet.

thanks.

Edit: Have replaced the SSD with another similar size (120Gb) and same result, i.e. it seizes either:
1) with wifi connected, when browser starts, or
2) without wifi connected during completion of the registration (name, password, etc) screen.

Same results attempting to install Ubunutu Gnome 16.04 from DVD

I am now replacing the new RAM  with the original and the computer is running the usual battery of tests that it offers when the RAM is changed. So far no negative test results, but if same ultimately occurs will report back.

Assuming no test failures, will attempt to reinstall again.

---

