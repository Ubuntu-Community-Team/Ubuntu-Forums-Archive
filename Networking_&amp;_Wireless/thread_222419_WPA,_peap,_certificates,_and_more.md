---
title: "WPA, peap, certificates, and more"
date: 2006-07-25
forum: Networking &amp; Wireless
---

### Post by rickst13 on 2006-07-25
Hello.  I am glad to see WPA support in Dapper.  I have been wanting to switch my laptop completely over to Ubuntu for a while now.  My college uses WPA.  I have Network-Manager, but I don't know how to configure the network in Linux.  Is there a way to do certificates, PEAP, etc?

Here are the [Windows Connection Procedures]("http://www.utdallas.edu/ir/cats/network/wlan/8021x/winxp/index.html").  I am trying to figure out how to do these same things using Ubuntu.  If Network-Manager cannot, is there another program that might help, like Wifi Radar?

Thank you very much for any help.

---

### Post by nchankov on 2006-07-25
Hello, I am also new user in non Windows world... I will tell you what I know about this.

so you shuld check if you have wpa_suplicant and wpa_passphrase under terminal. if yes then create passphrase with:

```
wpa_passphrase <ssid> <passphrase>
```
i.e.
```
wpa_passphrase accesspoint secretphrase
```

this will generate the code which you shuold put into /etc/wpa_suplicant.conf if there is no such file you should create it. this file should look like this:

```

ctrl_interface=/var/run/wpa_supplicant
network={
        ssid="accesspoint"
        #psk="secretphrase"
        psk=82bc0acdc4fab9f450f2c08ed79eb98f0cbe08680908bb51940cb128bec5dd0c
}

```

After this you should change your /etc/network/interfaces file by adding at the bottom of your wireless definition the following line:

```

wpa-conf /etc/wpa_supplicant.conf

```

the part for your interface should be something like:

```

auto eth0
iface eth0 inet dhcp
    wpa-conf /etc/wpa_supplicant.conf

```

in my case wireless is eth0 but yours probably will be on eth1, so put that wpa line under correct device.

I am not so familiar do you need restart of network only or you need complete restart, so first try with 
```

ifdown eth0
ifup eth0

```
this should do the job.

One warning: I spend a weekend to do this configuration /but not because it's difficult to make it ;)/, the final kernel doesnt working properly with WPA on my machine. It's probably because I try to play with ieee802 and ipw which I shouldnt do. Anyway, now I am working on kernel 2.6.15-25 and I am waiting for the new one - 2.6.15.27 :).

Could you try this and tell me if it's working on 2.6.15026 kernel?

Thanks

---

