---
title: "Rt61 revisited this seems to work for me"
date: 2006-12-03
forum: Networking &amp; Wireless
---

### Post by snorkelman on 2006-12-03
hi there new to this I doubt it'll help most folks out with Rt61 probs but hopefully it'll help someone out who finds themselves in same position as I did (with the RT61 *almost* working straight out of the box).

I installed current Ubuntu 6.10 and found that my wifi card (a generic RT61 chipset PCI card) was actually detected 

Two entries for it were available under **System/Administration/Network Settings** (**wlanmaster0** and **wlan0**)

Only trouble was enabling those, setting them to DHCP and assigning their ESSID didnt seem to help drag a wifi connection into life.. but the soultion was pretty straightforward..

i ran **$ iwconfig wlan0 ** which listed the card as follows 

[I]wlan0     IEEE 802.11g  ESSID:"[COLOR="Red"]belkin54g[/COLOR]"  
          Mode:Managed  Frequency:[COLOR="Red"]2.412[/COLOR] GHz  Access Point: [COLOR="Red"]Not-Associated[/COLOR]   
          RTS thr:off   Fragment thr=2346 B   
          Encryption key:off[/I]


I then ran **$ iwlist wlan0 scan**

[I]wlan0     Scan completed :
          Cell 01 - Address: [COLOR="Red"]00:12:AA:04:C2:99[/COLOR]
                    ESSID:"[COLOR="Red"]belkin54g[/COLOR]"
                    Mode:Master
                    Frequency:[COLOR="Red"]2.462[/COLOR] GHz
                    Encryption key:off
                    Extra:tsf=0000004895f14541
[/I]

That showed that the frequency of the card wasn't matching that of the AP
(2.412GHz versus the 2.462GHz of the AP) and gave me the address I needed for the AP at the same time 

so it was then just a case of taking those bits of info above and executing following commands with those as the parameters (obviously you need to substitute the red details in following with the ones that match your requirements) :
 
[B]$ iwconfig wlan0 essid -- "[COLOR="Red"]belkin54g[/COLOR]"  
$ iwconfig wlan0 freq [COLOR="Red"]2.462[/COLOR]G
$ iwconfig wlan0 ap [COLOR="Red"]00:12:AA:04:C2:99[/COLOR]
$ dhclient wlan0
[/B]

with a running connection now confirmed it was then just a case of writing a script to automate the four commands, making the script executable and creating a symbolic link for it to run it at boot up. Sorted!

stevie

---

### Post by mickfromperth on 2006-12-03
Hi Stevie.

I'm going though the hoops learning about wireless.  I have this card (well, I have a dlink card that has this chipset).

I was unable to get it working (I only spent 10 minutes on it before moving on to try my usb adapter, as the arial on this card is lost and therefore signal sucks all the time).

Anyways.. some advice..

/etc/network/interfaces is a config file where you can store these settings.

man interfaces offers advice on format of the file.  However, for wireless extensions I'm not sure where the best data is; but I got my card working last night automagically by putting the settings there.

Mick

---

### Post by snorkelman on 2006-12-05
Cheers Mick I gave it a whirl.. 

Oddly enough though the *exact* same wireless settings specified in /etc/network/interfaces rather than via my script leave the card without a lease 

Its not that they haven't been set - iwconfig shows that the settings *have* been applied (with same values setting them via my script would) is just I end up with no connection on log in and DHCLIENT point blank refuses to get a lease 

I eventually gave up and took the path of least resistance - took the freq and ap wireless- entries back out of etc/network/interfaces and reverted back to using the script to set those :)

stevie

---

