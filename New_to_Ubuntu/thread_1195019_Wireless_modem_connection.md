---
title: "Wireless modem connection"
date: 2009-06-23
forum: New to Ubuntu
---

### Post by umeshpr on 2009-06-23
Just receive my copy of Ubuntu 9.04 and installed as dual boot for Windows XP.:)


I have a wireless USB modem connection to access the internet!


How do I connect to the net thru' this USB wireless modem?


I am a newbie & please explain in simple terms please!


Any help appreciated!!:)

---

### Post by matthanielcm on 2009-06-23
It should work out of the box like the one I'm using now does. 

However, if it doesn't, you'll need to dial into your service.

In *Preferences* -> *Network Connections*, there should be a tab that says "Mobile Broadband". Click "Add" and follow the instructions. I'm not a complete expert on this, however, I've dealt with this many times.

---

### Post by aeiah on 2009-06-23
if what was suggested doesnt work you may need to install drivers or something. first thing you'll want to find out is what your card actually is. since the same card can have many different names the best way is to ask ubuntu to list all of your usb devices. open a terminal (accessories > terminal) and type lsusb. that's an L at the beginning. this will list all your usb devices that are currently plugged in and powered on and should include your mobile broadband dongle.

try googling with its name and ubuntu in the search term and see if people have any problems and solutions, or post the modem type here and someone will no doubt lend a hand

---

### Post by Tholley on 2009-06-23
You might try this...
 
**[SIZE=2]Give yourself full user rights on USB devices[/SIZE]**
[FONT=georgia][SIZE=2]Particularly using scanners can be tricky, because as a user you don't have full rights over all USB devices. A security feature, but an annoying exaggeration. Remedy this as follows:

System - Administration - Users and Groups[/SIZE][/FONT]
[FONT=georgia][SIZE=2]Click on your user name[/SIZE][/FONT]
[FONT=georgia][SIZE=2]Click on the button "Unlock"[/SIZE][/FONT]
[FONT=georgia][SIZE=2]Properties button - tab User Privileges[/SIZE][/FONT]
[FONT=georgia][SIZE=2]and make sure that every category is ticked.[/SIZE][/FONT]
[FONT=georgia][SIZE=4][SIZE=2]Are there other user accounts but yours? Then repeat these steps for the other accounts. But, of course, for those others don't tick "Administer the system". That's a privilege that belongs only to the administrative user account (you).[/SIZE][/SIZE][/FONT]
[SIZE=4][SIZE=2][/SIZE][/SIZE] 
[SIZE=4][FONT=Georgia][SIZE=2]you can find more newbie stuff here...[/SIZE][/FONT][/SIZE]
[FONT=Georgia][SIZE=2][/SIZE][/FONT] 
[http://ubuntutip.googlepages.com/home](http://ubuntutip.googlepages.com/home)
 
Hope that helps! :P
[SIZE=4][FONT=Georgia][SIZE=2][/SIZE][/FONT] 
[FONT=georgia]
[/FONT]
[/SIZE]

---

### Post by umeshpr on 2009-06-24
Thanks everybody for taking the time to help out!:)


But still no luck.:(


Tholley- I did as told.:) unlocked in users & groups & ticked all categories in User Privileges.


aeeiah- My list of usb devices says:

Bus 001 Device 001 : ID 1d6b: 0002  Linux Foundation  2.0 root hub
Bus 002 Device 002 : ID 1b7d : 070a
Bus 002 Device 001 : ID 1d6b : 0001 Linux Foundation  1.1 root hub

For hardware drivers- it says: No proprietary hardware devices found on this system.:confused:



matthanielcm - I did the adding. but the entry says *never* in faded.


When I click on the internet connection on the right hand corner- it says 'configure VPN'


How do i do that?


Help me out guys!:)

---

