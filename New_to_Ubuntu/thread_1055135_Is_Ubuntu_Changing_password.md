---
title: "Is Ubuntu Changing password?"
date: 2009-01-30
forum: New to Ubuntu
---

### Post by Quarkrad on 2009-01-30
I have 8.10 that is connected to router via 802.b  -  all has been fine fr a few months.  Yesterday I had some trouble with router - had to do a factory reset and reconfigure.  I have set a new password for the wifi connection and using WPA&WPA2 Personal wireless security.  This is the problem:

At the Desktop the connection rotates in the top task bar trying to make the connection.  Eventually I get the two PC icon with a warning triangle showing me that there is no connection and the Wireless Network Authorsation Required window appears.

OK - this makes sense.  In the Wireless Security box it is populated with WPA&WPA2 Personal - if I click on the Down arrow there is no other option.  I enter my security number and click the Show Password box to make sure it is OK.  I click on Connect and the Connect icon in the top task bar starts to rotate while it tries to make the connection.

Eventually it fails and the Wireless Network Authorsation Required window appears again.  If I chick on the Show Password there is gobbly-gook in the password box (random characters).

Perhaps this is OK - like windows it hides the actual code but I keep re-enterig my correct connect code and I cannot connect.  (WinXP on the sae physical PC connects OK with the new settings - why will Ubuntu not?).

Thanks.

Note.  I have also set up said config and codes in Network Configuration under Preferences.

---

### Post by cmnorton on 2009-01-30
This sounds like you to need to setup a default key in passport and encryption settings, or configure to use a flat unprotected text file for your encryption key.

---

### Post by bodhi.zazen on 2009-01-30
You are seeing your password go form english to encrypted.

This is how network manager works and is normal.

I struggled with this on 8.04 and found wicd works better for WPA.

[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

---

### Post by Quarkrad on 2009-01-30
Ok - I've configured security back to WEP and it works OK.  But I understand WPA is better then WEP but Ubuntu seems to work only with WEP.  Not sure what to do now - at least I have connection.

---

### Post by COLiNx86 on 2009-01-30
> **Quarkrad said:**
> Ok - I've configured security back to WEP and it works OK.  But I understand WPA is better then WEP but Ubuntu seems to work only with WEP.  Not sure what to do now - at least I have connection.
Do what the poster above you said, install wicd.
If you don't want to read it then I'll post it here.

[quote=wicd site]
 Installing Wicd in Ubuntu is very simple. You just have to add the Wicd repository to the Ubuntu package manager. To open the package manager in Gnome, go to Administration > Synaptic Package Manager. When it appears, go to Settings > Repositories > Third Party Software > Add..., and enter the following line: [INDENT] deb [http://apt.wicd.net](http://apt.wicd.net) hardy extras [/INDENT]where gutsy is your version of Ubuntu in lowercase (dapper, edgy, feisty, gutsy, hardy, intrepid).   You'll also need to add the key used for signing Wicd by running the following command in a terminal:[INDENT] wget -q [http://apt.wicd.net/wicd.gpg](http://apt.wicd.net/wicd.gpg) -O- | sudo apt-key add - [/INDENT]Now, click Reload, and wait while the package lists are downloaded. Now, search for "Wicd", and right click on it. Select Install, then press Apply, and Wicd will automatically be downloaded and installed for you. This will also keep you automatically up to date with the latest and greatest version of Wicd. Please note that this will remove network-manager, which is the default GNOME network manager and may cause loss of network connection temporarily.[/quote]

where it says "deb [http://apt.wicd.net]("http://apt.wicd.net/") hardy extras" just change hardy to intrepid

---

### Post by thezood on 2009-01-30
I have this exact same problem and wicd did not work any better. I don't really understand why wicd would work better, anyway. Both NetworkManager and wicd uses the same programs to connect, right?

---

### Post by teh_yodeler on 2009-01-30
I also have this similary problem, and wicd did not help.

I found that I have to use WPA-PSK (TKIP) and not WPA2 and not WPA AES

maybe that will help

---

### Post by bodhi.zazen on 2009-01-30
Wireless is complex, even on windows.

First step is hardware. Is your wireless card detected ? do you see it listed with 

```
iwconfig
```

Second, what are your wireless connections ? I suggest you start by truning off encryption, then if that works go to WEP and finally to WPA.

Depending on the problem then you are looking at anything from installing different drivers to de-bugging your encryption.

---

### Post by thezood on 2009-01-31
> **bodhi.zazen said:**
> Wireless is complex, even on windows.

First step is hardware. Is your wireless card detected ? do you see it listed with 

For me, this isn't a problem. The wireless can see my network (and my neighbor's networks), which means the card works.

[QUOTE=bodhi.zazen]
Second, what are your wireless connections ? I suggest you start by truning off encryption, then if that works go to WEP and finally to WPA.

Depending on the problem then you are looking at anything from installing different drivers to de-bugging your encryption.[/QUOTE]

A big problem for me is that I can't change encryption settings on my router, since it's provided by my ISP. It has no interface that I can reach. I'm pretty much stuck with WPA-PSK.
I have tried different drivers (madwifi and ndiswrapper) with the same results: I have to re-enter my password several times before I can connect.

Edit: maybe my problem really is unrelated to this topic. Perhaps I should start a new.

---

### Post by thezood on 2009-02-22
Just to update: I don't experience this problem any more since installing a kernel that has built-in support for my Wifi card. That leads me to believe this is a problem with ndiswrapper.

---

