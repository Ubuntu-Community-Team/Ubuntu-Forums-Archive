---
title: "Horrible 3g install user experience in 8.10 Intrepid"
date: 2008-10-30
forum: Networking &amp; Wireless
---

### Post by jeffme on 2008-10-30
Any help is most appreciated!

I am having problems getting my Sierra AC-860 3G UMTS AT&T PCMCIA card working on my IBM x60 Laptop running the released version of 8.10.

Situation so far:
- Ubuntu installed using Wubi
- Sierra AC-860 was in the PCMCIA slot during 8.10 instalation
- I don't see any related options when I click on the signal strength monitor in the upper right hand corner of my desktop
- I go to System -> Preferences -> Network Configuration -> Mobile Broadband -> Add 
- I then step through the wizard, selecting plain old "AT&T" as my service provider and use the default name of AT&T for that setting
- Then... I get no feedback indicating what to do next, just the presence of my new connection in the Mobile Broadband tab list and a button that says, "x Close", so I hit that... now what?
- I go back to the signal strength monitor and don't see anything labeled AT&T
- I go to the Ubuntu help files and get absolutely zero returns on "mobile broadband"
- I go back to the AT&T profile and select "connect automatically" - nothing happens & I still don't see any info related to AT&T under the signal strength bars
- I go back to the AT&T profile and select "system setting" and deselect "connect automatically" - still nothing happens
- I go back to the AT&T profile and see that the "system setting" state has magically changed from checked to unchecked. I repeat this several times to make sure I wasn't doing something wrong.
- Still no clue what's up
- I have an "Unknown interface" on the device called "wmaster0"
- The green light on my card is flashing, which I think just means power is good
- I have no clue how to tell if the system has even recognized my pcmcia card or not

Reasons for frustration:
- No clear way to know where to find 3G-related stuff for a noob
- I click on "Network Configuration" but am returned a screen titled "Network Connections"... are they the same thing?
- "Mobile broadband" returns no hits in the built-in help files
- Not clear what "system setting" means in the network connection profile tab for the mobile broadband profile & no info in the documentation
- No clear way to see if system has recognized the PCMCIA card
- No tactile feedback indicating if my changes to the Mobile Broadband profile settings have had any effect or prompting to see if you want to test the connection or just start using the connection
- Inexplicable state loss of checked "system setting" box

I have been reading lots of favorable reviews about this highlight of Intrepid, but IMO, this feature should not have shipped in its current condition. The fact that it "just works" for some people is no excuse for zero documentation and zero workflow context UE in a distribution designed to be user friendly and for the masses. 

That rant all said, if anyone is still reading and willing to help, that would be fantastic! Thanks in advance. ; )

p.s. in spite of the noob status, I'm not afraid of the command prompt, I'd just like to see the cool UI stuff "just work" for me. I'd rather use my PC than set it up...

---

### Post by jeffme on 2008-10-31
Take 1:

Ok... this thread was very helpful:
[http://ubuntuforums.org/showthread.php?t=786905&highlight=sierra+860&page=2](http://ubuntuforums.org/showthread.php?t=786905&highlight=sierra+860&page=2)

Short version of what's up:
- My laptop was, in fact, not recognizing the PCMCIA card, but Ubuntu provided no tactile feedback that this was the case

Key diagnostic commands:
> root@ubuntu:~# pccardctl ident
Socket 0:
  product info: "Sierra Wireless", "AC860", "3G Network Adapter", "R1"
  manfid: 0x0192, 0x0710
  function: 6 (network)

Key point: "function: 6 (network)" sounds good, but is not. The network manager is looking for a serial modem device.

Next step: see what the system thinks is going on when you plug in your PCMCIA card
> root@ubuntu:~# tail -f /var/log/messages
Oct 31 10:51:49 ubuntu kernel: [ 3061.679806] pccard: card ejected from slot 0
Oct 31 10:51:56 ubuntu kernel: [ 3068.632063] pccard: PCMCIA card inserted into slot 0
Oct 31 10:51:56 ubuntu kernel: [ 3068.633597] pcmcia: registering new device pcmcia0.0
Oct 31 10:51:56 ubuntu kernel: [ 3068.635030] firmware: requesting SW_7xx_SER.cis


Ok... it's looking for some file called SW_7xx_SER.cis

A little digging around on the Ubuntu forums reveals that Ubuntu wants these files to be stored in /lib/firmware & that they help the PC do it's own little plug'n'play auto-install when the device is plugged in. The fact that your green light is flashing away quite nicely only means that you in fact have a PCMCIA card and that your computer knows that it's a PCMCIA card and is doing all sorts of other things properly, but it does not understand that the card contains a cool 3G serial modem.

Other digging around on the Internet reveals this web page:
[http://www.sierrawireless.com/faq/ShowFAQ.aspx?ID=92](http://www.sierrawireless.com/faq/ShowFAQ.aspx?ID=92)
And a download file called AirCard_8xx_Linux.tar.gz
(In general, when searching for these files, just type something like:
"AirCard XXX Linux site:sierrawireless.com", where XXX is your AirCard model into the Google search bar and start digging.

Download this file to your desktop.
Extract its contents by right-clicking on the AirCard_8xx_Linux.tar.gz file icon on your desktop and selecting "Extract Here".
This should create a folder called AirCard_8xx_Linux on your desktop.
Open the AirCard_8xx_Linux folder by double-clicking on it.
Double-check that there's a file there called SW_8xx_SER.dat there.
Go to "Places" found in the upper-left corner of your Ubuntu desktop screen.
Click on it and then select "Computer"
Double-click on the "Filesystem" icon in the Computer folder.
Double-click on the "lib" folder in the "/ " File Browser window.

Aha... there's no way to move files as root using Nautilus without doing some trickery... rats. Another Ubuntu usability shortfall.

---

### Post by jeffme on 2008-10-31
Take 2:

Now, there's no way around using the terminal, so, you'll need to use the command terminal:

Click on the Ubuntu icon in the upper left-hand corner of your desktop.
Select Accessories -> Terminal
Execute the following steps using your own password where it says "password for jeffme" - yours will say whatever your username is, instead of "jeffme":

> jeffme@ubuntu:~$ sudo bash
[sudo] password for jeffme: 
root@ubuntu:~# ls Desktop/AirCard_8xx_Linux
ac850  ac850chat  SW_8xx_SER.dat
root@ubuntu:~# mv Desktop/AirCard_8xx_Linux/SW_8xx_SER.dat /lib/firmware/SW_7xx_SER.cis 

Now, see what happens when you pull your card out and put it back in (don't forget to enter the "tail -f" command before pulling the card out and putting it back in.

> root@ubuntu:~# tail -f /var/log/messages
Oct 31 13:16:54 ubuntu kernel: [11766.494488] pccard: card ejected from slot 0
Oct 31 13:16:58 ubuntu kernel: [11770.728069] pccard: PCMCIA card inserted into slot 0
Oct 31 13:16:58 ubuntu kernel: [11770.728717] pcmcia: registering new device pcmcia0.0
Oct 31 13:16:58 ubuntu kernel: [11770.730213] firmware: requesting SW_7xx_SER.cis
Oct 31 13:16:58 ubuntu kernel: [11770.781595] 0.0: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A

Double-check that the system identification for this device has changed:

> root@ubuntu:~# pccardctl ident
Socket 0:
  product info: "Sierra Wireless", "AC850", "3G Network Adapter", "R1"
  manfid: 0x0192, 0x0710
  function: 2 (serial)
root@ubuntu:~# 
root@ubuntu:~# 

Ok - the system sees a serial modem... things are looking good so far.
Go back and start the tail again:

> root@ubuntu:~# tail -f /var/log/messages

Now, keep an eye on that terminal while you go up to the network manager in the upper right-hand corner of the screen. Hopefully, you will see the Network Connection profile you created on your way to discovering that the AirCard wasn't working quite yet.

Hopefully, you should see messages like this:
> Oct 31 13:54:32 ubuntu pppd[21835]: Plugin /usr/lib/pppd/2.4.4/nm-pppd-plugin.so loaded.
Oct 31 13:54:32 ubuntu pppd[21835]: pppd 2.4.4 started by root, uid 0
Oct 31 13:54:32 ubuntu pppd[21835]: Using interface ppp0
Oct 31 13:54:32 ubuntu pppd[21835]: Connect: ppp0 <--> /dev/ttyS0
Oct 31 13:54:32 ubuntu pppd[21835]: CHAP authentication succeeded
Oct 31 13:54:32 ubuntu pppd[21835]: CHAP authentication succeeded
Oct 31 13:54:36 ubuntu pppd[21835]: Could not determine remote IP address: defaulting to 10.64.64.64
Oct 31 13:54:36 ubuntu pppd[21835]: local  IP address 10.95.140.89
Oct 31 13:54:36 ubuntu pppd[21835]: remote IP address 10.64.64.64
Oct 31 13:54:36 ubuntu pppd[21835]: primary   DNS address 172.18.7.170
Oct 31 13:54:36 ubuntu pppd[21835]: secondary DNS address 172.18.7.170

If not, keep posting here & hopefully someone will come and help you out.

---

### Post by jeffme on 2008-10-31
Summary of issue:

Network manager should recognize that there's no 3G device available and let user know that in some way shape or form.

Hotplug manager should provide notification that an unrecognized device has been inserted and that some things may not function as desired.

Nautilus should allow permission-based file copies for root-access folders.


This whole affair is still waaaay too difficult for a typical PC user.

---

### Post by Skaught11 on 2008-11-08
I too found the process to not at all be easy.  And have yet to get it working.

I am on Rogers

I think I am very close, I get this:

Nov  8 06:31:58 skaught-laptop pppd[8668]: Using interface ppp0
Nov  8 06:31:58 skaught-laptop pppd[8668]: Connect: ppp0 <--> /dev/ttyS0
Nov  8 06:32:03 skaught-laptop pppd[8668]: CHAP authentication succeeded
Nov  8 06:32:03 skaught-laptop pppd[8668]: CHAP authentication succeeded
Nov  8 06:32:03 skaught-laptop pppd[8668]: Modem hangup
Nov  8 06:32:03 skaught-laptop pppd[8668]: Connection terminated.
Nov  8 06:32:04 skaught-laptop pppd[8668]: Exit.

It seems to connect then instantly disconnect.  It also asks me for a password but rogers says there is no password.  Many online guides say to use PAP but if I select PAP, Ubuntu ignores my config change and simply reverts to defaults no matter what I do.

---

### Post by Skaught11 on 2008-11-09
There is definitely some sort of interface bug.  When I try changing the user name or password it rarely saves my config change.  I have to set it 10 or 20 times for the setting to take.

Is there a conf file someplace I can edit instead?

---

