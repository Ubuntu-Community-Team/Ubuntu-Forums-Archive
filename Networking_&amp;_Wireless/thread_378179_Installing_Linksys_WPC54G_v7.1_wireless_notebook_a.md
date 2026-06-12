---
title: "Installing Linksys WPC54G v7.1 wireless notebook adapter"
date: 2007-03-06
forum: Networking &amp; Wireless
---

### Post by Fitzcarraldo on 2007-03-06
Today I installed a wireless CardBus card in my notebook PC and configured it to use my home network, which uses WPA-PSK ("WPA-Personal"). It turned out to be quite quick and painless to set up. This is a summary of what I did, just in case it is of help to others.

I chose the Linksys WPC54G (EU) v7.1 wireless notebook adapter card (brand new for £12.50 + £1.50 p&p on eBay) because, from reading [here](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsLinksys) and [here](http://www.ubuntuforums.org/showthread.php?t=345584), it seemed to have a good chance of working 'out of the box'.

I was surfing the Web in less than half-an-hour. The card worked first time with ubuntu 6.06 LTS Dapper Drake on a Gateway Solo 9300 notebook PC. Up until today, this notebook PC had been connected to my home hub via a wired Ethernet CardBus card and Ethernet cable. However I wanted to add wireless capability to the notebook PC so that I have the choice of wired or wireless connection wherever I am in the house.

One of my criteria for choosing a wireless card was that it should work with a WPA-PSK ("WPA-Personal") network, as my existing home network is configured for that rather than WEP (WPA-PSK is more secure than WEP). The Linksys WPC54G (EU) v7.1 wireless card supports WPA-PSK as well as WEP.

After reading a *lot* of Web forums and blogs over the last couple of weeks, I decided that the applications I needed to use are Network Manager, Network Manager Gnome (the GUI front-end of Network Manager), and wpa_supplicant. I believe these three applications are installed by default when you install ubuntu Dapper Drake but, if not, they can be installed manually either by: a) using terminal commands (see later); or b) by installing Network Manager using System > Administration > Synaptic Package Manager; or c) by installing Network Manager using Automatix2 (if you have Automatix2 installed). Network Manager is intended to make it easy for the user to switch between networks or between network adapters (wired and wireless).

I describe below what I did, to the best of my recollection:
 
1. I booted up with my existing wired Ethernet CardBus card inserted in the notebook PC as usual, and made sure ubuntu installed all pending automatic updates as usual. I just wanted to make sure ubuntu was up-to-date.

2. On my notebook PC the NetworkManager Applet icon has been on the Panel, near to the Network Monitor icon, for as long as I can remember. I don't recall installing Network Manager and Network Manager Gnome, so I believe these were installed automatically when I installed ubuntu from CD. Anyway, I checked using Applications > Add/Remove... that Network Manager was ticked (not kNetworkManager, which is the version for kubuntu if I understand correctly). It was.

3. I had previously found a useful 'How To' on the Web [here](http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html) and basically I followed his instructions as explained below. I am very grateful to the guy for going to the trouble of posting an easy-to-follow guide. =D> 

Here is what his 'How To' says to do, with some edits and notes by me:

a) sudo apt-get
(I did not bother to do this step.)

b) sudo apt-get install wpasupplicant
(I did this step just as a precaution in case wpasupplicant was not installed or up-to-date, but ubuntu informed me that the latest version was already installed.)

c) sudo apt-get install network-manager-gnome network-manager
(I did not do this as Network Manager/Network Manager Gnome were already installed, presumably automatically when I installed ubuntu from CD.)

d) sudo gedit /etc/network/interfaces
   and comment out everything other than "lo" entries in that file and save the file

This is what the file /etc/network/interfaces contained after I edited it:

  auto lo
  iface lo inet loopback

Note that [this](https://help.ubuntu.com/community/WifiDocs/NetworkManager) ubuntu Community document states: *"Any already configured devices that you want to be available in Network Manager will need to de-configured, as otherwise they will be ignored. The easiest way to do this is by going to System > Administration -> Networking and then going to "Properties" of each connection. In Properties, just untick the "Enable this connection" checkbox. Logout then log back in again. These connections should now be available in Network Manager."* Well, I tried de-configuring my wired Ethernet card using this method, just to see what effect it had on Network Manager and on the file /etc/network/interfaces, and the answer was: not a lot (the entries were still in the file /etc/network/interfaces and the connection was not available in Network Manager). So I had to edit /etc/network/interfaces manually using gedit as specified above.

(By the way, I actually did the following before performing step d above:

 sudo cp /etc/network/interfaces /etc/network/interfaces.bak

just in case I wanted to revert.)

e) Use gedit to create a file called /etc/default/wpasupplicant, add entry ENABLED=0 and save the file

f) sudo touch /etc/default/wpasupplicant

g) Reboot your PC or use the following command: sudo /etc/init.d/dbus restart

h) Once you log back in to your machine you need to left-click the Network Manager icon on the Panel and select your wireless network. It should prompt for password, type, etc and it will then ask you to choose a password for your new “keyring”.

i) After entering all the details, the wireless network should be connected and working fine (you should see the Network Manager icon on the Panel change to a 'bar chart' icon, showing signal strength).

j) The PC should also detect any available wireless networks around the home and any wired network you have connected (you can see these by clicking on the Network Manager icon on the Panel).

k) If you want to connect to an existing wireless point that is not listed you can click on Connect to Other Wireless Network... and a popup box will ask for details of the wireless network.

l) If you want to create a new wireless network you can click on Create New Wireless Network... and a popup box will appear with the available options and, after entering all the details, you need to click on Connect.

m) Possible Error and Solution

If you see the following error message: "The NetworkManager applet could not find some required resources. It cannot continue." try entering the following command:

sudo gtk-update-icon-cache -f /usr/share/icons/hicolor/ 


4. When I rebooted (step g above), the wired Ethernet card was recognised by Network Manager, and I could surf the Web using it as usual. I then inserted the Linksys WPC54G v7.1 wireless card into the second CardBus/PCMCIA slot in the notebook PC and its lights came on but nothing happened: both the Network Manager icon and the Network Monitor icon on the Panel had little crosses at the bottom if I recall correctly.

5. I then rebooted again and the lights on the Linksys card started flashing. I unplugged the Ethernet cable from the wired Ethernet card, and Network Manager detected the Linksys card (but I think unplugging the Ethernet cable was a red herring - Network Manager probably would have recognised the wireless card anyway - see later).

6. I clicked on the Network Manager icon, selected 'Connect to Other Wireless Network...', typed in my network's name (the SSID) in the Network Name box, selected 'WPA Personal' for Wireless Security, entered my Password (network key) and selected TKIP for the Type. Then I clicked Connect. 

7. A window then popped up asking me to "Choose password for default keyring". Each time you reconnect to the network (after rebooting and logging in again, for example) you must provide this password. If your notebook PC were stolen or misplaced, this password would prevent someone else from using your notebook PC to connect automatically to your wireless network. The password does not have to be the same as the password in Step 6 above. However, I just entered my network key again, rather than trying to invent and forget yet another password.

8. The Network Manager icon became a little bar chart icon showing signal strength, and I launched Firefox and was able to surf the Net.

9. I then plugged in the Ethernet cable again to my still-inserted wired Ethernet card (the notebook PC has two CardBus/PCMCIA slots). I can click on the Network Manager icon and then click on Wired Network in the pull-down menu to switch back to the connection via the wired Ethernet card. I can then click on the Network Manager icon and click on my wireless network's name in the pull-down menu to switch back to the connection via the Linksys wireless network card. So Network Manager does indeed make switching easy.

10. I also tried rebooting to make sure everything still works, and it does. Big sigh of relief!

Hope this is of some use to someone.

---

### Post by Fitzcarraldo on 2007-03-07
By the way, in Point 7 in my previous post I mentioned that, rather than thinking up a new password, I entered my network key when I was prompted to specify the default password for the Gnome Keyring Manager ("Choose password for default keyring").

Today I decided that I wanted to change the default keyring password to something more memorable. Now, it is possible to change the default keyring's password for the Gnome Keyring Manager by entering either of the following two commands in a terminal window:

```
mv ~/.gnome2/keyrings/default.keyring ~/Desktop/default.keyring.bak
```

or

```
rm ~/.gnome2/keyrings/default.keyring
```

and then entering a new default keyring password when prompted after rebooting and logging in again.

I prefer the first command because you then have a backup of the keyring with the original default password in case something goes wrong.


Note that the following command will not enable you to change the password of the default keyring after you reboot:

```
mv ~/.gnome2/keyrings/default.keyring ~/.gnome2/keyrings/default.keyring.bak
```

I believe this is because Gnome Keyring Manager looks for the file default.keyring in the keyrings folder and, if it does not find it, looks in other files in that folder. As the file default.keyring.bak is in the same folder, Gnome Keyring Manager prompts the user for the default password stored in that file, which is the same as the password one is trying to change in the first place!

So the solution is make sure the folder keyrings is completely empty. Then you will be prompted to choose (i.e. create) a *new* default keyring password next time you log-in.

---

