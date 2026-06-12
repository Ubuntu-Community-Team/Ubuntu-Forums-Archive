---
title: "BCM94352HMB drops after sleep"
date: 2017-08-21
forum: Networking &amp; Wireless
---

### Post by kosak2 on 2017-08-21
I am a fully converted Linux user, all my laptops and custom builds run Linux. In this case, my Asus X550LDV with a Broadcom BCM94352HMB Combo BT runs smoothly. :D
But when I put it to sleep, the WiFi drops and can't connect to anything after resuming. The only solution is toggling airplane mode on and then back off. That makes it work.
Any way I could avoid this nuissance???   :confused:
Running on Ubuntu GNOME 17.04 all up to date. Regards and thanks in advance!

---

### Post by Hadaka on 2017-08-21
Hi please COPY and paste..
```
echo 'SUSPEND_MODULES="wl"' | sudo tee -a /etc/pm/config.d/config
```

*Note the full echo command in single quotes '   ' and wl in double quotes "wl"
hence the suggestion to COPY and paste.
Thanks.

---

### Post by kosak2 on 2017-08-22
Thank for the suggestion, but it doesnt work unfortunately...

I get this:
```
joe@chochiJoey:~$ echo 'SUSPEND_MODULES="wl"' | sudo tee -a /etc/pm/config.d/config
tee: /etc/pm/config.d/config: No such file or directory
SUSPEND_MODULES="wl"
```

---

### Post by Hadaka on 2017-08-22
Hi please post the output of..
```
cd /etc/pm/config.d
iwconfig
```
Thanks

---

### Post by kosak2 on 2017-08-22
```
joe@chochiJoey:~$ cd /etc/pm/config.d
bash: cd: /etc/pm/config.d: No such file or directory
joe@chochiJoey:~$ cd /etc/pm/
joe@chochiJoey:/etc/pm$ ls
sleep.d
```



```
joe@chochiJoey:/etc/pm$ iwconfig
wlp3s0    IEEE 802.11  ESSID:"Casa_Falesia"  
          Mode:Managed  Frequency:2.472 GHz  Access Point: C0:AC:54:F6:3A:66   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          
lo        no wireless extensions.


enp2s0f1  no wireless extensions.
```
  

Thanks in advance for replying ! :KS

---

### Post by Hadaka on 2017-08-22
Hi please open a terminal then copy and paste..
```
sudo sed -i 's/3/2/' /etc/NetworkManager/conf.d/*
```
Boot and then verify the above command turned Power Management. off
```
iwconfig
```
*If..yes/off then test sleep/suspend.
report your findings please.
Thanks

---

### Post by kosak2 on 2017-08-24
Worked like a charm! It works 4/4 times, so I think your tip resolved the issue 100%

```
joe@chochiJoey:~$ sudo iwconfig
wlp3s0    IEEE 802.11  ESSID:"Casa_Falesia"  
          Mode:Managed  Frequency:2.472 GHz  Access Point: C0:AC:54:F6:3A:66   
          Bit Rate=144 Mb/s   Tx-Power=200 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=70/70  Signal level=-37 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


lo        no wireless extensions.


enp2s0f1  no wireless extensions.
```

Thanks so much

---

### Post by Hadaka on 2017-08-24
Glad that worked for you !
 Please take the time to mark your thread Solved by logging in
to your thread and clicking **Thread Tools** [upper right area] then
click **Solved**.
Thanks.

---

### Post by kosak2 on 2017-08-25
It is still happening but less often, so I will mark as solved! Thanks for the persistence in helping! Best Regards

---

