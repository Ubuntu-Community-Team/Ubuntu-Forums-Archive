---
title: "Setup Wireless Connection on Ubuntu 6.10"
date: 2007-02-03
forum: Networking &amp; Wireless
---

### Post by sydneyfx on 2007-02-03
I'm a new user to linux but have had some exposure to command line on a Unix box so I can get around a command line without too much trouble.

I've just installed Ubuntu 6.10 on a BenQ Joybook 5100 laptop which has now replaced the original OEM Windows XP Operating system.

The install went well except that I can't access the internet from my inbuilt wireless adapter.  I've installed all the latest updates using the wired ethernet card but the wireless still isn't connecting.

I've done an iwlst scan from the command line and my wireless connection is listed but I run a WPA-PSK encryption and I'm not sure it that is the problem.

Any ideas on how to set this up to work correctly?

---

### Post by phossal on 2007-02-03
What is the output to:
```
iwconfig
```

And what type of wireless device is it?

---

### Post by andytof47 on 2007-02-03
> **sydneyfx said:**
> I've done an iwlst scan from the command line and my wireless connection is listed but I run a WPA-PSK encryption and I'm not sure it that is the problem.

Any ideas on how to set this up to work correctly?

Did you go through [this?]("http://ubuntuforums.org/showthread.php?t=318539")

What sort of firewall is it?

A router? Linux firewall? Is mac filtering enabled etc?

---

### Post by sydneyfx on 2007-02-03
the output of the iwconfig is as follows
```

lo        no wireless extensions.

eth1    unassociated  ESSID:"RAILS"  Nickname:"ipw2100"
          Mode:Managed  Channel=0  Access Point: Not-Associated   
          Bit Rate=0 kb/s   Tx-Power:16 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

sit0      no wireless extensions.

```

The device manager has it listed as an Intel Corporation PRO/Wireless LAN 2100 3B Mini PCI

I'm trying to connect to a Netgear wireless router which has all the login info for my internet access.

I haven't yet tried the wireless security post that andytof47 mentioned as I thought I might see if it connecting wireless was just a simple fix first.

---

### Post by phossal on 2007-02-03
I'm not a security expert, but I do take the time to configure WPA on my router. However, when first establishing a connection, it's best to make it as simple as possible. For that reason, I recommend disabling WEP/WPA on your router, configuring /etc/network/interfaces or using the GUI tools until you're up. Once connected successfully, you can configure your network as it should be, for permanence and security.

I prefer to use the *iwconfig* command. With no router security, the *key* parameter is unnecessary. I usually set the ESSID and the CHANNEL only. 

It appears you've set the essid, but not the channel (which isn't absolutely necessary). Rereading your post, it seems like your router *is* protected. Disable it, and then issue this:
```
sudo iwconfig eth1 essid <YOUR_ESSID> channel <YOUR_CHANNEL>
```

If that appears successful, then issue this:
```
sudo dhclient eth1
```

---

### Post by sydneyfx on 2007-02-03
I turned off the WPA security on the router and issued the command

sudo iwconfig eth1 essid RAILS channel 8 

and got the following error

```
Error for wireless request "Set Frequency" (8B04) : SET failed on device eth1 ; Operation not supported
```

I've got the router set up on channel 8 but I'm not sure if the parameters and syntax I entered for the command are entirely correct which I've listed above.

---

### Post by phossal on 2007-02-03
That makes me think you're using the wrong driver. It looks like the essid was already set. Try the *dhclient* command.

---

### Post by tacm on 2007-02-03
> **phossal said:**
> I'm not a security expert, but I do take the time to configure WPA on my router. However, when first establishing a connection, it's best to make it as simple as possible. For that reason, I recommend disabling WEP/WPA on your router, configuring /etc/network/interfaces or using the GUI tools until you're up. Once connected successfully, you can configure your network as it should be, for permanence and security.

I prefer to use the *iwconfig* command. With no router security, the *key* parameter is unnecessary. I usually set the ESSID and the CHANNEL only. 

It appears you've set the essid, but not the channel (which isn't absolutely necessary). Rereading your post, it seems like your router *is* protected. Disable it, and then issue this:
```
sudo iwconfig eth1 essid <YOUR_ESSID> channel <YOUR_CHANNEL>
```

If that appears successful, then issue this:
```
sudo dhclient eth1
```Hey Phossal, thats the way we did it when you helped me last week...and thanx again..I dont mean to hijack but if I just had a really weird problem.  if you are still online could you take a look at my above post.  Thanx

---

### Post by phossal on 2007-02-03
What post? Where? :)

---

### Post by tacm on 2007-02-03
wireless and networking.....I just put it up

---

### Post by sydneyfx on 2007-02-03
I've managed to find a fix for this problem and it worked.  It's a pretty simple fix providing you know how to use the terminal and edit and create a couple of files.

You can find the guide on [how to setup WPA wireless on Ubuntu]("http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html")

Thanks phossal for the support that you provided as it was appreciated.

---

