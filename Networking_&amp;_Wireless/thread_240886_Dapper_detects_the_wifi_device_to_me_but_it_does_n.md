---
title: "Dapper detects the wifi device to me but it does not detect ANY network"
date: 2006-08-21
forum: Networking &amp; Wireless
---

### Post by SuckerBlood on 2006-08-21
I have a wireless device by USB of telefonica (Spanish operator), this is detected without no kind of problem by Dapper, but when it tried to connect me to a network (system/Administration/Network) did not find any network.
I have tried with wifiradar, and anything. The only thing that “has worked” has been when installing network-manager + network-manager-gnome. This put an icon in the writing-desk and “it was able” to detect my network but NEVER it got to connect itself, put my password (I believe that it is WEP of 128bits) (he is the typical one to router wireless of Telefónica) and nothing to him, that are not connected: S. When for some reason the device becomes disconnected or after reinitiating or what it is, suddenly the network-manager no longer returns to recognize it (there is nothing no connected according to him) neither to detect the more networks (logically), but (system/Administration/Network) YES it detects the apparatus, but no network (we go, like at the outset). 
[traducido by google]


Tengo un dispositivo inalambrico por USB de telefónica, este es detectado sin ningún tipo de problema por Dapper, pero cuando intentaba conectarme a una red (sistema/Administración/Red) no encontraba ninguna red. :S

He probado con wifiradar, y nada. La única cosa que ha "funcionado" ha sido al instalar el network-manager + network-manager-gnome. Esto ponía un icono en el escritorio y "conseguia" detectar mi red pero NUNCA llegaba a conectarse, le ponia mi contraseña (creo que es WEP de 128bits) (vamos, es el tipico router inalambrico de telefonica) y nada, que no se conecta :S. Cuando por alguna razón el dispositivo se desconecta o después de reiniciar o lo que sea, de pronto el network-manager ya no vuelve a reconocerlo (no hay nada conectado según él) ni a detectar más redes (lógicamente), pero el (sistema/Administración/Red) SÍ detecta el aparato, pero ninguna red (vamos, como al principio).


What can i do? :(

---

### Post by lupine_nickt on 2006-08-21
Can you connect to your wireless network if you turn WEP off (in the router, and on your computer)?

What is the output of the command:-
```

iwlist <interface name> ap

```

Where <interface name> is wlan0, ath0, eth1, rausb0, ra0, or similar.

Also, is your router set to "broadcast" the SSID? (it should be)

--

¿Puede conectar usted a su red radiofónica si usted apaga WEP (en el rúter, y en su computadora)? 

Qué es la producción de la orden:-

```

iwlist <comunique el nombre> ap

```

Dónde <comunique el nombre> Es wlan0, ath0, eth1, rausb0, ra0, o semejante.

¿También, es su conjunto de rúter para "transmitir" el SSID? (debe ser)

---

### Post by SuckerBlood on 2006-08-21
```
$ iwlist eth1 ap
eth1      Interface doesn't have a list of Peers/Access-Points
```

Also, is your router set to "broadcast" the SSID? (it should be).
My router it has activated that option. When “the detection of networks worked”, my network was seen (redblood).

Can you connect to your wireless network if you turn WEP off (in the router, and on your computer)?
The same, i cant see my network (redblood).

---

### Post by SuckerBlood on 2006-08-22
...please?:frown:

edit:

pleasy... any help?

---

### Post by SuckerBlood on 2006-08-23
jur... ahh!! :(

---

### Post by SuckerBlood on 2006-08-28
.... please!!! ¬¬

---

### Post by Cubiq on 2006-08-28
Is your Access Point broadcasting the SSID?

---

### Post by SuckerBlood on 2006-08-28
what's acces point? is the wifi adapter?
My wifi adapter doesn't detect any networks (my SSID? (redblood))
please :)

edit:

I webconfig of my router:
[...]
ESSID: redblood
Hide ESSID: No or Yes <--- Yes ;)
[...]

It's ok, no? :S

---

### Post by Cubiq on 2006-08-29
> **SuckerBlood said:**
> what's acces point? is the wifi adapter?
My wifi adapter doesn't detect any networks (my SSID? (redblood))
please :)

edit:

I webconfig of my router:
[...]
ESSID: redblood
Hide ESSID: No or Yes <--- Yes ;)
[...]

It's ok, no? :S

The wireless access point is the function of your router that let you connect to internet wirelessly ;)

BTW, your router is not broadcasting the ESSID (it's hiding it). Try to set "Hide ESSED" to "No". It worked for me. Plus, if your router has functions such as speed burst, 108mbps, 125mbps and so on, disable all of them. Put your router to plain 54g mode.

---

### Post by SuckerBlood on 2006-08-29
i'm stupid xD
Hide ESSID: No or Yes <--- is NO, no yes, i'm stupid ](*,) 

ok... this is my actual configuration:
[[IMG]http://img169.imageshack.us/img169/3199/imagenrouterwebwifi1zi4.th.jpg[/IMG]](http://img169.imageshack.us/my.php?image=imagenrouterwebwifi1zi4.jpg)

I change something?? :-k 

tnx!

---

### Post by SuckerBlood on 2006-08-30
I think wifi adaptar's driver has the problem because the current router's config works on windows.
mmm.... the driver installed by ubuntu is the default, so... is it recomendable to change (the driver)?
if the answer is yes, witch one?

---

### Post by SuckerBlood on 2006-09-02
please... ¬¬

---

