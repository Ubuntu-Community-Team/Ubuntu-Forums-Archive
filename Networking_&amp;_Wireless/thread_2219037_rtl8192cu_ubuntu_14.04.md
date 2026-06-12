---
title: "rtl8192cu ubuntu 14.04"
date: 2014-04-22
forum: Networking &amp; Wireless
---

### Post by makragic2 on 2014-04-22
Ok guys, I really searched everywhere before this post...

I have TP-LINK WN-8200ND wireless adapter with rtl8192cu chipset and ubuntu 14.04. I wanna somehow make this work, because adapter won't connect to internet.

Now, the only thing I use is wireless internet, so there's no way that I can install something from Ubuntu, i'm writing this answer from dual-boot Windows. I can tranfer downloaded files from Win to Ubuntu.

So I beg you, if you know answer for my problem, please (i'm new to Linux) explain me how to enable wireless, I'll be eternally grateful. 

Thanks a lot!

---

### Post by varunendra on 2014-04-23
Welcome to the forums makragic2!

Please follow the "Wireless Script" link in my signature, download and run the script as per instructions there, and post back the report it generates. Use the "No Internet" method described in the linked post.

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Use Code Tags" link in my signature.

---

### Post by simon34 on 2014-04-25
> **makragic2 said:**
> Ok guys, I really searched everywhere before this post...

I have TP-LINK WN-8200ND wireless adapter with rtl8192cu chipset and ubuntu 14.04. I wanna somehow make this work, because adapter won't connect to internet.

Now, the only thing I use is wireless internet, so there's no way that I can install something from Ubuntu, i'm writing this answer from dual-boot Windows. I can tranfer downloaded files from Win to Ubuntu.

So I beg you, if you know answer for my problem, please (i'm new to Linux) explain me how to enable wireless, I'll be eternally grateful. 

Thanks a lot!

TP-LINK WN-8200ND uses modified hardware not entirely compatible with the original rtl8192cu specifications from Realtek.

You will have no luck trying to run any generic Realtek drivers with this device neither in Linux nor in Windows. Even though the device gets initialized, you will be getting frequent network failures, crippled bandwidth and truly miserable speeds.

However, in Ubuntu you can use the Win XP x86 version of the proprietary TP-Link driver [http://www.tp-linkru.com/resources/software/TL-WN8200ND_V1_Driver.zip](http://www.tp-linkru.com/resources/software/TL-WN8200ND_V1_Driver.zip) with Ndiswrapper (a standard utility that allows running Win XP wireless drivers in Linux that is readily available from the default repository)

Please mind that you will only be able to use the 32 bit version of the driver in 32 bit Ubuntu only! (You might consider running a PAE kernel so your 32 bit Ubuntu recognizes extra RAM above 4 Gb)

Installing the 32 bit driver in Ubuntu x64 will give you an error. Installing the 64 bit driver in Ubuntu x64 will immediately result in kernel panic.

Even with the 32 bit Windows XP driver running in 32 bit Ubuntu via Ndiswrapper, certain issues remain:

1. Trying to acquire a DHCP lease may repeatedly fail, even more so if WPA2 encryption is used (tested with multiple Wi-Fi router chipsets: Atheros, Broadcom, Ralink)
2. WPA2 authorization may take up to 2 minutes even if a client-defined static IP is used instead of DHCP.

Aside from these two issues, everything works perfectly. I had to abstain from DHCP with TP-Link 8200ND in Ubuntu and it takes ages before it hooks up to a network, but once it's through, **the bandwidth and stability remain perfect**. If you can do without WPA2 (I'd call that risky at best!), you are not going to face any DHCP / network address acquisition lag or issues.

P.S. Tcpdump reports suggest the driver's inability to correctly probe / pick the best available bandwidth / mode when WPA2 is used, forcing the adapter into some very lame mode that prevents it from correctly acquiring a DHCP lease and / or passing the WPA2 handshake without prolonged periods of trial and error. However, once the authorization is over, the glitches are instantly gone. Since I've been able to run the generic 8192cu Windows driver from Realtek in Ndiswrapper without such issues (of course with a different, fully 8192cu-compliant Wi-Fi adapter) I must admit that the weird behaviour of TP-Link 8200ND is more likely a driver issue than Ndiswrapper's fault. I was never able to tell any comprehensible pattern behind the authorization time weirdness, it seems absolutely random besides the fact that it's caused by WPA2 and / or DHCP. Right after Ubuntu boots up, the first authorization attempt is almost always instant and successful even with DHCP / WPA2, subsequent attempts range from instant success to many seconds of awkward security key / DHCP advertisment exchange failures or plain silence as exposed by tcpdump. The average "redial" time amidst my Ubuntu work session is 25 seconds (when I unplug and plug back the adapter for experiment's sake). This behaviour pertains across distributions, tested on Ubuntu / Kubuntu / Xubuntu / Lubuntu since 12.04, still present in 14.04 and must have been around since the adapter hit the market. I love TP-LINK 8200ND in Windows for its stability and power and very bitterly miss a bug-free implementation in Linux, especially when it comes to amd64 distributions.

Sorry for poor English and unneeded verbosity.

---

