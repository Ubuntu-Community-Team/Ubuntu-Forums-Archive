---
title: "WMP54G with Ubuntu 7.10"
date: 2007-11-11
forum: Networking &amp; Wireless
---

### Post by cmillar6 on 2007-11-11
has anybody had any success getting the linksys wireless card WMP54G working with Ubuntu v7.10?  if so how did you get it working?  My wifi network show ups and I enter my WEP key but it will not connect. It worked just fine with version 7.04

---

### Post by koenbeek on 2007-11-14
Hi,

  I have used gutsy on a dell with this card and was finally able to connect to the network after some tries

  I'm not sure anymore what I did that made it work at a certain moment
  I remember that I installed "wifi radar" via add/remove applications at a certain moment and played with that
  I also remember playing with the router setting it wide open at a certain moment (broadcast of SSID and no encryption at all)

  I'm not sure what did it, but after trying for about an hour it connected with WEP enabled and after that it worked perfectly

  I changed my hardware setup a week ago, so I don't have the configuration anymore

---

### Post by jtbalt on 2007-11-20
After 10 days and much swearing, I finally got the Linksys WMP54Gv4.1  wireless networking card working under 7.10 gutsy.  This was the best guide I found so far:

[https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT61](https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT61)

Stop before you get to the Fiesty Fawn Installation Section.

I would offer the following suggestions:

1.  I did this with a clean install of 7.10 (left the card plugged into the PCI slot during the install and downloaded the updates that showed up when the system was restarted after the install).

2.  I had a problem with the first step where you enter the command
                    sudo apt-get install linux-headers build-essential gcc
     I got a message saying that I needed to specify the linux header, in my case I had to do the above command as three separate commands
                   sudo apt-get install linux-headers-2.6.22-14-generic
                   sudo apt-get install build-essential
                   sudo apt-get install gcc

3.  The Ralink driver I downloaded was 1.1.1.0 (not the 1.1.0.0 mentioned in the how-to)

4.  When you get to the section "Configuration of Module" I did not use the vi way, I used the gedit way

5.  I'm using WPA and entered my settings into the /etc/network/interfaces file as mentioned.  For the WPAPSK you'll need to go to the command line and type
                        wpa_passphrase yourssid yourpassword      and this will generate your secret key which you can cut and paste into WPAPSK=lotsofstuffgetspastedherewhichisthekey

6.  I panicked when I got to enter the command     iwconfig    and saw "no wireless extensions" but that's what comes up - don't panic

7.  When doing the echo commands (there's three of them) add sudo in front of echo

8.  in the /etc/network/interfaces file I wanted mine set for DHCP so it looked like this:
          iface ra0 inet dhcp
          wireless-essid mynetworknamegoeshere
          auto ra0

That's it - and it works!  The only problems I have now is that  it only works if my router is broadcasting the ssid all the time (in fact, make sure you're broadcasting before you do this setup procedure), and I can't see any other machines when I go to 'Places - Network'.  I can see "Windows Network" but no machines come up - weird.  I'm still checking to why that's the case.  I'm not sure if it's related or not. 

Good luck, don't give up ( I almost did but it can be done)
John

---

### Post by sgtbilko on 2007-11-24
Thank you!  
:D :D :D :D

I have been struggling with this card and ubuntu for months.  I followed this and it's now working perfectly.  I had to amend the /etc/network/interfaces file to include the following instead of wireless-essid, but it works!

pre-up iwconfig ra0 essid "my network name"

Thanks again!

---

### Post by jtbalt on 2007-12-24
Well, I ended up doing a reinstall on this computer, and ran into some problems on this go around.

When I issued this command:

gksudo gedit --encoding=ISO-8859-15 /etc/Wireless/RT61STA/rt61sta.dat

it gave me an error and I had to re-issue the command without the --endcoding=ISO8859-15 command, which did work.

When I got to this step:

modprobe --remove rt61pci

I again got an error saying something like "Permission denied."

I had to issue this command instead:  sudo rmmod rt61pci
which did the trick.

This is a real pain in the neck - it's not like this card is some off-the-wall brand.  But hey, at least it works, if you're reading this post!

Good luck,
John

---

### Post by JAds217 on 2008-01-21
I have been following this thread and got to the section labeled Compilation of the Module.  I downloaded the v1.1.2.0 version of the RT61 driver.  It fails when I attempt to run make all.  Originally, it said no directory:  /lib/modules/2.6.22-14-386/build.  I created a build directory there and now it enters that directory, but says "No rule to make target `modules'.  Stop."  I therefore cannot go any further because I don't have any of the files necessary.  Does anyone know how to fix this?

---

### Post by jtbalt on 2008-01-29
I know it's not a good answer, but all I can say is that I had success by doing a complete reinstall of the OS, then (using hardwired LAN) downloading all the updates that were available, THEN doing these steps.  

To be honest, I'm not sure if there's a better or easier way, but this was the only way I could get it to work, and was able to replicate it on another reinstall.  If I have to do it again I'll try to pay close attention to what messages come up during various steps, but I seem to recall that there were some messages that came up that looked as if they were error messages.  Unfortunately, I cannot recall them at the moment.

It sure would be nice to have this fixed in the NEXT Ubuntu release - even though the card works, it works very slowly and doesn't seem to be breaking any speed records in the wireless arena.

Good luck,
John

---

