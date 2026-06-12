---
title: "HP2133, BCM4310 STA Drivers WPA Problems"
date: 2008-11-19
forum: Networking &amp; Wireless
---

### Post by rushfan on 2008-11-19
Hello, I am running an HP2133 with the STA drivers and cannot connect to any WPA networks. I configured everything with Network Manager, however I just cannot connect. I connect to unencrypted networks fine.

I wish I could provide more useful information, but I've had a wireless card before and have no idea where to begin.

So I would appreciate some help in getting to the bottom of the issue.

Thank you in advance

---

### Post by peterthewolf on 2008-11-19
Install WICD
Search forum for wicd for more info

---

### Post by hunter24x7 on 2008-11-22
Change your wireless network AP to WPA2 for security.  It looks like there's a problem with wpa_supplicant getting the encryption negotiated correctly with some WPA/WPA2 networks.  WPA2-only seems to work correctly every time.
If iwconfig output for your wireless interface shows *lots* of crypt errors, the change to WPA2 should fix your problem.  It did for me.

As always ---> YMMV

---

### Post by Olivier2371 on 2008-11-22
I have the same family of adapters from broadcom.

If you are using ubuntu 8.04, try to use the b43 wireless adapter instead of using STA. 

If you can't find it do an update.

---

### Post by Ayuthia on 2008-11-22
> **Olivier2371 said:**
> I have the same family of adapters from broadcom.

If you are using ubuntu 8.04, try to use the b43 wireless adapter instead of using STA. 

If you can't find it do an update.

Actually, this option will not work for this card.  This card is not yet supported by the b43 driver.  The STA option or ndiswrapper are the options for this card.

---

### Post by Olivier2371 on 2008-11-22
You are correct, I found this link you should read it.

[http://linuxwireless.org/en/users/Drivers/b43]("http://linuxwireless.org/en/users/Drivers/b43")

---

### Post by hunter24x7 on 2008-11-23
The STA driver works fine for me with a 4311 and 8.10
All I did after the OS load and initial (wired) update was activate the STA driver and then change my wireless router to WPA2 security due to the crypt errors I was getting with the WPA/WPA2 security setting.

---

### Post by Olivier2371 on 2008-11-23
Is it working yet?

---

### Post by Joe2Shoe on 2008-11-23
> **hunter24x7 said:**
> The STA driver works fine for me with a 4311 and 8.10
All I did after the OS load and initial (wired) update was activate the STA driver and then change my wireless router to WPA2 security due to the crypt errors I was getting with the WPA/WPA2 security setting.

hunter,
the same procedure worked for me on a fresh install of v8.10 using the Broadcom BCM4312 rev. 02 wifi card.

Stick with the "Broadcom STA wireless driver" and WPA & WPA2 Personal encryption.

I'm dual-booting v8.10 and Vista, wireless works on both.

Joe2Shoe.

---

### Post by aloyr on 2008-12-02
same problem here with the STA driver not working with WPA2 encryption. The broadcom in question is BCM4311 and it looks like I will pull out a microsoft and reinstall ibex. Very frustrating and untimely.

---

