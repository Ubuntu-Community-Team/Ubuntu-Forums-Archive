---
title: "8198 Realtek misery"
date: 2008-10-28
forum: Networking &amp; Wireless
---

### Post by collapsing wave on 2008-10-28
I have a Toshiba L300 satellite pro with a Realtek wireless card that is supposed to be a 8187b but on typing lsusb into the terminal it is infact seen to be 8198

See all threads attributed to this user for hopeless running around in circles. I thought i was closing in on a solution at
[http://odeiowindows.wordpress.com/2008/07/17/ndiswrapper-and-rtl8187b-ubuntu-804/](http://odeiowindows.wordpress.com/2008/07/17/ndiswrapper-and-rtl8187b-ubuntu-804/)****
 but got a link to

[http://www.thecashplanet.com/ubuntu/rtl-win98-ndiswrapper.zip](http://www.thecashplanet.com/ubuntu/rtl-win98-ndiswrapper.zip)

nice...

and as i realised this is a fix for 8197B and not the good old 8198.
I am using a desktop to write this as the L300 has no internet connection because you have to disable the LAN in the bios to get the thing to boot up.

I haven't a clue what I am doing and need very clear instructions
All i want at this time is a wired connection to the internet.
Can anybody help me?

---

### Post by pytheas22 on 2008-10-28
Please post the exact PCI ID of the card (that is, the XXXX:XXXX string that you get from the 'lsusb' command).  With that I can provide specific instructions on what to do.  Also, are you running 32 or 64-bit Ubuntu?

---

### Post by collapsing wave on 2008-10-29
bus 007 Device 002: ID 0bda:8198 Realtek semiconductor Corp
bus 007 Device 001: ID 0000:0000
bus 006 Device 003: ID 0bda:0158 Realtek semiconductor Corp
bus 006 Device 002: ID 04f2:b070 Chicony Electronics Co., Ltd
bus 006 Device 001: ID 000:000
bus 005 Device 001: ID 000:000
bus 004 Device 001: ID 000:000
bus 003 Device 001: ID 000:000
bus 002 Device 001: ID 000:000
bus 001 Device 001: ID 000:000

32 bit ubuntu 99 per cent sure

thankyou

---

### Post by pytheas22 on 2008-10-29
From what I'm reading, this card should work out-of-the-box on Ubuntu 8.10.  The simplest solution for you may be to wipe out your 8.04 installation and replace it with 8.10.

If you don't want to do that or it doesn't work, we can try some other things, so please let me know.

Also, did you have two USB wireless cards plugged in when you ran the 'lsusb' command before?  Because it lists two very similar Realtek cards...

---

### Post by collapsing wave on 2008-10-29
I have gathered the same about 8.10 but I was really after the long term stability of 8.04 because I really really know nothing!

There were no usb wireless cards plugged in.

---

### Post by pytheas22 on 2008-10-29
> There were no usb wireless cards plugged in.

I'm confused...isn't this wireless card a USB stick?  If no USB wireless devices were plugged in, what are these two Realtek devices listed in lsusb:

```
bus 007 Device 002: ID 0bda:8198 Realtek semiconductor Corp
bus 006 Device 003: ID 0bda:0158 Realtek semiconductor Corp
```
> 
I have gathered the same about 8.10 but I was really after the long term stability of 8.04 because I really really know nothing!

It's true that 8.04 has longer-term support than 8.10, but 8.10 will still be supported for a year and a half, and it will be supported just as well as 8.04.  As long as you don't mind upgrading your system once every eighteen months, you should be fine using 8.10.  At the least, you could burn an 8.10 live CD and see if your wireless 'just works' under the live environment (running the live CD of course would not make any permanent changes to any systems installed on your hard drive).

---

### Post by collapsing wave on 2008-10-29
I really have no idea what they are.
there were no usb sticks plugged in. 100%. Zip. Nada. Nix
I think that I may have to try 8.10 because every question I ask seems to get me further in! 
Thanks for your time

---

### Post by styrofoam cup on 2008-11-02
its working now

[http://ubuntuforums.org/showthread.php?t=900791](http://ubuntuforums.org/showthread.php?t=900791)

using the compat-wireless drivers and 8.10. check out the link above, about post number 40

---

### Post by justmates on 2009-03-05
Hi All, I have a Toshiba laptop L300 that is supposed to have a RTL8187B Wifi card built in.
Have done a clean install of windows Vista Premium and of course have no driver disc with the laptop (surely it wouldnt be so hard to find them) I have installed the suggested realtek driver from the toshiba site and its sitting there just fine, no conflicts, but it wont work. I have tried many times to set it up and it just doesnt work as a wifi, always wants a cable.

I have read that I might need a moderfied driver?

Im so stuck and with such lack of sleep im just not sure what else I can do, toshiba are shocking as they say they wont support the new laptop as they sold it with vista home and the premium is not supported.

Please help!!!
email me at [email]xxcatxx@gmail.com[/email] 

P.S If i need to check Ids or anything like that please explain as Im not right up to date on checking the ID on my drivers and so on.

---

### Post by pytheas22 on 2009-03-05
> Hi All, I have a Toshiba laptop L300 that is supposed to have a RTL8187B Wifi card built in.
Have done a clean install of windows Vista Premium and of course have no driver disc with the laptop (surely it wouldnt be so hard to find them) I have installed the suggested realtek driver from the toshiba site and its sitting there just fine, no conflicts, but it wont work. I have tried many times to set it up and it just doesnt work as a wifi, always wants a cable.

I have read that I might need a moderfied driver?

Im so stuck and with such lack of sleep im just not sure what else I can do, toshiba are shocking as they say they wont support the new laptop as they sold it with vista home and the premium is not supported.

Please help!!!
email me at [email]xxcatxx@gmail.com[/email]

P.S If i need to check Ids or anything like that please explain as Im not right up to date on checking the ID on my drivers and so on.

justmates: you don't mention Ubuntu or Linux anywhere in your post.  Are you trying to make this card work on Windows, or are you using Linux?  If you're looking for Windows help, I'm afraid I can't assist; I've never used Vista.  This website has a section dedicated to Windows support where you might get help, but otherwise you should probably look for a different forum--this site is mainly intended for users of Ubuntu Linux.

If you are using Ubuntu, this card should be supported out-of-the-box in version 8.10 (I think it should also work in the 8.04.2 release).  If that's the version you're using and the card is not working, let me know and we can figure out how to make it work.

---

