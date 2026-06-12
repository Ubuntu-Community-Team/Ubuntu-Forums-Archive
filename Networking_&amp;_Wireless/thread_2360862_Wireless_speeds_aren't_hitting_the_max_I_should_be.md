---
title: "Wireless speeds aren't hitting the max I should be getting"
date: 2017-05-09
forum: Networking &amp; Wireless
---

### Post by sandeepsb1 on 2017-05-09
Hi

I've installed Ubuntu Gnome 17.04 and it had detected my wireless card out of the box, the card in question is 

Network controller: Broadcom Limited BCM43602 802.11ac Wireless LAN SoC (rev 01)

The issue I'm facing is that my wireless speeds can go up to 220 Mbps but I'm only getting around 60 Mpbs with the card - is there anything that I need to do to fix this?

I've attached my "wireless-info" data to the post, is there anyone that can assist me?

Thanks
Sandeep

---

### Post by chili555 on 2017-05-09
> SSID                  BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY   ACTIVE  * 
Hogwarts              <MAC 'Hogwarts' [AN1]>  Infra  11    2462 MHz  54 Mbit/s  100     &#9602;&#9604;&#9606;&#9608;  WPA2       no        
--                    <MAC '--' [AN2]>  Infra  11    2462 MHz  54 Mbit/s  100     &#9602;&#9604;&#9606;&#9608;  WPA2       no        
Hogwarts              <MAC 'Hogwarts' [AN3]>  Infra  1     2412 MHz  54 Mbit/s  92      &#9602;&#9604;&#9606;&#9608;  WPA2       no        
--                    <MAC '--' [AN4]>  Infra  1     2412 MHz  54 Mbit/s  92      &#9602;&#9604;&#9606;&#9608;  WPA2       no        
--                    <MAC '--' [AN5]>  Infra  36    5180 MHz  54 Mbit/s  82      &#9602;&#9604;&#9606;&#9608;  WPA2       no        
--                    <MAC '--' [AN6]>  Infra  36    5180 MHz  54 Mbit/s  82      &#9602;&#9604;&#9606;&#9608;  WPA2       no        
--                    <MAC '--' [AN7]>  Infra  6     2437 MHz  54 Mbit/s  80      &#9602;&#9604;&#9606;_  WPA2       no        
Hogwarts              <MAC 'Hogwarts' [AN8]>  Infra  6     2437 MHz  54 Mbit/s  80      &#9602;&#9604;&#9606;_  WPA2       no        
--                    <MAC '--' [AN9]>  Infra  36    5180 MHz  54 Mbit/s  75      &#9602;&#9604;&#9606;_  WPA2       no        
--                    <MAC '--' [AN10]>  Infra  36    5180 MHz  54 Mbit/s  75      &#9602;&#9604;&#9606;_  WPA2       no        
Hogwarts              <MAC 'Hogwarts' [AN11]>  Infra  36    5180 MHz  54 Mbit/s  75      &#9602;&#9604;&#9606;_  WPA2       no        
[COLOR="#FF0000"]Hogwarts              <MAC 'Hogwarts' [AN12]>  Infra  36    5180 MHz  54 Mbit/s  67      &#9602;&#9604;&#9606;_  WPA2       yes     * [/COLOR]
House Network UK 2.4  <MAC 'House Network UK 2.4' [AN13]>  Infra  11    2462 MHz  54 Mbit/s  59      &#9602;&#9604;&#9606;_  WPA1 WPA2  no        
--                    <MAC '--' [AN14]>  Infra  36    5180 MHz  54 Mbit/s  55      &#9602;&#9604;__  WPA2       no        
Hogwarts              <MAC 'Hogwarts' [AN15]>  Infra  36    5180 MHz  54 Mbit/s  55      &#9602;&#9604;__  WPA2       no        
--                    <MAC '--' [AN16]>  Infra  36    5180 MHz  54 Mbit/s  55      &#9602;&#9604;__  WPA2       no        
House Network UK 5.8  <MAC 'House Network UK 5.8' [AN17]>  Infra  44    5220 MHz  54 Mbit/s  40      &#9602;&#9604;__  WPA2       no        
TALKTALK3CD132        <MAC 'TALKTALK3CD132' [AN18]>  Infra  3     2422 MHz  54 Mbit/s  39      &#9602;&#9604;__  WPA1 WPA2  no        
VM371006-2G           <MAC 'VM371006-2G' [AN19]>  Infra  11    2462 MHz  54 Mbit/s  37      &#9602;&#9604;__  WPA1 WPA2  no        
The asterisk indicates the ESSID to which you are connected. As you can see, you are connected to 'Hogwarts' with a signal strength of 67 (on a scale of 100), although there is a Hogwarts nearby with a signal strength of 100! 

As you know, as signal strength declines, so does connection speed. That suggests that the solution may be to force Network Manager to connect to the 100 Hogwarts and not the 67 Hogwarts. Here is how you can do that: [https://askubuntu.com/questions/425583/ubuntu-connect-drops-worked-for-a-while-then-started-dropping-again/425617#425617](https://askubuntu.com/questions/425583/ubuntu-connect-drops-worked-for-a-while-then-started-dropping-again/425617#425617)

You shouldn't specify the 'wlan0' interface as in the link. It is quite sufficient to do:```
sudo iwlist scan
```

---

### Post by sandeepsb1 on 2017-05-09
Hi

Thanks for the detailed info, I had tried changing my BSSID to the value of the 100% "point".
I'm still getting issues - I believe it's just the distance from my Wireless adapter and the nearest access point.

Thanks
Sandeep

---

### Post by chili555 on 2017-05-09
Have you confirmed that you are, indeed, connected to the strongest Hogwarts?```
sudo nmcli dev wifi list
```

---

### Post by sandeepsb1 on 2017-05-09
So I did include the Address of the point that was 100% but when running


```
sudo nmcli dev wifi list
```

An asterisk is next to a point that is at 80% - I have even tried turning wifi on and off and rebooting.

EDIT: I had figured out the correct address, it's giving me around 90% signal strength now, it's doubled my speeds to around 120 Mbps, not the 200Mbps that I want but it's pretty decent considering it's up 2 flights of stairs.

For a bit of context I have the Amplifi HD Mesh Network, so the Cube router is at the ground level then one mesh access point is on the next floor and another on the floor above (which I'm connected to).

---

### Post by chili555 on 2017-05-09
What do other nearby wireless devices get? No matter that your wireless card is capable of stupendous speeds; what is the service provider capable of? 

At the 80% signal strength instance of Hogwarts, what result do you get here with all other internet activities, browser tabs, etc., closed? [http://www.dslreports.com/speedtest](http://www.dslreports.com/speedtest)

Please try an experiment. Run the test above and note the result. Then, from the terminal:```
sudo -i
echo "options cfg80211 cfg80211_disable_40mhz_24ghz=Y"  >  /etc/modprobe.d/cfg80211.conf
exit
```Reboot and try the test again. Better or worse?

---

### Post by sandeepsb1 on 2017-05-09
If I stand next to the router I would get 22 Mb/s, my ISP (Virgin Media) provides ~200 Mbps Fiber broadband.

As for the speed test:

- Before modifying the file
[http://www.dslreports.com/speedtest/15022350](http://www.dslreports.com/speedtest/15022350)

- After the modification
[http://www.dslreports.com/speedtest/15022552](http://www.dslreports.com/speedtest/15022552)

---

### Post by chili555 on 2017-05-09
> If I stand next to the router I would get 22 Mb/s,Not 94 Mbps? That's what your speedtest says. Were you standing right next to the router?

Is this your router, over which you have administrative privileges? If so, please check the settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, you may have better connectivity with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz, although it is likely to affect N speeds. I also have better luck with a fixed channel, either 1, 6 or 11, rather than automatic channel selection. Also, be certain the router is not set to use N speeds only; auto B, G and N is preferred. After making these changes, reboot the router. 

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

The tests with and without the cfg80211 parameter are identical; it seems to make no difference with or without it.

---

### Post by sandeepsb1 on 2017-05-09
> **chili555 said:**
> Not 94 Mbps? That's what your speedtest says. Were you standing right next to the router?

Well 94Mbps (9.4 Mb/s) is what I go from my Ubuntu machine, if I'm next to the router then I get 220Mbps (22 Mb/s)


> **chili555 said:**
> 
Is this your router, over which you have administrative privileges? If so, please check the settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, you may have better connectivity with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz, although it is likely to affect N speeds. I also have better luck with a fixed channel, either 1, 6 or 11, rather than automatic channel selection. Also, be certain the router is not set to use N speeds only; auto B, G and N is preferred. After making these changes, reboot the router. 


My router is a Dual Band Wireless AC Router.

- Network key is already set to WPA2-PSK
- 2.4Ghz Channel is set to 6 (Automatic)
- 5Ghz Channel is set to 36 (Automatic)
- 2.4 Ghz channel width is already set to 20Mhz not 20/40Mhz
- 5Ghz width is set to 80Mhz

> **chili555 said:**
> 
Then set your regulatory domain explicitly. Check yours:```
sudo iw reg get
```If you get 00, that is a one-size-maybe-fits-all setting. 


Output is

```

global
country GB: DFS-ETSI
    (2402 - 2482 @ 40), (N/A, 20), (N/A)
    (5170 - 5250 @ 80), (N/A, 20), (N/A), AUTO-BW
    (5250 - 5330 @ 80), (N/A, 20), (0 ms), DFS, AUTO-BW
    (5490 - 5710 @ 160), (N/A, 27), (0 ms), DFS
    (57000 - 66000 @ 2160), (N/A, 40), (N/A)

```

> **chili555 said:**
> 
Next, I'd set IPv6 to Ignore in Network Manager: [http://docs.fedoraproject.org/en-US/Fedora/18/html/Installation_Guide/images/netconfig/network-connections-ipv6-ignore.png](http://docs.fedoraproject.org/en-US/Fedora/18/html/Installation_Guide/images/netconfig/network-connections-ipv6-ignore.png)  This example is for ethernet, but you want wireless.


Set

My DSL Report Speed test after any changes

[http://www.dslreports.com/speedtest/15024332](http://www.dslreports.com/speedtest/15024332)

---

### Post by chili555 on 2017-05-09
> Well 94Mbps (9.4 Mb/s)One of us is not understanding something here. Your speedtest clearly says 94 Mbps which is the exact same as 94 Mb/s. The p in Mbps stands for 'per'; another way to say 'per' is /. 

> it's doubled my speeds to around 120 Mbps, not the 200Mbps that I want but it's pretty decent considering it's up 2 flights of stairs.I agree.

Frankly, I'd say you are all set.

---

### Post by sandeepsb1 on 2017-05-09
> **chili555 said:**
> One of us is not understanding something here. Your speedtest clearly says 94 Mbps which is the exact same as 94 Mb/s. The p in Mbps stands for 'per'; another way to say 'per' is /. 

Yeah you're right, was a bit confused.


> **chili555 said:**
> 
I agree.

Frankly, I'd say you are all set.

Yep it all looks good! Thanks a lot for your guidance and an insight to the tools that linux has available.

---

