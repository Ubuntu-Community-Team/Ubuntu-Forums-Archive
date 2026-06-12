---
title: "Not associated with router - card seems to be installed and active"
date: 2007-01-02
forum: Networking &amp; Wireless
---

### Post by vyoufinder on 2007-01-02
Warning - total newbie here using Belkin F5D7000

I'm trying to connect to the internet on my Ubuntu box and been reading the WifiDocs/WirelessTroubleShootingGuide at [https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide#connection](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide#connection).  I get to step 4.3 ROUTER CONNECTION.  When I type in "iwconfig" it shows that my wireless card is not associated with my router.  I have entered in the correct essid and taken out any encryption, making it an unsecured wireless network.  This still gives me the same result.  In the troubleshooting guide it tells me to look at the "man page" but there is no link to it.  I also searched for the man page and am given no result as to where it might be.  The further instructions aren't helping either.  That's why I came here.  Can anyone help?  I'm putting a screenshot of what I am talking about here and hoping to get this working.  I've been trying for more than a month now and needless to say but I will anyway, I am pretty frustrated.  However, I am still trying and still have some patience with this since I've had even less luck with Fedora or Suse.  Here's the screenshot:[IMG]http://www.vyoufinder.com/delete/Screenshot.jpg[/IMG]

---

### Post by vyoufinder on 2007-01-02
.

---

### Post by x64Jimbo on 2007-01-02
sudo iwconfig <interface> essid <ssid> key <key>
sudo dhclient <interface>

Any time there are <> brackets around a word, it means fill that in with the information indicated. Do NOT type the <> characters.

---

### Post by vyoufinder on 2007-01-02
I'm still trying but not quite there yet.. I keep getting an error telling me "unrecognised wireless request" and then lists my wep key I have been inputting.  I managed to figure out that xx:xx:xx:xx:xx: is supposed ot be replaced with a mac address, correct?  But which one I am not sure.  I tried the mac address for my wireless card, wlan network mac address from the router, and lan mac address from the router but none seems to work.  I'm attaching another screenshot in hope that it helps whoever the hero is who was kind enough to offer help, thanks for trying, I am still here and still hoping and trying to get this going.  One note to developers, it might help if in the troubleshooting instructions you tell people what to put in place of the xx's and not to input the <> brackets when typing in commands - it's a little unclear.  Another note to developers, on the instructions at [https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide#connection](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide#connection) section 4.3 - links to network scanners don't work and leaves a person stuck in troubleshooting (just so you know..)  Thank you in advance gurus!

[IMG]http://www.vyoufinder.com/delete/Screenshot-2.jpg[/IMG]

I also noticed in your post (x64Jimbo) it looks like you gave a different command than that listed at the troubleshooting page.  I tried it and something happened, but still unable to connect.  I think I did it correctly and here's a screenshot of what happened:[IMG]http://www.vyoufinder.com/delete/Screenshotother.jpg[/IMG]

...but still not working.  Ideas?

---

### Post by vyoufinder on 2007-01-03
Solved it.  I can't say for sure what it was exactly but I tried installing Ubuntu server (Dapper Drake?) on the machine as a test.  It didn't work and got hung up on the install and never finished installing.  When I did that I tried a different wireless card and then after it would not install all the way through I went back and re-installed Ubuntu 6.1.  I forgot that I had left the other wireless card in and Ubuntu didn't even recognize that a device was there, let alone that it was a wireless card.  That's when I realized that I had left the wrong card in the machine so I shut it down, put the Belkin card back in and rebooted.  Bam!  Worked.  Didn't even have to fuss or do anything, it just worked.  So my advice to anyone who has the same trouble I had with the same card, try re-installing Ubuntu without hte card in the machine then reboot with the card and maybe you'll have the good luck I had too.  That's not the answer but it might work anyway.

---

