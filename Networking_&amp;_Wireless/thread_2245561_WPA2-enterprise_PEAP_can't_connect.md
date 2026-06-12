---
title: "WPA2-enterprise PEAP can't connect"
date: 2014-09-24
forum: Networking &amp; Wireless
---

### Post by joe138 on 2014-09-24
So.

I have an HP dv4t-5100 laptop with a Ralink RT5390 wireless card. It works wonderfully when I'm in Windows connecting to most everything.  However, in Ubuntu (14.04 LTS), I can't connect to my school's WPA2-enterprise wireless. I can connect to home wireless and whatnot, but at school, it prompts me for my username and password, thinks for a minute, and then promts me for my username and password. Rinse, repeat. I've seen a buncha posts on this general problem, but none recent, and none with solutions that work.

So here I am.  I'm pretty new to Ubuntu and whatnot, so let me know what further information from command outputs and stuff could be useful, and I'll happily post. 

Thanks!

---

### Post by varunendra on 2014-09-25
Welcome to the forums joe138,

Please download the wireless_script mentioned here : [http://ubuntuforums.org/showpost.php?p=13024222](http://ubuntuforums.org/showpost.php?p=13024222) . Copy it to your Desktop.

When you are in school, try to connect to its network, let it fail. Then open a terminal (Ctrl-Alt-T) and run this script with the following commands -
```
cd Desktop
chmod +x wireless_script
bash wireless_script
```
..assuming the name of the downloaded script remains "wireless_script". Some browsers may automatically append ".txt" to its name. If that happens, please use that name in the commands above.

Supply your login password when asked by the script. It will generate a file named "wireless-info.txt" or "wireless-info.tar.gz" on the desktop containing all the important info about your wireless setup required for troubleshooting. Please attach this file in your next post here so we can see the problem and try to troubleshoot it.

---

### Post by joe138 on 2014-09-25
Thanks for the reply.

I did a method 2 in the link you sent me (downloaded and copied on a USB) but I figure it should be the same deal.  

Anyways,  I ran it while the network was trying to connect after 3 password  re-prompts. hopefully this is adequate. Additionally, I noticed that the  network details list a CA certificate being used, but I know the school  doesn't require one. I think. Not sure off the bat how to remove that,  but I've tried ten thousand times to connect with and without CA  certificates, and it doesn't work either way. Anyways, I tried to post it as one attachment, but it wouldn't let me. So I split it into two files. 

Thanks again =)

---

### Post by varunendra on 2014-09-25
> **joe138 said:**
> ....I noticed that the  network details list a CA certificate being used, but I know the school  doesn't require one...

Simply delete that line with -
```
sudo sed -i '/ca-cert/ d' "/etc/NetworkManager/system-connections/WSU Wireless"
```
Disconnect --> Reconnect and see if it lets you. If not, please post the entire contents of the file with user ID and password removed/obscured. You'll need root privilege to read it, so this will do -
```
sudo cat "/etc/NetworkManager/system-connections/WSU Wireless"
```

I believe the "ca-cert" line should be the only thing preventing you from connecting.

You can also try to delete the currently saved profile(s) and let a new one be generated automatically when you try to connect to it again with the settings as shown in the following image -

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=256691&stc=1&d=1411681849[/IMG]

---

### Post by joe138 on 2014-09-25
Hey,

I tried both things you suggested above (first removing the line and then deleting the profile and remaking with exactly the settings you show). Still no dice, exatly the same problem, except now it warns me after each password prompt that I am not entering a CA certificate. 

Here are the contents of the file (after deleting and remaking the profile, and trying to connect again, and failing.)

> [ipv6]
method=auto

[connection]
id=WSU Wireless
uuid=e2b36326-3c62-4179-8790-2566674ca348
type=802-11-wireless

[802-11-wireless-security]
key-mgmt=wpa-eap
auth-alg=open

[802-11-wireless]
ssid=WSU Wireless
mode=infrastructure
mac-address=84:4B:F5:4D:01:66
security=802-11-wireless-security

[802-1x]
eap=peap;
identity=*USERNAME*
phase2-auth=mschapv2
password-flags=1

[ipv4]
method=auto



---

### Post by varunendra on 2014-09-25
Something I ignored previously in the report -
```
[   91.907523] wlan0: associate with <**[COLOR="#FF0000"]MAC C-07 WSU Wireless[/COLOR]**> (try 1/3)
[   91.910151] wlan0: RX AssocResp from <MAC C-07 WSU Wireless> (capab=0x431 status=0 aid=4)
[   91.910253] wlan0: associated
[  102.120114] wlan0: **deauthenticating from <MAC C-07 WSU Wireless> by local choice (reason=3)**
[  120.191973] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  129.277794] wlan0: **authenticate with <[COLOR="#FF0000"]MAC C-04 WSU Wireless[/COLOR]>**
[  129.293115] wlan0: direct probe to <MAC C-04 WSU Wireless> (try 1/3)
[  129.496606] wlan0: direct probe to <MAC C-04 WSU Wireless> (try 2/3)
[  129.700693] wlan0: send auth to <MAC C-04 WSU Wireless> (try 3/3)
[  129.701786] wlan0: authenticated
....
```
..so it seems NM is hopping between two APs of the same SSID and almost same signal strength (both are weak by the way). This could be due to the weak signal, or due to an old bug in NM. As a test, please try binding NM with any one of these APs whose signal strength appears to be relatively stronger.

The output of-
```
sudo iwlist scan
```
..will show you both the MAC addresses of the detected APs, and their signal strength. Pick the one with stronger signal and save its MAC address in the "BSSID" field of Network Manager. Save and close it, and try to reconnect. If it fails again, please generate a fresh report and post it back here.

---

### Post by joe138 on 2014-09-26
you are a genius. It connects now =).  Do you think there is a fix for making NM not jump ship to a different AP halfway through connecting? Or what "by local choice (reason 3)"  means? This is definitely progress, but tethering the wireless to one AP means that if I move to a different place on campus, I'll need to re-find the MAC addresses and specify which one to connect to. Not the end of the world, and heads and shoulders better than not connecting at all, but if there's a more direct fix for the NM it could be a little more convenient.

Thanks again!

That is all.

---

### Post by varunendra on 2014-09-26
> **joe138 said:**
> Do you think there is a fix for making NM not jump ship to a different AP halfway through connecting?
If there were some smart and automatic way to make NM handle this more smartly, I think it would have been committed in the upstream code by now. So no, at least I'm not aware of such a smart way to do this that can handle the situation automatically.

Also, I personally have absolutely zero experience with WPA-Enterprise networks. But based on a recent experiment with the WPA-Personal network of my office, I think you can do something like this -

[LIST=1]
[*]Manually create multiple profiles for the same SSID, but with different profile names (for example, "AP-Class", "AP-Library", "AP-Lab",....etc.).
[*]Save different BSSIDs in these profiles that are most suitable for the corresponding places.
[*]Once the above is done, when you will pull down the Network Manager's available connection list, you will only see the SSIDs of the corresponding APs. But when you hover the pointer over the SSID of your school, it should slide open a sub-menu showing all the different profile names to let you choose one to connect to it.
[*]Clicking on any of these profile names will use that profile to connect to the network. Since each profile is bounded to its corresponding AP, it will only connect to that one.
[/LIST]

I tested this on my office network with two profiles a few days ago and it worked as expected. But the difference in my test profiles was the "Method" to connect - one was using DHCP, other a manual configuration. But I hope it shouldn't matter what the difference in the profiles is, and it should work the same way for you too. If it does, I think it can't be done in any better way.

If not, I'm afraid you are stuck with manually saving BSSIDs everytime you move. Although I can help you to create a script to do that easily. For example, we can set the script so that you only have to type "ap lab" in the terminal to replace the existing BSSID of the saved profile with the BSSID of your lab's preferred AP.

> Or what "by local choice (reason 3)"  means?
I like curiosity. :p

Here's a nice list of reason codes : [http://www.aboutcher.co.uk/2012/07/linux-wifi-deauthenticated-reason-codes/](http://www.aboutcher.co.uk/2012/07/linux-wifi-deauthenticated-reason-codes/)

---

