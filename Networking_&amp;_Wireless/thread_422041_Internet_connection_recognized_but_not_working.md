---
title: "Internet connection recognized but not working"
date: 2007-04-24
forum: Networking &amp; Wireless
---

### Post by brian. on 2007-04-24
Hey all, I'm very new to Linux and don't know much about working with it. I recently installed 'Ubuntu 7.04'.Tthe installation went fine and its been working great since. I've had to problems until today. Today I switched the internet cable chord from my Dell (OS: Windows XP) to my other computer that I had installed 'Ubuntu 7.04' on, that computer also shares it hard drive with another copy of Windows XP. Once I had the cable internet connection chord plugged in, I logged on to Unbuntu. It then recognized the internet connect. So then I clicked Mozilla to browse the internet, however no pages would load. After that I went about trying some of the other features that need internet:

Add/Remove programs section
Checking emails

And as you probably guessed none of them worked either. To double check things I then restarted computer and logged onto the OS of Windows XP. The internet connection was recognized however no web pages would load. (FYI: This computer has never had internet connected to it since a new version of Windows XP was installed)

I thought perhaps there was a problem with my cable chord. So I then unplugged the cable chord from the 'Ununtu/Windows XP' computer to the only 'Winows computer' which the internet has worked on for years. As normal the internet worked fine. I was able to get to web pages and use other applications that need internet.

I am lost of what to do. Any help is amazing! Thank you in advance for any help. 

PS: I've checked the other threads with people who had similar problems most of them didn't work for me or just plain confused me :confused: .  Please remember I am new to Linux.

---

### Post by jakev383 on 2007-04-24
> **brian. said:**
> Hey all, I'm very new to Linux and don't know much about working with it. I recently installed 'Ubuntu 7.04'.Tthe installation went fine and its been working great since. I've had to problems until today. Today I switched the internet cable chord from my Dell (OS: Windows XP) to my other computer that I had installed 'Ubuntu 7.04' on, that computer also shares it hard drive with another copy of Windows XP. Once I had the cable internet connection chord plugged in, I logged on to Unbuntu. It then recognized the internet connect. So then I clicked Mozilla to browse the internet, however no pages would load. After that I went about trying some of the other features that need internet:

Add/Remove programs section
Checking emails

And as you probably guessed none of them worked either. To double check things I then restarted computer and logged onto the OS of Windows XP. The internet connection was recognized however no web pages would load. (FYI: This computer has never had internet connected to it since a new version of Windows XP was installed)

I thought perhaps there was a problem with my cable chord. So I then unplugged the cable chord from the 'Ununtu/Windows XP' computer to the only 'Winows computer' which the internet has worked on for years. As normal the internet worked fine. I was able to get to web pages and use other applications that need internet.

I am lost of what to do. Any help is amazing! Thank you in advance for any help. 

PS: I've checked the other threads with people who had similar problems most of them didn't work for me or just plain confused me :confused: .  Please remember I am new to Linux.

Are you hooked directly to a cable/DSL modem? I know Brighthouse (Time Warner) here caches the MAC address. When you want to change computers you have to power cycle the modem or you won't get a valid IP address.
What IP are you getting on the Linux machine? Does it by chance start with a 169?

---

### Post by jerrylamos on 2007-04-24
Feisty has a "Network Manager" by default.  On this system it always disables the internet connection on booting up.  The icon for the Network Manager looks like two little monitors, on the top right of your screen, on my system just left of the speakers icon and the date/time info.

If there's a little red mark on the Network Manager icon, then left click on the icon.  A drop down menu should appear.  Click on the Wired Connection selection.  In my case that enables the connection again and FireFox can get the internet.

Cheers, Jerry

---

### Post by brian. on 2007-04-24
Yes I am hooked directly to a cable/DSL modem. I do use Time Warner, I have Roadrunner through them. And for the IP address Linux is giving me a 0.0.0.0 and Windows is giving me one that starts with a 169. 
 How do I power cycle to modem? 

To Jerry, it was originally set to 'Wired Connection' but thanks for the suggession anyways.

---

### Post by jakev383 on 2007-04-25
> **brian. said:**
> Yes I am hooked directly to a cable/DSL modem. I do use Time Warner, I have Roadrunner through them. And for the IP address Linux is giving me a 0.0.0.0 and Windows is giving me one that starts with a 169. 
 How do I power cycle to modem? 

To Jerry, it was originally set to 'Wired Connection' but thanks for the suggession anyways.
Just unplug the power for 20-30 seconds, then plug it back in.
To be sure, unplug the power for the cable modem for 30 seconds, then plug it back in. Once the lights go solid (the cable light stops blinking), turn the computer on. Or if the computer is already on, have it renew the IP address (sudo dhclient eth0)

---

### Post by brian. on 2007-04-25
Thanks, that worked, I'm currently on the Linux computer.

---

### Post by jakev383 on 2007-04-25
> **brian. said:**
> Thanks, that worked, I'm currently on the Linux computer.

Glad to hear it. Enjoy!

---

