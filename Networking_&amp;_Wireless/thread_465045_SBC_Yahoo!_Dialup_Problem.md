---
title: "SBC Yahoo! Dialup Problem"
date: 2007-06-05
forum: Networking &amp; Wireless
---

### Post by TheThinker on 2007-06-05
:(

Hey everyone!I've got my Conexant dial-up modem working with its own Linuxant driver (free version) and the Restricted Drivers Manager says it's running. I've also downloaded GNOME PPP and other modem packages from Ubuntu using an alternate computer with internet access. My ISP is SBC Yahoo!. It's my dad's ISP, but I copied his IP address and the server's IP address as well as the number. I'm using Feisty Fawn and my modem (and driver) are HSF based. 

Problem:
1) Gnome PPP dials the number, I hear the lovely screech of the internet, and it connects for only 2 seconds before dropping. Log File says something like "password and/or account not authenticated; Bad account or Password?". So I know the modem dials the number; it's just not communicating to the ISP. It could also be because I'm confused on how to add the different IP addresses (the server and the client) into Gnome PPP. Hmmm. I know that the ISP utilizes PAP authentication methods, which is what PPP supports.

2) Whenever I fiddle with the modem settings using the System-->Administrative--->Network (for example, changing from tone to pulse dialing), GNOME PPP says it cannot find the modem. GNOME PPP's automatic modem-search gets nothing (even though it worked before). HOWEVER, when I use the terminal and enter "sudo HSFconfig" and do the usual configuration, GNOME PPP can automatically detect the modem afterward. Very Strange.

Miscellaneous things:

1) I've used/configured wvdial and configured PPP in the terminal (then "connect to the ISP named 'provider' " and "sudo wvdial") to no avail. PPP says that the password and user-name are invalid and wvdial says the same thing. Modem does not dial anything in both cases.

Conclusions:

Man, I can almost taste my internet freedom! Problem #1 is my primary concern, so any help is GREATLY appreciated. Chow!

---

### Post by TheThinker on 2007-06-06
By the way, I did use the correct user-name and password for problem #1.

---

### Post by Mark_in_Hollywood on 2007-06-06
This makes me suspicious that your modem is actually "on the computer". Yes, I know it's sitting on the backplane of the motherboard.

If you remember back to Windows 95/98 MS had many complaints about 4 COM ports and only 2 IRQs. This was resolved by placing the modem at COM5 and irq2, because the mouse uses irq1.

For some reason, Ubuntu and maybe all Linux cannot place the modem on /dev/ttyS5 and have it resolve irq2. Or irq1. Believe me, I've tried. You can search my user name and the word modem and see many unanswered posts.

My advice is: buy an external modem. I did. I had an internal "controller-based" or "hardware" modem and it didn't work for squat. And it was a Gateway made modem. Try a thrift store if  you are in a large city. Maybe you can get one for $5.

---

### Post by TheThinker on 2007-06-08
> **Mark_in_Hollywood said:**
> This makes me suspicious that your modem is actually "on the computer". Yes, I know it's sitting on the backplane of the motherboard.

If you remember back to Windows 95/98 MS had many complaints about 4 COM ports and only 2 IRQs. This was resolved by placing the modem at COM5 and irq2, because the mouse uses irq1.

For some reason, Ubuntu and maybe all Linux cannot place the modem on /dev/ttyS5 and have it resolve irq2. Or irq1. Believe me, I've tried. You can search my user name and the word modem and see many unanswered posts.

My advice is: buy an external modem. I did. I had an internal "controller-based" or "hardware" modem and it didn't work for squat. And it was a Gateway made modem. Try a thrift store if  you are in a large city. Maybe you can get one for $5.

Actually, Ubuntu Feisty places my modem at /dev/SHMF (or something like that; can't really remember). The only way I found this out was by using GNOME PPP's automatic-modem-search feature. That's how I got the modem to finally work. Yeah, I know; Windows 98 was actually okay when it came to putting the modem on an open port and even letting you identifying which port it uses. On Ubuntu's Hardware Properties, however, I have yet to see which port the modem is using. Perhaps I overlooked it?

Here's an update: My local college gives free internet service to all of its registered students. Thus I set up GNOME PPP to dial my college's server number, and with a little more tweaks (such as setting it to Dynamic IP address and the like) and my password/user-name...I got connected!! Tadaa! In spite my modem's driver being the free (and slow) Linux version of Conexant, it is descent for a dial-up service. The best it can do is load text (and pictures ;)), which is the minimum I need in my connection.

Strange. No matter how I try (even setting up to Dynamic IP Address and such), SBC Yahoo still refuses to authenticate my user-name and password. I'm betting that it's their proprietary software that's needed to do this, and I LOATH to look around for a Linux version of it. Trust me, I've looked and I've found NADA, ZIP, ZERO. Apparently SBC Yahoo doesn't support Linux, which is a shame because my Dad was thinking of switching over to Ubuntu once I got that ISP to work on mine.

If anyone knows of a Linux version of SBC Yahoo!, please let me know! So far that seems to be my only solution for utilizing their service! Thanks a bunch! 

(Note: My internet connection now works! I just can't use this particular ISP).

---

### Post by TheThinker on 2007-06-08
Say, does anyone think it's possible to install SBC Yahoo! using Wine-X and using Wine-X's API to hook that software up to the internet?

---

