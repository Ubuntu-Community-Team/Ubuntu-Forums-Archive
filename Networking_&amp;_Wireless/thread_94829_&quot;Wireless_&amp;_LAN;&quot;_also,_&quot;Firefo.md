---
title: "&quot;Wireless &amp; LAN;&quot; also, &quot;Firefox, WTF?&quot;"
date: 2005-11-24
forum: Networking &amp; Wireless
---

### Post by LadyDoor on 2005-11-24
I've got two separate problems. They're both really just annoyances, but I'd like to be rid of them. So I got ndiswrapper working on my laptop, so now it works and starts up with the computer. However, whenever it does boot up with the computer, the bootup takes a long time because I invariably am told after a wait that on the "Synchronizing clock to ntp.ubuntulinux.org" step I get a "temporary error in name resolution." When either the LAN or the wireless is not active this doesn't happen. Also, when I log in, in order to actually use the internet (though the connection status thing tells me that it's sending and receiving properly), I have to go and switch off the LAN and then switch it back on for either to work. Does anyone know a way to keep from having to do this every time I turn on my computer, and/or a way to fix the "name resolution" thing?

Also, on an unrelated note, every time I try to install an extension in Firefox (any extension--I chose at random from Firefox's site, and on different days and times), it doesn't install because, supposedly, it doesn't have an install script--or rather, the "install script [is] not found." This is also quite irritating because, well, I'd like to be able to install an extension if necessary. And it just ignores themes altogether. I use Ubuntu Breezy and Firefox 1.07. And I've tried the "change the version to 1.04 and/or 1.05" trick, and neither helped.

I've searched the fora for both of these topics, but haven't found any that matched. If anyone has the answers, you shall find me seeking for truth.

--
"My name is my own"
"My name is unspeakable / And if spoken, / Malediction" --Einstürzende Neubauten

---

### Post by Lambert on 2005-11-25
Answer on first issue only:)

You can change the server in /etc/default/ntpdate 

Mine says this

# servers to check.   (Separate multiple servers with spaces.)
#NTPSERVERS="pool.ntp.org"
NTPSERVERS="ntp.ubuntu.com"

During startup if it's taking a long time you can hit ctrl+c and it stops initializing that stop.

There's also a way to keep it from starting on boot with a command update-rc.d if you want to search this. You can post back and somebody could help you more if this option appeals to you.

---

### Post by LadyDoor on 2005-11-25
Thanks muchly...I'll see if that works.

---

