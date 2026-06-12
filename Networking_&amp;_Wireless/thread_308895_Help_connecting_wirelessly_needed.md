---
title: "Help connecting wirelessly needed"
date: 2006-11-28
forum: Networking &amp; Wireless
---

### Post by Steven Waltari on 2006-11-28
Thanks for looking at my problem!

I've a laptop with a wireless card that I believe might be working, but I'm not sure.  I think it's working (somewhat) because when I go to -> system, -> network settings, this panel shows that I have a wireless connection and that "The interface wlan0 is active".  When I highlight the wireless connection and then click the "properties" button, I get a form titled "Interface properties".  This form has a listbox titled "Network name (ESSID):".  When I click on the dropdown arrow on the listbox, I see that my computer has detected several possible wireless networks to connect to.  Some of the networks have a sine wave icon beside their names and some also have a small key icon along with the sine wave.  I assume that since my computer can detect these networks that it is possible for it to connect to them.  I also assume that the key icon means that I need a WEP key to connect to that particular network.  (I haven't tried to connect to any of those, I figure they're private networks...and I don't know the keys anyway!)

So...I choose any of the non-key networks and leave everything else default ("Key type"- Hexadecimal, "WEP key"- blank, "Configuration"- DHCP, and the other 3 are grayed out)

I click OK, everything seems to work, but I am still unable to access the internet via Firefox.  

Any ideas?

Thanks for your time & help!

---

### Post by MasterOfDisaster on 2006-11-29
Are you connecting to a wireless network that you set up yourself, or have permission to use?  If so, find the ESSID and key for the network, and input them Properties dialog.

Not sure, about this, but just the wave may mean WPA, which does need a network key.

---

### Post by Threbus5 on 2006-11-29
As you observed, a key icon indicates encryption. Unless you know that a network is public or have permission from the owner you should not asssume that it is free. (After all, how would you feel if someone started using your telephone line and because they were using it you had trouble making calls?)

Concerning using Firefox for an Internet connection through your own or another public network -
1. Make sure that Firefox is configured to use a continuous connection and not a dial-up
2. Not everyone uses DHCP, even the non-encrypted networks may use fixed IPs and they could use routers that only allow specific IPs regardless of encryption
3. Detecting a network does not necessarily mean sufficient signal strength for a connection
4. You could "play" with your wireless in some of the restaurants that provide free wireless. But, be careful! If you are operating unencrypted/unfirewalled your machine is vulnerable.
5. Best bet for wireless would be your own encrypted network.

Have fun

---

