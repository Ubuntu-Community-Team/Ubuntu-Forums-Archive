---
title: "Ubuntu 14.04 with Realtek RTL8101E: wifi connects but does not work"
date: 2015-05-23
forum: Networking &amp; Wireless
---

### Post by sdpete on 2015-05-23
Hi,
I recently upgraded from Ubuntu 12.04 to 14.04 (running the bio-linux environment), and can't get the internet to work.  I am on a HP Pavilion g6-1b59wm, that has a Realtek RTL8101E/RTL8102E Ethernet controller and a Ralink RT5390 network controller (that I think is working okay as I can connect to wireless).  
I can connect to both wireless and Ethernet cables, but have no internet connection.  
I ran the diagnostic in the sticky above and am attaching the results. (by downloading it onto another computer and transferring to the problem machine).
Any help is greatly appreciated!
Thanks much,
Peter

---

### Post by chili555 on 2015-05-23
Is this your router; the one to which you intend to connect?> [  462.025572] wlan0: send auth to <MAC '[COLOR="#FF0000"]xfinitywifi[/COLOR]' [AC10]> (try 1/3)
[  462.081233] wlan0: send auth to <MAC 'xfinitywifi' [AC10]> (try 2/3)
[  462.084756] wlan0: authenticated
[  462.088900] wlan0: associate with <MAC 'xfinitywifi' [AC10]> (try 1/3)
[  462.186552] wlan0: associate with <MAC 'xfinitywifi' [AC10]> (try 2/3)
[  462.200374] wlan0: RX AssocResp from <MAC 'xfinitywifi' [AC10]> (capab=0x421 status=0 aid=1)
[  462.200552] wlan0: associated
[  462.426379] wlan0: deauthenticating from <MAC 'xfinitywifi' [AC10]> by local choice (reason=3)Or is this?> [ 1198.368991] wlan0: authenticate with <MAC 'Belkin_G_Wireless_BC35FF' [AC1]>
[ 1198.376692] wlan0: send auth to <MAC '[COLOR="#FF0000"]Belkin_G_Wireless_BC35FF[/COLOR]' [AC1]> (try 1/3)
[ 1198.378524] wlan0: authenticated
[ 1198.379846] wlan0: AP has invalid WMM params (AIFSN=1 for ACI 2), disabling WMM
[ 1198.383646] wlan0: associate with <MAC 'Belkin_G_Wireless_BC35FF' [AC1]> (try 1/3)
[ 1198.424929] wlan0: RX AssocResp from <MAC 'Belkin_G_Wireless_BC35FF' [AC1]> (capab=0x421 status=0 aid=13)
[ 1198.425432] wlan0: associatedNeither seems to have any encryption. They should be very easy to connect to and even easier to hack.

---

### Post by sdpete on 2015-05-23
Hi Chili555,
Thanks for your reply. Yes, that is my current home router in which I am trying to connect.  As I did my update on my school WAP2 (which is generally not very linux compatible), I was trying to get the internet on the least secure (=hopefully easiest) connection I could make at home (which is not the norm). 
For what it is worth - I have attempted to re-install the most recent driver from Realtek and think* I have searched pretty hard for solutions across the web.
Thanks again for your suggestions.  Any additional help is much appreciated.
-Peter

---

### Post by chili555 on 2015-05-24
I gave you the choice of* two *networks that I guessed might be yours and you said:> Yes, that is my current home routerNext, you say:>  As I did my update on my school WAP2 (which is generally not very linux compatible)I assume you mean WPA2. I don't think it is in the least not Linux compatible. I recommend it exclusively and use it myself. All of the wireless devices I have had and used, currently three, connect and operate smoothly to WPA2. If, however, you intended to say that the encryption method TKIP is not very Linux compatible, I'd agree completely. I recommend that you change the settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, you may have better connectivity with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz, although it is likely to affect N speeds. I also have better luck with a fixed channel, either 1, 6 or 11, rather than automatic channel selection. Also, be certain the router is not set to use N speeds only; auto B, G and N is preferred. After making these changes, reboot the router. 

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

Now, how does the wireless work?

Next, I'd set IPv6 to Ignore in Network Manager: [http://docs.fedoraproject.org/en-US/Fedora/18/html/Installation_Guide/images/netconfig/network-connections-ipv6-ignore.png](http://docs.fedoraproject.org/en-US/Fedora/18/html/Installation_Guide/images/netconfig/network-connections-ipv6-ignore.png)  This example is for ethernet, but you want wireless.

---

### Post by sdpete on 2015-05-24
Hi Chili555,
Thanks again for the reply.  Sorry about the router confusion - I am using the Belkin router and didn't realize there was a xfinity router in my area (which is also my service provider).  I have re-set the Belikin router to be my default.  I am connecting fine to the internet via my router (and also Ethernet cable), but when I open web browser I get a "server not found" error. Similarly, when I try to access a different computer via ssh I get "could not resolve hostname xxx.edu: Name or service not known" error.
Yes, you are correct in that don't have issues with my university's WPA2 specifically, but the other network security in place (which is currently only set to work for windows, mac, iOS, and android).  
Thanks for the router advice - I am running a pretty old router and don't have access to make the changes you suggested (that I am aware of). As I can currently connect to the router and also connect via Ethernet cable and get the same errors, i don't think this is a router issue and hope I am okay not making the suggested changes there.
I checked my regulatory domain as you suggested and get:


sudo iw reg get
 
country US:
    (2402 - 2472 @ 40), (3, 27)
    (5170 - 5250 @ 40), (3, 17)
    (5250 - 5330 @ 40), (3, 20), DFS
    (5490 - 5600 @ 40), (3, 20), DFS
    (5650 - 5710 @ 40), (3, 20), DFS
    (5735 - 5835 @ 40), (3, 30)
    (57240 - 63720 @ 2160), (N/A, 40)
    
I then set my regulatory domain permanently as you suggested: REGDOMAIN=US


lastly, I set IPv6 to Ignore in the Network Manager.


I still connect to the internet okay, but am getting the same "server not found error".


Thanks again for your time.  Any additional suggestions?
-Peter

---

### Post by chili555 on 2015-05-24
> the other network security in place (which is currently only set to work for windows, mac, iOS, and android). I assume you are suggesting there is a router you've tried to connect to but can't as it's set to work for windows, mac, iOS, and android only. Is that what you are saying? I have never heard of such a thing and, in my position, I've heard of a lot! I have personally connected to networks all over the world and never been blocked or unable to do so because of the operating system i use. I hope I am mistaken.>  I am running a pretty old router and don't have access to make the changes you suggested (that I am aware of). But yet you:> I was trying to get the internet on the least secure (=hopefully easiest) connection I could make at home (which is not the norm). So didn't you turn off encryption? How did you do so without access to the router's administration pages?> could not resolve hostname xxx.edu: Name or service not known" error.That suggests a DNS error.Let's try to see where things are going wrong.```
ping -c3 192.168.2.1
ping -c3 8.8.8.8
ping -c3 91.189.89.118
ping -c3 www.ubuntu.com
```Next, unplug the router for about 15 seconds, plug it back in, wait for it to get a new IP address from your ISP and try these commands again.>  i don't think this is a router issueSince it happens with both wired and wireless and all the symptoms point to DNS and since you get DNS information from the router, at this point, I think it *IS* a router-related issue.```
IPv4 Settings:
    Address:         192.168.2.18
    Prefix:          24 (255.255.255.0)
    [COLOR="#FF0000"]Gateway:         192.168.2.1
[/COLOR]
    [COLOR="#FF0000"]DNS:             192.168.2.1[/COLOR]
```

---

