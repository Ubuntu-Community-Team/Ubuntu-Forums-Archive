---
title: "Bluetooth on !4.04"
date: 2014-10-15
forum: Networking &amp; Wireless
---

### Post by Photobug on 2014-10-15
I have just bought a Bluetooth dongle to use with my Ubuntu HTPC.  I have plugged it in and have been able to use the Bluetooth software to recognize and pair with my (also new toe me) BT headset and speaker. I have tested out both headset and speaker with my phone and they work with my phone.  However I can not get the BT products to receive sound from the Ubuntu HTPC even when paired.

I am using Bluetooth Manager in Ubuntu combined with a "Plugable USB-BT4LE".  How can i get the sound to come through to the BT headset and not through to the stereo speakers?

---

### Post by Vladlenin5000 on 2014-10-15
It doesn't change the audio output device automatically just because there's an headset paired. You also need to go to Sound Settings and select it there.

---

### Post by Photobug on 2014-10-15
> **Vladlenin5000 said:**
> It doesn't change the audio output device automatically just because there's an headset paired. You also need to go to Sound Settings and select it there.

How do I then choose the BT headphones?  

I have been playing around in the sound settings as well I have three options to choose from in sound settings none of them are the BT devices.  Also I have some problems with the Bluetooth settings.

---

### Post by Vladlenin5000 on 2014-10-16
If it doesn't appear listed as an audio device it wasn't correctly paired. Remove it and pair again.
This time around make sure the PIN selection isn't automatic because it only works for phones and similar. Instead choose '0000' which is the standard for A2DP/HFP devices. Then select it as the audio output.

---

### Post by Photobug on 2014-10-19
> **Vladlenin5000 said:**
> If it doesn't appear listed as an audio device it wasn't correctly paired. Remove it and pair again.
This time around make sure the PIN selection isn't automatic because it only works for phones and similar. Instead choose '0000' which is the standard for A2DP/HFP devices. Then select it as the audio output.

I have tried numerous times to pair the two BT devices. It is inconsistent sometimes pairing sometimes not but even when it pairs correctly I do not get the option to choose as an output in sound setting for either the BT headphones or speaker.  After many many attempts at removing and re-pairing the two BT items I eventually lost my ability to access the settings application, which I was able to restore by reinstalling the desktop.  I still can't get the BT devices to show up on the sound settings tab.

I am using the stock BT application from Ubuntu.  Might another BT app work better for pairing?

---

### Post by Lars Noodén on 2014-10-19
I'm finding something similar with [14.04 failing to find a properly paired bluetooth headset](http://ubuntuforums.org/showthread.php?t=2241437).  Just adding my "me, too" here in case something turns up.

---

### Post by weatherman2 on 2014-10-19
I noticed when playing with 14.04 that I had some issues pairing a Bluetooth speaker.  It is a bit flaky, but I did find this trick: even after a device is paired, for some bizarre reason sometimes the device would still be "disabled."  Really??  Simply enabling it in the list of Bluetooth devices - even after already paired - would allow it to work.

---

### Post by Photobug on 2014-10-20
> **weatherman2 said:**
> I noticed when playing with 14.04 that I had some issues pairing a Bluetooth speaker.  It is a bit flaky, but I did find this trick: even after a device is paired, for some bizarre reason sometimes the device would still be "disabled."  Really??  Simply enabling it in the list of Bluetooth devices - even after already paired - would allow it to work.

weatherman thanks for the input.

Can you clarify this for me?  What do you mean by "enabling" it?  

When I click on the BT manager in the bar on the right side of my screen it pulls up the list of BT devices.  My headset is boldened and all 3 bars (orange, green, and blue show optimals send/receive ratios.  When I right click I get the following options:

Connect to
Headset services
Input Service
Audio Sink
Audio Source
_____________
Disconnect from
Headset services
_______________
Pair
Untrust 
Setup
Refresh Services
_____________
Remove
__________
Disconnect

I have tried numerous times to disconnect and remove and setting up the BT devices and pairing them in different ways to try to get them visible in the sound settings list with no luck.  I have also tried to access these functions from the BT symbol on the top of the screen and the BT settings in settings.  Is there another place I could look to try to access the BT functions to enable the headset?

---

### Post by Photobug on 2014-10-20
[ATTACH=CONFIG]257383[/ATTACH]
Here is a photo of my screen.  Does this look like I have the right tools to make this happen or do I need a different application for BT management?

---

