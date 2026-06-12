---
title: "[SOLVED] How to connect to network after removing network monitor?"
date: 2015-07-10
forum: Networking &amp; Wireless
---

### Post by petrokh on 2015-07-10
Hi all,
I wanted to switch from network monitor to wicd. So, I have installed wicd and wicd-cli
and purged network monitor. Purging was my mistake, I should of just stop it. 
Now I am unable to connect to network (wired or wireless) :(

I tried to connect usong wicd-cli, it works on another computer but on the one I am talking about it stops on ¨obtainig IP adress¨ forever.

I have tried to add 
# The primary network interface
auto eth0
iface eth0 inet dhcp

to /etc/network/interfaces
I did not help as well, during boot it is waiting for network configuration for some time and then boots without network.

Any hints where should I look to fix it?

Thanks.
Petro.

P.S. I have solved it.
Firstly I run

sudo dhcp eth0

Then I have installed wicd-curses
This did not help me.
But, when I installed wicd-gtk it worked

Any idea why I was not able to connect without wicd-gtk?

---

### Post by cowboy.bebop on 2015-07-11
You should still be able to connect without the Network Manager or WicD.

Ctrl+Alt+T to open terminal (Default working directory should be /home/<username>/.)

```
#: wpa_passphrase [ssidname] [passphrase] > wpa.conf

Example: wpa_passphrase TheBatCave Pa55word
```

If your [passhrase] contains special characters, terminal might throw an exception. Resort to this command

```
#: wpa_passphrase [ssidname] > wpa.conf
[passphrase prompt] <enter>

Example: #: wpa_passphrase TheBatCave > wpa.conf 
~!Pa55word!~ <enter>
```
this will generate a file located in /home/<username>/wpa.conf which will contain

```

network={
    ssid="[ssidname]"
    #psk="[passphrase]"
    psk=59e0d07fa4c7741797a4e394f38a5c321e3bed51d54ad5fcbd3f84bc7415d73d
}
```

Next, scan for wireless networks to make sure your SSID is being broadcasted

```

#: iwlist scan | more

```

Once you have identified your networks SSID is broadcasting. Let us setup wpa_supplicant (I will be using wlan0 which is my network interface);

```

#: wpa_supplicant -D [driver] -i [networkInterface] -c [pathToConfig]

Example: wpa_supplicant -Dwext -iwlan0 -c/home/<username>/wpa.conf

```

If you don't know what driver to use, resort to the default which is 'wext'
Once you hit enter leave the screen as is and open a new Terminal tab Ctrl+Shift+T and type in

```
dhclient wlan0
```

Then your device should be connected. Now, the moment you close the terminal or close the tabs you will be disconnected. You could throw in the '-B'

```
Example:  wpa_supplicant -B -Dwext -iwlan0 -c/home/<username>/wpa.conf
```

Which will fork the daemon into the background, buts entirely preference. To check if you are connected, Run

```
ifconfig wlan0
```

For a status, check to see if IP, Netmask and Gateway were obtained and see if Tx-Rx packets were exchanged. If they were then you could open a new term tab Ctrl+Shift+T and Run

```
sudo apt-get install network-manager*
```

which will install all network manager packages including network-manager-gnome. From here your problem should be resolved with restoring network manager. If however it does not, I can only suggest backing up your /home directory and reinstalling ubuntu.

---

