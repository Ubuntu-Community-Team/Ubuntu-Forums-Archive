---
title: "Wireless WPA enterprise on broadcom chipset not connecting"
date: 2008-09-26
forum: Networking &amp; Wireless
---

### Post by skroops on 2008-09-26
Wireless works fine at home, on unsecured and on WEP.

When I'm at school, they are running WPA Enterprise.  Of course the school doesn't officially support linux, but they've directed me to the following page: [http://8help.osu.edu/2672.html](http://8help.osu.edu/2672.html)

... which indicates that I need to use these settings:

[LIST]
[*]**Encryption:** WPA Radius with TKIP key exchange
[*]**Authentication:** 802.1x with PEAP and MSCHAPv2
[*]**SSID:** osuwireless
[/LIST]
I've configured it that way with network-manager, but it just tries to connect forever.  It hangs for a while on "Attempting to join..." and if it makes it past that point, it says something about "Retrieving key" (in the tooltip) or some such message .

If I go into "Edit wireless networks", and select it, this is what I have:

Security: WPA Enterprise
EAP Method: PEAP
Key Type: TKIP
Phase2 Type:  MSCHAPV2
Identity: <identity>
Password: <password>
Everything else is blank

One strange behavior is that when I try to configure from the pop-up dialog or from "Connect to other wireless", whatever I set the password to is also automatically set to the Private Key Password field.  I have tried resetting this to null as well as leaving as my password, with no change.

I have also tried setting the Anonymous Identity field to my login name.

I have looked at a few tutorials and they all seem to deal with wpa_supplicant.conf, or /etc/network/interfaces,  which aren't used by nm-applet, atleast not as far as I can tell.  nm-applet is getting is storing its config in a gconf xml in the home directory "~/.gconf/system/networking/wireless/networks/osuwireless/%gconf.xml".

[COLOR=Silver]*I'd like to paste the contents of the file but I can't (right now).*[/COLOR]
edit: here it is
```
<?xml version="1.0"?>
<gconf>
        <entry name="wpa_eap_anon_identity" mtime="1222443719" type="string">
                <stringvalue></stringvalue>
        </entry>
        <entry name="leap_key_mgmt" mtime="1222358138" type="string">
                <stringvalue>WPA-EAP</stringvalue>
        </entry>
        <entry name="leap_username" mtime="1222358131" type="string">
                <stringvalue>v*****c.1w</stringvalue>
        </entry>
        <entry name="wpa_psk_key_mgt" mtime="1222358115" type="int" value="4">
        </entry>
        <entry name="wpa_psk_wpa_version" mtime="1222358082" type="int" value="2">
        </entry>
        <entry name="wpa_eap_have_private_key_passwd" mtime="1222441557" type="bool" value="false">
        </entry>
        <entry name="wpa_eap_have_passwd" mtime="1222441557" type="bool" value="true">
        </entry>
        <entry name="wpa_eap_identity" mtime="1222441627" type="string">
                <stringvalue>v*****c.1w</stringvalue>
        </entry>
        <entry name="wpa_eap_key_mgt" mtime="1222441627" type="int" value="1">
        </entry>
        <entry name="wpa_eap_wpa_version" mtime="1222441627" type="int" value="2">
        </entry>
        <entry name="wpa_eap_phase2_type" mtime="1222441627" type="int" value="196608">
        </entry>
        <entry name="wpa_eap_key_type" mtime="1222441627" type="int" value="4">
        </entry>
        <entry name="wpa_eap_eap_method" mtime="1222441627" type="int" value="16">
        </entry>
        <entry name="we_cipher" mtime="1222441627" type="int" value="32">
        </entry>
        <entry name="bssids" mtime="1222440762" type="list" ltype="string">
                <li type="string">
                        <stringvalue>00:0B:86:91:42:E0</stringvalue>
                </li>
                <li type="string">
                        <stringvalue>00:0B:86:96:83:20</stringvalue>
                </li>
                <li type="string">
                        <stringvalue>00:0B:86:94:89:60</stringvalue>
                </li>
                <li type="string">
                        <stringvalue>00:0B:86:94:8C:20</stringvalue>
                </li>
                <li type="string">
                        <stringvalue>00:1A:1E:AE:FC:40</stringvalue>
                </li>
                <li type="string">
                        <stringvalue>00:0B:86:91:41:00</stringvalue>
                </li>
                <li type="string">
                        <stringvalue>00:0B:86:57:F4:A0</stringvalue>
                </li>
                <li type="string">
                        <stringvalue>00:0B:86:91:2D:00</stringvalue>
                </li>
                <li type="string">
                        <stringvalue>00:0B:86:91:30:00</stringvalue>
                </li>
        </entry>
        <entry name="timestamp" mtime="1222441627" type="int" value="1222441627">
        </entry>
        <entry name="essid" mtime="1222441627" type="string">
                <stringvalue>osuwireless</stringvalue>
        </entry>
</gconf>
```This file has a good chunk of integer based settings as well as some other illegible settings, so I can't really manipulate it much.

I would like to see the output of what nm-applet and wpa-supplicant are doing in the terminal, but I don't know how to do it.  Also I can't find any log file related to nm-applet or wpa-supplicant.  I know wpa_supplicant.log is supposed to be in /var/log, but it's not there (probably because of the way nm handles wpa-supplicant)


I've got a BCM4315.
Please help.

---

### Post by dbsoundman on 2008-09-26
I have a similar problem, also. I'm also trying to use the osuwireless network in Ubuntu 7.04 with network manager 0.6.something. My problem is strange, however: most of the time, when I try to select osuwireless from the list of available networks, it prompts me for a WEP passphrase, and there is no WPA option at all. If I try to do it by "connect to another network", it never works. The only way I've gotten in is by repeatedly selecting the network on the list until it finally comes up with a WPA prompt instead of a WEP-only prompt. Is this related to the OP's problem, or am I opening a new one?

-Dan

---

### Post by skroops on 2008-09-26
Make sure you have the wpa-supplicant package installed

I'm not on 7.04 but try right clicking the networkmanager icon and looking for Edit wireless connections.  You should be able to customize the settings for osuwireless then.

Please write back with the results :)

---

### Post by skroops on 2008-09-30
Today I tried using wpa_gui to determine exactly what was going on.  wpa_gui could not connect with wpa_supplicant or find any network devices on my system. wtf?

Edit:  I guess it's a bug?  Anyway I upgraded to intrepid and it works fine

---

### Post by novicetopro on 2008-10-09
> **skroops said:**
> Today I tried using wpa_gui to determine exactly what was going on.  wpa_gui could not connect with wpa_supplicant or find any network devices on my system. wtf?

Edit:  I guess it's a bug?  Anyway I upgraded to intrepid and it works fine

Hey I am also trying to connect to my school network and it hasn't work with exactly the same results u were getting. Did upgrading to intrepid just solve your problem. So are you now about to connect to WPA enterprise with no problem. Just asking to be sure...I am downloading the beta right now and will install it pending your confirmation. Thanks.

---

### Post by skroops on 2008-10-13
Yes, after installing intrepid, it just worked.  I had to get the settings right, but it worked no problem.\

---

### Post by novicetopro on 2008-10-29
Upgrading to intrepid didn't solve my problem. I still cannot connect to my school's TTLS/PAP WPA Enterprise using network manager. I am trying to just use wpa-supplicant but no luck with that. I have feeling this not going to work anytime soon. I see too many posts like mine, too bad, Ubuntu hasn't been able to deal with this wireless mess. 

Issues like this makes me give Microsoft a lot credit, even though a lot of people attack them and defend ubuntu. I haven't spent even close to the amount of time trying to get trivia things like wireless or getting my laptop to sleep (doesn't even work) to work on my vista partition. I like them both but until those big issues work well...ubuntu will still be a toy os for me.


I have Broadcom 4312.

---

### Post by skroops on 2008-10-29
I don't know, I should have been clear that I didn't upgrade to intrepid, I did a fresh install.  Things like this are really outside my knowledge but perhaps doing an upgrade preserved some settings that are still breaking your WPA?

[_This thread_]("http://ubuntuforums.org/showthread.php?t=870086") deals with getting 4312 to work with WPA using ndiswrapper.  I've never been able to figure out ndiswrapper but I know that it works for some people.

Have you tried the other WPA options? I know one option was something like version that I had to change to make it work, even though my school didn't say so.

Btw, I've marked this thread unsolved again, but you may want to start a new thread.

---

### Post by novicetopro on 2008-10-29
Thanks, I will try again. I may wait to 8.10 is officially released (two days) and do a fresh install. Then see what happens. 

My school has two networks, the other is unsecured but doesn't let you do much (just broswing). You have to log in the browser. I haven't been able to connect to that one the last few days too, it connects in network manager but browsers try to connect for a very long time, it doesn't even to get to say website not found or whatever error it gives you when your not connected. 

Wireless works perfectly with my regular WPA connection in my home network. Just has issues with WPA Enterprise and now unsecure, although the unsecure one is just wierd. 

I will spend some time this wknd looking at it again.

---

