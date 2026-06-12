---
title: "No Ethernet or Wi-Fi Connection Please Help"
date: 2008-07-25
forum: Networking &amp; Wireless
---

### Post by JamMasterJ on 2008-07-25
I have a laptop that will not connect to either the wired or wireless connections. I believe that it is an RT2500 but as I am green in the Linux community I am unsure of anything to this point. I had an error message when I re-installed 7.10 and was able to capture the message(attached). I also did as it requested and ran dmesg in the terminal (attached), but once again I have not a clue as to what I am looking for in the results. Another oddity to this machine is that it somehow identifies a network SSID but will not connect.

Thank you Ubuntu Community for your time and patience with those of us that believe in this product.

Jeremie

---

### Post by caljohnsmith on 2008-07-25
Strange that Ubuntu seems to having problems loading that wireless module. But first I would ask the question, is there a special reason why you installed 7.10 instead of 8.04? 8.04 may install fine without having problems with that module, and it would save alot of troubleshooting.

---

### Post by JamMasterJ on 2008-07-25
Believe me I wish it were that simple. I have tried a flat install with 8.04 as well as the text based CD install to assure it was not the GUI interfering with it. 8.04 will not install, it hangs at different points of the process on either types. I have checked all the CD's for their integrity as well. I figured since 7.10 would at least install I could update from there. Without any means of connectivity to the net I am unable to do so...

Thanks for your reply. Any and all help is appreciated. 

Jeremie

---

### Post by caljohnsmith on 2008-07-25
That sounds suspicious that your computer would have such a difficult time with Hardy. :-k What is your setup, i.e. is it an older computer, how much RAM, etc? I mean is there anything out-of-the-ordinary about your hardware? Do you remember exactly what the problems were when you tried installing Hardy? And lastly, how did you verify the integrity of your Live CD? Please provide as much info as possible because it seems to me you may have some sort of hardware issue. It would probably be good to run that memtest86 utility just to make sure your RAM is not an issue.

---

### Post by JamMasterJ on 2008-07-25
This is an Averatec Laptop. It has a 1.6mhz cpu I believe with 512mb of ram (not upgradable). 80gb hard drive 12in. tft. DVD ROM/burner. It is dual booting XP home and 7.10 currently. All devices work on the XP side.

As for my 8.04 install, I have tried the disk that I used to install on a current running laptop with, which had no problem on the other machine. This disk fails right before the image I attached in the first post. The text based install disk will allow me to partition and begin installing, but fails during the witting of files at around 45%. It hangs and never recovers. I checked the integrity of the GUI install disc from the menu.

Thanks again,

Jeremie

---

### Post by caljohnsmith on 2008-07-25
Jeremie, have you tried running the Ubuntu Live CD on that laptop and seeing if it can connect via ethernet/wireless? And do you get any error messages when booting the Live CD? And do you by chance have any other Live CDs of other distros you can try to give us more clues?

---

### Post by JamMasterJ on 2008-07-25
The 7.10 live CD gives the same result (no connection) as the install. The 8.04 live CD fails in the beginning load. It never makes it to the live CD Desktop. I do have a Knoppix CD (not with me) and will attempt that to see what happens as soon as possible.

---

