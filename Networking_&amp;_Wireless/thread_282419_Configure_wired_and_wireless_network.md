---
title: "Configure wired and wireless network"
date: 2006-10-22
forum: Networking &amp; Wireless
---

### Post by TrD on 2006-10-22
Hi

Im trying to configure a home network but Im having some trouble.

I have one ubuntu pc with 2 ethernet cards eth0 and eth1. eth0 connects to a wired router, eth1 connects to a winxp computer through a crossover cable. Both eth0 and eth1 are bridged (br0) 

Recently Ive bought a laptop with a wireless card and I want to add it to the network, so I also bought an asus WL-167g usb WLAN adapter for the ubuntu machine.

Now I can share folders between the laptop and the ubuntu pc but I cant share internet because the laptop cant see the router (connected to eth0).

Is there a way to add the asus device to the bridge (br0) so that I can share internet with my laptop?

Sorry if it sounds confusing. Hope someone can help me.

---

### Post by TrD on 2006-10-23
Anyone?

---

### Post by AAM on 2006-10-23
Am I right in understanding that you want to connect the laptop via USB access point to a wireless router?

---

### Post by TrD on 2006-10-23
No, I dont have a wireless router, only a wired one.
I want to connect the laptop via a usb acess point to this router wich is connected to br0.

Ive managed to do this in XP but I prefer ubuntu.

---

### Post by dbott67 on 2006-10-23
Have you checked out this thread?
[http://ubuntuforums.org/showthread.php?t=91370](http://ubuntuforums.org/showthread.php?t=91370)

There are a few different threads in the forums on "internet connection sharing" --- the common element seems to be using dnsmasq & iptables (other ideas include using ipkungfu, which seems to be the easiest way [http://freshmeat.net/projects/ipkungfu/](http://freshmeat.net/projects/ipkungfu/))

-Dave

---

### Post by TrD on 2006-11-03
Hello again

I have successfully configured ipkungfu to share internet with my wired computer, but my wireless laptop refuses to connect. 

I have installed the correct drivers for my usb pen (asus wl-167g) on the computer who is acting as router.

Here is my ifconfig:
```
eth0       Encapsulamento do Link: Ethernet  Endereço de HW 00:0B:6A:35:6D:E8
          inet end.: 192.168.1.2  Bcast:192.168.1.255  Masc:255.255.255.0
          endereço inet6: fe80::20b:6aff:fe35:6de8/64 Escopo:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Métrica:1
          pacotes RX:7412 erros:0 descartados:0 excesso:0 quadro:0
          Pacotes TX:3248 erros:0 descartados:0 excesso:0 portadora:0
          colisões:0 txqueuelen:1000
          RX bytes:2003742 (1.9 MiB) TX bytes:398963 (389.6 KiB)
          IRQ:201 Endereço de E/S:0xd400

eth1       Encapsulamento do Link: Ethernet  Endereço de HW 00:02:44:AB:DC:87
          inet end.: 192.168.0.2  Bcast:192.168.0.255  Masc:255.255.255.0
          endereço inet6: fe80::202:44ff:feab:dc87/64 Escopo:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Métrica:1
          pacotes RX:392 erros:0 descartados:0 excesso:0 quadro:0
          Pacotes TX:748 erros:0 descartados:0 excesso:0 portadora:0
          colisões:0 txqueuelen:1000
          RX bytes:40273 (39.3 KiB) TX bytes:194679 (190.1 KiB)
          IRQ:209 Endereço de E/S:0xd000

lo         Encapsulamento do Link: Loopback Local
          inet end.: 127.0.0.1  Masc:255.0.0.0
          endereço inet6: ::1/128 Escopo:Máquina
          UP LOOPBACK RUNNING  MTU:16436  Métrica:1
          pacotes RX:28 erros:0 descartados:0 excesso:0 quadro:0
          Pacotes TX:28 erros:0 descartados:0 excesso:0 portadora:0
          colisões:0 txqueuelen:0
          RX bytes:2452 (2.3 KiB) TX bytes:2452 (2.3 KiB)

rausb0     Encapsulamento do Link: Ethernet  Endereço de HW 00:17:31:C7:92:8B
          inet end.: 192.168.0.3  Bcast:192.168.0.255  Masc:255.255.255.0
          endereço inet6: fe80::217:31ff:fec7:928b/64 Escopo:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Métrica:1
          pacotes RX:0 erros:0 descartados:0 excesso:0 quadro:0
          Pacotes TX:85 erros:0 descartados:0 excesso:0 portadora:0
          colisões:0 txqueuelen:1000
          RX bytes:1040714 (1016.3 KiB) TX bytes:20672 (20.1 KiB)

```

and here is my iwconfig:
```
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.

rausb0    RT2500USB WLAN  ESSID:"casa-portatil"
          Mode:Ad-Hoc  Frequency=2.412 GHz  Cell: DE:E3:E3:CB:F4:FB
          Bit Rate=11 Mb/s
          RTS thr:off   Fragment thr:off
          Link Quality=63/100  Signal level:-79 dBm  Noise level:-206 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

```

Can someone give a hand here?

P.S.
Dave, thanks for letting me know about ipkungfu.

---

