---
title: "Problems accessing Internet via ASUS USB-N!3 Adapter"
date: 2016-08-11
forum: Networking &amp; Wireless
---

### Post by Rebecca_D on 2016-08-11
I recently purchased an ASUS USB-N13 Wi-fi adapter for my desktop running Ubuntu 14.04 Trusty 64x. I installed the driver using the instructions given in this post [http://askubuntu.com/questions/168627/connecting-asus-usb-n13-wireless-adapter]("http://askubuntu.com/questions/168627/connecting-asus-usb-n13-wireless-adapter") downloading the correct Linux driver from Realtek and also installed the fixes suggested in this post [http://askubuntu.com/questions/456759/asus-usb-n13-wireless-adapter-problems-with-ubuntu-14-04]("http://askubuntu.com/questions/456759/asus-usb-n13-wireless-adapter-problems-with-ubuntu-14-04").

When plugged in, my network is recognised,

[http://www.nodular-prurigo.org.uk/images/network1.jpeg](http://www.nodular-prurigo.org.uk/images/network1.jpeg)

but I cannot connect any program (Firefox, Chrome, Filezilla etc.) to the internet. Firefox just gives me this. I have then to use a wired connection which is what I want to get rid of.

[http://www.nodular-prurigo.org.uk/images/network2.jpeg](http://www.nodular-prurigo.org.uk/images/network2.jpeg)

**lsusb** gives the following output
```
rebeccad@mishkamoo:~$ lsusb
**Bus 002 Device 010: ID 0b05:17ab ASUSTek Computer, Inc. USB-N13 802.11n Network Adapter (rev. B1) [Realtek RTL8192CU]**
Bus 002 Device 007: ID 0572:1329 Conexant Systems (Rockwell), Inc. 
Bus 002 Device 006: ID 0bc2:3000 Seagate RSS LLC FreeAgent Desktop
Bus 002 Device 005: ID 172f:0500 Waltop International Corp. Media Tablet 14.1"
Bus 002 Device 004: ID 2001:f103 D-Link Corp. DUB-H7 7-port USB 2.0 hub
Bus 002 Device 009: ID 046d:08c9 Logitech, Inc. QuickCam Ultra Vision
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 046d:c534 Logitech, Inc. Unifying Receiver
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 058f:9360 Alcor Micro Corp. 8-in-1 Media Card Reader
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

so it would appear that it is working. I am frustrated as in researching for a wireeless adapter this one was suggested as the easiest to install within Ubuntu. Any help or suggestions would be gratefully received.

Please bear in mind I have limited experience 'under the hood' of Linux, so walk me through if you can.

Thanks.

---

### Post by wildmanne39 on 2016-08-11
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

Please use the default font color and properties unless you need to highlight or draw attention to a part of your post, but they are not intended to be used for an entire post.

Please click on the wireless script in my signature and follow the directions for running the script and posting the results here. 
Thanks

---

### Post by Rebecca_D on 2016-08-11
Thanks for the reply Wild Man. Sorry that I have not yet learnt the formatting etiquette of this forum yet. Will try better! Will run your script and post results back.

---

### Post by Rebecca_D on 2016-08-11
Have run update successfully. Attached is the wireless info file [ATTACH]270657[/ATTACH].

---

### Post by chili555 on 2016-08-11
> Cell 01 - Address: <MAC 'EE-BrightBox-b7cjek' [AC1]>
                    ESSID:"EE-BrightBox-b7cjek"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:144 Mb/s
                    Extra:wpa_ie=dd1a0050f20101000050f20202000050f2040050f20201000050f202
                    IE: WPA Version 1
                        [COLOR="#FF0000"]Group Cipher : TKIP[/COLOR]
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Extra:rsn_ie=30180100000fac020200000fac04000fac020100000fac020c00
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Quality=48/100  Signal level=100/100  Many, probably most, Linux drivers are troubled by TKIP. I'd change it and a few other things to try to tweak connectivity.

First, check the settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, you may have better connectivity with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz, although it is likely to affect N speeds. I also have better luck with a fixed channel, either 1, 6 or 11, rather than automatic channel selection. Also, be certain the router is not set to use N speeds only; auto B, G and N is preferred. After making these changes, reboot the router. 

Next, I recommend that your regulatory domain be set explicitly. Check yours:

    ```
sudo iw reg get
```

If you get 00, that is a one-size-maybe-fits-all setting. Find yours here: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) Then set it temporarily:

    ```
sudo iw reg set IS
```

Of course, substitute your country code if not Iceland. Set it permanently:

    ```
gksudo gedit /etc/default/crda
```

Use nano or kate or leafpad if you don't have the text editor gedit.

Change the last line to read:

   ```
 REGDOMAIN=IS
```

Proofread carefully, save and close the text editor.

Next, I'd set IPv6 to Ignore in Network Manager: [http://docs.fedoraproject.org/en-US/Fedora/18/html/Installation_Guide/images/netconfig/network-connections-ipv6-ignore.png](http://docs.fedoraproject.org/en-US/Fedora/18/html/Installation_Guide/images/netconfig/network-connections-ipv6-ignore.png)  This example is for ethernet, but you want wireless.

If these changes don't help, please do another wireless_script and we'll dig deeper.

---

### Post by Rebecca_D on 2016-08-11
Thanks for all the info. I will see whether this helps. Watch this space!

---

### Post by Rebecca_D on 2016-08-11
OK.

My router (supplied by broadband provider) only has WPA, WPA2 and WPA/WPA2 Mixed Modes. Set at WPA.
Wireless Mode is set to B+G+N, 20Mhz (there is the option of 20/40Mhz)
I have set the channel to 11.
Regulatory domain set to GB and saved.
IPv6 set to Ignore for wireless.
Rebooted

No change. Still without access to internet via wireless.

Attached latest wireless info file [ATTACH]270662[/ATTACH]

---

### Post by chili555 on 2016-08-11
> wlan0     Scan completed :
          Cell 01 - Address: <MAC 'EE-BrightBox-b7cjek' [AC1]>
                    ESSID:"EE-BrightBox-b7cjek"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:144 Mb/s
                    Extra:wpa_ie=dd1a0050f20101000050f20202000050f2040050f20201000050f202
                    IE: WPA Version 1
                        Group Cipher : [COLOR="#FF0000"]TKIP[/COLOR]
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Extra:rsn_ie=30180100000fac020200000fac04000fac020100000fac020c00
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : [COLOR="#FF0000"]TKIP[/COLOR]
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Quality=48/100  Signal level=100/100  I don't see a single change. Are you sure you attached the latest and not the earliest?> My router (supplied by broadband provider) only has WPA, WPA2 and WPA/WPA2 Mixed Modes. Set at WPA.Please set it to WPA**2**. Also, please detach the ethernet to make all these tests. Afterwards, then re-attach the ethernet only to post the results. Network Manager will default to ethernet if it is available.

---

### Post by Rebecca_D on 2016-08-12
Thanks again. May have sent wrong file as I did not realise the attachment process of this forum and didn't rename second version.

Have changed to WPA2 before test. 

This attachment was created while router was not connected in **any** way [ATTACH]270665[/ATTACH].

---

### Post by wildmanne39 on 2016-08-12
If you run the wireless script more then once it replaces the one you ran before it so you only see the new one.

---

### Post by wildmanne39 on 2016-08-12
If you run the wireless script more then once it replaces the one you ran before it so you only see the new one.

---

### Post by Rebecca_D on 2016-08-12
Thanks Wild Man. The file I have just submitted is the most recent. I have been confused not by the fact that the file is overwritten as you say, but the forum's attachment interface which lists all files that have been uploaded. As the filename can the same each time, selecting the correct one is confusing for the first time user. This is why I have renamed it so that I can select the correct one each time.

---

### Post by wildmanne39 on 2016-08-12
Actually I was posting the part about the script for chili555 because he asked if you posted the latest information and not the earliest. There was a time the script created a file every time it was ran so you had to watch which one you posted but the script was improved so that is not a concern anymore.

---

### Post by jeremy31 on 2016-08-12
And if you installed pastebinit, the script will prompt you if you want to upload the results to pastebin and give you a URL to post

---

### Post by chili555 on 2016-08-12
This is from your latest script:> Cell 03 - Address: <MAC 'EE-BrightBox-b7cjek' [AC3]>
                    ESSID:"EE-BrightBox-b7cjek"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:144 Mb/s
                    Extra:rsn_ie=30180100000fac020200000fac04000fac020100000fac020c00
                    IE: IEEE 802.11i/WPA2 Version 1
                        [COLOR="#FF0000"]Group Cipher : TKIP[/COLOR]
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Quality=48/100  Signal level=100/100  Will you please check again. Most Linux drivers will hardly if ever connect to TKIP. I suggest WPA2-CCMP, sometimes calles AES.

Then reboot the router.

---

### Post by Rebecca_D on 2016-08-12
I have solved the issue but not in the way that you kind people have been trying to.

I received an automated notice from Ubuntu asking whether I wanted to upgrade to 16.04LTS. In researching what changes had been instituted in this new version, I discovered a lot of negative comments. Amongst some of these one person sang the praises of Manjaro, an OS that I have not heard of before. 

Investigating further I downloaded the ISO and launched it on a Live-DVD. Apart from liking what I saw, Manjaro instantly recopgnised and provided a netowrk connection for my ASUS USB-N13. It seems that Canonical is yet again behind the curve.

Sending this to you via my ASU and guess what I'm thinking of doing!!!

---

