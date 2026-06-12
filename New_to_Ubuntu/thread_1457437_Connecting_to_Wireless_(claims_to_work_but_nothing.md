---
title: "Connecting to Wireless (claims to work but nothing happens)"
date: 2010-04-18
forum: New to Ubuntu
---

### Post by WooWah on 2010-04-18
I'm on a MSI Wind u120 and everything is fine except WiFi.
Here's the details:

I've done this 
sudo apt-get install --reinstall bcmwl-kernel-source
And I get this in terminal
```
iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     802.11b/g  Mode:Managed  Frequency=2.422 GHz  
          Access Point: Not-Associated   Bit Rate:11 Mb/s   
          Retry:on   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/100  Signal level=0 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```I can't get a list of available networks. How do I get from where I am to get on the internet using wifi?

---

### Post by anewguy on 2010-04-18
Click on the network manager icon and be sure "enable wireless" is checked.

Also, you may need to set the mode to roaming in order to see available networks.


Dave ;)

---

### Post by WooWah on 2010-04-18
Wireless is enabled, but I can't figure out to enable roaming. It looks like roaming is enabled by default and I couldn't find any help using google to confirm if mine is enabled. 

I tried creating a wifi access point because I had the option, but no luck finding it using my other computers. It makes me think that the wireless card thinks it's working but in reality it isn't.

---

### Post by WooWah on 2010-04-20
I've gotten the wifi to work by using KNetworkManager, which is available in the Ubuntu Software Center.

The only catch is I have to give it access to the KeyChain every time I boot up.

---

### Post by anewguy on 2010-04-20
I think you mean the keyring?  Usually when it first asks for a password for that (the very first time, not each boot, etc.) you enter in your login password and then it doesn't ask again.

If you look under Applications/Accessories, you will see the entry "Passwords and Encryption Keys".  Check the 2 key tabs in that and see if you see one for the keyring.  If so, I *think* you can clear that (I haven't gone through it because I haven't had that problem), then when it asks for the keyring password again just put in your login password.

Dave ;)

---

### Post by LewRockwell on 2010-04-20
Saw this earlier today so I went back and grabbed the link.

[http://www.linuxplanet.com/linuxplanet/tutorials/7044/1/](http://www.linuxplanet.com/linuxplanet/tutorials/7044/1/)

.

---

