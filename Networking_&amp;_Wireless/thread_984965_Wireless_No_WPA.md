---
title: "Wireless No WPA?"
date: 2008-11-17
forum: Networking &amp; Wireless
---

### Post by jay300zx on 2008-11-17
Hi

Pretty new to all this, Got a Toshiba Satellite Pro SP6100 running Ubuntu 8.10

It connects to my wireless AP if I use WEP or no encryption fine.
When I set my AP with WPA/WPA2 My wireless Netowrk Authenticaion Required box only offer me 4 securities, WEP / WEP 128 / LEAP / Dynamic WEP

There is no WPA option - however if I click on the EDIT NETWORK CONNECTIONS It offers me WPA as a security - but when I manually edit this the Authentication box comes up again with just the 4 WEP settings.

---

### Post by meastwood on 2008-11-17
I'm just looking into this now.

first you have to check that your wireless router and wireless card support WPA.

then check that wpa_supplicant supports the network driver you are using [http://hostap.epitest.fi/wpa_supplicant](http://hostap.epitest.fi/wpa_supplicant)

The linux ndiswrapper is supported though I'ld rather buy another card than implement windows code on a linux box!!!

Hardy 8.04.1 comes with wpa_supplicant-0.5.8 which in my case does not support my usbcard's driver 
- to test support
# wpa_supplicant -c <wpa_supplicant.conf file> -i <wireless interface> -D <driver> -d
will report if driver is supported or not.

What I have to do now is download the wpa_supplicant source and recompile support for my driver into it. Then install.

if anyone knows how I should go about installing the new binaries wpa_supplicant is I believe part of the base system) without screwing things up I'ld be grateful.  Would overwriting the existing binaries be OK?

---

### Post by jay300zx on 2008-11-17
cheers - any way to show what wifi chipset is in it?

if I run IWConfig it shows a Hermes chipset but not sure if thats WPA compatible.

---

### Post by meastwood on 2008-11-17
according to that website -

Agere Systems Inc. Linux Driver (Hermes-I/Hermes-II chipset) support WPA but not WPA2

wpa_supplicant-0.5.8 also has support for Hermes. Whether that support is compiled in the ubuntu version I do not know. it should be according to the man pages. Open a terminal from your desktop,

$ sudo wpa_supplicant -c</path/to/wpa_supplicant.conf> -i<your wireless interface> -D hermes -d

and see what it comes up with

---

### Post by blog4me on 2008-11-17
Know how to use ubuntu more by building and deploying java programms on

[http://kiranonblog.blogspot.com/](http://kiranonblog.blogspot.com/)

---

### Post by jay300zx on 2008-11-17
done a lspci - CAnt find owt reporting an 802.x

---

### Post by meastwood on 2008-11-17
not quite sure where you're at.

unfortunately I rarely use GUIs, usually do things from the cmd-line.

established that the installed wpa_supplicant (should) support your hermes driver and that the hermes driver supports WPA.

wpa_supplicant needs to be configured to run as it is responsible for the link-layer encryption and clearly runs before any networking services e.g. dhcp etc. can run

try installing the package -  wpagui
and use this to configure wpa_supplicant

---

### Post by meastwood on 2008-11-17
Ok - have got my WPA2 working so this may help if you have had no joy with the wpagui.

know your card, driver etc. works as you can connect using wep.  The driver should support WPA but not WPA2.

your router will have security settings like:
Encryption: WPA pre-shared key                   [others available]
WPA Unicast Cipher Suit: WPA(TKIP)               [others available]
Pre-shared Key Format: Passphrase                [or Hex]
Pre-shared Key: *******                          e.g. your-pass-key

On your laptop - will need to open a terminal and use the cmd-line; not sure how comfortable you are with that. 
If you are not root the you will need to prefix any command with sudo 
1. generate the Passphrase key into hex 
# wpa_passphrase your-essid your-pass-key >> /etc/wpa_supplicant.conf

2. edit /etc/wpa_supplicant.conf
**From** (in italics)
[I]network={
        ssid="My-essid"
        #psk="my-pass-key"
        psk=768620f80a8619a9d88b6867f074d01d3836f3fb11735b917bf3ac6b790895b7
}[/I]

**To** (in italics)
[I]ctrl_interface=/var/run/wpa_supplicant
network={
   ssid="My-essid"
   key_mgmt=WPA-PSK
   proto=WPA
   psk=768620f80a8619a9d88b6867f074d01d3836f3fb11735b917bf3ac6b790895b7
}[/I]

3. edit /etc/network/interfaces

[I]# rt73 wireless network device using DHCP
iface rausb0 inet dhcp
        wpa-driver ralink
        wpa-conf /etc/wpa_supplicant.conf
auto rausb0[/I]

*** you will need to change **rausb0** to reflect the interface your wireless card/usb is on e.g. wlan0 or whatever
*** you will need to change **ralink** to reflect the cards driver
*** if you are using the linux **wext** driver you do not need the wpa-driver line.

4. bring the interface down if it is up
# ifdown rausb0                 (change rausb0 to your interface)

5. bring the interface up
# ifup rausb0                   (change rausb0 to your interface)
with any luck it may work.

# iwlist rausb0 auth            (change rausb0 to your interface)
rausb0    Authentication capabilities :
                WPA
                WPA2
                CIPHER-TKIP
                CIPHER-CCMP
          ................................
          Current TKIP countermeasures : yes
          Current Drop unencrypted : yes
          Current Authentication algorithm :
                open                          (used by WPA)
                shared-key
                LEAP
          ................................ 

If problems a good place to start is
# ifup --verbose rausb0         (change rausb0 to your interface)

Read the docs in /usr/src/doc/wpasupplicant/
The above is for Managed mode, the docs mentioned above cover a lot more.

---

### Post by wozalawena on 2008-11-18
I have the same problem and am using a toshiba satellite 6100 also.  Please post the solution if you figure it out.  I wonder if wpa_supplicant would help?

---

### Post by syscrusher on 2008-11-18
I can replicate this problem in recent versions of network manager under both 8.04 and 8.10, multiple laptops with different wifi chipsets. Thinkpad R51 with Intel 2200BG (Calexico2), Thinkpad R50p also with Intel 2200BG, and HP 2133 mini-notebook with Broadcom BCM5788. The HP is running an ndiswrapper driver rather than the native one.

In every case, things seem to work fine with WEP but not with WPA. Interestingly, two different laptops, I saw the situation where older versions of Ubuntu *did* work with WPA, but upgrading to the latest Ubuntu broke this.

It's kind of unusual to see hardware compatibility go backwards in Linux. Anyone know what happened here? This problem seems to be experienced by many people, because there are posts about it all over the net.

Kind regards,

Scott

---

