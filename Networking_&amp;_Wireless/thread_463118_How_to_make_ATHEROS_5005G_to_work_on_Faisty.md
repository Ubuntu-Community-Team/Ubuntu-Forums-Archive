---
title: "How to make ATHEROS 5005G to work on Faisty"
date: 2007-06-03
forum: Networking &amp; Wireless
---

### Post by decatett on 2007-06-03
I have "Atheros Communications, Inc. AR5005G 802.11abg " and with nm-aplet dont work ... finaly I make to work with WICD


Step by Step

1. kill nm-applet from System Monitor
2. "sudo aptitude remove network-manager" in terminal, remove Network Manager from ubuntu
3.  download wicd from "http://sourceforge.net/project/showfiles.php?group_id=194573"  on Desktop
4. in terminal "cd Desktop"
5 in terminal "sudo dpkg -i wicd_1.2.7-all.deb"
6. after install pret ALT + F2 and type "/opt/wicd/tray-edgy.py"
7. in "System > Preferences > Sessions" add new line for WICD to start on reboot "/opt/wicd/tray-edgy.py" its OK work with edgy in feisty 

[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/) , wicd homepage
[http://wicd.sourceforge.net/wiki/doku.php?id=faq&DokuWiki=e5527b1e809f2c95f3732233cd4a9c0b](http://wicd.sourceforge.net/wiki/doku.php?id=faq&DokuWiki=e5527b1e809f2c95f3732233cd4a9c0b), wicd FAQ

---

### Post by tagrat on 2007-06-06
The only issue I had is that uninstalling nm-applet messed up my wired connection too

---

### Post by decatett on 2007-06-06
first you nead to kill nm-applet 
alternative way is to type in  terminal  "top" command and then you wil see nm-applet runing 
then you wil type in terminal "sudo kill -9 xxxx" where xxxx is the PID number of nm-applet in "top" command

then next step

"
2. "sudo aptitude remove network-manager" in terminal, remove Network Manager from ubuntu
3. download wicd from "http://sourceforge.net/project/showfiles.php?group_id=194573" on Desktop
4. in terminal "cd Desktop"
5 in terminal "sudo dpkg -i wicd_1.2.7-all.deb"
6. after install pret ALT + F2 and type "/opt/wicd/tray-edgy.py"
7. in "System > Preferences > Sessions" add new line for WICD to start on reboot "/opt/wicd/tray-edgy.py" its OK work with edgy in feisty
"

i can tell you WICD is more better the Network Manager

PS sorry for my eanglish

---

### Post by rpaller on 2007-06-07
Thanks for the tip on this. I have installed it and will test it with my wireless network (WPA) tonight. I was really discouraged to loose my WPA wireless ability after the recent upgrade. Hopefully this is the cure.

---

### Post by rpaller on 2007-06-08
It worked! Thanks for the info on WICD. For some reason my Gnome session won't reload the panel icon. I can manage with this though...

---

### Post by hoodwink on 2007-06-09
I finally got it to work, but a little bit of guesswork was required.

1. The kernel updates do not automatically upgrade linux-restricted-modules-generic when a new kernel image is installed. This caused my Atheros card to be ignored. After installin the appropriayte restricted drivers, at least the card was detected.

2. wicd assumes that the wireless is wlan0, but iwconfig showed me that ath0 is the correct entry.

3. After updating wicd preferences and refreshing, card isw now working.

Anyone know how to put wicd in the panel for xubuntu?

---

### Post by ugm6hr on 2007-06-10
> **hoodwink said:**
> 
2. wicd assumes that the wireless is wlan0, but iwconfig showed me that ath0 is the correct entry.

Anyone know how to put wicd in the panel for xubuntu?

Wicd does not get the wpa driver correct either - a bit of googling revealed that prism2 chipset requires *hostapd.*  But it does work.  Shame that the documentation leaves a lot to be desired.  I did find that the "stable" 1.2.7 release was a lot more unstable than the "testing" 1.2.9 version in Feisty.

In Xubuntu - to add to panel:
1. Applications->Settings->Autostarted Applications:
2. Add
3. Name: Wicd / Command: /opt/wicd/tray-edgy.py

I'm not sure that the panel entry does anything useful, that can't be achieved by selecting Wicd from Applications->Network

EDIT:
I just remembered why I read this thread - I have the 5005G in my Acer laptop, which works happily with Network Manager.  Bizarre, because I initially got intermittent dropped connections with WPA - which prompted a switch to WEP - but having discovered Wicd (for another laptop), I switched back to WPA - and now it works with Network Manager (RE-EDIT: NM still drops intermittently - just not as often).

---

### Post by Cavaco on 2007-06-15
Hi Guys,

Thanks for these posts , I had similar troubles with an Acer 5050 and the 5005g Card, I tried this proceedure and it worked without a hitch !!

---

### Post by Unreal223linux on 2007-06-17
Ok I really am having a hard time following this procedure. 
I have a toshiba laptop and in windows it says this:
Artheros AR5005G  Wireless Network Adapter 

So I guess I have the card this fix is for. I had all kinds of problems with ubuntu wireless so I had to switch back to windows. I fell in love with ubuntu while I was using it though(actually mint linux. same thing though really).

Does wict connect to the internet fast like it should? Can you easilly and graphically change networks with it? 
With networkmanager I had to wait what seemed like 5minutes or so after a reboot for it to connect. Then once it connected it would drop connection every 20 minutes or so. Also it wasn't getting nearly as much range as I do on windows.(I can be outside of my house in windows but in ubuntu I couldn't even go into another room)

Did changing to wic fix all of these issues?

---

### Post by Unreal223linux on 2007-06-17
Ok I installed this and it seems to be working but I don't how to make it autostart up and be on my panel. I'm on ubuntu

---

### Post by Unreal223linux on 2007-06-17
Nevermind I missed the last step. :P
Sorry. :(

---

### Post by Unreal223linux on 2007-06-18
:(

I'm still getting embarisingly bad range. I cant even go out of the room from the router. 
On the plus side it seems to work every time now and isn't dropping connection but that isn't good enough. :(

In windows I can go to my neighbors house and still use my internet, with ubuntu I cant even go upstairs. Is there anything I can do to bump up my range?

---

### Post by ugm6hr on 2007-06-18
> **Unreal223linux said:**
> :(

I'm still getting embarisingly bad range. I cant even go out of the room from the router. 
On the plus side it seems to work every time now and isn't dropping connection but that isn't good enough. :(

In windows I can go to my neighbors house and still use my internet, with ubuntu I cant even go upstairs. Is there anything I can do to bump up my range?

Hmmm...  Not sure.  While Wicd gives a low signal %, it has an excellent range on my laptop in Xubuntu, with a permanently connected signal despite signal strength of as low as 17%.  Can't think of any good reason why the range should be different between Windows and Ubuntu.

---

### Post by stchman on 2007-06-18
> **decatett said:**
> I have "Atheros Communications, Inc. AR5005G 802.11abg " and with nm-aplet dont work ... finaly I make to work with WICD


Step by Step

1. kill nm-applet from System Monitor
2. "sudo aptitude remove network-manager" in terminal, remove Network Manager from ubuntu
3.  download wicd from "http://sourceforge.net/project/showfiles.php?group_id=194573"  on Desktop
4. in terminal "cd Desktop"
5 in terminal "sudo dpkg -i wicd_1.2.7-all.deb"
6. after install pret ALT + F2 and type "/opt/wicd/tray-edgy.py"
7. in "System > Preferences > Sessions" add new line for WICD to start on reboot "/opt/wicd/tray-edgy.py" its OK work with edgy in feisty 

[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/) , wicd homepage
[http://wicd.sourceforge.net/wiki/doku.php?id=faq&DokuWiki=e5527b1e809f2c95f3732233cd4a9c0b](http://wicd.sourceforge.net/wiki/doku.php?id=faq&DokuWiki=e5527b1e809f2c95f3732233cd4a9c0b), wicd FAQ

That card should work out of the box with Feisty.  If not enable the restricted drivers for Atheros.

---

### Post by Unreal223linux on 2007-06-18
Do you use WPA encryption ugm6hr?
I have WPA on my router just to keep the neighbors off my network(since I have a computer completely open with all my files on it. Sort of a file server I guess). WEP is too confusing for me and I've heard its easy to crack. 

Could my range problems be with WPA? It doesn't make sense though because it should at least be able to connect.

---

### Post by ugm6hr on 2007-06-18
> **Unreal223linux said:**
> Do you use WPA encryption ugm6hr?
I have WPA on my router just to keep the neighbors off my network(since I have a computer completely open with all my files on it. Sort of a file server I guess). WEP is too confusing for me and I've heard its easy to crack. 

Could my range problems be with WPA? It doesn't make sense though because it should at least be able to connect.

I use 4 different networks: WEP 64-bit / WEP 128-bit & MAC filtering / WPA-TKIP (2 networks - I think it's TKIP).

And Wicd behaves just as in Windows on all networks.

---

### Post by Unreal223linux on 2007-06-18
Did you change the WPA driver thing in wicd? I changed it to madwifi but that didn't work either.
Do you think getting the driver from windows and using ndiswrapper would work?

---

### Post by teachop on 2007-06-18
Just in case WICD doesn't work for somebody...

My Acer Aspire 3100 has the same wireless chip, and I couldn't get network managers to work in a reliable fashion.  With Network Manager, the connection would drop and reconnect constantly.  With WICD for some reason resume from suspend was not reliable at all.

This is what worked for me to get WPA going with good range and functioning suspend / resume (but no roaming unfortunately):

disable Network Manager in System>Preferences>Sessions

add a set up for wpa in /etc/network/interfaces
	auto ath0
	iface ath0 inet dhcp
	wpa-driver madwifi
	wpa-conf /etc/wpa_supplicant.conf

create /etc/wpa_supplicant.conf
network={
        ssid="your_ssid"
	proto=WPA
	key_mgmt=WPA-PSK
        psk=your_value_in_hex
}

Note: use the program "wpa_passphrase" to get the hex value.

I got that stuff out of Ubuntu help pages.  Now I am running reliably wired or wireless, and waiting for a Network Manager update so I can get roaming too.  Till then I am happy enough where I am...

---

### Post by ugm6hr on 2007-06-19
> **Unreal223linux said:**
> Did you change the WPA driver thing in wicd? I changed it to madwifi but that didn't work either.
Do you think getting the driver from windows and using ndiswrapper would work?

I use the default Restricted Drivers for the card (just ticked the box in options) - and in the preferences of Wicd - use the *wext* wpa-supplicant.  The interface is *ath0.*  I have never had to use ndiswrapper.

As stated - the resume from suspend doesn't work with Wicd though - doesn't matter to me - I never suspend anyway.  Hopefully will be sorted if (?when) Wicd has the option to disconnect from a network (shame it doesn't).

For me - roaming is more important since I use multiple networks.

---

### Post by dardack on 2007-06-19
> I use the default Restricted Drivers for the card (just ticked the box in options)

I had problems with the default Restricted Driver for the AR 5005G.  I was getting signal strength only around 20% or less.  The connection would drop randomly for 45 to 2 minutes and then come back up, but became very annoying.  Finally, i followed the ndiswrapper instructions, found the pci bus number on the NDISWRAPPER website, downloaded that driver, did like i should, and now i get 60% or better strength, and so far no network drops.

---

