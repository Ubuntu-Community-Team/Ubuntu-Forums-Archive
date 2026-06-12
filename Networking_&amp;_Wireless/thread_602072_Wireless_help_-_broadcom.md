---
title: "Wireless help - broadcom"
date: 2007-11-03
forum: Networking &amp; Wireless
---

### Post by dano80 on 2007-11-03
first off, let me explain that I am new to Linux, but not to windows. Having said that, I would love to get away from it. I have just mastered vista and am sick of the sloppy nature of windows. I am having tremendous trouble connecting my desktop to my wireless network. I am using a broadcom chipset. Gutsy sees the card but will not let me enable the restricted drivers because I am not on a network to download them.......catch 22 anyone??? I saw the post about broadcom wireless the easy way..... but it says that the offline installer will not work with gutsy. How does one use the drivers if a wireless connection is the only available means of connecting. I can also add that I enabled all the software sources in package manager, but will not do much since it wont download anything anyways.
Here is the 2nd part. I use a router with WPA TKIP+AES encryption. I am pretty comfortable with routers and setting configs, so I am 100% positive that the router is not part of the problem. I used the offline installer to copy all the broadcom firmware to /lib/firmware, and /lib/firmware/"kernel"...........this still did not work.(i think the script is the part that will not work, all the files are there and the readme says that is what it does anyways, so I did it manually)  I see a lot of people posting info for people able to connect and download software this is not my case. I am looking for a simple answer - Does gutsy work with broadcom or not . I have not used ndiswrapper, I cant download it. Please help and use simple linux language, as again I am new to the world of linux. One more thing, I am using a clean install of gutsy, not an upgrade.

---

### Post by mirzmaster on 2007-11-03
dano, I just walked my friend through the same problem.  The wireless situation on Gutsy is, unfortunately, not straightforward.  What I recommend you do is plug into a wired network just so you can enable the restricted driver for your wireless device.  Bear in mind, you will need to make sure you have all the software repositories enabled first.

You can enable the repositories by going to System -> Administration -> Software Sources.  There you'll find a bunch of checkboxes for the various software repositories, with different repositories for varying levels of openness.  Make sure to enable all the repositories listed on the "Ubuntu Software" tab in the diaglo, including the restricted and multiverse repositories.

---

### Post by dano80 on 2007-11-04
yeah thats what I was afraid of - once enabled I should have no issues right? I have a laptop blessed with the intel chipset, this one connects just fine right out of the box. I love ubuntu, and hope that the hardware support will catch up to current windows specs. I would like to be a part of the solution instead of waiting for others to do it for us. Hopefully in a couple years I will be able to offer some assistance. What is all the details on this ndiswrapper, and getting WPA to enable. I am aware of all the flaws inherent in wireless connections, and do not want to go back to WEP. My laptop does not have any issues connecting to a WPA, but I have been reading that broadcom might?????? Is this true???? Thanks again for the help.

---

