---
title: "Another noob can't get something working!"
date: 2011-03-25
forum: New to Ubuntu
---

### Post by bobgoblin on 2011-03-25
Hi,
 
I'm brand new to Ubuntu and have installed 10.10 on a Dell dimension Tower but the ethernet card doesn't work (established that long before installing Ubuntu) so I bought a Belkin F6D4050 usb wireless adapter as I had seen that someone on this forum had one working with Ubuntu.
 
It didn't work out of the box and I didn't expect it to really so I followed the instructions in post no.2 of the following thread, which seem to have worked for a lot of people:
 
**[FONT=Verdana][SIZE=1][FONT=Verdana][SIZE=1][http://ubuntuforums.org/showthread.php?t=1509403](http://ubuntuforums.org/showthread.php?t=1509403)[/SIZE][/FONT][/SIZE][/FONT]**

 
[FONT=Verdana][SIZE=1][FONT=Verdana][SIZE=1]I restarted, plugged the adapter in and........... nothing.[/SIZE][/FONT][/SIZE][/FONT]

 
[FONT=Verdana][SIZE=1][FONT=Verdana][SIZE=1]I restarted with the adapter in and ............nothing.[/SIZE][/FONT][/SIZE][/FONT]

 
[FONT=Verdana][SIZE=1][FONT=Verdana][SIZE=1]And now because I'm so new to Ubuntu I don't even know how to check if the system has installed it. I don't know how to search for my wireless network. And I haven't the first clue where to go from here. Can anyone help please - it might just be a really basic thing but I just don't know what the hell I'm doing! It reminds me of an MS-DOS course I went on years and years ago when the tutor said to open a folder and I said "what's a Folder?"[/SIZE][/FONT][/SIZE][/FONT]

 
[FONT=Verdana][SIZE=1][FONT=Verdana][SIZE=1]Baby language please ;-)[/SIZE][/FONT][/SIZE][/FONT]
 
[FONT=Verdana][SIZE=1][FONT=Verdana][SIZE=1]Many thanks,[/SIZE][/FONT][/SIZE][/FONT]
[FONT=Verdana][SIZE=1][FONT=Verdana][SIZE=1]Bob[/SIZE][/FONT]
[/SIZE][/FONT]

---

### Post by Arijit_Kundu on 2011-03-25
can you post the output of 
> 
lsusb

(run in Accessories>Terminal) when you reboot eeping the device plugged in?

---

### Post by bobgoblin on 2011-03-25
Thanks for the fast reply, here's the output:
 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 413c:3200 Dell Computer Corp. Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 050d:935a Belkin Components 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
 
I can see the name of it there so I guess the system can see it....
 
Bw,
Bob

---

### Post by Arijit_Kundu on 2011-03-25
yes, your device is detected. it'll not show up in the desktop. So, right click the network manager and edit the connection.

am i missing something?

---

### Post by bobgoblin on 2011-03-26
[SIZE=2]No, you're probably not missing anything - I'm just a fish out of water here! I can solve most problems in Windows but this is a whole new ballgame for me.[/SIZE]
 
[SIZE=2]As an example its just taken me a good five minutes of staring at the screen trying to work out what the Network manager was. When I realised what it was I could see that it had a red exclamation mark on it.[/SIZE]
 
[SIZE=2]I right clicked and the resulting menu showed that the Network connections and Notifications were enabled. I clicked Edit and had to add a wireless connection. I edited it as follows:[/SIZE]
 
[SIZE=2]'Connect automatically' box - checked[/SIZE]
[SIZE=2]SSID box - I put in the SSID for my Sky Broadband Router[/SIZE]
[SIZE=2]Mode - I've tried 'Infrastructure' and 'AD-HOC' with no success[/SIZE]
[SIZE=2]BSSID - blank[/SIZE]
[SIZE=2]Device MAC Address - blank[/SIZE]
[SIZE=2]Cloned MAC Address - blank[/SIZE]
[SIZE=2]MTU - Auto[/SIZE]
[SIZE=2]'Available to all users' box - checked[/SIZE]
 
[SIZE=2]Still no network connection. Tried rebooting - nothing. That little red exclamation mark has firmly refused to go.[/SIZE]
 
[SIZE=2]At this stage in Windows I'd be checking in the device manager to see if there was a driver problem with the device - I guess the 'lsusb' exercise checked that? If that was ok I'd go to 'Nework Connections' and 'View available wireless networks'. I've been looking for a similar option in Ubuntu to get it to search for wireless networks but haven't found anything yet.[/SIZE]
 
[SIZE=2]So that might be a clue to just how ignorant I am of all things Linux ;-)[/SIZE]
 
[SIZE=2]Cheers (for your patience as well as your know-how!)[/SIZE]
[SIZE=2]Bob[/SIZE]

---

### Post by Grafens on 2011-03-26
Left click on the wireless icon on your taskbar and see if your router shows up, it should be there.

---

### Post by GenericBox on 2011-03-26
Perhaps its the same USB issue a few of us are having atm. Do you have an external hdd or usb drive you can plug in and see if it is mounting?

---

### Post by Arijit_Kundu on 2011-03-26
bobgoblin, what is happening if you try to add in the tab "mobile broadband". The point is, there your device should show up. Unless your device or the wireless connection is showing up, there you can not add manually.

---

### Post by bobgoblin on 2011-03-26
Hi All,
 
Sorted! Thanks loads everyone for your help.
 
I read back through all your posts and for the first time tried to logically work out how Ubuntu worked with/displayed devices and networks.
 
Once I'd got my head around that I realised that the computer is seeing the device but can't use it so the first thing I did was plug the device into my Windows laptop and install it there to see if it was working properly (cos I know what I'm doing with Windows!) It was.
 
So back to the Ubuntu pc and try again - still no luck.
 
So now it was back to carefully walking through everything I'd done from the start and that's where I found the problem - obviously the Ubuntu pc is not on the internet so all my forum stuff has been done from my Windows laptop. when I had been to the original thread that had the instructions for getting the device working in the first place I needed to get the text off so that I could copy and paste the commands as the thread advised. So I used Adobe Acrobat to create a pdf of the page the thread was on. This moved the text of the commands I had to paste into two lines. When I did paste it on the Ubuntu machine I was savvy enough to put it back into one line but not clever enough to realise I had deleted one space in each of the lines of code!!!!#-o
 
I put the spaces back in, rebooted, plugged in the device and it all worked:guitar:
 
I'd be posting this via that machine but its currently downloading 300Mb of updates.
 
Thanks again all, couldn't have solved it without you.
 
Best wishes,
Bob.

---

