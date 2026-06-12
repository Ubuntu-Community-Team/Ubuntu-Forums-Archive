---
title: "Wireless Connection Issue"
date: 2016-08-23
forum: Networking &amp; Wireless
---

### Post by rwacker on 2016-08-23
Hi, 
I am new to this forum and linux in general. I have installed 14.04 on an old Dimension 2400 with dual boot capability to Windows. Have USB Wi-Fi adapter pulgged in and cannot connect to home network. I know adapter works fine because Windows connects with no problem. However on linux side I cannot get an IP4 address established. I am using a ndiswrapper which seems to work fine as I see an associated AP using iwconfig. It does occasionally connect to IP6 after a long time but I don't understand what that means. I have run the Ubuntu script wireless-info script and have a wireless-info.txt and wireless-info.tar.gz to share. Just can't figure out how to send. Forum says attachments too large.

---

### Post by wildmanne39 on 2016-08-23
Paste the wireless-info.txt file here
[http://pastebin.com/](http://pastebin.com/)
then paste the link in the forum so we can see it.

---

### Post by rwacker on 2016-08-24
[http://pastebin.com/cbfmttw6](http://pastebin.com/cbfmttw6)
Think I did this right. I title the paste raw-wire but could not find it.

---

### Post by rwacker on 2016-08-25
[COLOR=#181818][FONT=Consolas][http://pastebin.com/cbfmttw6](http://pastebin.com/cbfmttw6)

[/FONT][/COLOR]

---

### Post by chili555 on 2016-08-25
Please check here: [https://ubuntuforums.org/showthread.php?t=2264020&highlight=wna3100](https://ubuntuforums.org/showthread.php?t=2264020&highlight=wna3100)

If you'd like to try to fine-tune your chances of connection, check the settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, you may have better connectivity with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz, although it is likely to affect N speeds. I also have better luck with a fixed channel, either 1, 6 or 11, rather than automatic channel selection. Also, be certain the router is not set to use N speeds only; auto B, G and N is preferred. After making these changes, reboot the router. 

Next, I recommend that your regulatory domain be set explicitly. Check yours:```
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

If these changes don't help, then I'd invest in a fully supported device. I paid US$13 for my TP-Link TL-WN722N. I am certain there are others.

In my experience, ndiswrapper is tricky, unstable and frustrating.

---

### Post by rwacker on 2016-08-25
Unfortunately no joy with your suggestions. I may have mislead in my original post that I had intermittent connectivity. Have never established anything other than IPv6. No outside communication to any internet, ping to machines, etc. Connection speed no issue on the Windows side. I thought my driver was fine but I am not certain.

---

