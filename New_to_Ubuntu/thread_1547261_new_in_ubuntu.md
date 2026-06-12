---
title: "new in ubuntu"
date: 2010-08-06
forum: New to Ubuntu
---

### Post by windsor carrasco on 2010-08-06
Hi, i'm new in ubuntu and want to get some help...
I have an MSI NetOn (all in one) that has web cam, speakers, mic, SD card reader & cd/dvd rom integrated on the screen, and I had originally installed windows XP.

this week i have make decision to change mi OS to Ubuntu, I have done it but i have some troubles with all internal devices...

please i need your help to config my pc asap 

thanks for your promply reply

Windsor
Bolivia

---

### Post by Zorgoth on 2010-08-06
Please post the hardware specs.

And I understand you might have a lot of problems, but please do post what they are so we can help you.

Welcome to Ubuntu!

---

### Post by windsor carrasco on 2010-08-06
[LEFT]Sistema Operativo[/LEFT]
 [LEFT]Windows® XP Home [Original]("javascript:ShowToolTip()")[/LEFT]
   [LEFT]Tipo de soporte al inicio[/LEFT]
 [LEFT]Procesador Intel® Atom N270 [/LEFT]
   [LEFT]Chipset[/LEFT]
 [LEFT]Intel®945GSE+ICH7-M[/LEFT]
   [LEFT]LCD[/LEFT]
 [LEFT]Pantalla LCD 18.5" WXGA 16:9[/LEFT]
   [LEFT]VGA[/LEFT]
 [LEFT]Controlador[/LEFT]
 [LEFT]Intel® GMA950 [/LEFT]
   [LEFT]VRAM[/LEFT]
 [LEFT]Memoria compartida de hasta 228MB[/LEFT]
   [LEFT]Memoria[/LEFT]
 [LEFT]Tipo[/LEFT]
 [LEFT]DDR2 533, 1GB (por Módulo solamente)[/LEFT]
   [LEFT]Config[/LEFT]
 [LEFT]DDR2 SO-DIMM x 1 slot[/LEFT]
   [LEFT]Máxima[/LEFT]
 [LEFT]2GB ( 2048MB x 1 )[/LEFT]
   [LEFT]Audio[/LEFT]
 [LEFT]Parlantes[/LEFT]
 [LEFT]Audio de alta definición (HD), 2 parlantes[/LEFT]
   [LEFT]Webcam[/LEFT]
 [LEFT]Webcam de 1.3 Megapíxeles[/LEFT]
   [LEFT]Comunicaciones[/LEFT]
 [LEFT]LAN[/LEFT]
 [LEFT]10/100/1000 M LAN[/LEFT]
   [LEFT] LAN Inalámbrica[/LEFT]
 [LEFT]802.11 b/g[/LEFT]
   [LEFT]Conectores[/LEFT]
 [LEFT]Lector de Tarjeta[/LEFT]
 [LEFT]4-en-1(Soporta SD,MMC,MS,XD)[/LEFT]
   [LEFT]Entrada Mic / Salida Auriculares[/LEFT]
 [LEFT]1 / 1[/LEFT]
   [LEFT]USB 2.0[/LEFT]
 [LEFT]4[/LEFT]
   [LEFT]RJ11 / RJ45[/LEFT]
 [LEFT]0 / 1[/LEFT]
   [LEFT]Almacenamiento[/LEFT]
 [LEFT] Disco Duro[/LEFT]
 [LEFT]160 GB (2.5" SATA)[/LEFT]
   [LEFT]Drive Optico[/LEFT]
 [LEFT]DVD Super-Multi[/LEFT]
   [LEFT]Alimentación[/LEFT]
 [LEFT]Adaptador AC [/LEFT]
 [LEFT]65W[/LEFT]
   [LEFT]Características Físicas[/LEFT]
 [LEFT]Dimensiones[/LEFT]
 [LEFT]550 x 420 x 35mm[/LEFT]
   [LEFT]Peso del Sistema Completo[/LEFT]

---

### Post by Zorgoth on 2010-08-06
I don't see anything that obviously *shouldn't* work in there.

What are your main problems?

Sound?  Video card?  Webcam?  Microphone?

In the vase of sound problems run the command "alsamixer" in the terminal (you get a terminal my going to Applications > Accessories > Terminal) and make sure all the options are unmuted (toggle mute with m) and at full volume, particularly PCM and Mic, etc.

---

### Post by windsor carrasco on 2010-08-06
cd/dvd is not working on permission at properties it shows "permisions not allowed"

MIC does not work 

WEB CAM at Emphaty dont work so i cant use it to video calls

ill check now

---

### Post by Zorgoth on 2010-08-06
Is your version of Ubuntu 10.04?

---

### Post by windsor carrasco on 2010-08-06
my friend I have wirte "alsamixer" at Terminal but it does not run 

how can i restore my system to a past date?

---

### Post by windsor carrasco on 2010-08-06
yes it is 10.04

---

### Post by _h_ on 2010-08-06
> **windsor carrasco said:**
> MIC does not work

Ubuntu has input devices disabled/muted by default.

Left click Sound Icon -> Sound Preferences -> Input tab. Uncheck Mute, move volume slider all way to the right or wherever you feel it needed.

---

### Post by windsor carrasco on 2010-08-06
_h_

I have done that but also it doesn't has any hardware recognized

---

### Post by windsor carrasco on 2010-08-06
friends i have this error msg

W: Duplicate sources.list entry [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_lucid_partner_binary-i386_Packages)


what means????

---

### Post by _h_ on 2010-08-06
> **windsor carrasco said:**
> _h_

I have done that but also it doesn't has any hardware recognized

Are you using a built-in microphone on like a laptop, or a headset type of mic?

---

### Post by windsor carrasco on 2010-08-06
built-in

my pc has all integrated at screen

---

### Post by corrytonapple on 2010-08-06
> **windsor carrasco said:**
> cd/dvd is not working on permission at properties it shows "permisions not allowed"

MIC does not work 

WEB CAM at Emphaty dont work so i cant use it to video calls

ill check now
Is the webcam and microphone built in? Please take a screenshot of your error by going to **Applications>Accessories>Take Screenshot.** We only need to see the error window.
Too slow, aren't I H?

---

### Post by windsor carrasco on 2010-08-06
[IMG]file:///home/windsor/Escritorio/Pantallazo.png[/IMG]

---

### Post by corrytonapple on 2010-08-06
Um, where is th error? Bring the Window to the front by clicking on it, then in the Screenshot application, select "Grab the Current Window", clicking on the error window.

---

