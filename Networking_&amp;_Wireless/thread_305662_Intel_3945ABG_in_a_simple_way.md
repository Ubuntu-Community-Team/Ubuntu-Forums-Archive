---
title: "Intel 3945ABG in a simple way"
date: 2006-11-23
forum: Networking &amp; Wireless
---

### Post by oskar.hansen on 2006-11-23
On the Ubuntu wiki, it claims that the drivers (ipw3945.sf.net) already are installed, and it should work "out the box".

Can someone tell me a quite simple way to get my Intel 3945ABG wireless card working?

Thank you for the time.

---

### Post by jacoby on 2006-11-23
mine works fine, after a little setup.

Goto System Menu > Administration > Networking.

Click Wireless Connection, Click the checkbox by it, then the Properties button.

Fill in the various details of your network. (Note: WPA takes extra software.  WEP works though.)

Decide on manual addressing or DHCP. Click Okay.

At the top of the Network Settings window click the save current configuration button and type a name (Home, Work, School, etc)

Now in your tray, (top right) click the network icon and change  to "lo" (loopback) to "eth1" (might be eth0 but that interface is wired on my laptop.  It should connect and show you signal strength. You're done! Click close!

---

### Post by oskar.hansen on 2006-11-26
so you didn't had to setup anything else?

My problem is that there's no wireless option

---

### Post by oskar.hansen on 2006-11-29
So there's no one who got any idea, how to get an intel 3945ABG wireless card working in ubuntu 6.10?

---

### Post by rorzer on 2006-11-29
> **oskar.hansen said:**
> So there's no one who got any idea, how to get an intel 3945ABG wireless card working in ubuntu 6.10?

I'm struggling through setting up ipw3945 on my new Dell 640m.  After much mucking around searching the internet and reading that it 'just works' this is where I've got to:

1) Initially my radio (wireless and bluetooth) was off on startup, turn it on with the button on your laptop (on mine, it's Fn-F2)

2)  the Networking tool in System>Administration uses WEP encryption.  You need to set this up on your wireless router, and copy the hex code to the  properties in the wireless connection

3) enable the connection the networking tool.

4) Everyone seems to recommend NetworkManager, but my card doesn't show up in the panel applet. Syslog shows that it's detected then disabled.  Any clues?

5) I'd like to have WPA working, but WEP will do for now.

---

### Post by oskar.hansen on 2006-11-30
> **rorzer said:**
> I'm struggling through setting up ipw3945 on my new Dell 640m.  After much mucking around searching the internet and reading that it 'just works' this is where I've got to:

1) Initially my radio (wireless and bluetooth) was off on startup, turn it on with the button on your laptop (on mine, it's Fn-F2)

2)  the Networking tool in System>Administration uses WEP encryption.  You need to set this up on your wireless router, and copy the hex code to the  properties in the wireless connection

3) enable the connection the networking tool.

4) Everyone seems to recommend NetworkManager, but my card doesn't show up in the panel applet. Syslog shows that it's detected then disabled.  Any clues?

5) I'd like to have WPA working, but WEP will do for now.
So the big secret (it seems) is to turn off the wireless cards on startup!
It sounds pretty easy, I'm going to try this when I come home.

My home network is WEP right now, because i haven't got time to figuring out how to get wpa working on my own laptop (RT2500 chipset). But it shoundn't be that hard to setup, when the card is working?

---

### Post by oskar.hansen on 2006-12-01
Nope didn't work.

The big secret is the firm i bought the laptop at. Cuz There's no wireless card in the computer at all! ](*,) (thanks for their good support, I'll have it back in the middle of next week.([www.zepto.dk]("http://www.zepto.dk")))
I will suppose that the card is working, when it's installed ;) 

Sorry for disturbing with this dead end.

---

### Post by Biochem on 2007-02-04
rorzer you're the king :KS 

Who would have thought to start the radio :lolflag: 

You solved all my wireless problem Thank you   ):P

---

