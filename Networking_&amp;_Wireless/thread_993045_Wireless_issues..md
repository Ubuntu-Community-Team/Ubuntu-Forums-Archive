---
title: "Wireless issues."
date: 2008-11-25
forum: Networking &amp; Wireless
---

### Post by melisandre on 2008-11-25
Hi;

I'm using Ubuntu 8.10 (both LiveCD and a persistent USB installation) on a Vostro 1000 laptop (64-bit, though I doubt that matters). The Wireless Card is a Dell Wireless 1395 WLAN minicard. I know there is a special "program" that came with the laptop for dealing with wireless internet when it came preinstalled with XP, but when I run Ubuntu I can't manage to connect. All wireless in the area are encrypted, and I can't access our home network. (So I haven't been able to test this on an unencrypted network).

After I input the WEP passphrase it attempts to connect, shows the two green circles next to the clock, and then tells me "Requesting a Network Address from the Wireless Network". Then it respits the "Authentication required by wireless network" input screen for the passphrase.

Are there any packages/drivers that need to be installed? Or is this a lost case?

Thanks!

-Melisandre

---

### Post by Ayuthia on 2008-11-25
> **melisandre said:**
> Hi;

I'm using Ubuntu 8.10 (both LiveCD and a persistent USB installation) on a Vostro 1000 laptop (64-bit, though I doubt that matters). The Wireless Card is a Dell Wireless 1395 WLAN minicard. I know there is a special "program" that came with the laptop for dealing with wireless internet when it came preinstalled with XP, but when I run Ubuntu I can't manage to connect. All wireless in the area are encrypted, and I can't access our home network. (So I haven't been able to test this on an unencrypted network).

After I input the WEP passphrase it attempts to connect, shows the two green circles next to the clock, and then tells me "Requesting a Network Address from the Wireless Network". Then it respits the "Authentication required by wireless network" input screen for the passphrase.

Are there any packages/drivers that need to be installed? Or is this a lost case?

Thanks!

-Melisandre

From what I have seen so far with this wireless card series, it looks like the driver does not like WEP.  It tends to do fine with WPA or unencrypted networks.  

Are you able to access the home network with a wired connection?

The other option is to try using NDISwrapper.  Here is a good link that might help:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

You will need to search for 4315.  Your chipset should be a 14e4:4315 if I recall correctly.  To verify this, go to the Terminal and type:
```
lspci -nn|grep 14e4
```You should see something in brackets that has [14e4:4315].  If you need further help with this, feel free to ask in this thread.

---

### Post by melisandre on 2008-11-25
> **Ayuthia said:**
> From what I have seen so far with this wireless card series, it looks like the driver does not like WEP.  It tends to do fine with WPA or unencrypted networks.  

Are you able to access the home network with a wired connection?

The other option is to try using NDISwrapper.  Here is a good link that might help:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

You will need to search for 4315.  Your chipset should be a 14e4:4315 if I recall correctly.  To verify this, go to the Terminal and type:
```
lspci -nn|grep 14e4
```You should see something in brackets that has [14e4:4315].  If you need further help with this, feel free to ask in this thread.

Yes, I'm working on my USB Ubuntu connected to the same network through a router, and it's wired. There aren't any issues here.

Yep, it says:

```
05:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g [14e4:4315] (rev 01)
08:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4410-B0 100Base-TX [14e4:170c] (rev 02)
```

What does this mean?

Thanks

---

### Post by Ayuthia on 2008-11-25
> **melisandre said:**
> Yes, I'm working on my USB Ubuntu connected to the same network through a router, and it's wired. There aren't any issues here.

Yep, it says:

```
05:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g [14e4:4315] (rev 01)
08:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4410-B0 100Base-TX [14e4:170c] (rev 02)
```

What does this mean?

Thanks
The 14e4:4315 means that you are using the Broadcom STA driver (wl) so you most likely will encounter the WEP problem.  The second item on the list is the wired card.  This means that your system needs to have the b44 driver also.  If you try using the NDISwrapper option, you will need to use the ssb fix that is listed in the guide that I provided in my previous post.

If you are able to access the home router, can you change the router settings to unencyrpted to test and see if you can connect?  If that works, then you might try to change it to WPA so that you can still stay secured.  If you are not able to do this, you should try the NDISwrapper option.

---

### Post by melisandre on 2008-11-25
Ok, so I am doing that. but it tells me that the package cabextract is missing (I have universe enabled, that's not the issue. It just tells me it's gone).....

---

### Post by Ayuthia on 2008-11-25
> **melisandre said:**
> Ok, so I am doing that. but it tells me that the package cabextract is missing (I have universe enabled, that's not the issue. It just tells me it's gone).....
Can you post the error message?  I am curious if it is the package that is missing or if it is the cab files.

If you are extracting a Dell .exe file, you should be able to extract it by unzipping the file.  For example:
```
unzip R174291.exe
```

---

### Post by signdog on 2008-12-14
> **melisandre said:**
> Hi;

I'm using Ubuntu 8.10 (both LiveCD and a persistent USB installation) on a Vostro 1000 laptop (64-bit, though I doubt that matters). The Wireless Card is a Dell Wireless 1395 WLAN minicard. I know there is a special "program" that came with the laptop for dealing with wireless internet when it came preinstalled with XP, but when I run Ubuntu I can't manage to connect. All wireless in the area are encrypted, and I can't access our home network. (So I haven't been able to test this on an unencrypted network).

After I input the WEP passphrase it attempts to connect, shows the two green circles next to the clock, and then tells me "Requesting a Network Address from the Wireless Network". Then it respits the "Authentication required by wireless network" input screen for the passphrase.

Are there any packages/drivers that need to be installed? Or is this a lost case?

Thanks!

-Melisandre

I don't know if this will help or not... I had same problem... I didn't want to mess with work-arounds so I hooked my laptop directly to the broadband... If the is first time it will probably find a bunch of updates... After they install look up on the taskbar and their should be an icon that says new drivers... click on it... You should see  a broadcom update... load it and then reboot... That should do it.. You might have to hit FN +F2 for wireless but it detected network on mine right off.. Next it will probably ask you for your wireless password... type it in and you should be good to go...

---

