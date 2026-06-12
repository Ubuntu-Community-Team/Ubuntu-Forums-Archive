---
title: "Vpn ubuntu 18.04 only connects once"
date: 2020-07-29
forum: Networking &amp; Wireless
---

### Post by onesixtyfourth on 2020-07-29
Hi everybody I have recently started using my Ubuntu machine for work (yay I am a c# developer and love the fact that I can work in Ubuntu now) I have everything set up except for the vpn I need for some operations. I am able to work 80% without it. I am attempting to connect to an Azure virtual gateway and I have followed [this]("https://docs.microsoft.com/en-us/azure/vpn-gateway/point-to-site-vpn-client-configuration-azure-cert#linuxgui") to get it set up. It does work but only once. I have a url that requires me to go through the vpn for access and when I set it up initially I can connect. If I turn the vpn off and then back on again it does not work and I get a dns error. If I close and then re-open the browser it again works but again only once. closing and re-opening a second time does not work with the dns error.

I am a long time linux user but nowhere near as geeky on it as I used to be so let me know what information you want from me please.

The tunnel type is IKEv2 and SSTP (SSL).

There cannot be much wrong as I do connect just not consistently. Not sure if it makes a difference but I do have the ubuntu-studio packages installed (including the real time kernel I think.)

[edit]
Been looking through var/log/syslog and found this:

```

Jul 30 08:24:24 lg-MS-7A71 charon-nm: 12[NET] sending packet: from 192.168.0.16[60851] to 137.116.207.242[4500] (65 bytes)
Jul 30 08:24:24 lg-MS-7A71 charon-nm: 04[NET] error writing to socket: Invalid argument
Jul 30 08:24:24 lg-MS-7A71 kernel: [ 5778.770849] RTW: ==>rtw_ps_processor .fw_state(8)
Jul 30 08:24:26 lg-MS-7A71 kernel: [ 5780.818875] RTW: ==>rtw_ps_processor .fw_state(8)
Jul 30 08:24:28 lg-MS-7A71 kernel: [ 5782.868938] RTW: ==>rtw_ps_processor .fw_state(8)
Jul 30 08:24:29 lg-MS-7A71 gnome-shell[3978]: Object St.Widget (0x55a552bc9840), has been already deallocated - impossible to access it. This might be caused by the object having been destroyed from C code using something such as destroy(), dispose(), or remove() vfuncs
```


Does this help anyone trouble shoot for me?

[edit]
Have been investigating today but not much furthrt forward. I do connect to my test page occasionally but not consistently. After checking through the instructions above I realised that the gui version of configuring strongswan did not create config properly (which I find confusing as it has connected) so I foolowed the cli version of the instructions. If I run ipsec up dv0_vnet everythign looks ok

  ```
requesting ocsp status from 'http://ocsp.digicert.com' ...
  ocsp response correctly signed by "C=US, O=DigiCert Inc, OU=www.digicert.com, CN=DigiCert Global Root CA"
  ocsp response is valid: until Aug 05 18:28:15 2020
certificate status is good
certificate policy 2.16.840.1.114412.1.1 for 'C=US, ST=Washington, L=Redmond, O=Microsoft Corporation, CN=f18aabe2-417c-4912-b2c8-2909b4ac5d04.vpn.azure.com' not allowed by trustchain, ignored
certificate policy 2.23.140.1.2.2 for 'C=US, ST=Washington, L=Redmond, O=Microsoft Corporation, CN=f18aabe2-417c-4912-b2c8-2909b4ac5d04.vpn.azure.com' not allowed by trustchain, ignored
  reached self-signed root ca with a path length of 1
authentication of 'C=US, ST=Washington, L=Redmond, O=Microsoft Corporation, CN=f18aabe2-417c-4912-b2c8-2909b4ac5d04.vpn.azure.com' with RSA signature successful
```

but when I then turn the vpn on through the network manager I still cannot browse to the page.

---

### Post by onesixtyfourth on 2020-08-04
I have figured this out now. There were a few issues I found so  will detail what I had to do here just in case it is helpful.

Install and configure strongswan (I found [these instructions]("http://wiki.ciscolinux.co.uk/index.php?title=Azure/Point-to-Site_VPN") most useful for this)
Set the mss/mtu values in the charon configuration as in [answer here]("https://serverfault.com/questions/840920/how-connect-a-linux-box-to-an-azure-point-to-site-gateway")
Install and configure [resolvconf]("https://askubuntu.com/questions/1220311/need-to-manually-set-resolve-conf-after-successfull-vpn-install") (Azure sets it own dns servers so this is required or that part fails on connection but not fail the connection)
Set up NetworkManager gui element as [shown here]("https://docs.microsoft.com/en-us/azure/vpn-gateway/point-to-site-vpn-client-configuration-azure-cert#linuxgui")

With this I am able to select the network manager and turn the vpn on, then I start the connection through ```
sudo ipsec up <name>
``` command, Then I am able to browse to my test site that is behind the gateway.

---

