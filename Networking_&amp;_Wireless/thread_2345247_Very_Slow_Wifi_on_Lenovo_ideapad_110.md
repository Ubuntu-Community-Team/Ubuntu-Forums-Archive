---
title: "Very Slow Wifi on Lenovo ideapad 110"
date: 2016-12-02
forum: Networking &amp; Wireless
---

### Post by said-el on 2016-12-02
Hello,

I installed xubuntu 16.04 on a new lenovo ideapad 110 , But I noticed the Wifi speed is very slow , 
Here is the result of wireless-info : [http://paste.ubuntu.com/23566662/](http://paste.ubuntu.com/23566662/)
Would you please help on this

Thnx

---

### Post by chili555 on 2016-12-02
> flat9            <MAC 'flat9' [AN1]>  Infra  6     2437 MHz  54 Mbit/s  60      &#9602;&#9604;&#9606;_ **[COLOR="#FF0000"] WEP[/COLOR]**        yes     * WEP wireless encryption is the most insecure encryption there is. You may as well place all your valuables in a shoebox on the front porch!!!

First, check the settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, you may have better connectivity with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz, although it is likely to affect N speeds. I also have better luck with a fixed channel, either 1, 6 or 11, rather than automatic channel selection. Also, be certain the router is not set to use N speeds only; auto B, G and N is preferred. After making these changes, reboot the router. 

Then set your regulatory domain explicitly. Check yours:```
sudo iw reg get
```If you get 00, that is a one-size-maybe-fits-all setting. Find yours here: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) Then set it temporarily:```
sudo iw reg set IS
```Of course, substitute your country code if not Iceland. Set it permanently:```
gksudo gedit /etc/default/crda
```Use nano or kate or leafpad if you don't have the text editor gedit.

Change the last line to read:```
REGDOMAIN=IS
```Proofread carefully, save and close the text editor.

Next, I'd set IPv6 to Ignore in Network Manager: [http://docs.fedoraproject.org/en-US/Fedora/18/html/Installation_Guide/images/netconfig/network-connections-ipv6-ignore.png](http://docs.fedoraproject.org/en-US/Fedora/18/html/Installation_Guide/images/netconfig/network-connections-ipv6-ignore.png)  This example is for ethernet, but you want wireless.

Reboot the computer and let us know how it's working.

[https://en.wikipedia.org/wiki/Wired_Equivalent_Privacy](https://en.wikipedia.org/wiki/Wired_Equivalent_Privacy)> In 2005, a group from the U.S. Federal Bureau of Investigation gave a demonstration where they cracked a WEP-protected network in 3 minutes using publicly available tools.

---

