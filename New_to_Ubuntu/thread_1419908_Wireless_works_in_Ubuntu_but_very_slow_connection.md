---
title: "Wireless works in Ubuntu but very slow connection"
date: 2010-03-02
forum: New to Ubuntu
---

### Post by psam3 on 2010-03-02
I installed Ubuntu on one of my computers and it seems the wireless card installed fine, it asked me for the password and stuff and says it's connected, but seems to drag very slowly. The connection strength seems to go up and down between two and three bars. It can't be the internet connection, I have 10Mbps download speed. It also worked very fast when Windows was installed. The connection is also working as usual on this wired connection. Anybody have any idea what could be causing this? 

Thanks

---

### Post by Arijit_Kundu on 2010-03-02
can you say which driver you are using? some driver are not still up to the mark (for example, some broadcom driver).

---

### Post by psam3 on 2010-03-02
Well, I know that it's a Netgear wireless card. Is there a way to find the specific driver I'm using?

---

### Post by Arijit_Kundu on 2010-03-02
can you run iwconfig in a terminal and post the output?

---

### Post by Idaho Dan on 2010-03-02
Also, what shows up when you go to System, Administration, Hardware Drivers?

---

### Post by psam3 on 2010-03-02
This is iwconfig

```
eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"115634825"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:22:3F:33:78:AA   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=60/100  Signal level:-41 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.
```

When I go into Hardware drivers, the only thing that comes up is an ATI display driver.

---

### Post by Arijit_Kundu on 2010-03-02
the problem is your settings limit the speed to 1 mb/ps ( Bit Rate=1 Mb/s)

run the following in a terminal, this will probably solve the problem after a reboot:

sudo iwconfig wlan0 rate 54M

---

### Post by psam3 on 2010-03-02
> **Arijit_Kundu said:**
> the problem is your settings limit the speed to 1 mb/ps ( Bit Rate=1 Mb/s)

run the following in a terminal, this will probably solve the problem after a reboot:

sudo iwconfig wlan0 rate 54M

Thanks, I ran this and restarted then ran iwconfig to confirm that it has changed. It has, but it still won't load web pages for some reason. I wonder if for some reason it's getting a weak connection? It says it's only at 40%, which seems weird, because it was almost full in Windows.

---

### Post by Arijit_Kundu on 2010-03-02
After searching a bit in the net, I found that, there are indeed problems with Netgear wireless card. I dont know whether you are suffering for the same. A **serial monkey** driver can make it better. Check it
[http://ubuntuforums.org/showthread.php?t=766724]("http://ubuntuforums.org/showthread.php?t=766724")

---

### Post by psam3 on 2010-03-02
> **Arijit_Kundu said:**
> After searching a bit in the net, I found that, there are indeed problems with Netgear wireless card. I dont know whether you are suffering for the same. A **serial monkey** driver can make it better. Check it
[http://ubuntuforums.org/showthread.php?t=766724]("http://ubuntuforums.org/showthread.php?t=766724")

Thanks! :D

---

### Post by Arijit_Kundu on 2010-03-02
as this thread suggests, you may first try to use wicd instead og gnome networm manager.

But reinstall network-manager-gnome (search through synaptic), so that, in case wicd wont work, you can get back to this.

---

