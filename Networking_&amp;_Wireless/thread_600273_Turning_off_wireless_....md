---
title: "Turning off wireless ..."
date: 2007-11-02
forum: Networking &amp; Wireless
---

### Post by asearle on 2007-11-02
I have an ASUS laptop (Z9200va) with integrated Wireless LAN which works perfectly with Ubuntu (all recent versions).  However most of the time, I leave the wireless disactivated (in Ubuntu networking) and work with my normal LAN cable connection.

The laptop has a WiFi light to indicate whether the wireless is on or off but I find that, under Ubuntu, even though the WiFi is disactivated, the light stays on.

My question here is whether the WiFi really is off (despite the light being on) or whether it is still active?

For me this has two implications:

If it is on, then it will be ...
a.) Running down my batteries
b.) Bombarding me with radio waves

Anyway, maybe someone out there can tell me of a simple method to check whether the wireless networking is really on or off?

Many thanks,
Alan Searle

---

### Post by ddrichardson on 2007-11-03
iwconfig from the command line will say ESSID: off/any if it off.

---

### Post by asearle on 2007-11-04
Yes, I checked iwconfig (copy below) and it seems that eth1 is active.

I went into KDE / System Settings / Network Settings  ... and switched the Wireless network to 'Disabled' (which as accepted) and then re-ran iwconfig.  But still got an active eth1.

I'm going to google on iwconfig and find out how to switch the wifi on and off from the command line and then see if that works.  But I still find it very strange that when I disable wireless in the 'Network Settings', it doesn't really disactivate.

Any thoughts?

Many thanks for the tips and I will report back giving the syntax once I get it workings.

Cheers,
Alan.

searle@fred:~$ sudo iwconfig
[sudo] password for searle:
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:""
          Mode:Managed  Channel=0  Access Point: Not-Associated
          Bit Rate:0 kb/s   Tx-Power=20 dBm   Sensitivity=8/0
          Retry limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by ddrichardson on 2007-11-04
> **asearle said:**
> But I still find it very strange that when I disable wireless in the 'Network Settings', it doesn't really disactivate.I'd imagine its disabling the kernel module rather than turning the card off.

---

### Post by asearle on 2007-11-04
I have been reading the man files for the command iwconfig and have tried the command ...

asearle@fred:~$ sudo iwconfig eth1 txpower off

... which gives me the following iwconfig ...

asearle@fred:~$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      radio off  ESSID:""
          Mode:Managed  Channel:0  Access Point: Not-Associated
          Bit Rate:0 kb/s   Tx-Power=off   Sensitivity=8/0
          Retry limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

Here it states 'radio off' but I am still not sure that the whole thing is shut down.

Have I found the correct syntax or is there a more definitive or cleaner way to do it?

Many thanks,
Alan Searle

---

### Post by kevdog on 2007-11-04
sudo ifconfig eth1 down

or 
sudo ifdown eth1

That is what you want

---

### Post by asearle on 2007-11-04
Yes, after running 'sudo ifconfig eth1 down' eth1 disappears when I run 'ifconfig'.  And in System Settings / Network Settings 'eth1' is marked as 'disabled'.

This seems to indicate that, yes, it is now switched off.

However, with 'iwconfig' I get the following ...

eth1      unassociated  ESSID:""
          Mode:Managed  Channel=0  Access Point: Not-Associated
          Bit Rate:0 kb/s   Tx-Power=20 dBm   Sensitivity=8/0
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

... and the wireless indicator light on my laptop is still on.

But now I am assuming that it really is off.  This is the case, isn't it?

Many thanks for the help and, yes, from now on I will use 'ifconfig' to control my wifi  :-)

Cheers,
Alan.

---

### Post by kevdog on 2007-11-04
Off -- well that depends

The transmitting capabilities of the card are off (kind of like a software off switch), however I believe the card is still drawing power.  Dont you still have lights on when looking at the card?

---

### Post by asearle on 2007-11-05
Yes, I do still have the indicator light on even though my system tells me that the network is disabled.

And, yes, my main issue is to be able to really switch of WiFi so that I can get maximum power from my battery.

So this is an irritating thing if I am not really able to shut down the card.

Any other ideas/tips on this one?

Cheers and thanks,
Alan.

---

### Post by kevdog on 2007-11-05
Try unloading the driver module

sudo modprobe -r <driver module name>

If lights are still on -- I cant think of anything else.

---

### Post by asearle on 2007-11-17
I'm back on this one again as my light is still on and I am sure that it is dramatically shortening my battery life.  Arrgghh!

Anyway, yes, now I want to try deinstalling or disactivating the wireless driver.

I want to try and use your syntax but first I need find the name / location of the appropriate driver.  I hoped that I would see it by running ifconfig but driver information doesn't seem to be displayed.

Maybe there is a flag that I can set on 'modprobe'?

Does anyone have a snippet of syntax to help me identify the driver details?

Many thanks,
Alan Searle

---

### Post by ijkn on 2007-11-17
i got the same problem too....unable to make the wifi light off even after disabled the wifi.

Now, I simply disabled the wifi in Bios that solve the problem as I can't find a better method...:(

I have searched the web...still can't find solution to resolve the issue, so finally report it as a bug.:(

---

### Post by asearle on 2007-11-17
Ah-ha, so I can disable it in BIOS.  That's good.  I'll do that until a more structured fix comes along.

Many thanks  :-)

---

### Post by kevdog on 2007-11-17
lshw -C network

This should tell you the kernel module driver you are using.  You can then temporarily remove the module from loading into the kernel with the sudo modprobe -r statement.  (this will not delete the module).

---

### Post by asearle on 2007-11-17
Great, thanks.

That'll give me more flexibility  :-)

---

### Post by asearle on 2007-11-17
I am happy with the replies.

Is there a way for me to set this thread as 'satisfactorily closed' ?

Regards,
Alan.

---

