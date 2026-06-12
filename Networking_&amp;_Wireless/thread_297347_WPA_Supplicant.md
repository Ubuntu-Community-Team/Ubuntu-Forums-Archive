---
title: "WPA Supplicant"
date: 2006-11-11
forum: Networking &amp; Wireless
---

### Post by opensourcerocks on 2006-11-11
Hi, I was wondering if I could get some help setting up the WPA Supplicant. I am running Kubuntu 6.06 with a Successful Ndiswrapper driver. I also have the WPA Supplicant installed. Although I have no idea how to configure it. I really just need to know what to type in after this is installed. 

I am still a newbie when it comes to non graphical data entry but some how I was able to figure out how to put in the NDiswrapper successfully.

Any Help would be much appreciated
Thanks

---

### Post by FaBi3ttO on 2006-11-11
Well, it's a little bit difficult to help you without knowing what are looking for.
I mean, what kind of connection are you trying to estabilish?
Post all the details, read the wpa_supplicant manpage and tell us where do you encounter some problem ;) 


Fabio

---

### Post by opensourcerocks on 2006-11-11
Hi, 
I am just trying to establish a connection to my router. It worked in SUSE 10.0 but the OS ran to slow for the computer. Also I am using a WUSB54Gv2 as well. I think that I mainly need help with setting up the configuration file. 

I don't know if this is what I typed in or not, but it was probably something like this:

wpasupplicant -dndiswrapper -(?)wlan0 -c etc/wpasupplicant/(????)

The question marks are because I don't remember what I typed in. I think that everything was correct, but I somehow need to back out of my home folder to get to main directory. I just don't know how to do this though. I tried the DOS way and the HTML way but no luck. 

So maybe if someone showed me what exactly to type in to create the config file, I might just be good. 

Also if this helps any, here are the settings on my linksys router:

WPA shared key 
Tikp or Tipk? 
ESSID: Wireless Network
IP: 192.168.1.1 

Thanks for any assistance you can provide

---

### Post by FaBi3ttO on 2006-11-11
So you have ndiswrapper properly set up right?
Well try this commands and tell me what's happen:
```
iwconfig wlan0 essid Wireless Network
```
This way you set the essid of your network (assuming wlan0 as your wireless interface).

then edit your /etc/wpa_supplicant/wpa_supplicant.conf as root:
Are you sure of using TKIP? If so you have to use a certificate and a little more complexity is added. I'll write you the example configuration for a WPA-PSK connection
```
 
ctrl_interface=/var/run/wpa_supplicant
eapol_version=1
ap_scan=1 
fast_reauth=1
network={
ssid="Wireless Network" #insert here your ssid
scan_ssid=1
proto=WPA
key_mgmt=WPA-PSK
psk="your psk password"
}
```

Then you must try this command:
```
sudo wpa_supplicant -B -i wlan0 -c /etc/wpa_supplicant/wpa_supplicant.conf -D wext -dd

```
and see what happen. If there are no errors type:
```
sudo wpa_cli 
```
This command opens a little interactive shell to see if the authentication has succeeded.
Use the command "status" to see how's going with the authentication and then "quit" to exit.

Hope it helps,


Fabio Pozzi

---

### Post by opensourcerocks on 2006-11-11
Thanks for the Help FaBi3ttO, it will help me greatly in the next step when I get back to the office on Tuesday. :) 

Although you mentioned this:

> then edit your /etc/wpa_supplicant/wpa_supplicant.conf

This is a trouble part for me. I don't appear to have this file when I browse for it graphically and I am not too sure how to create it using the terminal. :-k  I guess this is kind of a newbie question, sorry. :( 
 
But thanks again FaBi3ttO I know that it will help me in the next step :-D

---

### Post by opensourcerocks on 2006-11-12
Sorry, maybe I am not being to clear here. :(  I was just wondering how do you edit and create your "/etc/wpa_supplicant/wpa_supplicant.conf"? 

But thanks again FaBi3ttO for help
It is much appreciated :D

---

### Post by FaBi3ttO on 2006-11-13
Take the terminal and type:
```
sudo nano -w /etc/wpa_supplicant/wpa_supplicant.conf
```

And write there your configuration. At the end press Ctrl + O to save the file and then exit with Ctrl + x. Nano is a good and easy text editor to use, I find it more easy than Vi, even is less powerful.


Fabio Pozzi

---

### Post by serlex on 2006-11-14
I'm having a similar problem, my university recomends
```
network={
        ssid="FreedomNetv2"
        mode=0
        proto=WPA
        key_mgmt=WPA-EAP
        eap=TTLS
        pairwise=TKIP
        group=TKIP
        identity="ece99999"
        password="yourpassword"
        ca_cert="/opt/UOP-b64.cer"
        phase2="auth=PAP"
        priority=2
} 
```

but when i type 
```

# wpa_supplicant -i eth1 -c /etc/wpa_supplicant.conf -D wext -ddd

```

output is alot of error messages. 

I can see the wireless connection in network-manager but can not connect to it! can someone tell me if its to do with wpa_supplicant or my wireless-card drivers?

---

### Post by FaBi3ttO on 2006-11-15
I don't know how is the certificate you get from your university.
Mine is in the .p12 format so I have to digit 
```
openssl pkcs12 -in Certificato.p12 -out /etc/wpa_supplicant/certificati/cert.pem
```
to convert that certificate in the .pem format, which is accepted by wpa_supplicant.
Hope it helps



Fabio Pozzi

---

### Post by serlex on 2006-11-15
been told to use
```
openssl x509 -out UOP-b64.cer -inform DER -outform PEM < UOP.cer 
```

is that accepted by wpa_supplicant?

there is no specific folder for certificates is there?

---

### Post by opensourcerocks on 2006-11-15
Thanks FaBi3ttO! :-D :-D :-D 
Your the Best!:KS  I now finally got it to work, with your help!

Thanks so Much!:-D :D

---

### Post by FaBi3ttO on 2006-11-17
Well I think it's supported by WPA supplicant.
There isn't a fixed directory to put your certificates, you can put them anywhere, in fact in the wpa_supplicant.conf file you tell the daemon where your certificate is, so the problem is resolved :mrgreen: 


Fabio Pozzi

---

