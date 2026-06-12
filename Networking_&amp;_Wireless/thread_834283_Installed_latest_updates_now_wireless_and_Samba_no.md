---
title: "Installed latest updates now wireless and Samba not working"
date: 2008-06-19
forum: Networking &amp; Wireless
---

### Post by ians1 on 2008-06-19
I had wireless connectivity and visibility of Samba over a windows network now the wireless does not work and Samba seems not to be running.

Its only  happened since recent updates were installed (about 40 I think 86Mb)

Its hardy heron 8.04

If I ping 192.168.0.20 (the netgear wireless router) I get 

```
From 169.254.7.12 icmp_seq=1 Destination Host Unreachable
```

and so on

ian

---

### Post by Sam324 on 2008-06-19
I totally agree.  It happened to me, too.:(

---

### Post by superprash2003 on 2008-06-19
please post your iwconfig output

---

### Post by jhmiller42 on 2008-06-19
Same here. Wireless networking on my laptop under 8.04 is borked following the 6.18.08 updates.

The network config applet works on it for awhile, then asks for the network key (which until the update had been stored), and then fails to connect when I enter the key. After two or three shots at entering the key, the wireless connection shuts down. I'm sure there's a better way of saying that, but that's what it does -- the network applet shows no available wireless networks, even when several are available. At this point I have to reboot to so much as try to connect. Needless to say, this makes trial and error a bit annoying.

This happens on two different networks, one WPA and one WEP. Also, FWIW I don't think it's kernel-related as the problem is the same whether I boot into the new 2.6.24-19 or the older 2.6.24-18 (which worked perfectly prior to the updates).

---

### Post by ians1 on 2008-06-19
I got the wireless working by reseting the WPA password/key, but I dont think that is the problem for Sam324.

```
ians@ians-unix:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"NETGEAR"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:18:4D:AD:DF:28   
          Bit Rate=54 Mb/s   Tx-Power:20 dBm   Sensitivity=-121 dBm  
          RTS thr=2347 B   Fragment thr=2346 B   
          Power Management:off
          Link Quality:84/100  Signal level:-42 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

ians@ians-unix:~$ 
```

looks fairly normal now.

However, Samba seems to not be running and I am not sure how to check that.  The network share I had is not visible from other PCs on the network, even though I know its working as there is Internet connectivity from the unbuntu box (as well as VNC which is how I got the iwconfig dump).

ian

---

### Post by jetsam on 2008-06-19
> Samba seems to not be running and I am not sure how to check that.

Try ```
sudo /etc/init.d/samba restart
```
then 
```
pgrep -l mbd
```
The pgrep command should output three or more processes like this (different numbers) if Samba is running:
```
5182 nmbd
5188 smbd
5205 smbd

```
Samba maybe just wasn't able to cope with the wireless issues.

---

### Post by ians1 on 2008-06-19
Yes the result is

```
4586 nmbd
4588 smbd
4643 smbd

```

but I had to remove the previously created share and add it again before it was visible on the Windows network.

I still have permission issues with the Samba share which I have raised in another thread, but basically I am back were I was 2 days ago before the update screwed things up.

ian

---

### Post by jetsam on 2008-06-19
> I had to remove the previously created share and add it again before it was visible on the Windows network.
That's... odd.  
...But so is Samba sometimes. :-k 

I posted in what I figured was your other [thread]("http://ubuntuforums.org/showthread.php?t=831621") about the permission issues.

---

