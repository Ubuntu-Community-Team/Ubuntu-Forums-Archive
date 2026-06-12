---
title: "Peap, and ip address problem"
date: 2007-08-31
forum: Networking &amp; Wireless
---

### Post by Ffuzzdaddy on 2007-08-31
i am trying to connect to the campus network, i am running fiesty.

my campus is using wpa, and peap. i am able to connect to the old network which is wep, thrugh network manager. but because network manager doesnt have wpa, i chose to go with WICD as my network manager. the proble im having is i type in the password and username into wicd and it keeps getting hanging up on obtaining ip address. i have used wicd to get on unsecure networks so i know it works. i just dont know why it wont work on a secured network. any help would be great.

---

### Post by Ffuzzdaddy on 2007-09-03
bump?

---

### Post by Ffuzzdaddy on 2007-09-05
i got the wep working in wicd by using the wext driver. but i still cant get it to work with wpa. i have tried all the drivers. i am using a intel pro/wireless 3945 with restricted drivers. i really need to get this problem fixed soon, because they are getting rid of the wep network. so any help would be greatly appreciated.

---

### Post by KCPokes on 2007-09-05
Have you installed the WPA supplicant?

```

sudo apt-get install wpa-supplicant

```

---

### Post by Ffuzzdaddy on 2007-09-05
i tried that and i get an error message

E: Couldn't find package wpa-supplicant

---

### Post by KCPokes on 2007-09-05
Sorry about that, I'm not in front of my machine right now, thus I'm doing it purely from memory.  Try:

```

sudo apt-get install wpasupplicant

```

If that's not right, I apologize and hopefully someone else will come up with the right package name.

---

### Post by Ffuzzdaddy on 2007-09-05
ok it looks like it worked, what do i do after that, and thanks for your help.

---

### Post by Ffuzzdaddy on 2007-09-07
i got the wpa supplicant but i don't know what to do from here, i try connecting to the wpa network and it still freezes on obtaining ip address.

an help would be greatly appreciated because there closing the wep network this weekend.

---

### Post by wirelessmonkey on 2007-09-07
my wpa_supplicant.conf file, on our network which uses WPA and PEAP:

ctrl_interface=/var/run/wpa_supplicant
network={
        ssid="uconnect.utah.edu"
        scan_ssid=1
        proto=WPA
        key_mgmt=WPA-EAP
        pairwise=TKIP
        eap=PEAP
        identity="u01234567"
        password="password"
        phase2="auth=MSCHAPV2"
}


Please click the link for WPA/PEAP in my signature if you need more help.

---

### Post by Ffuzzdaddy on 2007-09-07
i tried the link but i cant find anything on the website for how to get to edit the wpa_supplicant.conf file. i am supposed to use PEAP with GTC to connect to the network, so i don't know if that makes a difference in what i have to type out.

---

