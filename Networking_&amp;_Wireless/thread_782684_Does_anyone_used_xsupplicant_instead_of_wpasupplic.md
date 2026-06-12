---
title: "Does anyone used xsupplicant instead of wpasupplicant in gusty"
date: 2008-05-05
forum: Networking &amp; Wireless
---

### Post by jreubens on 2008-05-05
I am writing my thesis where i have to set up my own radius server. So far i succeeded in setting up the server and the access point. the network manager showed my network "testnet" when i tired to connect it works prefect.

but for my project i have to ( i have to... really really have to) use xsupplicant, but i couldnt able to configure, i guess i cannot run both wpa_supplicant and xsupplicant at teh same time... so i tired to add an entyr for wlan0 in my /etc/network/interfaces.

my entry is this 
auto wlan0
iface wlan0 inet dhcp

and my xsupplicant config file looks like the following
network_list = all
default_netname = testnet
roaming = xsupplicant // i dont if i can add this line or not but other the xsupplicant no valid network data or segmentation fault
use_eap_hints = yes
association = auto
default_interface = wlan0
allmulti = no
testnet
{ 
type = wireless
wireless_control = yes
allow_types = eap_peap
force_eapol_ver = 1
identity = anonymous
wpa_pairwise_cipher = tkip
wpa_group_cipher = tkip
 eap-peap {
      inner_id = testuser
      root_cert = /etc/xsupplicant/certs/cacert.pem
      chunk_size = 1398
      random_file = /dev/urandom 
      session_resume = yes
      eap-mschapv2 {
        username = testuser
        password = "password"
      }
  }
}

i cannot associate with my access point, i dont know i am really really depressed, i ahve finish it by this week. Can any one help me or point me in right direction. i searched the web for 2 weeks, everybody suggested to use wpasupplicant but my thesis requires to use xsupplicant. Plz helps this poor girl :-(

/jreubens

---

### Post by kevdog on 2008-05-05
Couldn't find any docs on the xsupplicant website -- Makes you wonder?

---

### Post by jreubens on 2008-05-05
there are lot of how to but all of them are out of date. i am using ubuntu gusty. network manager works fine.... the problem is i am asked to use xsupplicant not wpasupplicant. network manager use wpa_supplicant this is the problem in my case. There are lot of threads and lot of information for setting up network manager and wpa supplicant but not xsupplicant. :-(

i even posted my question to open1x mailing list, no answer so far... i am really really frustrated.

/jreubens

---

### Post by kevdog on 2008-05-05
Obviously a sign of a poorly maintained, poorly documented project.  Sorry I couldn't be of much help.

---

